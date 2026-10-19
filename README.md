# Stripe Payments Sandbox Integration & Testing Suite

A hands-on API testing portfolio project demonstrating core payment gateway workflows, transaction validation, refund handling, and idempotency using Postman and the Stripe API.

## 🚀 Key Workflows Covered & Scenario Breakdown

### 1. Customer Profile Verification (`GET /v1/customers`)
* **Objective:** Retrieve and validate customer entities in the sandbox environment.
* **Business Value:** Ensures proper customer record association prior to initiating payment processing.

### 2. Payment Creation & Confirmation (`POST /v1/payment_intents`)
* **Objective:** Simulate a successful customer checkout flow.
* **Implementation:** Used test credit cards (`pm_card_visa`) with automatic payment methods enabled and redirect constraints set to `never` for seamless headless execution.
* **Business Value:** Smooths the authorization process and captures funds reliably in a test environment.

### 3. Transaction Retrieval & Reconciliation (`GET /v1/payment_intents/{id}`)
* **Objective:** Check payment status from the merchant's backend perspective.
* **Implementation:** Queried the specific payment intent ID generated during creation.
* **Business Value:** Critical for order fulfillment verification—ensuring goods or services are only released after the status shifts to `succeeded`.

### 4. Refund Processing (`POST /v1/refunds`)
* **Objective:** Handle customer cancellations and charge reversals.
* **Implementation:** Issued a full refund linked directly to the transaction's payment intent ID.
* **Business Value:** Automates post-sale lifecycle management safely without manual merchant intervention.

### 5. Idempotency & Fault Tolerance (`Idempotency-Key` Header)
* **Objective:** Prevent duplicate charges during unstable network conditions.
* **Implementation:** Injected an `Idempotency-Key` header (`test-order-999`) across retries.
* **Business Value:** Protects users from accidental double-charging when network timeouts cause duplicate API requests.

## 📂 Repository Contents
* `postman/Stripe-Payments-Sandbox.postman_collection.json`: The complete, importable Postman collection containing all test scenarios.

## 🛠️ How to Use
1. Download the JSON collection file from the `postman/` folder.
2. Import it into [Postman](https://www.postman.com/).
3. Create an environment variable for `stripe_secret_key` using your Stripe test secret key to run and test the workflows.

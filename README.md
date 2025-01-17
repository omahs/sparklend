# Spark Lend

This is the respository for Spark Lend deploy scripts and custom code. Primarily this repository acts as an orchestration toolkit for deploying and managing Spark Lend instances across many chains. Apart from the custom code below everything is combined from third party vendors.

## Usage

Run tests: `make test`  
Deploy Spark Lend: `ETH_RPC_URL=<YOUR RPC ENDPOINT> make deploy`  
Deploy Config Engine: `ETH_RPC_URL=<YOUR RPC ENDPOINT> make deploy-engine`  
Deploy Spark Lend (Custom Instance): `INSTANCE_ID=<Custom Instance Name> ETH_RPC_URL=<YOUR RPC ENDPOINT> make deploy`  
Deploy Config Engine (Custom Instance): `INSTANCE_ID=<Custom Instance Name> ETH_RPC_URL=<YOUR RPC ENDPOINT> make deploy-engine`  

## Custom Code

### DaiInterestRateStrategy

A special interest rate strategy is used for the DAI market which anchors to the Dai Savings Rate (DSR). It is a flat rate up to the debt ceiling. If Maker needs to bring back liquidity by lowering the debt ceiling then the interest rate will spike to ensure user deposits and borrow repayments.

You can read more about this [here](https://forum.makerdao.com/t/mip116-d3m-to-spark-lend/19732#mip116c3-debt-ceiling-fee-structure-10).

### SavingsDaiOracle

This is the oracle for sDAI which will take the input of a standard DAI price feed and convert it via the `pot.chi` factor.

### SparkMigrationHelper

Fork of the AaveMigrationHelper which has some extra features like converting from USDC to DAI automatically.

## Plug and Play License

This code is open source, but use within a Maker SubDAO requires a 15% revenue share of all income generated by the usage of code inside this repository to the Ethereum address labelled by the ENS domain of sparkprotocol.eth. This Plug and Play revenue share license expires on January 1st, 2026 at 00:00 UTC.

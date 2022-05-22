# Ray Dex Subgraphs

Subgraph for Ray Dex on PulseChain.

### Setup

```
# Install dependencies (yarn or npm)
$ yarn or npm install

# Generate types constants
$ yarn or npm run codegen

# build subgraph
$ yarn or npm run build

# create local subgraph
$ yarn or npm run create-local

# deploy local subgraph
$ yarn or npm run deploy-local

```

### (README)

Deliver analytics & historical data for Ray Dex.
The Graph exposes a GraphQL endpoint to query the events and entities within the RayDex ecosytem.

## Example

Query 1h candles (3600 seconds) for first week of 2021: `2020-01-01` (1609459200) - `2020-01-07` (1609977600):

```graphql
{
  candles(where: { period: 3600, time_in: [1609459200, 1609977600] }) {
    id
    time
    open
    close
    low
    high
    token0TotalAmount
    token1TotalAmount
  }
}
```

## Schema

```graphql
type Candle @entity {
  id: ID! # time + period + srcToken + dstToken
  time: Int!
  period: Int!
  token0TotalAmount: BigInt!
  token1TotalAmount: BigInt!
  open: BigDecimal!
  close: BigDecimal!
  low: BigDecimal!
  high: BigDecimal!
}
```

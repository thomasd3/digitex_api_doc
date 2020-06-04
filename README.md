# DIGITEX Futures API Draft

## Market Data API

Every response has the following structure in case of success. Field `data` could be either an object or an array.

```json
{
  "status": "ok",
  "data": {}
}
```

And in case of error response would be like:

```json
{
  "status": "error",
  "code": 2222,
  "msg": "error description"
}
```

### Endpoints

#### Public - Contracts

**HTTP Request**

`GET /api/v1/public/contracts`

**Response**

```json
{
    "status":"ok",
    "ts":1590404891291,
    "data":[
        {
            "id":1,
            "name":"BTC/USD-PERP",
            "symbol":"BTCUSD-PERP",
            "type":"perpetual_futures",
            "tradable":true,
            "baseCurrency":"BTC",
            "quoteCurrency":"USD",
            "pnlCurrency":"DGTX",
            "marginCurrency":"DGTX",
            "lotSize":1,
            "tickPrice":1,
            "isQuanto":true,
            "isInverse":false,
            "underlyingAsset":"token",
            "indexSymbol":".DGTXBTCUSD",
            "premiumIndexSymbol":"",
            "fundingRate":0.0003,
            "fundingPeriod":28800,
            "indicativeFundingRate":0,
            "markType":"fair_price",
            "initMargin":0,
            "maintMargin":0,
            "deleverage":false,
            "isLeverage": true,
            "maxLeverage": 20,
            "createTime":0,
            "listingTime":0,
            "expiryTime":0,
            "settleTime":0,
            "makerFee":0,
            "takerFee":0,
            "settlementFee":0,
            "insuranceFee":0,
            "minPrice":0,
            "maxPrice":0
        }
    ]
}
```

------

#### Public - Assets

**HTTP Request**

`GET /api/v1/public/assets`

**Response**

```json
{
   "status":"ok",
   "ts":1590428686166,
   "data":[
      {
         "id":2,
         "name":"Bitcoin",
         "symbol":"BTC",
         "type":"coin",
         "precision":8,
         "hasDeposit":false,
         "hasWithdraw":false,
         "depositFee":0,
         "withdrawFee":0,
         "minDepositSize":0,
         "maxDepositSize":0
      },
      {
         "id":3,
         "name":"US Dollar",
         "symbol":"USD",
         "type":"coin",
         "precision":2,
         "hasDeposit":false,
         "hasWithdraw":false,
         "depositFee":0,
         "withdrawFee":0,
         "minDepositSize":0,
         "maxDepositSize":0
      },
      {
         "id":4,
         "name":"Ethereum",
         "symbol":"ETH",
         "type":"coin",
         "precision":8,
         "hasDeposit":false,
         "hasWithdraw":false,
         "depositFee":0,
         "withdrawFee":0,
         "minDepositSize":0,
         "maxDepositSize":0
      },
      {
         "id":5,
         "name":"Ripple",
         "symbol":"XRP",
         "type":"coin",
         "precision":8,
         "hasDeposit":false,
         "hasWithdraw":false,
         "depositFee":0,
         "withdrawFee":0,
         "minDepositSize":0,
         "maxDepositSize":0
      },
      {
         "id":1,
         "name":"Digitex Token",
         "symbol":"DGTX",
         "type":"token",
         "precision":4,
         "hasDeposit":false,
         "hasWithdraw":false,
         "depositFee":0,
         "withdrawFee":0,
         "minDepositSize":0,
         "maxDepositSize":0
      }
   ]
}
```

------

#### Public - Ping

**HTTP Request**

`GET /api/v1/public/ping`

**Response**

```json
{}
```

------

#### Public - Announcement

**HTTP Request**

`GET /api/v1/public/announcement`

**Response**

```json
{
  "status": "ok",
  "ts":1590402678700,
  "data": [
    {
      "id": 1,
      "link": "string",
      "title": "string",
      "content": "string",
      "date": "2020-05-21T08:08:49.464Z",
      "tags": ["tag1", "tag2"],
      "urgent": true,
    },
    {
      "id": 2,
      "link": "string",
      "title": "string",
      "content": "string",
      "date": "2020-05-21T08:08:49.464Z",
      "tags": ["tag3"],
      "urgent": false,
    }
  ]
}
```

------

#### Public - Time

**HTTP Request**

`GET /api/v1/public/time`

**Response**

```json
{
    "status":"ok",
    "data":{
        "iso":"2020-06-01T09:17:46.825",
        "timestamp":1590992266825
    }
}
```

------

#### Public - Orderbook

**HTTP Request**

`GET /api/v1/public/orderbook`

| Parameters | Type   | Description        |
| ---------- | ------ | ------------------ |
| symbol     | String | e.g. 'BTCUSD-PERP' |
| depth      | int64  | Default: 5.        |

**Response**

```json
{
    "status":"ok",
    "ts":1590737035730,
    "data":{
        "symbol":"BTCUSD-PERP",
        "updated":1590737035653,
        "bids":[
            [9530,15432],
            [9525,12640],
            [9520,73561],
            [9515,68109],
            [9510,19895]
        ],
        "asks":[
            [9535,63584],
            [9540,51424],
            [9545,79901],
            [9550,56939],
            [9555,161822]
        ]
    }
}
```

------

#### Public - Markets

**HTTP Request**

`GET /api/v1/public/markets`

**Response**

```json
{
    "status":"ok",
    "ts":1590993332256,
    "data":[
        {
            "symbol":"BTCUSD-PERP",
            "openTime":1590906900000,
            "closeTime":1590993300000,
            "highPx24h":9640,
            "lowPx24h":9390,
            "volume24h":682494894,
            "fundingTime":1590998400000,
            "fundingRate":0.0003,
            "bestBidPx":9555,
            "bestBidQty":16424,
            "bestAskPx":9560,
            "bestAskQty":31076,
            "lastTradePx":9555,
            "lastTradeQty":4936,
            "lastTradeTs":1590993332183
        }
    ]
}
```

------

#### Public - Trades

**HTTP Request**

`GET /api/v1/public/trades`

| Parameter | Type   | Description             |
| --------- | ------ | ----------------------- |
| symbol    | String | e.g. 'BTCUSD-PERP'      |
| count     | int64  | Default: 100. Max: 200. |

**Response**

```json
{
    "status":"ok",
    "ts":1590737141606,
    "data":{
        "symbol":"BTCUSD-PERP",
        "trades":[
            {
                "px":9530,
                "qty":26,
                "ts":1590737104653
            },
            {
                "px":9530,
                "qty":2,
                "ts":1590737104653
            },
            {
                "px":9530,
                "qty":1,
                "ts":1590737104653
            },
            {
                "px":9530,
                "qty":2,
                "ts":1590737104653
            },
            {
                "px":9530,
                "qty":48,
                "ts":1590737104653
            }
        ]
    }
}
```

------

#### Public - Klines

**HTTP Request**

`GET /api/v1/public/klines`

| Parameter | Type   | Description                                                  |
| --------- | ------ | ------------------------------------------------------------ |
| symbol    | String | Contract symbol or index symbol, e.g. 'BTCUSD-PERP', '.DGTXBTCUSD' |
| interval  | String | Default: '1min'. Possible values: '1min', '3min', '5min', '15min', '30min', '1h', '3h', '6h', '12h', '1D', '3D', '1W', '3W', '1M', '3M', '6M', '1Y' |
| from      | int64  | Default: 0.                                                  |
| to        | int64  | Default: 0.                                                  |
| count     | int64  | Default: 60. Max: 1500                                       |

**Response**

```json
{
    "status":"ok",
    "ts":1590737272724,
    "data":{
        "symbol":"BTCUSD-PERP",
        "interval": "1min",
        "klines":[
            {
                "id":1590736620,
                "o":9535,
                "h":9545,
                "l":9530,
                "c":9540,
                "v":382175
            },
            {
                "id":1590736680,
                "o":9540,
                "h":9545,
                "l":9525,
                "c":9530,
                "v":474006
            }
        ]
    }
}
```

------

#### Public - Index

**HTTP Request**

`GET /api/v1/public/index`

| Parameter | Type   | Description                        |
| --------- | ------ | ---------------------------------- |
| symbol    | String | e.g. '.DGTXBTCUSD'; ***optional*** |

**Response**

```json
{
    "status":"ok",
    "ts":1590999736854,
    "data":{
        ".DGTXBTCUSD":{
            "indexSymbol":".DGTXBTCUSD",
            "contracts":["BTCUSD-PERP"],
            "updated":1590999736783,
            "markPx":9549.4469,
            "fairPx":0,
            "spotPx":0,
            "components":{
                "binance":{
                    "weight":25,"ts":0,"px":0,"vol":0
                },
                "bitfinex":{
                    "weight":25,"ts":0,"px":0,"vol":0
                },
                "coinbasepro":{
                    "weight":25,"ts":0,"px":0,"vol":0
                },
                "kraken":{
                    "weight":25,"ts":0,"px":0,"vol":0
                }
            }
        }
    }
}
```

------


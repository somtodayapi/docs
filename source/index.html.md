---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - csharp
  - java

toc_footers:
  - <a href='https://github.com/somtodayapi'>GitHub pagina</a>

includes:
  - errors

search: true
---

# Introductie

Welkom bij de documentatie van de API van Somtoday. Deze documentatie en de bijbehorende libraries zijn gemaakt door mensen die op geen enkele manier geaccordeerd zijn met Somtoday, en dit zonder enige overleg gedaan hebben.

# Authenticatie

> Om in te loggen, gebruik een van de volgende codes:

```csharp
WIP
```

```java
SomAPI somAPI = new SomAPI();
Oauth oauth = somAPI.login("GEBRUIKERSNAAM", "WACHTWOORD", new SchoolManager().getSchoolByName("SCHOOL NAAM"));
//Vervang GEBRUIKERSNAAM met je inlog naam, WACHTWOORD met je wachtwoord en SCHOOL NAAM met de naam van je instantie, meer info daarover bij het kopje Scholen
```

> Vervang GEBRUIKERSNAAM met je inlog naam en WACHTWOORD met je wachtwoord.

> Dit zou er terug moeten komen
```json
{
    
}
```

Somtoday maakt voor de authenticatie gebruik van een speciale Authorization header, die gecreeërd wordt door een clientId en een secretId te encoden in Base64.

`Endpoint: https://productie.somtoday.nl/oauth2/token`

`Authorization: Basic RDUwRTBDMDYtMzJEMS00QjQxLUExMzctQTlBODUwQzg5MkMyOnZEZFdkS3dQTmFQQ3loQ0RoYUNuTmV5ZHlMeFNHTkpY`

Verder zijn deze headers ook verplicht in de request:
`Content-Type: application/x-www-form-urlencoded`
`Accept: application/json`

<aside class="notice">
Als je zelf de header wilt genereren kun je dat doen door dit te gebruiken:<br>
<code>ClientID = D50E0C06-32D1-4B41-A137-A9A850C892C2</code><br>
<code>ClientSecret = vDdWdKwPNaPCyhCDhaCnNeydyLxSGNJX</code><br>
<code>Base64.encode(ClientID + ":" + ClientSecret);</code>
</aside>

# Kittens

## Get All Kittens

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get()
```

```shell
curl "http://example.com/api/kittens"
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let kittens = api.kittens.get();
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 1,
    "name": "Fluffums",
    "breed": "calico",
    "fluffiness": 6,
    "cuteness": 7
  },
  {
    "id": 2,
    "name": "Max",
    "breed": "unknown",
    "fluffiness": 5,
    "cuteness": 10
  }
]
```

This endpoint retrieves all kittens.

### HTTP Request

`GET http://example.com/api/kittens`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
include_cats | false | If set to true, the result will also include cats.
available | true | If set to false, the result will include kittens that have already been adopted.

<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>

## Get a Specific Kitten

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get(2)
```

```shell
curl "http://example.com/api/kittens/2"
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.get(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "name": "Max",
  "breed": "unknown",
  "fluffiness": 5,
  "cuteness": 10
}
```

This endpoint retrieves a specific kitten.

<aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>

### HTTP Request

`GET http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to retrieve

## Delete a Specific Kitten

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.delete(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.delete(2)
```

```shell
curl "http://example.com/api/kittens/2"
  -X DELETE
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.delete(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "deleted" : ":("
}
```

This endpoint deletes a specific kitten.

### HTTP Request

`DELETE http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to delete


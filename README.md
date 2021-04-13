# Recipe Planet

Installation:

Første gang
```
$ npm install
$ npm run build
```

Herefter, skal du køre
```
$ npm run develop
```

Der er 2 brugere tilknyttet APIet:

Navn: Admin Adminsen  
Email: admin@recipe-api.com  
Adgangskode: Hul3p1ndsv1n

Navn: Albert Jensen  
Email: albert@recipe-api.com  
Adgangskode: 123Albert123

Du skal hovedsageligt kun bruge Albert.
#### Felter i en opskrift
* Navn på opskrift (`title`)
* Beskrivelse (`description`)
* Fremgangsmåde (`procedure`)
* Billeder (`images`, liste/array)
* Ingredienser (`ingredients`, liste/array)
* Kalorier (`kcal`)
* Protein (gram) (`protein`)
* Kulhydrater (gram) (`carbs`)
* Fedt (gram) (`fat`)
* Kategori (`category`)
* Type (`type`)
* Forberedelsestid (minutter) (`cook_time`)
* (Usynligt felt) Ophavsmand (hvilken bruger har forfattet denne opskrift) (`author`)


Når du kører APIet med `npm run develop`, er det tilgængeligt på http://localhost:1337.

En anonym bruger kan se opskrifter (READ/GET) (alle og enkeltvis) på http://localhost:1337/recipes/[1,2,3,...]

En autoriseret bruger kan oprette opskrifter (CREATE/POST), se opskrifter (READ/GET), redigere opskrifter (UPDATE/PATCH/PUT) og slette opskrifter (DELETE) på samme adresse som ovenfor.

En bruger kan autoriseres på (POST) http://localhost:1337/auth/local.

Eksempel på en autorisations-request (med axios):
```javascript
import axios from "axios";

var { data } = await axios.post("http://localhost:1337/auth/local", {
	identifier: "albert@recipe-api.com",
	password: "123Albert123"
});

console.log(data);
```

Eksempel på et kald til en resurse på APIet, som kræver token:
```javascript
import axios from "axios";

var response = await axios.delete("http://localhost:1337/recipes/42", {
	headers: {
		Authorization: "Bearer <insert token here>"
	}
});

console.log(response);
```
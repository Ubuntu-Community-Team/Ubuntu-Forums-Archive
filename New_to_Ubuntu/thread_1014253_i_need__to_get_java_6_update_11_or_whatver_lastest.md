---
title: "i need  to get java 6 update 11 or whatver lastest version is"
date: 2008-12-17
forum: New to Ubuntu
---

### Post by aszxcv on 2008-12-17
i am on ubuntu 8.04

i used sudo apt-get install sun-java6* awhile back but i got java 6.07 version

my input of javac -version produces javac 1.6.0_07
and java -version produces java version "1.6.0_0"
OpenJDK  Runtime Environment (build 1.6.0_0-b11)
OpenJDK Server VM (build 1.6.0_0-b11, mixed mode)

---

### Post by evilkastel on 2008-12-17
you have to uninstall OpenJDK. go to synaptic and search for openjdk and uninstall everything. check if you hace icedtea installed and if you have, uninstall it. Check what version says now. If if says gjc something... you'lll have to find the package and uninstall it too.
download java from sun and install it. check.
you should have java RTE 6u11.

---

### Post by binbash on 2008-12-17
or : 

sudo update-java-alternatives -l

(you can list them with -l and set it via -s name)

---

### Post by aszxcv on 2008-12-17
> **binbash said:**
> or : 

sudo update-java-alternatives -l

(you can list them with -l and set it via -s name)

what is this and what does it do?

---

### Post by erickelrojas on 2008-12-22
La instalación de la última versión de JRE la tengo siempre en mi web:
[URL="http://www.elleonplateadodeojosrojos.es/blog/instalacion-de-jre/"]
www.elleonplateadodeojosrojos.es/blog/instalacion-de-jre[/URL]

Hasta Siempre:KS

---

### Post by Sef on 2008-12-22
> La instalación de la última versión de JRE la tengo siempre en mi web:
[URL="http://www.elleonplateadodeojosrojos.es/blog/instalacion-de-jre/"]
www.elleonplateadodeojosrojos.es/blog/instalacion-de-jre[/URL]


Please write and link to website that are in English only in the forums, unless you are in loco subforum.  Thank you.

---

### Post by erickelrojas on 2009-01-08
Excuse me to help in Spanish, but if your you know a better manual than mine in English it indicates this link.

Hasta Siempre

---


---
title: "how do i install my grafix card driver?"
date: 2009-07-14
forum: New to Ubuntu
---

### Post by bl0kka on 2009-07-14
i cant find a driver 4 it

---

### Post by overdrank on 2009-07-14
Hi and welcome, what is the model of the graphics card and what version of ubuntu are you using?
You may use the command ```
lspci | grep VGA
``` in the terminal located under applications, accessories to identify your graphics card.
Moved to Absolute Beginner Talk

---

### Post by bl0kka on 2009-07-14
hi soz i postd double :(

my grafix card is a volari v8

---

### Post by swoll1980 on 2009-07-14
do a 

```
apt-cache search volari 
```

In your terminal. I checked their site. they have a linux driver, but it has to be compiled from source. it's[ here ]("http://www.xgitech.com/sd/sd_download3.asp?CTID={861772EF-231B-4029-AC27-64CEAA6F8F27}") see if there's a package for it in the repos first though, using the command above. Post the output. I would do it, but I'm logged into windows right now.

---


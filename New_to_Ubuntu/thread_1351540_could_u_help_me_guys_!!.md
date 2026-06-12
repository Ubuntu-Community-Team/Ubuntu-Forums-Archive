---
title: "could u help me guys ?!!"
date: 2009-12-10
forum: New to Ubuntu
---

### Post by Protect_Your_Mind on 2009-12-10
could u help help me guys ?!! i wanna know how to deal with Apache & create server for my home & local network

---

### Post by Physical Hook on 2009-12-10
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by Iowan on 2009-12-10
Depending on what kind of [server]("https://help.ubuntu.com/8.04/serverguide/C/index.html") you want...

---

### Post by Bucky Ball on 2009-12-10
You would get a lot more help with a descriptive thread title rather than 'can you guys help me?' :)

---

### Post by Ocxic on 2009-12-10
checkout webmin for easier configuration.

---

### Post by Protect_Your_Mind on 2009-12-10
> **Ocxic said:**
> checkout webmin for easier configuration.
what's the webmin ?

---

### Post by Protect_Your_Mind on 2009-12-10
> **Physical Hook said:**
> [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)
thx man

---

### Post by Protect_Your_Mind on 2009-12-10
> **Iowan said:**
> Depending on what kind of [server]("https://help.ubuntu.com/8.04/serverguide/C/index.html") you want...
thx man

---

### Post by Protect_Your_Mind on 2009-12-10
> **Bucky Ball said:**
> You would get a lot more help with a descriptive thread title rather than 'can you guys help me?' :)
choosen the right thread title, huh ? ;)

---

### Post by Geoff918 on 2009-12-10
Ubuntu is *really* easy to establish a server on. Ridiculously so, you can use the server kernel if it's dedicated. Or you could just install the normal software on an existing desktop install. It's already pretty much preconfigured by the gurus.

Pretty much just do an install of Apache2. It will be ready to go and show you the default start web page of "It Works!" within minutes.

Then you can add webpages and all from there.

sudo aptitude install apache2

Just that quick! (I feel like I could do an informercial here...maybe show somebody throwing a computer out the window trying to setup something up on a Windows system--a man with his fingers aching because of too many failed attempts typing up a script...yeah)
*****

Edit: You'll want to setup a static IP probably as well. Or at least be able to address the system by name. Okay, done. :)

---

### Post by Bucky Ball on 2009-12-11
> **Protect_Your_Mind said:**
> choosen the right thread title, huh ? ;)

Yea, lot of people will skip over a non-descriptive thread title. A descriptive one attracts those that can specifically help. ;-)

---

### Post by Protect_Your_Mind on 2009-12-11
> **Geoff918 said:**
> Ubuntu is *really* easy to establish a server on. Ridiculously so, you can use the server kernel if it's dedicated. Or you could just install the normal software on an existing desktop install. It's already pretty much preconfigured by the gurus.
 
Pretty much just do an install of Apache2. It will be ready to go and show you the default start web page of "It Works!" within minutes.
 
Then you can add webpages and all from there.
 
sudo aptitude install apache2
 
Just that quick! (I feel like I could do an informercial here...maybe show somebody throwing a computer out the window trying to setup something up on a Windows system--a man with his fingers aching because of too many failed attempts typing up a script...yeah)
*****
 
Edit: You'll want to setup a static IP probably as well. Or at least be able to address the system by name. Okay, done. :)
 
nothing else, just that ?!!

---

### Post by northern lights on 2009-12-11
> **Protect_Your_Mind said:**
> nothing else, just that ?!!
For apache, that would suffice.

However, if you're looking at serious web-design, even if you plan on using your server only for verification and testing of your code and not for hosting, you will eventually need php and mysql anyhow.

Hence I'd strongly advice to right away do the taksel install of [lamp]("http://en.wikipedia.org/wiki/LAMP_(software_bundle)"):```
sudo tasksel install lamp-server
```

Further, if you plan on working with mysql databases it is usefulto right away install *phpmyadmin* afterwards.```
sudo apt-get install phpmyadmin
```

The document PhysicalHook posted earlier ([https://help.ubuntu.com/community/ApacheMySQLPHP]("https://help.ubuntu.com/community/ApacheMySQLPHP")) is a really good summary that should answer all the problems you might encounter on the way (there shouldn't be any anyhow).

---

### Post by Protect_Your_Mind on 2009-12-11
> **northern lights said:**
> For apache, that would suffice.

However, if you're looking at serious web-design, even if you plan on using your server only for verification and testing of your code and not for hosting, you will eventually need php and mysql anyhow.

Hence I'd strongly advice to right away do the taksel install of [lamp]("http://en.wikipedia.org/wiki/LAMP_%28software_bundle%29"):```
sudo tasksel install lamp-server
```Further, if you plan on working with mysql databases it is usefulto right away install *phpmyadmin* afterwards.```
sudo apt-get install phpmyadmin
```The document PhysicalHook posted earlier ([https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)) is a really good summary that should answer all the problems you might encounter on the way (there shouldn't be any anyhow).

thx man, really appreciate ur help

---


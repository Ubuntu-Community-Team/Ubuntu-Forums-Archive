---
title: "removing games from Ubuntu 8.10"
date: 2008-12-10
forum: New to Ubuntu
---

### Post by manuleka on 2008-12-10
just installed Ubuntu 8.10 on my MSI WIND :) 

now i want to remove all the games that comes with it by default... 

and i want to install Apache/MySql/Php package - one similar to WAMP on Windows

how do i go about doing this?

---

### Post by jamesrl on 2008-12-10
paste into the terminal
```

sudo apt-get remove gnome-games
```

---

### Post by hyper_ch on 2008-12-10
simplest way for apache/mysql/php:

```

sudo taskel install lamp-server

```

for the games, go through synaptic and remove them :)

---

### Post by albandy on 2008-12-10
sudo apt-get remove gnome-games

To install apache, php, mysql, etc ... use the synaptic package manager, search for it and select for install.

---

### Post by manuleka on 2008-12-10
there's just too much application/packages on synaptic i get confused or just don't know which package to install for Apache/MySql/Php

i just need this for localy testing web pages and stuff... 

cheers for your help

---

### Post by ByteJuggler on 2008-12-10
> **manuleka said:**
> there's just too much application/packages on synaptic i get confused or just don't know which package to install for Apache/MySql/Php


Well, just search for and install the "lamp-server" metapackage, which will pull in all the needed bits.  Try it, its not that hard. :)

---

### Post by manuleka on 2008-12-10
can't find lamp-server

---

### Post by ByteJuggler on 2008-12-10
> **manuleka said:**
> can't find lamp-server

I'm very sorry -- I thought there was a lamp metapackage, but apparently there isn't.  My bad!

OK, well all you need to install is:
1.) Apache, package name is "apache2"
2.) MySQL, package name is "mysql-server", possibly also install "mysql-admin", and "mysql-client"
3.) PHP, package name is "php5", you probably also want "libapache2-mod-php5"

That should be pretty much it.

---

### Post by minsf on 2008-12-19
actually, you were not completely wrong... 
there IS a lamp-server "metapackage"
in synaptic, chose the "edit" menu, then "Mark Packages By Task" and then choose the "Lamp-server". this should mark all the packages that you need.
(and dont forget to click "Apply" to actually install them...)

---

### Post by cariboo on 2008-12-19
THe easiest way If you don't know what to install is to go to System-->Administration-->Synaptic Package Manager-->Edit-->Mark Packages by Task and select LAMP from the menu, then click OK. Synpatic will aitomagically install all the packages needed.

Jim

---

### Post by manuleka on 2008-12-20
thanks guys :)

---

### Post by minsf on 2008-12-21
> **hyper_ch said:**
> simplest way for apache/mysql/php:

```

sudo taskel install lamp-server

```



Just for future reference, I wanted to point out that hyper_ch's method from the command line had a TYPO- he really meant:
```

sudo tasksel install lamp-server

```
this is equivalent to the gui method i mentioned in my first post (synaptic>edit menu>mark packages by task>lamp-server), though i did not notice this at the time due to the typo.
by the way, cariboo, you just repeated what i already posted... lol

---

### Post by manuleka on 2008-12-21
thanks :)

---


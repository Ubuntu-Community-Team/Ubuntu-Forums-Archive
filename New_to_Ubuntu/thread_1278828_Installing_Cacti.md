---
title: "Installing Cacti"
date: 2009-09-30
forum: New to Ubuntu
---

### Post by ask123 on 2009-09-30
Hi, when I do apt-get install cacti on my Ubuntu server, it'start to download some perl modules, and I supposed that same one file
Get:1 [http://ru.archive.ubuntu.com](http://ru.archive.ubuntu.com) interpid-updates/main perl-modules 5.10.0.-11.1ubuntu2.3 [3273Kb]
.
.
.
.
Get:110 [http://ru.archive.ubuntu.com]("http://ru.archive.ubuntu.com/") interpid-updates/main perl-modules 5.10.0.-11.1ubuntu2.3 [3273Kb]
.
.
after 115 I STOP IT, I think something wrong here.
Have any idea? how can I fix it?
thx

---

### Post by jonobr on 2009-10-01
Just as a complete wag here,

You know that cacti is the front end for rrdtool so Im guessing you had that installed already before .
Also there are other php dependencies, as well as serverstats which I think uses perl.


Have you got those packages in there?

Maybe you coudl try loading with synaptic as it should be in the regular repos.

I use snmpwalk for regular queries and for any demos or trials I do I use opmanager, its pretty to look at but can be somewhat finicky.

---


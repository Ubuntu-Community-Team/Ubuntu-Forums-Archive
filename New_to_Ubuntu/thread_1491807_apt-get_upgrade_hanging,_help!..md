---
title: "apt-get upgrade hanging, help!."
date: 2010-05-24
forum: New to Ubuntu
---

### Post by sunrex on 2010-05-24
apt-get upgrade hangs on "preparing to replace mysql-server....'versionnumbersidontwanttotype'".

It's just sitting there, it was going fine but once it hit this package it just froze.

Any ideas?.

---

### Post by hryanjones on 2010-05-28
maybe try:

sudo apt-get check

and also try using the graphical front-end for apt-get synaptic -- it might give you more clues or things to try.  To start from command line:

sudo synaptic

---

### Post by sidzen on 2010-05-29
Do you need mysql?  If so, you may want to check here:
[https://help.ubuntu.com/8.04/serverguide/C/mysql.html](https://help.ubuntu.com/8.04/serverguide/C/mysql.html)

Alternatively, and as your first helper said,
[PHP]sudo apt-get check[/PHP][PHP]sudo apt-get -f install[/PHP][PHP]sudo apt-get dist-upgrade[/PHP]Repeat the last two, then

[PHP]sudo apt-get autoremove[/PHP]You may want to then try 

[PHP]sudo aptitude safe-upgrade[/PHP]If no aptitude, then

[PHP]sudo apt-get install aptitude[/PHP]before aptitude command

Hope these help!

---

### Post by urosdj on 2010-06-06
My apt-get has been stuck too but apt-get check (twice) and numerous relogin to get lock on apt-get again helped.

---


---
title: "network problem"
date: 2008-03-28
forum: Networking &amp; Wireless
---

### Post by deevik on 2008-03-28
hello,
   I am new to ubuntu. i have installed Ubuntu 7.10. but whenever i log in to ubuntu i have no network. but when i type this cmd sudo /etc/init.d/dbus start my network connection comes but it lasts till my next login ..again i have to type the same..

Please help

regards,

---

### Post by sandro87 on 2008-03-28
go to *system > preferences > sessions* and check if network is checked to start on every session.

u might have diabled it accidentaly ..

---

### Post by deevik on 2008-03-28
hi..thanks for the reply,
no it was already checked (START UP PROGRAM --NETWORK MANAGER)..
i have installed boot up manager(sudo apt-get install bum)...in that i have made the changes 

system---administration--boot up manager..
under start up and shut down ..i have checked readahead option..

is there any relation between what i have done and the problem..

i get "fail to initialize hal!" when i log in (always)

---

### Post by Eiríkr on 2008-03-28
Starting DBus to get your network up is a new one on me.  :o  Have a try at:
```
sudo /etc/init.d/networking start
```
... and see if that is any more successful.

Cheers,

Eiríkr

---

### Post by Iowan on 2008-03-28
Verify that **/etc/network/interfaces** has an **auto** line for your interface (eth0?).

---


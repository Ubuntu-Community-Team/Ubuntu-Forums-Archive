---
title: "How do I configure apache to allow ALL lan access?"
date: 2006-11-15
forum: Networking &amp; Wireless
---

### Post by tefflox on 2006-11-15
this is at the top of my /etc/apache2/apache2.conf  ---

<Directory "/var/www">
  Order Allow, Deny
  Allow from 192.168.1.100/50
  Deny from all
</Directory>


and this is my /etc/apache2/ports.conf

Listen 80

and firestarter is (i think) configured to allow access from the same ip range

i've made progress, instead of the attempted connection timing out, it comes back immediately that it won't work, so i must be making progresss, right ?

---

### Post by tefflox on 2006-11-16
hey, just needed to bump this.  I need help here. thanks for everything.  this forum is great.

who would've thought it'd be easier to access a windows share from linux than the other way around !

---


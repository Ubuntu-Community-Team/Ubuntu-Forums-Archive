---
title: "How to set google DNS??"
date: 2010-03-08
forum: New to Ubuntu
---

### Post by navaneethan on 2010-03-08
How to configure DNS for ubuntu?

i am having bsnl data card,when i used the data card using"wvdial" than i used to browse,it has slow mostly,i think bsnl dns problem is one reason? is any possible to speed up??by setting google DNS??
how to do it?? any suggestion to make my data card fast?? ....

---

### Post by stoogiebuncho on 2010-03-08
You can change your DNS settings by typing the following:
```
gksudo gedit /etc/dhcp3/dhclient.conf
```

Find the line that says "prepend domain-name-servers" and replace it with :
```
prepend domain-name-servers 208.67.222.222, 208.67.220.220;
```
(these domain name servers are for OpenDNS.  If you'd like to use google DNS or another service, simply enter those ip addresses instead)

I'm pretty sure there's a way to do this through Ubuntu's menus also, but I can't remember what it is right now.

---

### Post by oldos2er on 2010-03-08
[http://code.google.com/speed/public-dns/docs/using.html](http://code.google.com/speed/public-dns/docs/using.html) , scroll down to Linux.

---


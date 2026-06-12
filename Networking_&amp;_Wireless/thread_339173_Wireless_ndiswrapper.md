---
title: "Wireless ndiswrapper"
date: 2007-01-15
forum: Networking &amp; Wireless
---

### Post by Sierra_Dave on 2007-01-15
Hi,

I have ndiswrapper-1.34 extracted, but have a problem when I get link error:

E: /home/carol/downloads/ndiswrapper-1.34 not known on line 32 in source list /et/apt/source.list

E: the list of sources could not be found

I did the following from ndiswrapper install site:

ln -s /usr/src/linux-2.6.15.26-386 /lib/modules/2.6.15.26-386/build

Any Help would be greatly appreciated! :-?

---

### Post by aysiu on 2007-01-15
Sounds as i f you have ```
E: /home/carol/downlaods/ndiswrapper-1.34
``` as a line in your /etc/apt/sources.list. That's not a valid line.

Did you know *ndiswrapper* is on the installation CD?

Try these commands in the terminal: ```
sudo mv /etc/apt/sources.list /etc/apt/sources.list.old
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install ndiswrapper-utils
```

---


---
title: "/etc/network/interfaces"
date: 2008-07-04
forum: Networking &amp; Wireless
---

### Post by Red-Shield on 2008-07-04
i am looking for a bit of info my interface file it reads this for my 

laptop: serial-killer@AMD64:~$ cd /etc/network;more interfaces

auto lo

auto eth0

iface lo inet loopback

iface eth0 inet static

address 192.168.1.150

netmask 255.255.255.0

gateway 192.168.1.175

ESSID "linux4130"

this is my own configuration for my network i cant seem to find any info about what i can put in this file that ubuntu will understand what can i add and where can i find that info i mean are these arguments or what are they called..

---

### Post by chili555 on 2008-07-04
I suggest changing this line:```
ESSID "linux4130"
```to this:```
wireless-essid linux4130
```What about this does Ubuntu not understand? You can read more about what *interfaces* wants in:```
man interfaces
```

---

### Post by Red-Shield on 2008-07-05
thanks for the suggestion i will try that there is nithing that is in this file that ubuntu dose not understand i am looking to custamize more and the man file is not very helpfull

---


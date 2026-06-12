---
title: "crossover cables - how do I set up"
date: 2008-08-01
forum: Networking &amp; Wireless
---

### Post by Potatoj316 on 2008-08-01
Im about to buy a crossover cable and would like to know what configuration (if any) is going to be needed to have a network connection between two computers.  I would like to know how to connect a ubuntu computer to a debian computer (probably do the same thing on both) and a ubuntu computer to a windows xp computer.  

Yes I have a router and it is working fine.  I just want to have a crossover cable and know how to use it if I ever need one/want one.  

What I have found so far:
You need to assign each computer a unique IP address
you need to assign subnet mask and default gateway and they have to be the same for both

are these correct?  any help will be greatly appreciated

---

### Post by Njem on 2008-08-01
You may not need a crossover cable. Many ports these days automatically adapt.

You're right on IP etc. I'm not sure about how two linux boxes sort out identifying each other. In Win they look for a while for one box on the network designated as the name coordinator and if none is found they negotiate until one is chosen. If Linux doesn't do this then any looking at shares on the other box may need to explicitly be addresses by IP address. Other than that they should be able to share resources or do remote access of one another just fine.

---

### Post by lswb on 2008-08-01
Just make sure that avahi is installed and running on both systems. (It is included in default ubuntu installations for hardy and several previous versions) Then just plug in the cable. After a minute or so both systems will self-assign an IP address in the 169.254.x.x range. They will also both have a domain name of .local, i.e. you can ping them by using the hostname with the .local suffix, like ubuntu.local and debian.local

For ease of file transfer between linux/unix systems, IMHO it is hard to beat ssh/sshfs.

---

### Post by superprash2003 on 2008-08-01
you could have one pc as gateway and have the other pc choose the first pc as gateway..

---


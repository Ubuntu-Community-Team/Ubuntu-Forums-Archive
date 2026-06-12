---
title: "I`m only able to locate one network interface"
date: 2008-07-08
forum: Networking &amp; Wireless
---

### Post by jogge on 2008-07-08
Hello.

Im currently running Ubuntu server 8.04, with a total of 4 ethernet cards installed.

Im a bit new to the linux system, since i used to be a FreeBSD user.

In the /etc/network/interfaces configuration it seems that ubuntu can only find one network device (eth0).
All of the network cards is Intel Pro 100s, and i find it a little bit strange that only of them is showing in the interface config. Or is this normal?

Am i doing something wrong? Thanks in advance, for the answers!

---

### Post by superprash2003 on 2008-07-08
type ifconfig in the terminal and see if you find four network devices..if not it could be a driver issue and you might have to search for drivers

---

### Post by jogge on 2008-07-09
I've allready tried that, and it only shows one network card. But i think its strange if its a driver issue, since it can find one of the cards, and all of the cards is of the same type/model.

---

### Post by superprash2003 on 2008-07-09
hmmm..strange.. what is the output of **lshw -class network**

---


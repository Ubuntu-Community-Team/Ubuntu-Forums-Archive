---
title: "D-Link WDA-1320 installation problem in ubuntu 6.10"
date: 2007-01-25
forum: Networking &amp; Wireless
---

### Post by itwasthursday on 2007-01-25
hi, i'm using the instructions at [**this site**]("http://eureka.emmgee.com/2006/12/ubuntu-610-setting-up-wireless-network.html") to install the WDA-1320 wireless network adapter. However, i run into a problem in the first few steps. in the terminal, when i type [FONT="Courier New"]**sudo apt-get install linux-restricted-modules-`uname -r`**[/FONT] i get the following:

[FONT="Courier New"][B]reading package list... done
building dependency tree
reading state information... done
e: couldn't find package linux-restricted-modules-uname -r
[/B][/FONT]

anything i am doing wrong? or an easier way to install? thanks~

---

### Post by Floppyjoe on 2007-01-25
Try this:
```
sudo apt-get install linux-restricted-modules-$(uname -r)
```

---

### Post by oxalá on 2007-06-08
i guess that must have worked.
I'm going out to buy myself a wireless card and I'm betting my $40 on the WDA-1320.
good buy? bad buy?
the reviews i've read thus far are positive.

---


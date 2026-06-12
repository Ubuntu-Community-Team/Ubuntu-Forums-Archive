---
title: "problem with ethernet card"
date: 2005-11-13
forum: Networking &amp; Wireless
---

### Post by rap4ever on 2005-11-13
hello, 
i am an new user of the Linux world..
i install first time linux, Ubuntu linux
and i have a problem with my ethernet
i go in system > administration >networking and i activate the ethernet 
and i choose default getaway device

what else i can do to work?

---

### Post by foolsh on 2005-11-13
are you trying to share files on a windows network if so "sudo apt-get install samba"
or are you just trying to use the internet?

---

### Post by mips on 2005-11-14
Please be a bit more specific with you problem, you dont give us much information to work with.

---

### Post by rap4ever on 2005-11-16
mipi: i have gmail it`s ok!
foolsh i try only use the internet and i can`t
i can`t shared a folder .....because i don`t have router..
i have ethernet adsl 512...and i want to used the internet...
for start only that:P

---

### Post by mips on 2005-11-16
First look at this HOWTO,  [http://ubuntuforums.org/showthread.php?t=87643](http://ubuntuforums.org/showthread.php?t=87643)
and tell us which steps work and which ones dont.

Lets see your **/etc/network/interfaces** file
Lets see output of **ifconfig -a** command
Lets see output of **mii-diag** command
Lets see output of **mii-tool** command

Please post the following info in this thread:

1) Router Make & Model
2) Did you buy it or was it provided by the ISP
2) Connection type, Ethernet, USB or Wireless
3) Running in Bridged or Routed mode
4) Country you live in.
5) Your ISP and/or Broadband provider
6) What service are you subscribing to from them
7) Full TCP/IP config of PC + Router config details (PPPoE, VPI/VCI, DHCP, NAT etc)

Please provide links where possible to the above questions.

---


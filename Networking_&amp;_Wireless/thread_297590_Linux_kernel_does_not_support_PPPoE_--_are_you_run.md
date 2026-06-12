---
title: "Linux kernel does not support PPPoE -- are you running 2.4.x?"
date: 2006-11-11
forum: Networking &amp; Wireless
---

### Post by lazy_runner on 2006-11-11
Hello all,

I need a help with the following problem: Since a few days always if I try to start an internet connection with "sudo pon dsl-provider" I get that error message "Linux kernel does not support PPPoE -- are you running 2.4.x?".

Could anybody tell me how to fix this, please? It would be really nice. :-? 

Thank you in advance.

---

### Post by etherman on 2007-03-23
Didn't want to create a new topic, so I'll post here. I'm having exactly the same problem after updating from 5.10 to 6.06 via apt-get dist-upgrade. The uname command shows that my kernel version is 2.6.12-9-386. I see this topic hasn't received any replies for a very long time, however I hope that someone will have at least some hints on what might be wrong.

---

### Post by butternut on 2007-05-01
I got the same problem here - though after compiling my own ppp-2.4.2b3 with patches for mppe/mppc support. see: [https://launchpad.net/ubuntu/+source/rp-pppoe/+bug/48489]("https://launchpad.net/ubuntu/+source/rp-pppoe/+bug/48489")
The bug is 'unconfirmed'.

---

### Post by butternut on 2007-05-01
ah, looks like an update to the latest kernel available with Ubuntu 6.06 LTS fixed my issue. That is 2.6.15-28.53

I've included some commands bellow that may be of help...

To see the version of the running kernel:
```
$ uname -r
2.6.15-28-686
```

Running ppp (your interface might be something other than eth0):
```
$ sudo pppd eth0
Plugin /usr/local/src/ppp-2.4.2b3/pppd/plugins/rp-pppoe/rp-pppoe.so loaded.
RP-PPPoE plugin version 3.3 compiled against pppd 2.4.2b3
```

checking that the ppp modules are loaded into the kernel succesfully:
```
$ lsmod | grep ppp
ppp_mppe                7556  2
pppoe                  15712  2
pppox                   3816  1 pppoe
ppp_generic            33556  7 ppp_mppe,pppoe,pppox
slhc                    7456  1 ppp_generic
```

looking through ifconfig output to see if the ppp inferface is up:
```
$ ifconfig
...
ppp0      Link encap:Point-to-Point Protocol
...
```

---


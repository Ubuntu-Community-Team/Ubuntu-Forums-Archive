---
title: "Help...WIFI issue"
date: 2008-06-12
forum: Networking &amp; Wireless
---

### Post by BR1983 on 2008-06-12
I have recently installed ubuntu on my compaq presario f700 laptop and have run into issues regarding the wifi card. I beleve I have installed the amd64 version, finally got the necessary drivers along with ndiswrapper installed and recognizing my card. I have an  Atheros ar5007 wifi card that will not allow me to connect to a network. The spinning on the indication spins but never connects. Does anyone have any information or a way to solve this issue?

---

### Post by issih on 2008-06-12
1) Check if the networking works at all by turning off any encryption temporarily
2) if you are using wpa security look at installing wpa-supplicant.
3) if you are using wep, ensure you select the type of the key correctly passphrase/hex/asci
4) try manual configuration of ip address
5) I'm about out of ideas for now :p

Hope thats useful

---

### Post by BR1983 on 2008-06-12
Thanks ISSIH

I have tried disabling the network, changing to a wep encryption, etc.. still nothing

---

### Post by issih on 2008-06-21
I was going through my old posts to see if I'd accidentally abandoned anyone...looks like you were left hanging somewhat.....

This thread looks hopeful
[http://ubuntuforums.org/showthread.php?t=789824](http://ubuntuforums.org/showthread.php?t=789824)

and as its building a driver from source, theres a reasonable chance it will work ok on a 64 bit system.

---


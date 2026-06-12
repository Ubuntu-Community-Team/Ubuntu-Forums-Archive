---
title: "Problems configuring lo wireless device with madwifi"
date: 2007-08-20
forum: Networking &amp; Wireless
---

### Post by jtskinner on 2007-08-20
I have been trying to setup my wireless internet today on Ubuntu(Feisty Fawn). However, restrictive device manager pops-up and says I need a 'Atheros Hardware Access Layer' driver. So, I have been searching the internet trying to setup madwifi 0.9.3.2. I find nothing recent, nothing pertaining to the version I have, and the installation always messes up.

The errors I get are:
It picks up syntax errors and says everything is undefined
Cannot stat 'ath_pci.ko' no such file or directory
iwconfig says lo no wireless extensions and eth0 no
wireless extensions

Hardware specs:
Belkin Wireless G Router
Toshiba Satellite laptop

So can someone tell me how I can find what I need to setup my wireless. I have no clue what I've done wrong or what I'm doing at all. I have latest kernel upgrades.

Thanks in advance...

P.S.: Please do not make the advice too complicated I'm still learning the basics yet. In knowing this, please note that I am not a total idiot.

---

### Post by ntlam on 2007-08-21
what exactly is your wireless card?
Did you try installing ndiswrapper instead?

---

### Post by ntlam on 2007-08-21
I don't think you need the information of your router but you need to know what your wireless card is...

---

### Post by jtskinner on 2007-08-21
Okay I have the make file problem fixed but I cannot detect ath0, only lo and eth0. When I went 
dmesg | grep -i ath
I got:
[   15.808000] ath_hal: module license 'Proprietary' taints kernel.
[   15.808000] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   15.984000] ath_pci: 0.9.4.5 (0.9.3.2)

And with iwconfig I get:
jts@jts-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.:

I also get:
jts@jts-laptop:~$ ifconfig ath0 up
ath0: ERROR while getting interface flags: No such device

I'll try your suggestion, Madwifi is setup okay but something is not working.

---

### Post by jtskinner on 2007-08-21
Atheros Wireless LAN (802.11b/g) is my card,

---

### Post by ntlam on 2007-08-21
I have a toshiba too and got my problem solved:

[http://ubuntuforums.org/showthread.php?p=3202754#post3202754](http://ubuntuforums.org/showthread.php?p=3202754#post3202754)

hope it helps

---

### Post by jtskinner on 2007-08-21
Yep I have it have it solved now. Thanks a lot, and as RMS says 'happy hacking'.

---

### Post by ntlam on 2007-08-21
congratulations

---


---
title: "Problem with my wifi connexion with a Broadcom BCM43xx card"
date: 2007-04-08
forum: Networking &amp; Wireless
---

### Post by neburzaragoza on 2007-04-08
Hola,

My problem is taht i can't conect me with my wireless. I've an Acer Aspire 3630 and my card is a Broadcom BCM43xx. I also sent you some answer of the shell to help you:

*****:~$ iwconfig
lo no wireless extensions.

eth0 no wireless extensions.

eth1 IEEE 802.11b/g ESSID:"linksys" Nickname:"Broadcom 4318"
Mode:Managed Access Point: Invalid Bit Rate=1 Mb/s
RTS thr:off Fragment thr:off
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

sit0 no wireless extensions

****:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
wireless-essid linksys

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


****:~$ iwlist scan
lo Interface doesn't support scanning.

eth0 Interface doesn't support scanning.

eth1 No scan results
sit0 Interface doesn't support scanning. 


thanks

---

### Post by Iowa Dave on 2007-04-09
There have been many posts on the Broadcom wireless problem, as you will see when you hunt through the forums. The drivers were written specifically for Windows

Solutions suggested in the forums all involve the user performing a set of administrative tasks. 

An Ubuntu "How To" is located [_here_]("http://ubuntuforums.org/showthread.php?t=185174"). Read it through a couple of times before you start. It suggests that you bookmark the page and also print it out for reference.

I gave up trying to get it to work, but many others report success. Good luck!

---

### Post by bdogg64 on 2007-04-09
You can either use bcm43xx-fwcutter or you can use ndiswrapper. I have a Broadcom 4311 which works with ndiswrapper and here is the guide

[http://www.ubuntuforums.org/showthread.php?t=346083](http://www.ubuntuforums.org/showthread.php?t=346083)

---


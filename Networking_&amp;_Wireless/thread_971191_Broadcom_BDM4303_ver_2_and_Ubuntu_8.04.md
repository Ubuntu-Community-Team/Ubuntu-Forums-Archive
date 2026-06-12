---
title: "Broadcom BDM4303 ver 2 and Ubuntu 8.04"
date: 2008-11-04
forum: Networking &amp; Wireless
---

### Post by ockron on 2008-11-04
Hello all.

I ungraded today from 7.10 to 8.04 to my shock and horror...:mad:

My lovely laptop wireless stopped working.

I have tried several steps to get it to work ...
[LIST=1]http://penkin.wordpress.com/2008/03/28/ubuntu-804-broadcom-wireless/ ... does not work
[*][http://www.linuxwireless.org/en/users/Drivers/b43#bcm43xx.2Cb43legacy.2Cb43.2Csoftmac.2C...thefullstory](http://www.linuxwireless.org/en/users/Drivers/b43#bcm43xx.2Cb43legacy.2Cb43.2Csoftmac.2C...thefullstory) ... NOT working
[/LIST]

Part of the problem could be that all the forums refer to ver03 or later and mine is ver02.

Output from lspci is:
00:0c.0 Network controller: Broadcom Corporation BCM4303 802.11b Wireless LAN Controller (rev 02)

Outpout from lspci -n is:
00:00.0 0600: 1039:0650 (rev 80)
00:01.0 0604: 1039:0001
00:02.0 0601: 1039:0962 (rev 14)
00:02.1 0c05: 1039:0016
00:02.3 0c00: 1039:7007
00:02.5 0101: 1039:5513
00:02.6 0703: 1039:7013 (rev a0)
00:02.7 0401: 1039:7012 (rev a0)
00:03.0 0c03: 1039:7001 (rev 0f)
00:03.1 0c03: 1039:7001 (rev 0f)
00:03.2 0c03: 1039:7001 (rev 0f)
00:03.3 0c03: 1039:7002
00:04.0 0200: 1039:0900 (rev 90)
00:0a.0 0607: 104c:ac50 (rev 02)
00:0c.0 0280: 14e4:4301 (rev 02)
01:00.0 0300: 1039:6325


Can anyone help me please!!

---

### Post by Ayuthia on 2008-11-04
> **ockron said:**
> Hello all.

I ungraded today from 7.10 to 8.04 to my shock and horror...:mad:

My lovely laptop wireless stopped working.

I have tried several steps to get it to work ...
[LIST=1]http://penkin.wordpress.com/2008/03/28/ubuntu-804-broadcom-wireless/ ... does not work
[*][http://www.linuxwireless.org/en/users/Drivers/b43#bcm43xx.2Cb43legacy.2Cb43.2Csoftmac.2C...thefullstory](http://www.linuxwireless.org/en/users/Drivers/b43#bcm43xx.2Cb43legacy.2Cb43.2Csoftmac.2C...thefullstory) ... NOT working
[/LIST]

Part of the problem could be that all the forums refer to ver03 or later and mine is ver02.

Output from lspci is:
00:0c.0 Network controller: Broadcom Corporation BCM4303 802.11b Wireless LAN Controller (rev 02)

Outpout from lspci -n is:
00:00.0 0600: 1039:0650 (rev 80)
00:01.0 0604: 1039:0001
00:02.0 0601: 1039:0962 (rev 14)
00:02.1 0c05: 1039:0016
00:02.3 0c00: 1039:7007
00:02.5 0101: 1039:5513
00:02.6 0703: 1039:7013 (rev a0)
00:02.7 0401: 1039:7012 (rev a0)
00:03.0 0c03: 1039:7001 (rev 0f)
00:03.1 0c03: 1039:7001 (rev 0f)
00:03.2 0c03: 1039:7001 (rev 0f)
00:03.3 0c03: 1039:7002
00:04.0 0200: 1039:0900 (rev 90)
00:0a.0 0607: 104c:ac50 (rev 02)
00:0c.0 0280: 14e4:4301 (rev 02)
01:00.0 0300: 1039:6325


Can anyone help me please!!
Your card falls under the b43legacy group.  If you have a working connection in Ubuntu, you can install b43-fwcutter and it should install the firmware for you.  However, if that does not work, you might have to drop back to the bcm43xx driver (install bcm43xx-fwcutter) or try ndiswrapper.  The bcm43xx driver has been known to work for some of the older cards.  If you install bcm43xx-fwcutter you can test your wireless by doing the following:
```
sudo modprobe -r b43 b43legacy ssb ndiswrapper bcm43xx
sudo modprobe bcm43xx
sudo /etc/init.d/networking restart
sudo iwlist scan
```
The first two commands will not return anything if all works well.  The third command will restart your network and the last will scan for wireless sites.  

Hope that helps.

---


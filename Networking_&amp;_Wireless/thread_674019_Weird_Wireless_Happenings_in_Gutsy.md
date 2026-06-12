---
title: "Weird Wireless Happenings in Gutsy"
date: 2008-01-21
forum: Networking &amp; Wireless
---

### Post by PinkBullets9 on 2008-01-21
I just upgraded to Gutsy 1 day ago. I like the new normal effects for compiz but for some reason it will not automatically connect to my wireless network if they are on. If I turn all the  effects off my wireless connects to the network no problem. This is not a big problem because all it does is ask me for my password if I have the effects on but it is kinda annoying. Any help is appreciated...

---

### Post by rosegarden78 on 2008-01-22
It's probably the KWallet service managing your passwords.  You type in one password to access your Wallet.  Then the wallet manages passwords everywhere you need to enter them automatically.  So you have a little wireless bar?  If not for some reason press Alt-F2 and type nm-applet.  You may also need to check Settings - Network to turn on the wireless card.  If all else fails try resetting the router and using a non-conflicting ip address such as 192.168.3.1 for your wireless connection.  Hopefully you're not using a Broadcom wi-fi card or you might need the bcm43xx package from the repos.  Then you type

sudo modprobe bcm43xx

to install the firmware or bcm43xx drives into memory after you install it. You can also download a stand-alone drivers for use off-line.

---

### Post by PinkBullets9 on 2008-01-22
I actually fixed this problem I just needed to into the network tool and add it as my default network. Now it works no matter what Thanks though

---


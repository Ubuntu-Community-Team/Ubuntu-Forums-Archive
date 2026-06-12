---
title: "Connect to wireless at startup"
date: 2007-05-15
forum: Networking &amp; Wireless
---

### Post by trivialpackets on 2007-05-15
Hey there, 

Working with Feisty running bcm43xx for my broadcom wireless card.  My only complaint at this time with Ubuntu is that I cannot restart the system and have the network automatically connect any longer.  This is a big deal, as when I'm not around, I am constantly vnc'd into my system allowing me to run updates, access data etc.  So if I'm remotely connected and want to restart the pc for any reason, then it doesn't start up with is not good for me.  Any idea as to how to make this connect?  The one thing I was just thinking would be if I ditched network manager and went with the traditional gnome network setup.  Any ideas or anyone else who saw this.

---

### Post by c0reyf on 2007-05-15
Try using maual configuration and creating a "Default" profile. It should reboot under the last used profile.

---

### Post by javahollic on 2007-05-15
I have the same problem on one machine, but on a feisty box Im currently working on it does come up, the condition is that WEP is used, WPA-PSK was not functional last time I looked (maybefixed now)

lspci output:
01:08.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

your /etc/network/interfaces should have a section like:

iface eth1 inet dhcp
wireless-essid YOURSERVER
wireless-key YOURWEPHEXKEY
wireless-defaultKey 1
wireless-keymode restricted
wireless-rate 54M
#post up route add default eth1
auto eth1

it does work, but YMMV :popcorn:

---


---
title: "Dapper won't load with nic in the pc"
date: 2007-04-03
forum: Networking &amp; Wireless
---

### Post by flyer23 on 2007-04-03
My new wireless card was half working on the pc.  I could boot Ubuntu 6.06 and at least see other networks but couldn’t connect.  Total noob, so I tried a bunch of indiscriminate hacking, added the gnome wireless applet and rebooted.  My hacks apparently didn’t go so well.  (Card is rt61 chipset).

Now the boot process gets to “configuring network interfaces” and freezes.  If I pull the NIC out of the pci slot and fire up the pc then Ubuntu reboots fully with no problem.  Put the card back in and reboot only to see it freeze again at “configuring network interfaces.”  Frustrating because before I got hack-itis Dapper was booting with the card in.

The card works fine if I boot into Windows XP. So the card itself seems fine. How do I change the configuration so Ubuntu will again fully boot with the card in?  Thanks

---

### Post by zvacet on 2007-04-10
I don´t know what you did.You should come here before.You can try to change it 
```
gksudo gedit /etc/network/interfaces
```

See doas it look correct and if not change and save.Another way you can try is 
```
sudo ifup eth0
sudo ifdown eth0
sudo ifup etho
```

replace eth0 with ath0 or whatever you use for wireless

---

### Post by Dj Delta9 on 2007-04-11
I'm having the same problem.  I've been running dapper for awhile but am just now beginning to get into it since I'm having problems, so what I'm about to say may well be the most retarded thing you've ever heard, and will show my noobness  but here goes....

I can boot ubuntu up fine with the card in, but once I configure and activate it, thats when it will stall when booting.  So I take the card out, boot it back up, erase what is in /etc/network/interfaces that has to do with the card, put the card back in, and then reboot and it boots just fine.
...this is what my /etc/network/interfaces looks like without the card activated..

> auto lo
iface lo inet loopback



auto wlan0
iface wlan0 inet dhcp



auto ra0

this is what it looks like when its activated

> auto lo
iface lo inet loopback



auto wlan0
iface wlan0 inet dhcp



auto ra0

iface ra0 inet dhcp
wireless-essid thematrix
wireless-key XXXXXXXXXX

So is there some code that can be put in here that will allow this to stay in here and still boot?    Or did what I just type make absolutely no sense and make everyone dumber for having read it?:???:

P.S. Even though it is recognizing networks, I still cant connect to the internet...but the XP box does just fine.:(

---


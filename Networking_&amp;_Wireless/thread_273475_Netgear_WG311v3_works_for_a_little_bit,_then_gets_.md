---
title: "Netgear WG311v3 works for a little bit, then gets kicked off the network"
date: 2006-10-08
forum: Networking &amp; Wireless
---

### Post by da_maestro on 2006-10-08
Hey guys,

I recently changed from Debian to Ubuntu (I know it isn't much of a change but yeah) and at the same time installed a new Netgear WG311v3 wireless card.

I followed the instructions on [http://ndiswrapper.sourceforge.net/mediawiki/index.php/Ubuntu#5_-_Installing_ndiswrapper](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Ubuntu#5_-_Installing_ndiswrapper) and used the DHCP configuration.

I got the card working fine, but after about an hour of operation I have to ifdown and ifup the card to make it work again.

I use a SpeedStream router. When I look at the devices listing on the router from my windows laptop it identifies the Linux box fine and lists the IP address correctly, but after an hour or so the IP address changes to 0.0.0.0 and the card stops working, until I ifdown and ifup it again.

Frustrating ](*,)

I suspect that the IP address allocation is expiring and not being renewed, but I'm not quite sure how that works. I want to get this working without resorting to writing a script that ifdown and ifup the interface every hour. Anyone else have any trouble like this?

---

### Post by wieman01 on 2006-10-08
Have discussed a similar issue here: [http://www.ubuntuforums.org/showthread.php?t=271625&page=3]("http://www.ubuntuforums.org/showthread.php?t=271625&page=3")

My solution to the problem was to change the router settings and basically set the **[COLOR="Red"]"beacon interval"[/COLOR]** from default ([COLOR="Red"]100 milliseconds[/COLOR]) to [COLOR="Red"]10 milliseconds[/COLOR]. The system has been running stably for nearly 12 hours now, I recommend you to do the same & test the system. You're free to join our thread as well.

---

### Post by da_maestro on 2006-10-09
Ok I think I know my problem. The card drops out when it loses the wireless signal from the router, but doesn't get the signal back. As a result the router marks it as disconnected.

Does anybody know how to fix this problem?

---

### Post by wieman01 on 2006-10-09
I think auto-reconnect is only possible with NetworkManager. But I may be mistaken here. NetworkManager supports that for sure.

---

### Post by da_maestro on 2006-10-09
I fixed my problem I think. Turns out that Samba was having issues with the fact that the computer's host name was the same as the workgroup name. I don't know why this affected it's connectivity as a whole but there you go. All fixed, and a so far working (albeit sluggish) file-server.

---


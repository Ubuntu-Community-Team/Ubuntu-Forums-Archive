---
title: "[WLAN] ndiswrapper freezes boot - can't get into my system!"
date: 2007-06-26
forum: Networking &amp; Wireless
---

### Post by DFreeze on 2007-06-26
I've tried to get NDISwrapper to work with my onboard WiFi card (WinBond W89C33D). The driver loaded, the hardware was present, the module loaded fine. But on reboot, the system hangs on the "configuring network" part. In recovery mode, the verbose doesn't indicate an error, just that after mentioning ndiswrapper nothing else happens anymore. The system does however respond to CTRL-ALT-DEL (first the screen goes blank and then nothing, a second CTRL-ALT-DEL shuts it down). But CTRL-Z or -Q or -X does nothing...

How can I disable NDISwrapper, so I can at least boot into my system again. Is there a way to skip the networking part, or go into a terminal when the system is stuck and manually remove NDISwrapper?

---

### Post by Ayuthia on 2007-06-26
I think that if you take ndiswrapper out of /etc/modules, it will cause it to not start up.  Then if you want to start it up without rebooting, you can use 'modprobe ndiswrapper' and it should start back up.

Hope this helps.

---

### Post by DFreeze on 2007-06-26
I've booted in PCLinuxOS and found the etc/modules file on the UbuntuStudio disk, but there's no ndiswrapper module in there (only lp, sbp2, fuse). Could it be somewhere else?

---

### Post by Ayuthia on 2007-06-26
This is a guess, but you could try to go to /etc/network/interfaces and comment out the wireless option (eth1/wlan0/etc) and that might skip over the wireless on the startup.  I could be wrong though.  If you don't know how to comment, it is just putting a '#' in front of the line.  For example:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp

---

### Post by DFreeze on 2007-06-28
Thanx Ayuthia, that did in fact do the trick. Now I see that my xserver suddenly gives me the black screen when gdm starts [Ati X200], but that's an entirely other matter. I'll dig in to that issue tonight.

---

### Post by DFreeze on 2007-08-08
An update on the matter: I'm running Gutsy on a partition, and just yesterday I managed to get the WinBond wireless up in a matter of minutes. I downloaded the NDISwrapper stuff and NDIS-gtk for the GUI, and used that to install the driver. That was all: I could see my and other networks immediately...

Now, I couldn't get it to browse the internet just yet, but the connection to my AP worked fine (with WPA). I think that the browsing part is more likely due to my router being ill-configured (given that I haven't been able to browse with wireless on WinXP as well). Or do you have some other suggestions as to why internet only works with the wired LAN?

---

### Post by absolutroot on 2007-09-27
insert the install disk
mount your hard drive
remove /etc/modprobe.d/ndiswrapper

reboot, should now reboot successfully.  not sure what causes the problem, but i have ran into it several times with dlink cards/

---


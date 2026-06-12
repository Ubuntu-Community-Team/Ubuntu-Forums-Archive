---
title: "Wireless stops working randomly: colour me irritated"
date: 2008-05-14
forum: Networking &amp; Wireless
---

### Post by TheHeretic on 2008-05-14
Hey guys, first time poster, first time complainer.

So i'm using the latest ubuntu installation (8.04 - 2.6.24.17) and i'm using an Asus P5K E motherboard with inbuilt wireless which uses a little dongle. Ubuntu detects the network fine and connects quickly after asking for the networks password. After a while though, the internet just stops working. The network connection remains but the internet simply fails. I can fix it somewhat by going to the little networking icon in the GUI and disabling then re-enabling "wireless", though after a seemingly random amount of time and reconnection's this stops working as well (it simply fails to connect to the network). At this point I have to restart.

The router is a D Link 524 and everything works A-Ok in Vista, with which I can use the Asus proprietary drivers. This problem is pretty much making Ubuntu unusable, sometimes i'll have to boot 3 times in a row just to be able to connect, and other times i'll be fine for 4 hours without doing a thing.

Any help here would be appreciated, i've heard great things about this forum.

---

### Post by onone on 2008-06-04
I have been having a very similar issue with the base 8.04 install with kernal 2.6.24-16-generic.  After the connection goes down, I have to unplug then replug-in my USB Dell 1450 NIC before being able to reestablish connectivity.  *ifdown*/*ifup* *wlan0* doesn't do it.  The hardware seems to have to be disassociated.

Doing a *dmesg* gives the following:

[ 3613.473612] wlan0: no IPv6 routers present
[ 3633.774345] wlan0: No ProbeResp from current AP ##:##:##:##:##:## - assume out of range


I suspect that the gnome-network-manager is at fault here, but have had no luck setting up ndiswrapper and wpa_supplicant after getting rid of it.  One possible solution I can see would be to turn off IPv6.

Anyone know how? Or have ideas?

Thanks.

---

### Post by Bubba64 on 2008-06-04
Is this your own network or a open wireless connection. If it is a open wireless the signal may be dropping, use the roam option to get the bars for signal strength and drop down of whats available and strength.

---

### Post by onone on 2008-06-04
It's my own network.  I've been running 6.10 forever now and am only having issues since the mirgration to 8.04.  I know for sure that the network isn't the issue.

I eluded to the fact I've tried uninstalling the gnome-network-manager and installed ndiswrapper with no luck.  Under the ndiswrapper scenario there is a wmaster0 interface which is undefined in /etc/networking/interfaces but seems to persist no matter what I do.

Has anyone else seen this behavior?

Thanks.

---


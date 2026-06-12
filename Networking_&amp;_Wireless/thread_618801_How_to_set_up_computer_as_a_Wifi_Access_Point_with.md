---
title: "How to set up computer as a Wifi Access Point with Asus P5K-E WiFi-AP?"
date: 2007-11-20
forum: Networking &amp; Wireless
---

### Post by catsgomoo on 2007-11-20
I'm pretty much at a loss right now. I know my motherboard supports it, because it says so right on the box, but I am completely at a loss as far as how to do it under Linux. I refuse to go back to Windows, and I really want to use this feature, but this has me really stumped.

So how do I set up my PC as a WiFi access point under Ubuntu 7.10?

Much thanks in advance for any help.

---

### Post by Puntachu on 2007-11-26
I have a ver similar board (P5K DH Deluxe /Wi-fi AP).  I'm looking for the same info.  If you happen to get a response, I'd love to hear it, too.

---

### Post by MindFlayer on 2007-11-29
Same problem here. I'd like to know if it's possible to do it in Ubuntu before I install it again.

---

### Post by bobyy on 2007-11-29
Hello..
in my opinion you must change the "mode" of your wirelles card
try to do this:
[PHP]mode
    Set the operating mode of the device, which depends on the network topology. The mode can be Ad-Hoc (network composed of only one cell and without Access Point), Managed (node connects to a network composed of many Access Points, with roaming), Master (the node is the synchronisation master or acts as an Access Point), Repeater (the node forwards packets between other wireless nodes), Secondary (the node acts as a backup master/repeater), Monitor (the node is not associated with any cell and passively monitor all packets on the frequency) or Auto.
    Example :
    iwconfig eth0 mode Managed
    iwconfig eth0 mode Ad-Hoc
    iwconfig eth0 mode Master [/PHP]
I hope it will help you.
  regards

---

### Post by kevdog on 2007-11-30
Not all wireless cards can function as an access point -- its really dependent on your drivers.  Those cards that support MadWifi can definitely be set up this way. ndiswrapper - NO!  Not to be the voice of reason, but just go buy a linksys or other compatible router and flash with dd-wrt.  dd-wrt runs a specialized version of linux made for wireless routers/access points.  No matter how much you know about routers/ access points, there is no way you are going to customize your version of Ubuntu to run better or more efficiently than dd-wrt.  Those are strictly the facts.

---

### Post by kitejumping on 2007-12-05
using the iwconfig wlan0 mode <mode here> the only mode that it successfully changes to for me is "Managed".  The other modes like "Master" seem to fail with 
Error for wireless request "Set Mode" (8B06) : SET failed on device wlan0 ; Invalid argument.
No idea what to do from here, but it would be nice to share the internet connection with the laptop I just picked up on black friday.

---


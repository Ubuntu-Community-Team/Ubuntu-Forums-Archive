---
title: "[SOLVED] WPA network so close"
date: 2008-08-11
forum: Networking &amp; Wireless
---

### Post by SeanBlader on 2008-08-11
I've been reading the forums and Googling this for the last couple days. Today I got a connection, and then about 10 seconds later it drops.

Here's the setup:

WPA Enterprise network, no support for anything but XP from IT
PEAP, TKIP, EAP-MSCHAP v2, Equifax Secure Global eBusiness CA
Validate server certificate and connect to two servers
use domain authentication

I found I can get a brief connection with network manager by using everything listed above, except MSCHAP v2. If I use MSCHAP it connects, then drops. Lasts about as long as if you were to throw a chewed piece of gum at the wall.

I've run out of things to search for to get the connection to stick, any idea's?

---

### Post by PinkFloyd102489 on 2008-08-11
Do you have wpasupplicant installed? If so, check the /etc/defaults/wpasupplicant file and make sure it has ENABLED=0 in it.

---

### Post by SeanBlader on 2008-08-11
Definitely have WPASupplicant installed, and the wpasupplicant file has ONLY that line in it. Also I was able to connect and transfer data for a few moments, but then it dropped, so I'm sure the security config is finally right, there's just weirdness with it's stability.

---

### Post by PinkFloyd102489 on 2008-08-11
Any suspicious output in dmesg related to the wireless?

---

### Post by SeanBlader on 2008-08-11
Nothing that I noticed, but they're linked here:
[http://home.pacbell.net/spintec1/misc/wired.txt](http://home.pacbell.net/spintec1/misc/wired.txt)
[http://home.pacbell.net/spintec1/misc/wireless.txt](http://home.pacbell.net/spintec1/misc/wireless.txt)

The wireless stays connected while I leave the wired connection active. When I unplug the wire, the wireless connection lasts that sticky time and then drops. 

The wired network doesn't require authentication, you can just plug in and be online, but wireless you have to go through all this work so it can be "secure".

---

### Post by SeanBlader on 2008-08-12
Here's something else that's weird with it, After about 40 minutes or so, the network which I just setup disappears from the list of available networks in the network manager list. Does that have something to do with the hidden essid, or is there a visibility term that goes with that kind of access point? Regardless I still can't connect to it or stay connected to the wireless at the office unless the wired connection is still plugged in.

---

### Post by SeanBlader on 2008-10-20
Hah, took me a few tries, like in the 8 or 10 range, but I finally figured out what the problem was. On the properties page I needed to put in the cert file for BOTH the "Client Certificate File" and the "CA Certificate File" and after that it connected and authenticated even without needing to specify what servers it should verify with. Made my potential office connection that much more effective.

---


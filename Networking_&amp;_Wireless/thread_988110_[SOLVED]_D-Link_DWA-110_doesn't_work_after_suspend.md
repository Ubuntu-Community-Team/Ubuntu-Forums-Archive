---
title: "[SOLVED] D-Link DWA-110 doesn't work after suspend."
date: 2008-11-20
forum: Networking &amp; Wireless
---

### Post by gdoron on 2008-11-20
Hello,
I bought a D-Link DWA-110 for a client that has and old Sony PCG-F580/PCG-9211 with ubuntu 8.10. I installed ndiswrapper and configured the DWA-110 with ndisgtk. It works great untill I suspend and when I resume the wifi card is recognised by lsusb but ndiswrapper and network manager don't recognize it.
The computer has a USB 1.1 bus if it may be good information

---

### Post by loveeer on 2008-11-20
There is a native driver for the DWA-110 and it works very well.  The reference is:

[http://ubuntuforums.org/showthread.php?t=400236&highlight=dwa-110](http://ubuntuforums.org/showthread.php?t=400236&highlight=dwa-110)

Hope this helps

Cheers,   loveeer

---

### Post by gdoron on 2008-11-21
Thanks loveeer I didn't know the D-Link DWA-110 is RT73 based.

---

### Post by gdoron on 2008-11-21
When I return from suspend I get a blinking cursor and KDE doesn't return.

---

### Post by loveeer on 2008-11-22
G'day gdoron

I'm not sure I can help.  

1. Where does your suspend command come from? KDE or Gnome.  Is it NetworkManager?

2. Have you tried using the native driver for the DWA-110 (RT73)?

3. I'm not sure why you need a suspend command when you can easily turn the wireless off and on.

Cheers,   loveeer

---

### Post by gdoron on 2008-11-24
I moved to Kubuntu and there is KNetworkManager which shows that the RT73 works. but the problem is the pc turns the bus down on resume.

---

### Post by loveeer on 2008-11-24
I am not overly familiar with KDE and KNetworkManager, but from my reading, I understand that NetworkManager is seriously broken in Intrepid Ibex.  I suspect the same is true in KNetworkManager.  You may have to wait for a fix.

Cheers,  loveeer

---


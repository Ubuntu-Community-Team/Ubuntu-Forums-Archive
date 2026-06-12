---
title: "Intel Pro 3945 - KNetworkManager hangs"
date: 2006-08-17
forum: Networking &amp; Wireless
---

### Post by nrwilk on 2006-08-17
I've just gotten my new laptop, and everything works beautifully well, except the wireless.

I have looked at many, many threads here about this topic, but I cannot seem to find anything that addresses my specific problem.

I am trying to use KNetworkManager to connect to my home wireless WEP encrypted network.  It did connect successfully ONCE.  last night.  Now, I cannot get it to work again.  It hangs every time at either 28%, "Configuring Device," or 57%, "IP Configuration Started."  If it gets to the 57% stage, it always then shows me a "Connect to wireless netowrk" window with my saved options for the network that I'm trying to connect to.  I hit "Connect" and then KNetworkManager seems to quit and restart.  Most of the time, though It hangs at the 28% spot, and never gets any farther.

There's another wireless program on my laptop called "Wireless Assistant," at the bottom of the "Network" menu in the K-Menu.  With this utility, I CAN connect to my netowrk successfully.  But, this program has no systray icon to tell my signal strength, and it's interface is not as good as KNetworkManager's.  If I can connect with it, why can't I connect with KNetworkManager?

Any help is much appreciated!

nrwilk

---

### Post by nrwilk on 2006-08-17
YAY! Nevermind, I got it worked out.

I got KNetworkManager to work by selecting the "WEPhex" option for the key rather than just "WEP."

---

### Post by wyth on 2006-08-21
Did this continue to work, because this doesn't work for me.  I have 128 bit WEP, and have the exact problems you described above, only hex doesn't work.

---

### Post by nrwilk on 2006-08-22
Yes, my wirless has continued to work with this setup since I figured it out.

It even connects to the last used signal automatically on startup.

Sorry I couldn't be of more help!

---

### Post by oncemore on 2006-08-22
this is happening to me too...dont know how to fix it..(i use wephex too but still not working :/)

---


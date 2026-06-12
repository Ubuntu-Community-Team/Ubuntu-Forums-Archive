---
title: "Disconnect from Ethernet"
date: 2007-08-05
forum: Networking &amp; Wireless
---

### Post by Greasyfingers on 2007-08-05
I've just installed an ethernet card, never having used one before, and connect to the internet via a shared router. I want to be able to connect and disconnect from the network at will.

If I type ```
$ sudo ifconfig eth1 down 
```then Network Manager reports a disconnection OK, but then it comes right back up again.

Is there some sort of auto-connect thing I need to disable? 

Also, is there a way to make the bootup default to the disconnected state?

Any help appreciated.

---

### Post by HereInOz on 2007-08-05
I can't help with the second bit, but I reckon if you disable roaming mode in your network properties (System>Administration>Network) that should prevent Network Manager from trying to re-establish the connection you have just taken down.  The whole idea of Network Manager in roaming mode is that it attempts to maintain a network connection at all times.

Failing that, if you make your IP address of the Ubuntu machine as a Static IP, and manually enter your DNS adresses, that will give you full control over the network adaptor.

---

### Post by Greasyfingers on 2007-08-05
Thanks HereInOz, but things are not altogether clear to me.

I unchecked roaming mode, but no matter what I select in the rest of the box I either can't get a connection or it auto connects as before.

For the static IP option, I may be misunderstanding how to configure this, but so far I can't get it to make a connection, despite the fact that ifconfig says the connection is up.

However, I did find that the Network Manager panel applet has an 'Enable Networking' check box, which seems to do pretty much what I want - though it would be useful to know what the terminal commands for this would be, so that I can incorporate them into a script.

---


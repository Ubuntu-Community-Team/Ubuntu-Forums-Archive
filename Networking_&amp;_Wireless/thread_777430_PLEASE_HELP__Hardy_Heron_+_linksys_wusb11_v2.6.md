---
title: "PLEASE HELP:  Hardy Heron + linksys wusb11 v2.6"
date: 2008-05-01
forum: Networking &amp; Wireless
---

### Post by delysid on 2008-05-01
I have spent the last 4 days trying to get my linksys wusb11 ver 2.6 wireless adapter to work with Hardy Heron x86_64.  

I have tried to use the ndiswrapper method, but cannot find a 64-bit windows driver for the adapter.  

I have also tried to install the atmel at76_usb driver from [http://at76c503a.berlios.de/](http://at76c503a.berlios.de/).  When this driver is used, the wireless adapter is detected, and I can see my network in the network configuration utility, however the adapter will not connect to the network.

In addition to these, I also tried installing the drivers from [http://sourceforge.net/projects/atmelwlandriver/](http://sourceforge.net/projects/atmelwlandriver/).  After this driver was installed, ubuntu crashes when the adapter is plugged in.  If the adapter is plugged in during startup, ubuntu freezes at the loading screen

Has anybody gotten this wireless adapter to work?  I would like to make Ubuntu my permanent OS, and would be eternally grateful to anybody that can help me do this.

---

### Post by delysid on 2008-05-01
anybody?

---

### Post by Unix_Slayer on 2008-05-04
Funny you should ask...... I'm working on that as I post. Will let you know.

---

### Post by delysid on 2008-05-04
I have Gutsy on my box now.  This fixed all of the other problems I was having with Hardy (nvidia drivers and such).  

I still have not attempted to mess with the wireless yet because I don't want to screw anything up again.  Let me know if you get it working though.  I'm sure the fix will work for both versions. :)

---

### Post by Unix_Slayer on 2008-05-04
> **delysid said:**
> I have Gutsy on my box now.  This fixed all of the other problems I was having with Hardy (nvidia drivers and such).  

I still have not attempted to mess with the wireless yet because I don't want to screw anything up again.  Let me know if you get it working though.  I'm sure the fix will work for both versions. :)

Sorry.... My mistake. My adapter is the WUSB54GS. I've got it working, but I didn't realize you can't have two network adapters running at the same time. I had to disable my lan card, and enable my wlan card via KNetworkManager.

---


---
title: "Newbie... help connecting to wireless network"
date: 2009-11-05
forum: New to Ubuntu
---

### Post by agquintero on 2009-11-05
"Originally Posted by **KIAaze** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=8246809#post8246809") 				
 				Could you please post the output of?:
 	Code:
 	lspci -vvnn 
(Read [this]("https://help.ubuntu.com/community/UsingTheTerminal") if you don't understand what I said. :wink: )

Some first google results which might help:
[http://fourlovesfour.blogspot.com/20...less-with.html]("http://fourlovesfour.blogspot.com/2008/05/setting-up-broadcom-b43-wireless-with.html")
[http://ubuntuforums.org/showthread.php?p=8203365](http://ubuntuforums.org/showthread.php?p=8203365)
[http://ubuntuforums.org/showthread.php?t=1010751](http://ubuntuforums.org/showthread.php?t=1010751)"


The output of the above code is: 

	 	 00:0b.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)  
 	Subsystem: AMBIT Microsystem Corp. Device [1468:0312]  
 	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-  
 	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-  
 	Latency: 64  
 	Interrupt: pin A routed to IRQ 17  
 	Region 0: Memory at e2000000 (32-bit, non-prefetchable) [size=8K]  
 	Kernel driver in use: b43-pci-bridge  
 	Kernel modules: ssb

---

### Post by jimmy the saint on 2009-11-05
You should really post this as a reply to that thread rather than starting a new thread for a reply.  For one thing, if he is watching that thread to help you, he will be waiting for you to post it, for another, there is no guaruntee he will see this thread.

---

### Post by agquintero on 2009-11-05
> **jimmy the saint said:**
> You should really post this as a reply to that thread rather than starting a new thread for a reply.  For one thing, if he is watching that thread to help you, he will be waiting for you to post it, for another, there is no guaruntee he will see this thread.

He suggested i started a new post for different problem.... and I private messaged him... but if anyone else could help me find the driver for the wireless card above and help me install it i would really appreciate it. Thank you

---

### Post by KIAaze on 2009-11-05
Oops, it seems I posted in your [other thread about this]("http://ubuntuforums.org/showthread.php?t=1312202") before.

Anyway, now you know what to google for:
> Make and Model: Broadcom Corporation BCM4318 [AirForce One 54g] 
Device Id: 14e4:4318


First of all, check which kernel version you're running with:
```
uname -a
```
(On Karmic, it should be 2.6.31)

Check if the wireless works when you boot into an older kernel (they should still be listed in the grub menu if you upgraded from an older version).

I searched a bit and this sounds like it might work:
[http://ubuntuforums.org/showpost.php?p=5662097&postcount=6](http://ubuntuforums.org/showpost.php?p=5662097&postcount=6)

This might also be worth a try:
[http://fourlovesfour.blogspot.com/2008/05/setting-up-broadcom-b43-wireless-with.html](http://fourlovesfour.blogspot.com/2008/05/setting-up-broadcom-b43-wireless-with.html)

---

### Post by PeggySue on 2009-11-05
I have a Dell Vostro Laptop with a broadcom wireless card.  

With Ubuntu 9.10 I had to do this:
Insert the distribution CD, go to System | Administration | Synaptic Package Manager;
Under Settings | Repositories select the distribution CD and search for Broadcom drivers.  
I can't remember the details from here but there is a thread on the forum somewhere that explains this in more detail.
This worked for me and didn't involve any work with the terminal.  

Good luck using the forum search engine.  You might be better off using Google and include the term Ubuntu!

---

### Post by texla on 2009-11-05
agquintero, if you just want to your laptop get up and running, you might want to try downloading and using the live cd for 9.04.  I had the exact same install problem from the Xubuntu 9.10 live CD that you had on my laptop.  When I tried the 9.04 CD I had a perfect Live CD session, wireless and all.  Just an idea...

---

### Post by texla on 2009-11-13
Actually, I just got mine running with the Ubuntu 9.10 Karmic last week - no prob.  Not sure what's up with the Xubuntu Netbook remix - maybe it really only likes netbooks?  I could install it from USB on my netbook but the usb and the CD install were no good on my old laptop like i said above.  Strangeness there but all is good with the Karmic install for now.  I didn't realize that the install would automatically detect the laptop when installing, that's very helpful, too.

---


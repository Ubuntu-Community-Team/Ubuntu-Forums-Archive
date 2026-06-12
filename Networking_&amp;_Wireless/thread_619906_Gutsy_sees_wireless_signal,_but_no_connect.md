---
title: "Gutsy sees wireless signal, but no connect"
date: 2007-11-21
forum: Networking &amp; Wireless
---

### Post by mdpalow on 2007-11-21
Hi Everyone,

Let me first apologize 'cause I know I'm not going to have all the info I need, but I'm hoping someone will get me in the right direction.

Trying to help someone - long distance - get a wireless connection.

Running Live CD; Ubuntu is NOT installed.

They're using a Linksys Wireless USB antenna.

Ubuntu 7.10 sees the signal, but no connect.

Set the router to not use any encryption just for testing purposes.

Is this a driver issue?

If so, is there anything I can read until I find out tomorrow what kind of Linksys USB it is?

I wasn't too concerned about Linksys type at the moment 'cause we're also trying to get his Windows Laptop up and running again with wireless as well; then we'll focus on Ubuntu.

We haven't gotten Windows wireless up yet as we were in a rush and we're bouncing around between two machines. Tomorrow we'll have more time.

Sorry again for little info, but any thoughts or links would be a nice start for now.

Thanks in advance...

---

### Post by kevdog on 2007-11-22
Its probably a driver issue.  USB devices are tricky -- PCI devices are far more reliable.  In order for your USB device to get up and running you are going to have to find the chipset of the device.  Likely you are going to have to google for this since on the packaging it will not tell you.  Once you find the chipset, then  it will be actually easy for us to help you.  Its likely either a broadcom, ra, or realtek chipset.

---

### Post by mdpalow on 2007-11-22
Thanks Kevdog..

If anyone is good with drivers, can you pls subscribe to this thread until Friday? I'll have more info tomorrow evening and Friday for sure... Hopefully after Friday it'll be solved one way or another and then if you subscribed you can unsubscribe.

Thanks again in advance and Happy Thanksgiving...

---

### Post by rustybronco on 2007-11-22
That expert would be Kevdog, and for reading material see his signature, it will help you.

I'll be in and out (mostly out ) till sunday but I will keep an eye on this thread.

---

### Post by mdpalow on 2007-11-22
Hi Kevdog,

Believe it's a WUSB54GS that he's using to connect to the Internet and the router is a WRT54G.

Any thoughts?

TIA

---

### Post by mdpalow on 2007-11-22
I just found this link and noted the how to was written almost 18 months ago. Has connecting a WUSB54GS not been fixed in three newer versions of Ubuntu?! Do we still have to go through all this to get a wireless adapter working?

---

### Post by kevdog on 2007-11-22
mdpalow -- what is the chipset of this device??  And yes depending on the chipset it might take some work to get up and running.

---

### Post by kevdog on 2007-11-22
Is it one of these 

[HTML]
 Linksys
	

WUSB54G (Ver.1)
	

ndiswrapper
	

No
	

Yes
	

No
	

First remove islsm_usb then remove and add back ndiswrapper
	

2006-09-01
	

USB

Linksys
	

WUSB54G (Ver.4)
	

rt2500 / rt2570
	

?
	

Yes
	

Yes
	

Works fine with WEP on 6.06/Breezy when installed, but hung at activating using LiveCD; works on 7.04/Feisty w/ WEP with manual config and roaming other connections
	

2006-12-27
	

USB

Linksys
	

WUSB54GC
	

RAlink RT2571W/RT2671
	

No
	

Yes
	

No
	

Needs some hacking. See WifiDocs/Device/LinksysWUSB54GC
	

2006-11-19
	

USB 
[/HTML]

---


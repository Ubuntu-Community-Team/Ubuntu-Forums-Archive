---
title: "NetgearWG111: What does out-of-the box support mean exactly? (Attribute Error Fiasco)"
date: 2008-03-11
forum: Networking &amp; Wireless
---

### Post by uncleclinto on 2008-03-11
Okay,

So I need to move my computer to the another room (don't ask).  It has no card slot for my wireless card, and I'm scared to death to crack the case.  Obvious solution: USB Wireless adapter.  The thing is, 6 months with Ubuntu has made me smart.  "Don't buy anything without finding out if it's going to work".  So I find this list and do my homework: [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)  

I narrow it down to only adapters that say they work "out of the box", *******uming that this means that it will come from box to slot and work.  

Okay, so 4 hours and a lot of disillusionment later, I've installed ndiswrapper and all of the related goodies, downloaded the driver, and run the ndisgtk thing to install and I get this Attribute error crap.  Now ndisgtk crashes on startup so I can't even try anything else.  

Any suggestions or do I take this thing back and run 100 feet of ethernet cable across my floor?
WTF is an attribute error?
How do I fix ndisgtk because the old uninstall / reinstall doesn't work.

---

### Post by kool_kat_os on 2008-03-11
i run 100ft of Ethernet cord on my floor...:)but i also use a WRT54G with dd-wrt on it

---

### Post by kmurray on 2008-03-11
In my travels thru the interwebs (trying to find a wireless PCI card that works out of the box), I stumbled over this link:

[http://www.murrayc.com/blog/permalink/2007/02/17/linux-compatible-wireless-usb-adaptor-results/](http://www.murrayc.com/blog/permalink/2007/02/17/linux-compatible-wireless-usb-adaptor-results/)

Hope this helps.

---

### Post by uncleclinto on 2008-03-12
Okay,

So I may possibly not be able to take this one back.  This sucks because I DID do my homework ahead of time.  Either way, would anyone like to clue me in on how I may get this connected??  Perhaps we should begin by asking how I might fix this attribute error crap which is apparently causing ndisgtk to crash and be unuseable. 

Any thoughts???:confused:

---

### Post by lespaul_rentals on 2008-03-12
Okay, if you can return this, do so **now**.  Do whatever it takes to exchange this.  Get something else that is in fact supported.  Check the Linux HCL here: [http://www.linuxquestions.org/hcl/](http://www.linuxquestions.org/hcl/)

Netgear's WG111T sucks for Linux.  They are a scumbag company who will use Linux on their routers and claim it as a selling point, yet they are very rude and unsupporting to Linux clients.  **Do not support Netgear.  They are the Microsoft of the networking world.**

In fact, a Linux user asked for help in the Netgear support forum and was addressed very rudely by a member of the forum staff.  Other Linux users flocked in, and were met with the same hostility.  I joined as lol_at_netgear and bumped a year-old thread, stating that I thought their lack of support was unacceptable, and the same moderator told me, "dont let the door hit you on the way out."

[http://forum1.netgear.com/showthread.php?t=6949](http://forum1.netgear.com/showthread.php?t=6949)

I despise that POS company and will do anything in my power to refer people away from them.

Back to your question, I tried using ndiswrapper as well and for some reason, it would not work.  I even tried compiling the newest version from source, but I still couldn't get the USB wireless adapter to work.  The only way I've heard to get it working 100% of the time is through Linuxant.

---

### Post by uncleclinto on 2008-03-12
If this is the case, then someone should certianly consider removing this device from the supported "out of the box" list.

I can't believe this.:mad:

---


---
title: "Hardy 64-bit Linksys WUSB300N"
date: 2008-06-07
forum: Networking &amp; Wireless
---

### Post by mastermindg on 2008-06-07
I would like to get the WUSB300N adapter working on a 64-bit version of Hardy so that I can actually utilize my 6GB of memory and my processor power :)

The disc has 64-bit drivers for Vista. Ndiswrapper doesn't seem to like these. Any ideas?

---

### Post by Unix_Slayer on 2008-06-07
> **mastermindg said:**
> I would like to get the WUSB300N adapter working on a 64-bit version of Hardy so that I can actually utilize my 6GB of memory and my processor power :)

The disc has 64-bit drivers for Vista. Ndiswrapper doesn't seem to like these. Any ideas?

Try the WinXP 64 bit driver. I had problems with the same adapter. Ndiswrapper didn't like any of the Vista drivers. Worked fine with WinXP drivers,

---

### Post by paradoxxical on 2008-06-08
Unix_Slayer, are you referring to this driver?
[http://www.opendrivers.com/driver/238895/marvell-topdog-802.11n-g-b-wlan-driver-1.0.4.9-windows-98se-me-2000-xp-xp-x64-free-download.html](http://www.opendrivers.com/driver/238895/marvell-topdog-802.11n-g-b-wlan-driver-1.0.4.9-windows-98se-me-2000-xp-xp-x64-free-download.html)

So far that's the only package I've been able to find that might have the linksys WUSB300N XP 64 driver that you are referencing.

If not, it would be great if you could point us in the direction of the right driver.

---

### Post by Unix_Slayer on 2008-06-09
> **paradoxxical said:**
> Unix_Slayer, are you referring to this driver?
[http://www.opendrivers.com/driver/238895/marvell-topdog-802.11n-g-b-wlan-driver-1.0.4.9-windows-98se-me-2000-xp-xp-x64-free-download.html](http://www.opendrivers.com/driver/238895/marvell-topdog-802.11n-g-b-wlan-driver-1.0.4.9-windows-98se-me-2000-xp-xp-x64-free-download.html)

So far that's the only package I've been able to find that might have the linksys WUSB300N XP 64 driver that you are referencing.

If not, it would be great if you could point us in the direction of the right driver.

I used ndiswrapper, which you can get from Adept manager by typing in "ndis". I downloaded the drivers from Linksys ==>[http://www.linksys.com/servlet/Satellite?c=L_CASupport_C2&childpagename=US%2FLayout&cid=1166859916411&packedargs=sku%3D1160093476789&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=1641176789B03&displaypage=download]("http://www.linksys.com/servlet/Satellite?c=L_CASupport_C2&childpagename=US%2FLayout&cid=1166859916411&packedargs=sku%3D1160093476789&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=1641176789B03&displaypage=download")
And then I ran ndiswrapper, and added a new device. Pointed it to the WinXP .inf driver. And it's worked fine since.

---

### Post by lingenfr on 2008-10-25
There is no 64 bit driver for the wusb300n provided by linksys for anything other than Vista. Those don't work nor do the 32 bit drivers for XP. You did not get the 32 bit drivers running on a 64 OS. Please read the post. I tried the drivers that paradoxxical referenced and had no luck with those either. I am preparing to give up and go back to a 32-bit version of kubuntu or maybe look for a new adapter.

I found out that the wusb300n has the Marvell Topdog chipset. I have done quite a lot of looking and can't find non-Vista 64-bit drivers for that chipset. There are plenty that say they include XP_64, but I can't find any that actually do.

---

### Post by juanpecan on 2008-11-11
i am interested in switching to 64 bit from 32 but want to make sure my wusb300n will work.  have you resolved it?

---


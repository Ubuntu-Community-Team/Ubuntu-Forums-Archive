---
title: "Change wlan1 to wlan0"
date: 2008-05-14
forum: Networking &amp; Wireless
---

### Post by Tom--d on 2008-05-14
Is it a simple process?

and how do I do it?

I have NO wlan0. Did, but not there. (was a usb wireless stick but got internal wireless card working)

Thanks,
Tom

---

### Post by nixscripter on 2008-05-14
Generally, the device names are assigned by the drivers of the cards.

Why would you want to do it in the first place?

---

### Post by Tom--d on 2008-05-14
No point. Just me being me.

---

### Post by inportb on 2008-05-14
> **nixscripter said:**
> Generally, the device names are assigned by the drivers of the cards.

Generally, device numbers are assigned by udev.

Try tweaking this file: **/etc/udev/rules.d/70-persistent-net.rules**
(remember to do this with superuser rights and make a backup)

If you need more help, please post the contents of that file.

---

### Post by nixscripter on 2008-05-14
> **inportb said:**
> Generally, device numbers are assigned by udev.

Oh yeah, udev. Doh!

However, I think the names of the interfaces are in fact assigned by the drivers (wlan, ra, eth, etc.) :-P Yes, inportb is right, they are numbered by ubev on Ubuntu. :-)

I don't see why wlan1 isn't renamed wlan0 if the other device was removed anyway, unless udev is deciding to leave a hole for some reason.

---

### Post by jetsam on 2008-05-15
Udev seemed to have the same behavior in this [thread]("http://ubuntuforums.org/showthread.php?t=771981").  I looked into it a little: that file (70-persistent-net.rules) has the ability to identify a hardware interface by mac address and/or other identifying text from the hardware identifiers.  Then it assigns the interface name.  Even when you remove the interface hardware from the system, it seems that udev keeps that interface name assigned to that specific device only and doesn't clear its entry automatically.  

This is good behavior if you have a usb device which you're often plugging in and unplugging.  Maybe that's why they set it up that way; I'm just speculating, though.

I think that interface names are actually pretty flexible and you could call your **eth0** interface **xanadu** if you wanted to.  (Don't do this.  I just tried it and it works, but it breaks secondary software like network-admin and iptraf.:))  It's best to stick to the conventional names.  The drivers may have something to do with it as well.  I'm not sure how udev originally decides what name to give a particular device.

---

### Post by kevdog on 2008-05-15
Why dont you just post your udev file here?

---

### Post by Tom--d on 2008-05-17
I have now changed it :) 

Thanks. 

It still kept my old wireless MAC address. Deleted it and changed my current wireless card to wlan0

Easy :D

---

### Post by nobodyfamous on 2013-01-18
sorry to dig up an old thread, but. . . I just put a new card in my laptop, and yes, it is wlan1 rather then wlan0 - **is it necessary that I change this back to wlan0?**  (it is the internal card, so the old one will never be used again) The only place I noticed an issue was with my "netmon" screenlet, I had to update the device name (really not a problem) but will this cause issues with other software/hardware?

---


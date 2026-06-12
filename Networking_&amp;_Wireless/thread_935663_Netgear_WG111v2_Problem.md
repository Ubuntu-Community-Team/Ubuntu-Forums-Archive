---
title: "Netgear WG111v2 Problem"
date: 2008-10-01
forum: Networking &amp; Wireless
---

### Post by adhdkid13 on 2008-10-01
So after pluggin in my netgear wireless adapter wg111v2 into my usb slot on ubuntu hardy heron, it worked like a charm. I though to myself "hey, it could be better if i installed the correct drivers with ndiswrapper!" I was wrong.

I started the process, and before i knew it, i seemed to cause irreversable damage to my config. I am totally lost and have no idea what to do. It won't even recognize my card!

Ndiswrapper does not work for me.. so please don't suggest trying that again. Is there anyway i can reset the settings that were created for my netgear adapter? Anything I can do to revert to before i started messing with ndiswrapper?

---

### Post by iponeverything on 2008-10-01
[QUOTE=adhdkid13;5891272]So after pluggin in my netgear wireless adapter wg111v2 into my usb slot on ubuntu hardy heron, it worked like a charm. I though to myself "hey, it could be better if i installed the correct drivers with ndiswrapper!" I was wrong.

In almost every case the native driver works better that windows driver. It makes sense. 

Remove the driver from ndiswrapper -

list installed drivers:
sudo ndiswrapper &#8211;l 

remove driver:
sudo ndiswrapper &#8211;e <drivername>

edit /etc/modprobe.d/blacklist and remove the line were ndiswrapper blacklisted your native driver.

---

### Post by adhdkid13 on 2008-10-01
> **iponeverything said:**
> [QUOTE=adhdkid13;5891272]So after pluggin in my netgear wireless adapter wg111v2 into my usb slot on ubuntu hardy heron, it worked like a charm. I though to myself "hey, it could be better if i installed the correct drivers with ndiswrapper!" I was wrong.

In almost every case the native driver works better that windows driver. It makes sense. 

Remove the driver from ndiswrapper -

list installed drivers:
sudo ndiswrapper –l 

remove driver:
sudo ndiswrapper –e <drivername>

edit /etc/modprobe.d/blacklist and remove the line were ndiswrapper blacklisted your native driver.

No idea what my native driver is :/

---

### Post by iponeverything on 2008-10-01
I quick google search turned up rtl8187

---

### Post by adhdkid13 on 2008-10-01
> **iponeverything said:**
> I quick google search turned up rtl8187

I uninstalled the driver from ndiswrapper, and checked the blacklist at /etc/modprobe.d/blacklist to find that it wasn't even there. Here is my current blacklist.

> # This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

:/


I really appreciate all your help. If you have any other suggestions, please let me know.

---

### Post by iponeverything on 2008-10-01
you might need to reboot start with clean slate.

do a:

sudo modprobe rtl8187

if that fixes your card then do:

sudo echo rtl8187 >> /etc/modules

---

### Post by adhdkid13 on 2008-10-01
> **iponeverything said:**
> you might need to reboot start with clean slate.

do a:

sudo modprobe rtl8187

if that fixes your card then do:

sudo echo rtl8187 >> /etc/modules


You're the man!

Thanks :D

---


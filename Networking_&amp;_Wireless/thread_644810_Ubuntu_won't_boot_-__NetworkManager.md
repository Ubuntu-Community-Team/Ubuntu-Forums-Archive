---
title: "Ubuntu won't boot -  NetworkManager"
date: 2007-12-19
forum: Networking &amp; Wireless
---

### Post by Drone4four on 2007-12-19
Ubuntu won't boot.  Right before gdm starts, NetworkManager produces this error: 
```
*Starting DHCP D-Bus daemon dhcdbd [OK]
NetworkManager: <debug> nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial
```
There are random numbers, and then that message repeats itself with other hardware devices like /platformflooy, /volume, /storage_model DVD

How do I successfully start gdm?

---

### Post by Drone4four on 2007-12-19
btw, I am making this post via a knoppiz/debian based livecd called Elive.

---

### Post by lvleph on 2007-12-19
What type of WiFi card do you have? You may need to blacklist the drivers in /etc/modprobe.d/blacklist

In my case I have Realtek 8185, so I had to add
r8185
r8180
to that blacklist file.

---

### Post by Drone4four on 2007-12-19
> **lvleph said:**
> What type of WiFi card do you have? You may need to blacklist the drivers in /etc/modprobe.d/blacklist

In my case I have Realtek 8185, so I had to add
r8185
r8180
to that blacklist file.

It's not WiFI.  The connection is wired.

---

### Post by Drone4four on 2007-12-19
Pici on FreeNode thinks that linux-restricted-modules is not installed.  The fix? Reboot into the alternate kernel mode and enter: `sudo aptitude update` and then a `sudo aptitude  full-upgrade`

---

### Post by Drone4four on 2007-12-19
Those two commands downloaded and installed a new kernel and a few other apps, but the error messages persist.

---

### Post by Drone4four on 2007-12-19
bump

---

### Post by lvleph on 2007-12-19
Sorrry I won't be much help with this problem. I am sure someone must know something.

---

### Post by Drone4four on 2007-12-20
It's ok lvleph.  

I hope someone more knowledgeable can provide some advice without me having to bump this thread to the top. =D

---

### Post by rustybronco on 2007-12-20
Not more knowlegeable, but did you check the cd for errors first?

---

### Post by Drone4four on 2007-12-20
You mean the installation CD?  Why would I want to check the install CD for errors?  Ubuntu Gutsy has run just fine for a week or so.

---

### Post by rustybronco on 2007-12-20
> **Drone4four said:**
> You mean the installation CD?  Why would I want to check the install CD for errors?  Ubuntu Gutsy has run just fine for a week or so.Yes I mean the install cd, i've seen it be the root of problems before, just a thought.

---

### Post by Drone4four on 2007-12-21
On FreeNode, mitchp says: > Invert314: You would need to download the .deb package for it onto your hard drive while using the liveCD, then disable the networking script so it'll boot, then apt-get remove network-manager.  Then double click the .deb package to reinstall it.  However when you remove it you might delete your dependencies.  Let me go look at the debian site

---

### Post by Drone4four on 2007-12-21
Now mitchp> Invert314: ok well renaming the S40networking script in /etc/rcS.d   

put an underscore  in front of it to prevent it from loading but so you can easily change it back and if that works then that should help narrow it down.  It seems like the problem is iwth hardware that network manager is trying to load.

i made the change. now to reboot

edit:sp

---

### Post by Drone4four on 2007-12-21
it worked. ubuntu loads and i still have a connection to the internet.  thanks mitchp!

---


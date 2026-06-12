---
title: "Sillysod Can't Use MP3 Player In Ubuntu 9.04"
date: 2009-08-13
forum: New to Ubuntu
---

### Post by SillySod on 2009-08-13
I have just upgraded to Ubuntu 9.04 but when I plugged in my MP3 player to a USB port, nothing happened.

It used to show up in Places as a 1GB drive which I could then access to copy files to and from.

How can I fix this?

---

### Post by Buuntu on 2009-08-13
Try looking in /media for it.
If it's not there copy+paste the output of ```
lsusb
```
 
To mount automatically:
 
Go to System > Administration > Users and Groups click on the your user account then click on Properties. Go to the User Privelages tab and make sure "Access external storage devices automatically" is checked.
If it STILL doesn't work, go to "System > Preferences > Removable Drives and Media" and make sure all "Mount removable drives when ... " are checked.

---

### Post by SillySod on 2009-08-14
This is what lsusb gave me; the first entry shows up when the MP3 player is plugged in.  I tried all the other things, but they were already set correctly.

```

Bus 001 Device 009: ID 0402:0611 ALi Corp. 
Bus 001 Device 004: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 003: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 002: ID 0409:0059 NEC Corp. HighSpeed Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

I could use my MP3 player in Ubuntu 8.10 so I don't know what has happened.

---

### Post by Buuntu on 2009-08-14
So you did all the stuff I suggested and none of it worked?

---

### Post by karamu on 2009-08-15
I have the same issue- on my Dell Mini 10v- on the pre installed Dell version of Hardy my Toshiba Gigabeat mounted as a USB drive and worked fine- synced perfectly with Banshee.

But, I installed Jaunty as I got fed up with Dellbuntu and since then I haven't been able to use my MP3 player- when I plug in the USB cable it seems to mount momentarily- the icon appears on the desktop and the nautilus window appears.

However, the icon disappears and the nautilus window switches to the media folder which doesn't display any USB drives.

The settings mentioned were set correctly and when I try to run lsub I get a "command not found" error.

Any ideas?

---

### Post by Barrucadu on 2009-08-15
> **karamu said:**
> The settings mentioned were set correctly and when I try to run lsub I get a "command not found" error.

That would be because the command is "lsusb", not "lsub"

---

### Post by SillySod on 2009-08-15
> **Buuntu said:**
> 
To mount automatically:
 
Go to System > Administration > Users and Groups click on the your user account then click on Properties. Go to the User Privelages tab and make sure "Access external storage devices automatically" is checked.
If it STILL doesn't work, go to "System > Preferences > Removable Drives and Media" and make sure all "Mount removable drives when ... " are checked.

I tried all these things, but everything that you said to check was already checked.

On the display on the MP3 player it says "MTP" when I plug it in to a USB port.  I'm pretty sure it used to say this in the previous version of Ubuntu, but it used to mount automatically.  I haven't done anything to my MP3 player since the upgrade, but now nothing happens.

---

### Post by Bartender on 2009-08-15
I'm new to PMP's but everything I read said to set your player to MSC or in some cases "Auto".  My wife's new Fuze works fine in "Auto" but I'm sure it's going to MSC mode when jacked into the Ub 9.04 machine.
Apparently if you change the mode to MSC and can connect, the PC will not see the data that was stored on the PMP in MTP mode.

As I understand it, MSC mode allows the device to act like a simple USB drive.  MTP activates Microsoft-based DRM stuff.

---

### Post by karamu on 2009-08-16
> **Barrucadu said:**
> That would be because the command is "lsusb", not "lsub"

OK, good point. I get 

Bus 001 Device 003: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device
Bus 001 Device 002: ID 174f:1403 Syntek 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 413c:02b0 Dell Computer Corp. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

when I run it

---

### Post by SillySod on 2009-08-17
> **SillySod said:**
> On the display on the MP3 player it says "MTP" when I plug it in to a USB port.  I'm pretty sure it used to say this in the previous version of Ubuntu, but it used to mount automatically.  I haven't done anything to my MP3 player since the upgrade, but now nothing happens.

I tried again last night, and it worked!  I pressed the button on the front of my MP3 player, and after a few seconds, the drive was mounted.

I didn't have to do this in Ubuntu 8.10, it did it automatically, but at least I now know how to do it.

---

### Post by karamu on 2009-08-24
For what it's worth, I managed to resolve my issue with my Gigabeat- I installed the Alpha 3 of Karmic and now the MP3 automounts just as it did previously in my Dell Hardy. Only thing is the OS is still in aplha and is somewhat buggy..... Not too long until the full release though!

---


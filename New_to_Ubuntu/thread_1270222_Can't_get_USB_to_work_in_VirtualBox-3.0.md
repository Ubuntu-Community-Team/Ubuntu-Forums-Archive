---
title: "Can't get USB to work in VirtualBox-3.0"
date: 2009-09-19
forum: New to Ubuntu
---

### Post by andyzammy on 2009-09-19
Hi all,

I have installed VirtualBox 3.0 and i'm having a lot of trouble trying to get usb support to work. i have downloaded VB from the following page [http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads) because as far as i can tell thats the one that gives usb support.

I have installed guest additions and put a blank filter up but all devices remain uavailable.

Any help would be greatly appreciated.

Zammy

---

### Post by Graphite on 2009-09-19
Yes, virtualbox PUEL edition is the one you want to get USB working.

Howtoforge seems to be down at the moment, but when it comes back up, [_this page_](http://www.howtoforge.com/virtualbox-2-how-to-pass-through-usb-devices-to-guests-on-an-ubuntu-8.10-host) has very clear instructions.

From what I can remember, you need to open up "Manage Groups" / "Manage users" and find a group called "vboxusers". Add yourself (i.e. whatever user account you'll be logged in as when running virtualbox) to that group.

Then log out and log back in.

You might also need to create a new group called usbfs and add yourself to it, then log out then back in again.


I believe this gives virtualbox the permissions necessary to access the USB controller. Without those permissions, the host OS doesn't allow the guest inside virtualbox to see what's mounted.

---

### Post by andyzammy on 2009-09-19
> **Graphite said:**
> You might also need to create a new group called usbfs and add yourself to it, then log out then back in again.

this did the trick, thank you very much!! probably my poor searching skills but couldn't find this solution anywhere.

:D

---


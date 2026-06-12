---
title: "&quot;no configuration chosen from 1 choice&quot; -- usb-ethernet stopped working?"
date: 2006-10-27
forum: Networking &amp; Wireless
---

### Post by Jussi Kukkonen on 2006-10-27
Been trying to solve this myself, but I feel I need a little help...

I have a Edimax USB-ethernet adapter that worked out-of-the-box with Dapper (using the pegasus driver). Upgrade to Edgy broke it, although booting into an old kernel works as a work-around. I have tried to document the details in the [bug report ]("https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/67848").

Question:
The device seems to be recognised all right (*lsusb* shows it), but when the driver should get loaded this is logged instead: ***usb 1-1.3: no configuration chosen from 1 choice***. What's going on, what does that mean?

---

### Post by Jussi Kukkonen on 2006-10-27
Ok, looking at the code it seems that insufficient power could be a reason (or rather insufficient expected power). The check for this was only added in 2.6.16 --  I'll investigate this.

EDIT:yep, that's it: [http://lists.debian.org/debian-kernel/2006/07/msg00506.html](http://lists.debian.org/debian-kernel/2006/07/msg00506.html)

So, it wasn't a bug, but a feature -- it's still annoying since the device worked fine in Dapper...

---

### Post by Jussi Kukkonen on 2006-10-27
For the benefit of anyone else in the same situation:

A workaround that restores the old functionality:
```
echo -n 1 > /sys/bus/usb/devices/1-1.3/bConfigurationValue
```
as root. 
 Replace 1-1.3 with the usb device address (from e.g. *dmesg*). Also replace the echoed value "1" with whatever value your device normally uses.

Using this of course means that no-one guarantees how many amperes your usb devices get... I wouldn't suggest using this for e.g. usb hard drives.

---

### Post by javaJake on 2006-10-28
I'm having the same issues, except when plugged directly into my computer. I think I have to run that command before the device's drivers activate, but how...?

---

### Post by secundar on 2006-11-26
I can't run that cammand at all. Tried sudo, then sudo su but i still get "permission denied"!

I'm so sorry i upgraded to Edgy.](*,)

---

### Post by secundar on 2006-11-27
nevermind. i ended up reading a bit about another bug causing intermittent keyboard failure... [https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/39315](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/39315)

As soon as I killed gnome-power-manager and reinserted my mouse it came back to life... and stayed that way. Strange.

---

### Post by javaJake on 2006-11-27
> **secundar said:**
> I can't run that cammand at all. Tried sudo, then sudo su but i still get "permission denied"!

I'm so sorry i upgraded to Edgy.](*,)

I'm sorry as well, but someone's got to do the testing. :D
Anyway, that error is most likely because you are echoing into a file that doesn't exist, and the system will absolutely NOT let you create that file (which is good).


**See my next post (which is directed at everyone who's viewing this thread with the same issue) for complete step-by-step instructions that will allow your system to do this for you whenever you plug in your device.**

---

### Post by javaJake on 2006-11-27
**_ATTENTION Everyone Who Has This Issue!_**
I have found a really great work-around based on the solution mentioned here that has your system doing the work for you whenever your device is plugged in. It's at my HOWTO, who's link is below.

**Please read the following notes before continuing. I'd really really really appreciate it!**

[list][*]Please realize that it was meant for the WUSB54GS device! Please change the idProduct and idVendor numbers mentioned in the HOWTO to the appropriate numbers for your system. If you need help figuring this out, let me know here, not at that HOWTO.[*]Please do not ask for any help at the WUSB54GS thread unless you are using a WUSB54GS device! Ask for help here if it is related to this issue! You can contact me using anything in my profile for help if you need.[/list]

[http://www.ubuntuforums.org/showthread.php?t=225206](http://www.ubuntuforums.org/showthread.php?t=225206)
*(Scroll down or search for "Getting WUSB54GS to Work in Edgy")*

---


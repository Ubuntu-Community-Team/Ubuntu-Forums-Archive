---
title: "iftab and resume from standby"
date: 2006-11-11
forum: Networking &amp; Wireless
---

### Post by akao on 2006-11-11
Hi,

I have a thinkpad with a Intel 2200BG mini-pci wireless network.  When I do a clean install, the the network card is assigned to "eth1".  By changing iftab, I rename it to "wlan0".

This works right on bootup, but when the laptop resumes from standy or hibernation, it reverts back to "eth1".  Has anyone else encounter this?  How do you solve this?  What's the problem?

I can get it back it wlan0, by stopping networking, and restarting udev.  I don't think this is a viable solution.  


Thanks!

---

### Post by akao on 2006-11-12
Hi,

I haven't received any replies, so hopefully no one else is encountering this issue.  However, for posterity's sake I am detailing my workaround to this issue.

Modify /etc/acpi/resume.d/35-modules-load.sh
Add the line "sleep 3" right before:
# Load any drivers that we removed
for x in $MODULES; do
    modprobe $x;
done

What this modification does, is that it makes the system wait 3 seconds before loading all the modules, which for me, included the driver for the network card.


One very interest thing that I found is that you can recreate the problem I have, without even sleeping.  After I modify /etc/acpi/sleep.sh and comment out the line that does the actual sleep, I can reliably recreate the problem.


Cheers.

---

### Post by FrodoB on 2006-11-12
Curious, why do you want to change the name? Wireless device names have always included the ethX as well as wlanX and others.

---

### Post by akao on 2006-11-12
I didn't know that they have.  It  makes intuitive sense to me that they are treated so very differently, and so deserve to be named differently.  Practically, the Network Settings application that comes default with Ubuntu, shows a graphic of a regular ethernet card, when it is named eth1, but one of a wireless card when it is named wlan0.  The configuration screens also assume it is an ethernet card.

Perhaps you uses a better application to configure their wireless cards?

---

### Post by tmeller on 2008-02-04
Ok, this thread is somewhat outdated.
Nevertheless, I have a problem on edgy with my network interfaces.

My IBM T40 has 2 NICs, a wired one and a builtin IPW2100-based WLAN.
Additionally, I have a PC-card to get into several networks for professional reasons. (don't mind)

When hibernating, everything works ok, but after resume the lan interfaces sometimes get mangled, i.e. eth0 is eth2, eth1 is eth0, eth2 rests disabled and such.
%(

As far as I understand, this is what happens:

on hibernate, /etc/acpi/suspend.d/55-down-interfaces.sh  is called and removes my PC-card driver, eliminating eth0 this way.
Then, it shuts down all (remaining) NICs in this order:

eth1
eth2
lo
vmnet1 (ifdown doesn't impress this interface, ifconfig does but is not applied on resume)
vmnet8 (same as above. both are already shut down at this time as they rely on ethX)
irdaxxx (?)

the 70-modules-unload.sh removes some modules (dunno which) in a static order.

On resume, 
/etc/acpi/resume.d/35-modules-load.sh starts modules in the same order as they were removed, then the pc-card and the following
/etc/acpi/resume.d/62-ifup.sh starts up in this order:

eth0
eth1
eth2
lo
vmnet1 (doesn't get up, ifup is of no use)
vmnet8 (same as above)
irdaxxx (whatsoever, I don't mind at the moment)

the result is a completely mangled networking - module - IP mess.
/etc/iftab is ignored on hibernate/resume.

Is there a smart way to manage this problem?
If not, I will develop one if someone can explain to me, what is done, why and in which order on hibernation.

Somebody interested?

Help!
;-)

I am no dummy user, doing LinuX since 1994, but mostly on SuSe and RedHat.
Debian/Ubuntu is really new to me.
Once I understand the philosophy I will get to a solution for sure.

---


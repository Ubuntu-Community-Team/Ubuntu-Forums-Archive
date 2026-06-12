---
title: "Lighter Ubuntu a Fix for Low memory/bad Video Card Driver?"
date: 2008-12-29
forum: New to Ubuntu
---

### Post by Teasdale on 2008-12-29
I read the question about whether a lighter Ubuntu exists, and it's made me wonder whether a lighter Ubuntu might help with my problem.

I have computer that's 5-6 years old, it ran WinXP fine, but I installed Ubuntu a year ago and it's mostly slow ever since. I've tracked the problem down to an nVideo card that Ubuntu doesn't have a driver for - I've scoured the internet, tried various fixes, but nothing has worked. So my video card is sharing memory with my PC, and that makes it develop problems when I use Open Office, GIMP, preview screensavers, or view jpg images with Mirage or the default image viewer. I have to restart a lot to freshen up the memory because it locks up a lot when I do any of those kinds of things. 

Would a lighter version of Ubuntu make this computer run faster? And what would be the limits of a lighter Ubuntu? What would the computer not be able to do? I guess I'm not quite sure what "lighter" means - does it mean that it doesn't have the ability to watch YouTube videos, for example?

---

### Post by oilchangeguy on 2008-12-29
what are your computers specs? and what version of ubuntu are you using now?

---

### Post by balaknair on 2008-12-29
> **Teasdale said:**
> I read the question about whether a lighter Ubuntu exists, and it's made me wonder whether a lighter Ubuntu might help with my problem.

I have computer that's 5-6 years old, it ran WinXP fine, but I installed Ubuntu a year ago and it's mostly slow ever since. I've tracked the problem down to an nVideo card that Ubuntu doesn't have a driver for - I've scoured the internet, tried various fixes, but nothing has worked. So my video card is sharing memory with my PC, and that makes it develop problems when I use Open Office, GIMP, preview screensavers, or view jpg images with Mirage or the default image viewer. I have to restart a lot to freshen up the memory because it locks up a lot when I do any of those kinds of things. 

Would a lighter version of Ubuntu make this computer run faster? And what would be the limits of a lighter Ubuntu? What would the computer not be able to do? I guess I'm not quite sure what "lighter" means - does it mean that it doesn't have the ability to watch YouTube videos, for example?

Lighter= fewer snazzy effects, less eyecandy, audio previews, cute Gnome applets...
Xubuntu uses XFCE instead of Gnome(the default in Ubuntu) and is designed to use fewer system resources but still be fully functional and secure.

You can watch youtube videos on Xubuntu just as on Ubuntu(just install xubuntu restricted extras to get flash player). It comes with a web browser(Firefox 3), file browser(Thunar), word processor(Abiword), spreadsheets app(Gnumeric), chat client(Pidgin) etc. just like Ubuntu and Kubuntu. The default apps on Xubuntu use fewer system resources.

In addition, you can install any Gnome or KDE apps you want on Xubuntu(but this obviously will impact system performance).

---

### Post by Teasdale on 2008-12-29
The post where I asked about my video card/memory is here:
[http://ubuntuforums.org/showthread.php?t=906900](http://ubuntuforums.org/showthread.php?t=906900)
Based on the responses to that thread, I've ordered a new System76 desktop, but it would be nice to make this one useful enough to pass on to a friend. I'm squeamish about opening up the box, so rebuilding it  isn't really an option I'm considering. I've replaced drives and added RAM to a PC before, but the whole process makes me nervous.

I'm running Ubuntu 7.10

I'm not quite sure what information would be helpful and what would be too much to sift through.
The full hardware details are here:
[http://home.comcast.net/~tjlm/hardware.html](http://home.comcast.net/~tjlm/hardware.html)
And here's what I collected from that:

Motherboard: ASUS A7N266-VM ACPI BIOS Rev 1004/AA (08/23/2002) (size: 64KB, capacity: 192KB)

AMD Athlon(tm) Processor; 1666MHz (capacity: 2GHz, width: 32 bits, clock: 33MHz)

L1 Cache; size: 128KB, capacity: 128KB

L2 Cache; size: 256KB, capacity: 8MB

memory: slot (System board or motherboard)
size: 256MB capacity: 512MB

DIMM DRAM Synchronous; size: 256MB, width: 64 bits

Video card nForce CPU bridge; width: 32 bits, clock: 66MHz
configuration:	
driver=agpgart-nvidia
module=nvidia_agp

RAM memory: nForce 220/420 Memory Controller
width: 32 bits
clock: 66MHz (15.2ns)

memory:1
RAM memory
product:nForce 220/420 Memory Controller
physical id: 0.2
version: b2
width: 32 bits
clock: 66MHz (15.2ns)
configuration: latency=0

memory:2
RAM memory
nVidia Corporation
physical id: 0.3
version: b2
width: 32 bits
clock: 66MHz (15.2ns)
configuration: latency=0

nForce ISA Bridge
width: 32 bits, clock: 66MHz

serial: SMBus
nForce PCI System Management
width: 32 bits, clock: 66MHz
configuration: driver=amd756_smbus

---

### Post by Teasdale on 2008-12-29
> **balaknair said:**
> word processor(Abiword)

<snip>

The default apps on Xubuntu use fewer system resources.

How interesting - I installed AbiWord to see how I like it, and I think it does everything I need Open Office to do - columns, prints, changes fonts - and it's so much faster! It looks like it will even open Word documents.

I just might uninstall Open Office from this computer altogether. I was running it in the QuickStart menu; maybe that alone was tying up resources?

---


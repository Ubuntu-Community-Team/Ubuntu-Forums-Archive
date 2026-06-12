---
title: "No operating system"
date: 2010-02-18
forum: New to Ubuntu
---

### Post by raceon4 on 2010-02-18
I have been running Ubuntu 9.10 netbook remix for quite awhile with no issues.  Today when I opened the lid on my laptop I just had a blinking cursor.  I powered down and restarted only to get the following.  It is a Dell Mini 9.

Intel UNDI, PXE-2.1 (build 082)
Copyright (C) 1997-2000  Intel Corporation

For Realtek RTL810E/8102E PCI-E Ethernet Controller v1.08 (080408)
PXE-E61: Media test failure, check cable
PXE-M0F: Exiting PXE ROM
Operating System not found


I am lost on what to do next.  I did look in the BIOS and network boot was last.  The hard drive still seems to show up as the first boot option.  Is there anything I can do to get my computer back up and running?

---

### Post by hortstu on 2010-02-18
try running it from a live cd and try to see what's going on with your drive, is all your data still there?  ...sorry I can't help you much but at least this response will get you back to the top of the list.

---

### Post by undecim on 2010-02-18
> **hortstu said:**
> try running it from a live cd and try to see what's going on with your drive, is all your data still there?

+1

Everything up to the "Operating System not Found" message is your computer trying to do a network boot because it couldn't find a bootable drive. In other words, your BIOS doesn't see a boot sector on your hard drive.

It is likely a failed drive, but just to be sure, use a live cd to see if your drive shows up. If you don't have a cd drive, use unetbootin on another computer to create a live thumb drive.

---

### Post by raceon4 on 2010-02-18
Haven't had a chance to make a live usb stick yet.  But I was wondering if the fact that when I pull up the BIOS I still see the amount of data that should be on the disk showing up.  Does anyone know if that is a good sign?

---

### Post by RJARRRPCGP on 2010-02-18
Check the BIOS boot settings, they may have gotten screwed up, because of a bad CMOS battery. You should check to see if you can replace the CMOS battery.

---

### Post by undecim on 2010-02-18
> **raceon4 said:**
> Haven't had a chance to make a live usb stick yet.  But I was wondering if the fact that when I pull up the BIOS I still see the amount of data that should be on the disk showing up.  Does anyone know if that is a good sign?

That tells us the BIOS can see the drive, but we won't be able to tell much until we know what the live USB can see.

---

### Post by raceon4 on 2010-03-30
Ok so I got the live USB up and running.  When I run diskutility it says that my hard drive is healthy but unpartitioned.  it also says it is unrecognized.  What do you think is there any of my old data still there? do I need a new drive?  Not sure where to go now.

---

### Post by Paqman on 2010-03-30
> **raceon4 said:**
> When I run diskutility it says that my hard drive is healthy but unpartitioned.  it also says it is unrecognized.

Sounds like your drive is physically ok, but the filesystem is broken.

Is it a traditional magnetic drive, or an SSD?

---

### Post by raceon4 on 2010-03-30
It is SSD.

---


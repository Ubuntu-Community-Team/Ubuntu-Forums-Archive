---
title: "Can't install OS - period"
date: 2011-08-13
forum: New to Ubuntu
---

### Post by 'Cue Man on 2011-08-13
OK I've searched the threads and can't find anything so here goes.

I'm trying to install Ubuntu on a clean PC (no windows). I downloaded the 11.04 ISO and burned it to CD on another computer. I installed the CD into the clean PC and booted it up. I get a desktop, then I get an 'Ubuntu experienced an unrecoverable error' message and that it needs to boot in desktop mode. I click OK ( like a have a choice) and the monitor then goes black and after 15 minutes the PC shuts off. I tried another image using a different pack of CDs. Same thing. At work I downloaded 10.04 LTS and tried booting that: I/O error.  Didn't even get to the desktop. Any ideas or should I just give up?

---

### Post by -kg- on 2011-08-13
I think we'll need the make and model of the computer you're trying to install Ubuntu on, and if there's any add-on hardware, we'll need information on that.  That would include RAM upgrades, new CD-drives, video cards, etc.  Also, how old is the computer?

Also, when you downloaded those images, did you check the [md5sum checksums]("https://help.ubuntu.com/community/UbuntuHashes") before you burned the images to disk?  Did you check the integrity of the burn after you burned them?

There are a variety of things that will cause such errors; hardware malfunction, hardware incompatibility, and/or download- or burn-time errors or corruption.  We'll need more information to determine your specific problem(s) (yes, it might be more than one).

---

### Post by McLinux O'Debian on 2011-08-13
Run lspci from another liveCD from another distro and paste the info here, that should be a decent method of getting us the information.

---

### Post by amjjawad on 2011-08-13
> **'Cue Man said:**
> OK I've searched the threads and can't find anything so here goes.

I'm trying to install Ubuntu on a clean PC (no windows). I downloaded the 11.04 ISO and burned it to CD on another computer. I installed the CD into the clean PC and booted it up. I get a desktop, then I get an 'Ubuntu experienced an unrecoverable error' message and that it needs to boot in desktop mode. I click OK ( like a have a choice) and the monitor then goes black and after 15 minutes the PC shuts off. I tried another image using a different pack of CDs. Same thing. At work I downloaded 10.04 LTS and tried booting that: I/O error.  Didn't even get to the desktop. Any ideas or should I just give up?

Hello and Welcome :)

Please have a look at:

[http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)

and

[http://ubuntuforums.org/showthread.php?t=801404](http://ubuntuforums.org/showthread.php?t=801404)

No, the above won't fix your issue, but will help you in your Ubuntu Journey :)

Please, list your Hardware Details.
If your machine is 32bit, then you need to install the 32bit version of Ubuntu.
If your machine is 64bit, then you need to install the 64bit version.

After you download Ubuntu, please check MD5SUM:
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

After that, try to boot from your LiveCD and tell us what will happen :)

---

### Post by cmcanulty on 2011-08-13
you can also use unetbootin to make a flash usb drive with ubuntu or many other distors to try booting from. Did you hit the bios key as you boot to make sure the correct boot device is selected.Usually f2 f10 or f12 will get you to bios (has to be done right as computer powers on) also if those don't work try another f key or DEL

---

### Post by 'Cue Man on 2011-08-14
Hey,

Thaks for all the responses so far. I must apologize though for not getting back to this thread sooner. I just got off of work and this is the first chance to respond.

You asked for system specs so here they are

Compaq Evo D510 CMT
P4 2.0 GHz
40Gb HD
RAM 512Mb
48X CD ROM
16X DVD-RW
Onboard Video (chipset 845G)
Onboard NIC


MD5s hashes on both files do match the listy so they're good. Also someone asked to check the boot sequence - yeah that's solid as well. So as I said earlier, any ideas?

---

### Post by -kg- on 2011-08-16
Well, while the computer seems to be a little old, and the specs not exactly spectacular, it should ***at least*** boot to the Live CD (especially the 10.04 CD) and run.  Since you've checked the md5s and they check out, I'd start looking hard at a hardware malfunction or compatibility issues.

Have you tried booting to the Live CD with both CD drives?  I've had CD drives go out on me in exactly the same way.  All of the sudden they'd start having read errors which would throw me out of whatever installation or other thing I was trying to do.  If you haven't tried booting with "the other" drive, that's what I would try first.

From the specs on your computer (and through a little "Googling"), I really don't see anything that jumps out at me as far as the compatibility issue...perhaps someone else might have had some different experiences.

---


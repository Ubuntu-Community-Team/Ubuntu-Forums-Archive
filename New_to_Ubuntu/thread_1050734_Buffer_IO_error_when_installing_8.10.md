---
title: "Buffer I/O error when installing 8.10"
date: 2009-01-26
forum: New to Ubuntu
---

### Post by mount_evans on 2009-01-26
I am trying to install the 64 bit version of 8.10.  I get the following error message repeated over and over again:

**[INDENT]Buffer I/O error on device sr1, logical block 49165[/INDENT]**

I get this if I try to install Ubuntu, run it without installing it, or check the CD for defects.  I can run the memory test or boot to first hard drive just fine.

The first time I tried to install, I also got a complaint about there not being a hole in the memory.  I looked in my setup, and there was an option that said something about re-mapping memory around a hole, so I disabled it.  I no longer get that particular message.  But I get the chain of Buffer I/O error messages either way.


Any idea what the problem might be?  Do I have a computer that cannot run Ubuntu?

---

### Post by diablo75 on 2009-01-26
Someone else might know what the exact cause is... but I've seen errors like that before and more often than not, waiting long enough will cause the installation to continue without a hitch.  Try to boot the live CD again and ignore the errors for about 3 minutes to see if it moves on.

I'm curious:  What kind of hardware are you running on?

---

### Post by mount_evans on 2009-01-26
> **diablo75 said:**
> Someone else might know what the exact cause is... but I've seen errors like that before and more often than not, waiting long enough will cause the installation to continue without a hitch.  Try to boot the live CD again and ignore the errors for about 3 minutes to see if it moves on.

I'm curious:  What kind of hardware are you running on?

The motherboard is a XFX 8200 GeForce, AMD Sempron(tm) Processor LE-1250

---

### Post by diablo75 on 2009-01-26
What types of drives (hard drive, CD/DVD, Flash, etc.) are attached?

---

### Post by mount_evans on 2009-01-26
> **diablo75 said:**
> What types of drives (hard drive, CD/DVD, Flash, etc.) are attached?

I have two SATA drives made by Seagate; one is 1.5 Terabyte, and has been partitioned into 300GB for Windows XP, the rest for the accumulation of stuff.  The second one is 500GB, has not yet been formatted, and is where I was going to put Ubuntu.

The DVD R/W and DVD R, CD R/W drives are old and IDE-based.  Oh, there is also a floppy drive that still works.  I don't think any of my thumbdrives were attached at the time.

---

### Post by mount_evans on 2009-01-26
OK, I removed a CD that was sitting in the second drive, and I no longer get the Buffer I/O messages.  Yay!  Instead, the installation just sits there with the prompt (initramfs) and waits for me to enter a command.  I can type "help" to get a list of commands, but none of those is "continue the automatic installation for people who know nothing about Linux".

---


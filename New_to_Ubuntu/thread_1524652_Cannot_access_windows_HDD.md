---
title: "Cannot access windows HDD"
date: 2010-07-05
forum: New to Ubuntu
---

### Post by Samotl on 2010-07-05
I'm new to Linux so please excuse the (probably) nauseatingly repeated question.

I've installed Kubuntu 10.0.4 from the live CD onto en external hard drive (connected via USB) to be extra certain I don't interfere with my normal drive, I removed it from the laptop. The Installation went surprisingly well and I installed all the updates and bug fixes.

The problem arose when I replaced the drive (running XP Pro SP3) and tried to access it from Kubuntu. It shows up in Dolphin, correctly identified and separate from the external, but when I try to access I get the following error message:

The system responded: mount: according to mtab, /dev/sdb1 is already mounted on / mount failed

Is this because of my unusually paranoid installation method? and is there any way to fix it without reinstalling? (I don't really want to download all the updates and things again)

---

### Post by mikewhatever on 2010-07-05
So, you replaced the drive and tried to access it... What's that supposed to mean. Which one of the two did you try accessing, the replaced or the replacing one?
Anyway, whichever it is, make sure XP is shut down properly and not suspended to disk.

---

### Post by Samotl on 2010-07-06
Okay, just to clarify, here's what I did:
1. I removed the drive.
2. I connected the external via Usb.
3. I booted using the Live CD and installed Kubuntu.
4. I shut down and put the drive back (re-placed it)
5. I started the computer and booted Kubuntu (on the external).
6. When I tried to access the "internal" I got that error at the bottom of the Dolphin window.

---

### Post by Samotl on 2010-07-21
I've received this problem again while using the same Kubuntu-installed drive in another computer. It seems that the installation has a problem with drives that have Windows installed as an OS. Perhaps this is because the multi-boot option is turned off?

---


---
title: "Installed Ubuntu and now I can't get to XP"
date: 2010-03-15
forum: New to Ubuntu
---

### Post by Paul F on 2010-03-15
Hi,

I just installed Ubuntu on a Compaq Presario (S5100NX) that already had XP home on it.

I had pre-configured the partitions using Partition Magic so that the Ubuntu OS partition (ext3)would be right behind the XP OS.

The install went fine, no problems.

BUT... Now when I reboot the machine, I can't select an OS to logon to. It's as if my keyboard isn't being recognized by the bootloader. I can't use up/down arrows or C or E commands, so it times out and goes right into the Ubuntu OS.

Any help would be appreciated!

---

### Post by audiomick on 2010-03-15
Is that a desktop with a USB keybourd? If so, try going into the BIOS and looking for something called "USB Legacy" or similar. Enable that (loads USB drivers with the BIOS instead of waiting for the OS) and see if that helps.

---

### Post by Paul F on 2010-03-15
> **audiomick said:**
> Is that a desktop with a USB keybourd? If so, try going into the BIOS and looking for something called "USB Legacy" or similar. Enable that (loads USB drivers with the BIOS instead of waiting for the OS) and see if that helps.

Spot On! Thanks Mate!!! 

If anybody else with a same/similar machine runs into this problem, you'll find the offending program switch under: FEATURES SETUP/USB function for DOS.

---

### Post by natravis on 2010-03-15
Make sure to mark your thread as solved.

---

### Post by audiomick on 2010-03-15
> **Paul F said:**
> Spot On! Thanks Mate!!! 

If anybody else with a same/similar machine runs into this problem, you'll find the offending program switch under: FEATURES SETUP/USB function for DOS.
Hey great! Glad you got it sorted.

---


---
title: "Dual Boot Grub lost on windows reinstall"
date: 2011-03-02
forum: New to Ubuntu
---

### Post by Pechkin000 on 2011-03-02
Hello, I am hoping someone can help me.

I had a dual boot Windows 7/Ubuntu.  I needed to do a c lean reinstall of windows.  So i formated windows partition and reinstalled.  So now, when laptop boots up it automatically boots into windows.  How can a restore GRUB and have it recognize both OS'es?
Any help would be appreciated greatly

---

### Post by Th3W1z4rD on 2011-03-02
I had the same problem when I was dual-booting Ubuntu and Vista and I upgraded to Windows 7. What happens is the Windows install overwrites the MBR that Ubuntu sets up when you install Ubuntu. This [article]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") should help

---

### Post by Eternal_Light on 2011-03-02
This has all the information you might need. If you follow it step by step nothing can go wrong (i think ^^).

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Pechkin000 on 2011-03-02
Thank you guys! Exactly what I needed!

---

### Post by garvinrick4 on 2011-03-02
Just a few links that help with grub problems:

[Grub/XP/Vista Bootloader - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1014708")
[HOWTO: Purge and Reinstall Grub 2 from the Live CD -]("http://ubuntuforums.org/showthread.php?t=1581099")
[ Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1581099") [Grub2 - Community Ubuntu Documentation]("https://help.ubuntu.com/community/Grub2#/etc/default/grub")

---


---
title: "Dual booting..."
date: 2009-05-06
forum: New to Ubuntu
---

### Post by jenova_skill on 2009-05-06
Well I've been using Only ubuntu on my computer for About a year and a half now...   I've just installed the Windows 7 RC thing on a separate partition. Now of course it's booting strait to windows 7.
How do i put my Boot selector back that way i can select what i want to boot to.

---

### Post by presence1960 on 2009-05-06
> **jenova_skill said:**
> Well I've been using Only ubuntu on my computer for About a year and a half now...   I've just installed the Windows 7 RC thing on a separate partition. Now of course it's booting strait to windows 7.
How do i put my Boot selector back that way i can select what i want to boot to.

To restore GRUB do this:
```
1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Go SuperUser (that is, type "sudo -s"). Enter root passwords as 
   necessary.
4. Type "grub"
5. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)". 
   Use whatever your computer spits out for the following lines.
6. Type "root (hd0,1)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
7. Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or 
   whatever your hard disk + partition # is, to install GRUB to a 
   partition.
8. Quit grub by typing "quit".
9. Reboot and remove the bootable CD.
```

---


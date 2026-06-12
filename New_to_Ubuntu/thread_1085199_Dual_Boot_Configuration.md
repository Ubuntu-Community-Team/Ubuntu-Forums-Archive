---
title: "Dual Boot Configuration"
date: 2009-03-02
forum: New to Ubuntu
---

### Post by keeneye on 2009-03-02
OK - in an effort to not wipe out my WinXP install, I grabbed another hard drive, put it in my system, disconnected the WinXP drive and installed Ubuntu 8.10.

I then added my WinXP to the bus as the slave and can access my data from that drive (configured fstab to mount it).

I would like to boot to XP every now and again (TurboTax and Quicken which I can't seem to get working with Wine).

I can't seem to get grub to 'see' the WinXP install (at least, I haven't been able to).  I used 'startupmanager' and it didn't 'see' the XP install.

Is there a way for me to get this to work?

Thanks!!!
Ed

---

### Post by presence1960 on 2009-03-02
I have the same setup: my primary HDD has Linux and the secondary has Windows. Here is what the end of your menu.lst file should have so Windows will appear in the Grub menu when you boot

> # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP
root		(hd1,0)
savedefault
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

you will need to edit the dev/sdb1 to your setup, also change the root (hd1,0) to your setup. You will need the 2 lines that contain map since your OS's are in separate physical HDD's. If your Ubuntu drive is the first boot and your windows drive is secondary boot it should work as is.

---

### Post by keeneye on 2009-03-03
presence1960 - excellent!! Copy/Paste/Reboot and I get WindowsXP when I need it.

Thanks!!!
Ed

---

### Post by presence1960 on 2009-03-03
> **keeneye said:**
> presence1960 - excellent!! Copy/Paste/Reboot and I get WindowsXP when I need it.

Thanks!!!
Ed

I am glad you got it working! Dive in there now and pass on what you learn.

---


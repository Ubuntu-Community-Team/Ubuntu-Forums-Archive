---
title: "how to creat a bootable pen drive of ubuntu 10.10???"
date: 2010-10-12
forum: New to Ubuntu
---

### Post by shiblu on 2010-10-12
i can't make bootable usb flash drive of ubuntu 10.10 useing 
"Universal-USB-Installer-1.8.0.4" as ubuntu.com suggest me:(:(:(.
any one can tell me how can i make a bootable ubuntu 10.10 using my pen drive.:confused::confused::confused:
 i have the .iso file.i don't want to burn it into cd.

---

### Post by andrewthomas on 2010-10-12
[https://help.ubuntu.com/community/LiveCD/Persistence](https://help.ubuntu.com/community/LiveCD/Persistence)

---

### Post by Porkchop62882 on 2010-10-12
UNetbootin.  Search for it in the software center.  Easy way to make bootable USB.

---

### Post by AndyM3 on 2010-10-12
+1 for [Unetbootin]("http://unetbootin.sourceforge.net/"), I've been using it for two years or so without any problem to put create Ubuntu LiveUSBs. Works on Linux and Windows.

---

### Post by beew on 2010-10-12
> **Porkchop62882 said:**
> UNetbootin.  Search for it in the software center.  Easy way to make bootable USB.

The problem with Unetbootin is that it doesn't support persistence (unless there is some big changes lately)so for my purpose it is pretty useless. I wish people would point that out before they recommend it enthusiastically to new users.

If OP uses Lucid he could simply use the startup disk creator to make a Maverick usb with persistence (I created a Maverick live usb with 3 G's of persistence using sdu so I can say for sure that it works)

If he uses other Linux distros he may want to check out multiboot
[http://liveusb.info/dotclear/]("http://liveusb.info/dotclear/") (the actual program interface is in English, guess that depends on where you download it)

If he uses windows, this looks like an awesome tool. [URL="http://www.linuxliveusb.com/"]http://www.linuxliveusb.com/

[/URL] Maverick is supported.

There are many better alternatives to unetbootin unless you only want to create a faster version of the live CD (no writing back)

---

### Post by AndyM3 on 2010-10-12
> **beew said:**
> The problem with Unetbootin is that it doesn't support persistence (unless there is some big changes lately)so for my purpose it is pretty useless. I wish people would point that out before they recommend it to new users.
If I understand correctly, the OP just wants to install Ubuntu *from* a USB pendrive, not *to* one.
[QUOTE=shiblu]i have the .iso file.i don't want to burn it into cd.[/QUOTE]
Unetbootin is the easiest-to-use program that I know does just that.

---

### Post by t0p on 2010-10-12
> **beew said:**
> The problem with Unetbootin is that it doesn't support persistence (unless there is some big changes lately)so for my purpose it is pretty useless. I wish people would point that out before they recommend it enthusiastically to new users.

OP didn't say he wants persistence.  He just doesn't want to burn the .iso to a CD.

If you don't want persistence, unetbootin is excellent.  It's my utility of choice when I want to make a bootable flash drive.

---


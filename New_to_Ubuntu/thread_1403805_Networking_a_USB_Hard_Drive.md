---
title: "Networking a USB Hard Drive"
date: 2010-02-10
forum: New to Ubuntu
---

### Post by Image0fman on 2010-02-10
How can I network my usb hard drive in linux so it can be mapped on other systems for easy sharing (win/lin)?

---

### Post by Morbius1 on 2010-02-10
It depends on how the usb drive is formatted, how you've mounted it, what desktop environment you're using, and what version of Ubuntu you are running. 

If it's FAT32 or NTFS, it's automounted when connected, you're using Gnome, and it's Karmic you might try Nautilus-share:

Right click on the directory you want to share in /media/whatever
Select "Sharing Options"
Check off all three boxes
Select "Create Share"

There's one more thing you need to do though. The USB device is automounted with you as owner and with Read / Write permissions for you only. The guest user on the lan will be denied access. To resolve this you need to do this:

Open **Terminal**
Type **gksu gedit /etc/samba/smb.conf**

Add the following line to the [COLOR=Blue][global] [/COLOR]section of smb.conf:
```
force user = *your_ubuntu_user_name*
```Save the file, exit gedit, and back in the Terminal type: **sudo service samba restart**

---

### Post by nhasian on 2010-02-10
[edit]

whoops nevermind, Morbius1 covered it pretty well.

---

### Post by Image0fman on 2010-02-10
Sweet. Thanks my friend

---


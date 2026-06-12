---
title: "Can't save files to flash drive"
date: 2010-11-22
forum: New to Ubuntu
---

### Post by Rocklobstaa on 2010-11-22
I really don't know much about Ubuntu. Normally I can find a how to somewhere but all I've been finding is installing Ubuntu with a flash drive.

Anyways, I can saves files from my flash drive to my laptop but can never save files from laptop to the flash drive. Regardless of the file type I get the error 

Error opening file <filename>: Permission denied

If anyone could help me I'd appreciate it. This problem is becoming very annoying.

---

### Post by rmockler on 2010-11-22
For a start:
Go to a command line and key in:  gksu nautilus
This will start nautilus with root privileges, navigate to the USB drive
Right click on it, click on properties, permissions tab
Check/change the permissions
Make sure you can create/delete files and have read/write access
If necessary, change the ownership to you

---

### Post by Rocklobstaa on 2010-11-23
Thank you so much.... That worked perfectly.

---


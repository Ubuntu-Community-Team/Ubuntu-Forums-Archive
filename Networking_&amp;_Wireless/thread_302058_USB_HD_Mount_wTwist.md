---
title: "USB HD Mount w/Twist"
date: 2006-11-18
forum: Networking &amp; Wireless
---

### Post by mpierce on 2006-11-18
Using v6.10 on my server and XP pro on my docked notebook.
Want to know if this type of mount is possible:

I want to mount a USB hard drive that is connected to the notebook.
I can mount the hard drives on the notebook C: (named - xp) and D: (named - data) with the command:

   sudo mount -t smbfs -o credentials/home/mpierce/.smbpasswd //192.168.1.252/data /data

If I try to mount the 320Gb USB (v2.0) drive attached to notebook, I get an error message: 
   tree connect failed: ERRDOS - ERRnomem (Insufficient server memory to perform the requested function.)

Server has plenty of memory but lacks 2.0 USB ports. Haven't found answer using Google.

---

### Post by mpierce on 2006-11-18
Is the question too hard? I need someone to tell me if this is possible to mount; if so, how? Where are the big brains?

---


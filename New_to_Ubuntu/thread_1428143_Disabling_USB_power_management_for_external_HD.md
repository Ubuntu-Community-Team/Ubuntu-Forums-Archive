---
title: "Disabling USB power management for external HD"
date: 2010-03-12
forum: New to Ubuntu
---

### Post by gallifrey on 2010-03-12
[FONT=Trebuchet MS][SIZE=2]Hello all, 
            I am just trying to get a little help with a problem I have  been having of late. I have an external Seagate drive (not a FreeAgent),  which spins down, but won't wake up. I have googled for answers, and  tried everything from sdparm to writing udev rules, but nothing seems to  be helping. The most I have accomplished is keeping the drive alive for  45 minutes or so before it fails to respond. What's more, it won't  mount on boot-up. 

I am wondering if this might be down to USB power management not playing  nicely with the HD's power management. Is there any way to disable the  USB power management??
Or is there something else that I am missing which might help?

Your help would be most appreciated.[/SIZE][/FONT]

---

### Post by empty_spaces on 2010-03-12
Not sure if this applies to external disks, but have you checked **Power Management** to make sure that the **Spin down hard disks when possible** option is unchecked in the AC and Battery Power tabs?

---

### Post by gallifrey on 2010-03-12
> **empty_spaces said:**
> Not sure if this applies to external disks, but have you checked **Power Management** to make sure that the **Spin down hard disks when possible** option is unchecked in the AC and Battery Power tabs?


That was the first thing I checked. I believe this is a common problem with Seagate external drives, though all the fixes I have found seem only to work for FreeAgent.

---


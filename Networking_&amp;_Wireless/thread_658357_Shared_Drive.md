---
title: "Shared Drive"
date: 2008-01-04
forum: Networking &amp; Wireless
---

### Post by baucomboy on 2008-01-04
Hey guys, I've looked around for a few days now searching for an anwer, but alas, to no avail, lol. 
Anyways, I just bought a mybook usb external drive, but I can't share it to my network...which was kind of the whole reason I bought it. I can share folders on that computer's internal HDD just fine...I can access the external drive from it's connected computer just fine......I can see the folder/drive on the network....but I can't access it. 
I've been using the GUI based share settings utility, i'm not at home now and i forgot the official name, but i have not used any terminal commands to change the samba settings. Do I have to? I wouldn't think so....
Is there maybe just a default security type setting to not allow sharing of external drives?

---

### Post by dannyboy79 on 2008-01-04
please post the contents from within your /etc/samba/smb.conf file.

also, please post your /etc/fstab as well the output from this command

sudo fdisk -l

that'll show all your hard disks and partitions on each one. I can help from there.

---


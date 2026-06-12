---
title: "Mount NTFS on a network?????"
date: 2007-08-13
forum: Networking &amp; Wireless
---

### Post by joegiampaoli on 2007-08-13
Ok, I am really in a big sort of problem here.

I am going to try to explain this as well as possible to avoid loosing you on the way :)

I have one machine which is dual boot, (XP/ubuntu) and inside ubuntu I installed a virtual server which is also ubuntu. Now, the thing is that I need the apache webserver to be able to have ONLY READ permission on that virtual machine to a mounted NTFS drive on my physical ubuntu. I am installing the ampache music php-script (if you are not familiar with it do not worry about it), and all my MP3 collection is in that NTFS drive, I can read it perfectly on my REAL ubuntu machine (Physical that is), mounted as a normal NTFS partition but when I try to mount it as a network drive inside the virtual network (giving the IP address of the physical machine) it seems to mount it, actually I can browse through it when I connect via SSH to the virtual machine, but when I try to make apache read the contents it seems to fail, since I believe apache (or www) has no read permissions on that mounted drive, leading me to not being able to add any music files to my ampache music web interface.

Is this possible or am I just asking for too much?

I just need Apache on the virtual machine to be able to read all the contents of that networked (virtually) NTFS drive.

I have not found a single page that explains this at all.....

Should I just convert that partition to FAT32 and avoid cracking my head?

---

### Post by kidders on 2007-08-16
Hi there,

I'm not sure why the underlying filesystem would make any difference. Does your web server have the appropriate permissions to access your files?

---

### Post by joegiampaoli on 2007-08-16
I already fixed it, I only needed to have apache added to a secondar group with tha same gid number that the drive is mounted on the NFS server machine, now it has read access:guitar:

---


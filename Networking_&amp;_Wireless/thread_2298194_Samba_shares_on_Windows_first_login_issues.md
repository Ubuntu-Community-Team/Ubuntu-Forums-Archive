---
title: "Samba shares on Windows first login issues"
date: 2015-10-09
forum: Networking &amp; Wireless
---

### Post by ricardo35 on 2015-10-09
Hi all,

Little backgroud:
I had a Ubuntu server (CLI) build from scratch for the first time with Samba shares. Running good.

I reinstalled it and this time I installed Ubuntu Desktop to use it as server. I also installed Samba and configured it with users and rights. This time with help from the GUI and CLI. Just to practice a bit. Everything is running smoothly and perfect. I can access the shares through Windows, perfect. Untill...... I reboot the server...

When I reboot the server and I go to my Windows PC, I see the shares but when I want to open them, they won't let me to access them. 
I need to go back to my server, login to Ubuntu desktop with my Admin account and then (go back to my Windows pc) I'm able to access the shares from the Windows pc (over and over again as long as the Ubuntu server is on ). 

Any ideas what this might be? Since I have movies on this server and a media player next to my tv, when I want to watch a movie I don't want to first go to the Ubuntu Server and log in and then go back to the couch to be able to log in through the media player. Same thing with the Windows pc by the way.

---

### Post by TheFu on 2015-10-10
Did you choose to encrypt your HOME and are the shares  under the HOME?
Move the media files outside the encrypted HOME  and share them from the new location.

---

### Post by ricardo35 on 2015-10-11
Hi TheFu, 

No I did not encrypt my home folder. The shares are on a USB harddrive, don't know if that matters.

---

### Post by TheFu on 2015-10-11
Please post the output from **testparm** and use "code tags" for better help. My signature for code-tag help.

Have you considered using a media server, not just shared storage?  Something like Plex Media Server, perhaps?

---

### Post by ricardo35 on 2015-10-11
No, I just want the shares. It's not only media I'm storing.

Here's the output :

```
rfrancocantero@fileserver:~$ sudo testparm
[sudo] password for rfrancocantero: 
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[Beheerder]"
Processing section "[Series]"
Processing section "[Films]"
Processing section "[Music]"
Processing section "[Clonezilla]"
Processing section "[Guest]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
    map to guest = Bad User
    idmap config * : backend = tdb

[Beheerder]
    path = /home/rfrancocantero/Shares/Beheerder
    valid users = rfrancocantero
    write list = rfrancocantero
    read only = No

[Series]
    path = /media/rfrancocantero/EHD1/EHD1/Shares/series
    valid users = wd, rfrancocantero
    read list = wd
    write list = rfrancocantero
    force user = rfrancocantero
    read only = No

[Films]
    path = /media/rfrancocantero/EHD1/EHD1/Shares/Films
    valid users = wd, rfrancocantero
    read list = wd
    write list = rfrancocantero
    force user = rfrancocantero
    read only = No

[Music]
    path = /media/rfrancocantero/EHD1/EHD1/Shares/music
    valid users = wd, rfrancocantero
    read list = wd
    write list = rfrancocantero
    force user = rfrancocantero
    read only = No

[Clonezilla]
    path = /media/rfrancocantero/EHD1/EHD1/Shares/clonezilla
    valid users = rfrancocantero
    write list = rfrancocantero
    force user = rfrancocantero
    read only = No

[Guest]
    path = /media/rfrancocantero/EHD1/EHD1/Shares/guest
    force user = rfrancocantero
    read only = No
    guest ok = Yes


```

---

### Post by TheFu on 2015-10-11
Ok - see how those mount locations are /media/rfrancocantero/?
Don't let the OS pick the location for mounted storage.  You need to manually set it and mount it through the fstab or autofs.

THAT is the issue here.  I've posted recommendations about mounting and better places many times here.  Search for my userid and "fstab" to find those. The short answer is **NEVER** use /media for permanent mounts.  /media is meant for temporary storage use.

---

### Post by ricardo35 on 2015-10-11
In other words, 

If I mount the shares outside Media, they should be accessible from boot? Without having me needing to log into the system first?

---

### Post by TheFu on 2015-10-11
No.  If you mount the storage using either (autofs or fstab entries) AND is it outside /media.  Being outside /media probably is not required, but it is best to keep permanent storage outside that area. If you need more reasons-  search as suggested.

BTW - if the storage is not using a linux file system, you'll  get to learn about mount permissions.

---

### Post by ricardo35 on 2015-10-11
That would be great. Going to try this a.s.a.p.
So, mounting the USB HDD outside MEDIA with autofs or fstab would fix the issue?

---

### Post by bab1 on 2015-10-11
> **ricardo35 said:**
> So, mounting the USB HDD outside MEDIA with autofs or fstab would fix the issue?
It is not the location that is causing your problem.  It is the *mount procedure * you are using that is causing your problem.  If you allow the partition to be mounted via the OS udev/udisks2 you will always have that partition mounted **only after you log in**.  This is because the procedure needs to know where to mount the partition based on the login (i.e. /media/<user-name> or something similar). The routine waits until you login to complete this type of mount.

Mounting the partition by /etc/fstab changes the mount procedure.  The partition is mounted at boot time as per the instructions in the fstab file.  The /media file system is traditionally used for temporary mounds for a already logged in user (usb stick or CD of DVD,  You can use /media, but if you have to mount it via fstab then why put the data there?  You could use /data or any other mount point.

I have no experience with AutoFS so I can't really comment about that other than to say that a static mount configuration on a server (fstab) is always preferable over a dynamic mount such as AutoFS.

The bottom line here is; your problem is not *where* you mount the partition but **how** you mount the partition.

---

### Post by ricardo35 on 2015-10-12
Hi Bab1,

Thank you for your clear explanation! It worked like a charm :D
Learned a lot today!

---

### Post by TheFu on 2015-10-12
I use autofs for USB connected disks.  Have seen flaky USB connections before and when a large truck passed by, the connection might drop - with the fstab, the machine would be very unhappy. With autofs, it would recover the mount in a  few minutes. Plus autofs has more mount options to deal with other non-perfect situations - which seems common for USB disks.

But I definitely agree with Bab1 - use fstab for SATA/SCSI/SAS connected disks.  For USB and eSATA disks, I much prefer autofs.

---


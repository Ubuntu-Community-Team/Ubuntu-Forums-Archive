---
title: "mounts"
date: 2009-05-16
forum: New to Ubuntu
---

### Post by dimitriv on 2009-05-16
hi

I have a 50gb partition/volume called Work which has a mountpoint of /media/work
Currently each time I start the pc I have to click on Places then Work before I can access files from the Work. Is there a way i can have that permanently/automatically mounted so it's available immediately on startup?

Also, on a VM machine guest I enter a sudo mount command to mount a share between the guest and host. Can I put this sudo mount command in a startup script or process so that it's already mounted on startup?

Thank you

---

### Post by akimatsu123 on 2009-05-16
I am relatively new to Ubuntu as well, so please correct me if i'm wrong. I believe you can get your system to auto-mount partitions at startup by adding it to /etc/fstab. 

[http://ubuntuforums.org/showthread.php?t=283131]("http://ubuntuforums.org/showthread.php?t=283131")
[http://www.tuxfiles.org/linuxhelp/fstab.html]("http://www.tuxfiles.org/linuxhelp/fstab.html")

---

### Post by hobo14 on 2009-05-16
> **dimitriv said:**
> hi

I have a 50gb partition/volume called Work which has a mountpoint of /media/work
Currently each time I start the pc I have to click on Places then Work before I can access files from the Work. Is there a way i can have that permanently/automatically mounted so it's available immediately on startup?

Also, on a VM machine guest I enter a sudo mount command to mount a share between the guest and host. Can I put this sudo mount command in a startup script or process so that it's already mounted on startup?

Thank you

Sounds like your disk is already mounted. But... you'd like to see a link on the desktop?

Navigate to /media/ and use the middle button to drag work/ onto your desktop and choose "make link".

---

### Post by dimitriv on 2009-05-16
hobo14, for the first question i'm unsure of the status particularly as it shows up in Places.
Here's what happens
1. start pc up and login
2. run an app which requires files from the Work volume, errors encountered
3. click Places > Work, File Browser loads all looks good
4. run same app which requires files from the Work volume, app runs fine
Clearly it isn't completely mounted until I've clicked on Places > Work

akimatsu123, thanks, the tuxfiles link looks good. there seems to be a ton of information and options for something i thought would be fairly common.

thank you

---

### Post by click4851 on 2009-05-16
have the same problem.....very annoying

---

### Post by cjv8888 on 2009-05-16
> **dimitriv said:**
> hi

I have a 50gb partition/volume called Work which has a mountpoint of /media/work
Currently each time I start the pc I have to click on Places then Work before I can access files from the Work. Is there a way i can have that permanently/automatically mounted so it's available immediately on startup?

Also, on a VM machine guest I enter a sudo mount command to mount a share between the guest and host. Can I put this sudo mount command in a startup script or process so that it's already mounted on startup?

Thank you

First of all,find the uuid of your partition by 

> sudo blkid

then edit your /etc/fstab by

> gksudo gedit /etc/fstab

then add the following line to the end of the fstab file using the partition's uuid, assuming that it is ntfs type.

> UUID=XXXXXXXXXXXXXX /media/work ntfs defaults,umask=000,gid=46 0 1

When you boot up next time, the partition should be mounted.
You can make a desk top launcher then to point to it.

Have a look at [How to fstab here.]("http://ubuntuforums.org/showthread.php?&t=283131")

---

### Post by Paqman on 2009-05-16
Take a look in Applications > Add/Remove for a tool called Storage Drives Manager, it'll help you set up your drives without needing to mess about with UUIDs and /etc/fstab.

Oh and cjv8888, you should always use gksudo for gedit, not sudo. Sudo is for command line work, not GUI apps.

---

### Post by hobo14 on 2009-05-16
> **dimitriv said:**
> hobo14, for the first question i'm unsure of the status particularly as it shows up in Places.
Here's what happens
1. start pc up and login
2. run an app which requires files from the Work volume, errors encountered
3. click Places > Work, File Browser loads all looks good
4. run same app which requires files from the Work volume, app runs fine
Clearly it isn't completely mounted until I've clicked on Places > Work

akimatsu123, thanks, the tuxfiles link looks good. there seems to be a ton of information and options for something i thought would be fairly common.

thank you

I don't know how #4 is possible, but cjv8888 has given you the solution (although personally the options I add are: "uid=1000" and "umask=000").

EDIT: **Except**, I think you'll find there is already an entry for that disk's uuid in /etc/fstab, so don't add a new entry for it, just add/change the two options for it's existing entry.

---


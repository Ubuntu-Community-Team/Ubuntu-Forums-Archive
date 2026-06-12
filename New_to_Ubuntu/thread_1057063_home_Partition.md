---
title: "/home Partition"
date: 2009-02-01
forum: New to Ubuntu
---

### Post by Unanimated on 2009-02-01
Okay, yesterday I put a new 60GB hard drive in my computer, and formatted it to ext3 with the Live CD. I found out today how to move my home folder onto the drive, and I'm wondering if it's safe to cut everything inside my current home folder and place it in the new one without any problems. I just want to know before I accidentally do something stupid, and I don't feel like waiting hours for my home folder to be compressed at the moment.

---

### Post by taurus on 2009-02-01
[http://www.psychocats.net/ubuntu/separatehome#usingnew](http://www.psychocats.net/ubuntu/separatehome#usingnew)

---

### Post by XanTrax on 2009-02-01
> **Unanimated said:**
> Okay, yesterday I put a new 60GB hard drive in my computer, and formatted it to ext3 with the Live CD. I found out today how to move my home folder onto the drive, and I'm wondering if it's safe to cut everything inside my current home folder and place it in the new one without any problems. I just want to know before I accidentally do something stupid, and I don't feel like waiting hours for my home folder to be compressed at the moment.

Well, I have never done this personally but what would seem like it would work is:

- Move your entire home folder over to that hdd or partition
- Edit /etc/fstab so that your 60GB HDD with UUID=x where X is the UUID (ls -al /dev/disk/by-uuid) is mounted on /home

---

### Post by ugm6hr on 2009-02-01
> **Unanimated said:**
> I found out today how to move my home folder onto the drive, 

If your /home is already mounted on the new drive - then should be ok.

---

### Post by XanTrax on 2009-02-01
> **ugm6hr said:**
> If your /home is already mounted on the new drive - then should be ok.

I think he means he read up a bit and learned how to do it and just wants to double check here if it is the correct way or not

---

### Post by Unanimated on 2009-02-01
Okay, just for clarification - I went to Users and Groups, unlocked it, highlighted my user, then went to Properties and Advanced, then changed the /home directory to /media/Main/Sam/home. I accidentally named the disk Main yesterday when I formatted it.

---

### Post by XanTrax on 2009-02-01
> **Unanimated said:**
> Okay, just for clarification - I went to Users and Groups, unlocked it, highlighted my user, then went to Properties and Advanced, then changed the /home directory to /media/Main/Sam/home. I accidentally named the disk Main yesterday when I formatted it.

That seems like it would work BUT you're still going to want to edit fstab file so that your external HDD mounts to /media/Main and not whatever default name, like /media/disk, it may want to mount to first.  The link from above says how to edit your fstab file for a /home partition.

---

### Post by ugm6hr on 2009-02-01
I don't think that is the best option.

I would follow the link taurus gave to psychocats to ensure that your home directory is in /home.

---

### Post by Unanimated on 2009-02-01
Alright, it's moving over 115,000 files to the other hard drive. It'll apparently take 2 hours...

EDIT: Whoops, sorry. I started to move it over to the other drive before the page refreshed. I'll follow the instructions on the page if something gets screwed up.

---


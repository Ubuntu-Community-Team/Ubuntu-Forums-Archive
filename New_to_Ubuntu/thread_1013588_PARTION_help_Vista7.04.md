---
title: "PARTION help Vista/7.04"
date: 2008-12-17
forum: New to Ubuntu
---

### Post by pidu87 on 2008-12-17
OK so I have a dual boot vista and ubuntu 7.04.

Anyway I wan't to shrink the ubuntu main partition to give my vista some more gigs so I can burn DVDS. Ihave a laptop with one disc drive. Also I can't download wine.

Any help I downloaded qtparted, gparted wont download(Gives the message below).

"W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/c/cairomm/libcairomm-1.0-1_1.2.0-0ubuntu2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/c/cairomm/libcairomm-1.0-1_1.2.0-0ubuntu2_i386.deb)
  404 Not Found [IP: 91.189.88.31 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/glibmm2.4/libglibmm-2.4-1c2a_2.13.3-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/glibmm2.4/libglibmm-2.4-1c2a_2.13.3-0ubuntu1_i386.deb)
  404 Not Found [IP: 91.189.88.31 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gtkmm2.4/libgtkmm-2.4-1c2a_2.10.8-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gtkmm2.4/libgtkmm-2.4-1c2a_2.10.8-0ubuntu1_i386.deb)
  404 Not Found [IP: 91.189.88.31 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gparted/gparted_0.2.5-2ubuntu2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gparted/gparted_0.2.5-2ubuntu2_i386.deb)
  404 Not Found [IP: 91.189.88.31 80]


"


Any help, please.

---

### Post by Tatty on 2008-12-17
You can only alter partitions on an unmounted drive, so to do this you will need to boot to a liveCD then use gparted from there. 
On the liveCD you will find gparted already installed and accessible through System->Administration->Partition Editor.

To install wine  from the ubuntu repos just do:
```
sudo apt-get install wine
```

However, if you want a more up to date version of wine see this page:
[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

**EDIT:**Or you could use Vista's own partitioner to edit the partitions - i imagine that should be safe, but I have never done it myself.  Either way make sure you back up all your important data first, incase of disaster.

---

### Post by mrbiggbrain on 2008-12-17
Yes make sure you do a backup, and after resizeing do a chkdsk, also defrag the HDD before, and i linux's command is fdisk(correct if wrong)

---

### Post by Tatty on 2008-12-17
> **mrbiggbrain said:**
> Yes make sure you do a backup, and after resizeing do a chkdsk, also defrag the HDD before, and i linux's command is fdisk(correct if wrong)

fdisk is a partitioner.

---

### Post by pidu87 on 2008-12-17
I'm using Gparted on the LIVE cd now seems to be taking awhile......


I'll download wine if I can't get vista to do what I want.

Thanks for your help!

:popcorn:

---

### Post by mrbiggbrain on 2008-12-17
> **Tatty said:**
> fdisk is a partitioner.

i apologize, i douno what program im thinking of, i remember a discussion about something similar to chkdsk on windows, maybe im incorrect, do you know the one im thinking of?

---

### Post by Tatty on 2008-12-17
> **mrbiggbrain said:**
> i apologize, i douno what program im thinking of, i remember a discussion about something similar to chkdsk on windows, maybe im incorrect, do you know the one im thinking of?

I think you are thinking of fsck.

---

### Post by pidu87 on 2008-12-17
OK it worked but now I can't create a new partition (maxed out on those) and can't resize because different parts of hard drive.

any advice?

---

### Post by mrbiggbrain on 2008-12-17
> **Tatty said:**
> I think you are thinking of fsck.

AHH thats the one, thanks for correcting me, wouldnt want something going wrong there!

---

### Post by Tatty on 2008-12-17
> **pidu87 said:**
> OK it worked but now I can't create a new partition (maxed out on those) and can't resize because different parts of hard drive.

any advice?

If you need more than 4 partitions on your drive then you are going to have to change one into an extended partition and house all the remaining partitions as logical drives under that.

Unfortunately this is going to mean some nuking of your partitions and re-organising of your hard disk.  What set up are you trying to achieve?

---

### Post by pidu87 on 2008-12-17
Just extra space for windows to save to.

If I'm in Vista can I save to a linux partition(like vice versa in ubuntu)?

Can I put just the swap on an extended partition?

---

### Post by pidu87 on 2008-12-17
"Can I put just the swap on an extended partition?"

Ok so it already is an extended partition. 



So if I delete it and then recreate it how do I get ubuntu to recognize it as swap again?

---

### Post by Tatty on 2008-12-17
If you are simply resizing partitions then you should not need to create any new ones, 

Windows cant natively access linux partitions, however there is an open source driver for windows to allow it to do this. [http://www.fs-driver.org/](http://www.fs-driver.org/)

Yes you can just put your swap under an extended partition, though i believe afterwards you will have to edit your /etc/fstab file to let ubuntu know its new UUID.

---

### Post by Tatty on 2008-12-17
> **pidu87 said:**
> "Can I put just the swap on an extended partition?"

Ok so it already is an extended partition. 



So if I delete it and then recreate it how do I get ubuntu to recognize it as swap again?

Im not quite sure what you are trying to achieve here.  Why do you want to delete it and recreate it, if it is already under an extended partition?

---

### Post by pidu87 on 2008-12-17
ok it let me resize with out deleting. I'm gonna run vista and see how it went.

How do I check ubuntu for errors since I resized the main partition and didn't make a backup?

---

### Post by Tatty on 2008-12-17
I just thought, did you have swap on while you were tring to edit the partitions?  You need to right click on the swap partition and select "swapoff" to stop your live CD from using the swap partition.  That may have been the problem.

> **pidu87 said:**
> How do I check ubuntu for errors since I resized the main partition and didn't make a backup?  

```
sudo touch /forcefsck
```  Then it will run on the next boot.

---


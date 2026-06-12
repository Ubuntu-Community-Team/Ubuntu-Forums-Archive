---
title: "NTFS device says its full but isnt!"
date: 2009-09-16
forum: New to Ubuntu
---

### Post by ekaqu on 2009-09-16
I am using ubuntu 9.04 and my system is set up so that i have 1 windows partition, one ubuntu partition, and one shared data partition (ntfs).

I code my homework using vi and when I try to save files in the shared partition, i get an error saying "write error (file system full?)"

the df -h from my system is this (/media/share = shared data):
df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5              33G   15G   17G  48% /
tmpfs                 943M     0  943M   0% /lib/init/rw
varrun                943M  348K  943M   1% /var/run
varlock               943M     0  943M   0% /var/lock
udev                  943M  156K  943M   1% /dev
tmpfs                 943M  532K  943M   1% /dev/shm
lrm                   943M  2.2M  941M   1% /lib/modules/2.6.28-15-generic/volatile
/dev/sda6              36G   32G  3.3G  91% /media/share
/dev/sda1              23G   16G  7.1G  69% /media/windows

So it says I have 3 gigs left, so any ideas why this is happening?

---

### Post by AlexenderReez on 2009-09-16
if it doesn't contains data or just backup that data to other place..then reformat that partition using gparted .

perhaps,there are something more than data exists there, where you get it while using windows.

between...what kind of code is that..?use more than 3gig?usually code only required around 15kb.

---

### Post by zeroseven0183 on 2009-09-16
Install NTFS Configuration Tool and see what it can do to access your NTFS partition.

---

### Post by ekaqu on 2009-09-16
> **AlexenderReez said:**
> if it doesn't contains data or just backup that data to other place..then reformat that partition using gparted .

perhaps,there are something more than data exists there, where you get it while using windows.

between...what kind of code is that..?use more than 3gig?usually code only required around 15kb.

I was just writing small php scripts.

This issue came about when my drive got full 3-4 days ago.  I removed around 3 gigs of data off the drive using nautilus's and hitting the del key.  The data never went to my trashcan but df shows the data is gone (the data is no longer in the folder it was in ether).

Reformatting isn't really an option at the moment, so I have to find a way to fix it.


I looked into ntfs configuration tools and it seems that reading/writing is just fine (if i delete a few files, i can write that much space), but everything thinks the drive is full.

---

### Post by cariboo on 2009-09-16
Have you checked the trash can on the ntfs drive?

---

### Post by ekaqu on 2009-09-18
The RECYCLER folder is empty and the linux trash is also empty.

---


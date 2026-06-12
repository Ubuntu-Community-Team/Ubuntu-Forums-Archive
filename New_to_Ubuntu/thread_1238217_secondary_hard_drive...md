---
title: "secondary hard drive.."
date: 2009-08-12
forum: New to Ubuntu
---

### Post by numbness05 on 2009-08-12
Hey there I have two questions really.

Could any one try and tell me as simply as possible how to go about the following please.

I have an empty 200gb hard drive formatted as NTFS that I wish to install into my machine using a SATA cable (not sure if the SATA bit is relevant)but....

Will my machine automatically see this as an internal drive or a mountable device?. How would I go about making my machine recognise it instantly as an internal hard drive?.

Secondly the 200gb drive is bigger then the drive I have in my machine currently so I wish to transfer the data from the smaller (160gb again SATA drive) to the 200gb and make this my home drive if that makes sense.
I have been told I will have to format the 200gb to ext3 so...

How do I go about reformating to ext3 and then making this my home drive?.

I really am a real beginner so any help in simple laymens terms would be really very much appreciated.

Thank you very much in advance.

---

### Post by 3rdalbum on 2009-08-12
Connect the drive, install Gparted onto your Ubuntu, and then use Gparted to format the disk as ext3.

It will appear in your Places menu as a mountable disk, but you might find that your user doesn't have permission to write to it. If this happens, open a root file browser, find the disk's mount point in /media (it's usually /media/disk) and change the permissions so that "others" can read and write to it.

---

### Post by mapes12 on 2009-08-12
Then when Gparted has completed the formatting have a look at this to move /home across to the new HDD: [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---


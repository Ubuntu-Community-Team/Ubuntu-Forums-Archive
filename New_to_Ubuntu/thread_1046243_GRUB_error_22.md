---
title: "GRUB error 22"
date: 2009-01-21
forum: New to Ubuntu
---

### Post by sjvega on 2009-01-21
Hi, i'm kinda new to GNU/Linux, but until now I could somehow manage myself through.:D 
Recently I wanted to install Kubuntu 8.10, until then I was running Ubuntu 8.04, so I thought that before fully install it I should test it, so I partitioned my filesystem into two partitions, the old Ubuntu and a unallocated space for the installation. After testing it (and decided that KDE isn't for me), I went back to the regular Ubuntu 8.04, and then I deleted the partition with Kubuntu, so it's back to the unallocated state. After done with a few things I restarted, but when the GRUB starts to load an Error 22 appears.
I have my partitions in this disposition:
|--/sda1(DATA)--|--unallocated--|-unallocated(*)-|-/sda5(Ubuntu)-|-swap-|
                |  ex-Kubuntu   |extended--------->> 
* This space is only 8Mb and I don't know why it exists
I was hoping that something can be done in here...
Sorry for the bad english.
Thanks in Advance!

---

### Post by Michael.Godawski on 2009-01-21
hi,

I guess you have somehow nuked your grub.

Follow these instructions to recover it:


[LIST]
[*][https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Using%20the%20Ubuntu%20Desktop/Live%20CD](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Using%20the%20Ubuntu%20Desktop/Live%20CD)
[/LIST]

---

### Post by sjvega on 2009-01-21
Thanks I don't know why it happened but it's fixed now.

---


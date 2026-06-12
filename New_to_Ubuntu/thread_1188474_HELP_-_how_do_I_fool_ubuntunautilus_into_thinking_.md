---
title: "HELP - how do I fool ubuntu/nautilus into thinking 2 disks are one ?"
date: 2009-06-15
forum: New to Ubuntu
---

### Post by Debiant666 on 2009-06-15
Help !

Hi I am completely new to ubuntu & linux so please bear with if I sound a bit thick like.

I have recently installed Jaunty with WUBI and was wondering if I could fool Nautilus into thinking 2 disks are 1. I have a poor mans Raid card a sil0680 medley raid for my data and music disk which works OK under windows. I am not sure how nautilus handles creating it's mount points and wanted to know whether I can force Nautilus into only displaying 1 removable disk instead of 2 and creating a mount point which points to both disks (poor mans raid) .

Or even better - can anyone tell me how to get the raid card working under ubuntu !!

Thanks in advance

---

### Post by mgmiller on 2009-06-15
The package is called dmraid.  Here is a link that may help get you started.
I have no personal experiance using dmraid.  Only real hardware raid.  Hope this helps:

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by porchrat on 2009-06-15
> **Debiant666 said:**
> Help !

Hi I am completely new to ubuntu & linux so please bear with if I sound a bit thick like.

I have recently installed Jaunty with WUBI and was wondering if I could fool Nautilus into thinking 2 disks are 1. I have a poor mans Raid card a sil0680 medley raid for my data and music disk which works OK under windows. I am not sure how nautilus handles creating it's mount points and wanted to know whether I can force Nautilus into only displaying 1 removable disk instead of 2 and creating a mount point which points to both disks (poor mans raid) .

Or even better - can anyone tell me how to get the raid card working under ubuntu !!

Thanks in advance

Try dmraid...or mdraid I forget which. Although as far as I recall Ubuntu needs to format the drives to get it to work.

---

### Post by Debiant666 on 2009-06-16
> **porchrat said:**
> Try dmraid...or mdraid I forget which. Although as far as I recall Ubuntu needs to format the drives to get it to work.
 
Thanks - will have a look at DMRAID after I finish dealing with all these windows lusers (I am a wintel engineer by day !!). I wish I could afford proper hardware RAID but my bank balance tells me different !!
 
I hope you don't have to format the drives as they are very full (just under 1tb) .
 
Thanks both for your advice :)

---

### Post by porchrat on 2009-06-17
> **Debiant666 said:**
> Thanks - will have a look at DMRAID after I finish dealing with all these windows lusers (I am a wintel engineer by day !!). I wish I could afford proper hardware RAID but my bank balance tells me different !!
 
I hope you don't have to format the drives as they are very full (just under 1tb) .
 
Thanks both for your advice :)

IMO softRAID is more than good enough. Hardware RAID is very expensive for the small amount of performance increase you get. I run a softRAID RAID0 setup myself and have never had any issues with it, more than fast enough.

Here is a link to help get you started in case you need it:
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

There is actually another way to create a RAID array that I have tried before (other than DMRAID but the name escapes me at the moment), but DMRAID is the one most people use so I would recommend you stick with it because there is a lot more support out there.

---

### Post by Debiant666 on 2009-06-17
Well I have dmraid installed however I have to run sudo dmraid -ay after boot up.

This thens creates some block devices under /dev/mapper/{raidsetname}

I have found that I can then mount the created block devices using 

mount /dev/mapper{raidsetname} /data/ 

I was wondering is there any way I can do this at start up with init scripts ? or fstab ? ---- 

I tried creating an executable script with sudo dmraid -ay listed and set it as a startup script , boot a quick ps-ef | grep dmraid shows nothing after booting up .... maybe I'm stll thinking too windows here ?

Any help would be greatly appreciated :)

---

### Post by porchrat on 2009-06-17
Perhaps you could add it to the runlevels.

If you add the "dmraid -ay" command to the /etc/rc.local file (add the line before the "exit 0" statement) then it should execute at the end of the boot process, and the changes will be available to all sessions and all users. Also because all these commands are run as root you don't need the sudo.

I don't know how you would get it to mount automatically though.

---

### Post by zekopeko on 2009-06-17
try this:

[http://en.wikipedia.org/wiki/Aufs](http://en.wikipedia.org/wiki/Aufs)

---

### Post by Debiant666 on 2009-06-22
> **porchrat said:**
> Perhaps you could add it to the runlevels.

If you add the "dmraid -ay" command to the /etc/rc.local file (add the line before the "exit 0" statement) then it should execute at the end of the boot process, and the changes will be available to all sessions and all users. Also because all these commands are run as root you don't need the sudo.

I don't know how you would get it to mount automatically though.

Brilliant - thanks - Now have all my data disks mounted .. I kind of bodged it . Added the extra lines to my fstab which obviously dont boot until the rc script runs, so I just appended the bottom with mount -a and roberts your fathers brother . I just wanted to check if I did something bad ?

---

### Post by porchrat on 2009-06-23
> **Debiant666 said:**
> Brilliant - thanks - Now have all my data disks mounted .. I kind of bodged it . Added the extra lines to my fstab which obviously dont boot until the rc script runs, so I just appended the bottom with mount -a and roberts your fathers brother . I just wanted to check if I did something bad ?

nope that sounds fine actually, congrats :)

---


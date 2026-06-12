---
title: "Partition manager no drives"
date: 2011-02-07
forum: New to Ubuntu
---

### Post by Pevichaey5 on 2011-02-07
Hey forum,

I thought about trying 10.10 last night on my desktop as Windows was acting up hugely again and have decided to dual boot it for now and eventually it will be a Ubuntu machine with a windows vm etc

I ran the installer (from the live disk) and it all goes fine, until the bit where I choose the hard disk and partitions

On this screen, the partition table is empty and in the drop down box at the bottom it says /dev/sbin and thats it, so I'm a bit stuck

I booted back into windows and shrunk my windows partition creaitng a 50GB partition and rebooted into the live disk, but again the partition table was empty

I was using a Western Digital 640GB SATA2 drive with a ASUS P6T motherboard, there isn't any issues regarding these two things are there?

Thanks

---

### Post by mcduck on 2011-02-07
> **thexero said:**
> Hey forum,

I thought about trying 10.10 last night on my desktop as Windows was acting up hugely again and have decided to dual boot it for now and eventually it will be a Ubuntu machine with a windows vm etc

I ran the installer (from the live disk) and it all goes fine, until the bit where I choose the hard disk and partitions

On this screen, the partition table is empty and in the drop down box at the bottom it says /dev/sbin and thats it, so I'm a bit stuck

I booted back into windows and shrunk my windows partition creaitng a 50GB partition and rebooted into the live disk, but again the partition table was empty

I was using a Western Digital 640GB SATA2 drive with a ASUS P6T motherboard, there isn't any issues regarding these two things are there?

Thanks
Try the custom partitioning option, does it show the partitions correctly there?

Also you might want to delete the partition you created (if you don't, th installer will do that anyway) and instead leave it as unpartitioned space.

---

### Post by Pevichaey5 on 2011-02-07
There's a custom partitioning option?

I don't remember seeing that option when I was trying to install it last night

At the boot, I'd click 'Install Ubuntu' then I tick 'Install updates' etc then on the next screen, the table was blank and I don't remember seeing a way to proceed as it wants me to choose a partition

I will have another go when I get home and see what happens :)

---

### Post by ajgreeny on 2011-02-07
I think the wording is now "Choose your own partitions (Advanced)" or something similar to that.

What do you sere from the live CD if you use the command ```
sudo fdisk -l
```lower case L at the end, not 1.

Also run gparted from the System >Administration menu of the live CD and see what that finds.  Attach a screenshot using the paperclip at top of text input box, if it would help you.

---

### Post by Pevichaey5 on 2011-02-07
Cheers :)

I'm booted into the live disk right now, so I have network connectivity etc

[IMG]http://img821.imageshack.us/img821/6408/screenshotvgv.png[/IMG]

I can see my two partitions in the terminal which is obviously good, but not in install :(

---

### Post by ajgreeny on 2011-02-07
Very odd!

Do you only have the one disk?  What can you see if you use **System >Administration >Gparted** on the live CD?

---

### Post by Pevichaey5 on 2011-02-07
Normally I have 3 hard disks, however I removed those disks as they are my data backup disks and didn't want to have a chance of something going wrong and loosing all my backups

I also used gparted earlier today and messed with the spare partition

48GB ext3 ubuntu /
2GB swap

But other than that I still got the message screen during install, but I have heard about getting the Alternate install disk (downloading at present) as it supports dual booting better than the normal install disk.  Not sure how true that is but I will give that a go soon

---

### Post by coffeecat on 2011-02-07
Has the disc you are trying to install to ever been used for RAID? There was a thread where the OP saw the same weird empty 'Allocate Drive Space' installer window as you. It turned out that residual RAID metadata was the problem, although the OP of that thread couldn't remember the drive being used for RAID. This is the thread:

[http://ubuntuforums.org/showthread.php?t=1662128](http://ubuntuforums.org/showthread.php?t=1662128)

Have a look at Rubi1200's post #19 and his posted link.

---

### Post by Pevichaey5 on 2011-02-07
Yes it has, previously I had a 1.2TB RAID 0 setup (before a drive failed) but unfortunately I no longer use RAID as I lost everything

So I suppose thats one of the reasons why I have dedicated backup drives, not in any kind of RAID just standalone disks at the moment

I will look through that thread and see if my answer lives in there :)

---

### Post by Pevichaey5 on 2011-02-07
Thanks very much for your help guy :) Problem solved

```
sudo dmraid -r -E /dev/sda
```

So I will once again join you pretty soon hehe

---

### Post by minorgod on 2012-09-08
> **thexero said:**
> Thanks very much for your help guy :) Problem solved

```
sudo dmraid -r -E /dev/sda
```

So I will once again join you pretty soon hehe

Whoever gave you that info is awesome. I'd given up on switching from SageTV to Mythbuntu a year ago because of this problem, but today I decided to give it another shot and the above commands solved my problem too! It took a little doing just to be able to enter those commands though. I had to force the new mythbuntu 12 installer to use the old version install routine by hitting "esc" while the mythbuntu logo was showing at the beginning of the install sequence, then hit f6 to access the install options, turn on the "nomodeset" flag, then cancel the install when the partition manager came up in the first install and couldn't find /dev/sda, and let it finish booting to a livecd desktop, then open a terminal in the live cd and type your solution...
```
sudo dmraid -r -E /dev/sda
```
...then double-click the installer to restart the install, and finally the installer was able to find /dev/sda and kindly asked if I wanted to install Mythbutu alongside my existing Win7 OS. It's finally installing now. I just hope when this is all done it will be able to recognize my ancient PVR-250 card.

---

### Post by coffeecat on 2012-09-08
Old thread closed.

---


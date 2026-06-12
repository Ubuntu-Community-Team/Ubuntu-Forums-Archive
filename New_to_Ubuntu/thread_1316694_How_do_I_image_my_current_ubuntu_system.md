---
title: "How do I image my current ubuntu system?"
date: 2009-11-06
forum: New to Ubuntu
---

### Post by shane_c2003 on 2009-11-06
I have been looking around but not sure if i am not using the correct key search words. I am running 9.04 and have considered the upgrade to 9.10. At the current time, my computer is running near perfectly, and if possible, i would like to take an image of what i have now, and save of a jumpdrive or something of the sort. The reason i would like to do this, is if i ever screw up the system (again), it won't be as difficult to get everything back that i had lost. So my questions are:

1. How do i take an image of my current configuration to save on a jumpdrive? (unless there is a better way)
2. If i really screwed the computer, how would i reload the computer from that image i saved?

I am flexible on different options. This doesn't need to be the only solution. I would like to experiment and try things, but with my lack of knowledge i worry i could mess it up. At the moment i am not saving any documents, photos, music, or anything of the sort to the computer, until i can get a clean image. Plus i have learned to back all that sort of stuff up on other HDDs, just in case. Thank you for your help!

---

### Post by yanceypd on 2009-11-06
I use clonezilla and backup drives to a large usb stick or usb drive.  If things go bad with new software you can restore the entire drive in a few minutes.

---

### Post by ukripper on 2009-11-06
> **yanceypd said:**
> I use clonezilla 

+1 for clonezilla. It is the best and the fastest way to clone image so far for me.
For more info about clonezilla visit website and download live cd. [http://clonezilla.org/](http://clonezilla.org/)

---

### Post by shane_c2003 on 2009-11-06
Thanks guys for your help. It may take me a few days to try this out. I can only download during certain times of the day, or the network admins block my mac address! Its a real pain. Plus i download at 5 kb/s. Its a little ridiculous. I looked at the clonezilla page, and hopefully running this is a lot easier than it appears in the reading. I am not a skilled linux user just yet...

---

### Post by ukripper on 2009-11-06
> **shane_c2003 said:**
> Thanks guys for your help. It may take me a few days to try this out. I can only download during certain times of the day, or the network admins block my mac address! Its a real pain. Plus i download at 5 kb/s. Its a little ridiculous. I looked at the clonezilla page, and hopefully running this is a lot easier than it appears in the reading. I am not a skilled linux user just yet...

Clonezilla is not difficult to understand. you can get step by step cloning in this howto - check this link: [http://www.dedoimedo.com/computers/free_imaging_software.html](http://www.dedoimedo.com/computers/free_imaging_software.html)

---

### Post by peakpc on 2009-11-06
Although not technically free I use [BootitNG]("http://www.terabyteunlimited.com/index.htm") to .img any partition on any computer. You can make a BootitNG CD and just never install it.  The bootit people don't seem to mind. I've paid the $35 to load it on my laptop and use it to dual boot inplace of grub from there I can backup my partitions create or modify them. It's a very powerful tool. Only one downside and thats that while it will .img and create linux partitions it will only backup to fat(16 or 32)or NTFS format partitions. Oh They do have a "Image for Linux" but BootitNG does so much more.  I know other free options may be to your liking but, I started using BootitNG long before I thought of trying linux or Ubuntu (now I use all of them together) :D

---

### Post by zika on 2009-11-06
You might want to consider remastersys [http://www.geekconnection.org/remastersys/remastersystool.html](http://www.geekconnection.org/remastersys/remastersystool.html) .

---

### Post by muteXe on 2009-11-06
Is there some feature in 9.10 that you want that's NOT in 9.04?  If not, here's a wacky idea: why don't you carry on using your perfect system?! :o

---

### Post by shane_c2003 on 2009-11-07
Thank you all for your inputs. I looked through the step by step manual and it looks pretty simple. I'll give it a shot here soon and cross my fingers. Thanks again!

---

### Post by ratcheer on 2009-11-08
I am having some trouble with Clonezilla. Something seems very strange.

I attached a USB 2 external drive to my Ubuntu PC and verified that the system could see it. Then, I put the Clonezilla iso CD into the drive and rebooted. It found the drive I want to back up (sda) and the USB drive (hdb). I told it to use the beginner functionality. It analyzed and found the partitions on sda and everything looked perfect.

But, when I got to the final step of telling it to start the backup, it infiormed me that sda had no valid partitions. It offered to continue, but said the resulting image might not be usable. What is going on?

I think my drive is pretty normal:
```

Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/sda5     ext3     19G  1.3G   17G   8% /
udev         tmpfs    502M  360K  501M   1% /dev
none         tmpfs    502M  1.3M  500M   1% /dev/shm
none         tmpfs    502M  328K  501M   1% /var/run
none         tmpfs    502M     0  502M   0% /var/lock
none         tmpfs    502M     0  502M   0% /lib/init/rw
/dev/sda3     ext3     28G  685M   26G   3% /home
/dev/sda4     ext3     27G  2.8G   23G  11% /usr

```Thanks,
Tim

---

### Post by yanceypd on 2009-11-08
There's several versions there to download mine says its Clonezilla-Live Version.  Works great.

---


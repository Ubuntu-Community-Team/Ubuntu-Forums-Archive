---
title: "Switching OS from USB HD to HDD-2"
date: 2009-06-25
forum: New to Ubuntu
---

### Post by Ciril on 2009-06-25
Hello everybody,

I am new to Ubuntu Jakalopy 9.04 which I have installed in external HD "My Passport" 250gb. to try-it. It is connected to my table top computer via USB and my main OS is XP Home, Service Pack-2. It is running OK and most of the time it gives choice of selecting Ubuntu or XP ( some times get message "wait Ubuntu loading.... Error 21 ) dont know why but by using Ctrl-Alt + Del it will cycle and load OS selection screen. My questions are:

1 - How can I transfer Ubuntu to HDD-1 (HDD-0 is XP) in my main computer body from external HD ? The HDD-1 is now empty and formated NTFS with 160gb. space and I want to use the whole HDD-1 drive for Ubuntu. Do I use XP and tell it to send all from USB external HD to HDD-1 or??? and also will that action effect GRUB that is allready in HDD-0 ??? 

I do have the original disc with Ubuntu 9.04 i380 iso but also dont know the outcome of using it for HDD-1 (as far as allready installed GRUB is concerned). Also trying to avoid going through manualy entering all the "favorites" into Internet Brouser.

In "Ubuntu Pocket Guide and Reference" by Keir Thomas, I could NOT find reference/guide to this situation. 

_**Thank you for any and all info/guidance on this matter.**_ Please keep in mind I am the beginner and not as sharp with computers as yanger folks (69yrs and on hearth medicines keeps my mind sligthly fussy).

Ciril.

---

### Post by oldfred on 2009-06-25
I would suggest installing to your second hard drive from the CD. It should configure and find the the other operating systems you are using. I see many people have issues with GRUB but most can be solved with minor editing if you are not afraid of editing the menu.lst file.
You can configure Firefox and Thunderbird to use the same directory for all your operating systems. If you have space I recommend a "shared" FAT32 partition. Ubuntu can read & write the NTFS partitions and supposedly Windows can read the ubuntu ext3 partitions but not write them. I have Firefox data on my Fat32 partition and regularly dual boot, but use the same firefox and thunderbird data directories without problems.

---

### Post by LewRockwell on 2009-06-25
First of all...WONDERFUL FIRST POST! You did better than 99 percent! Well Done!

Get [http://www.partedmagic.com/](http://www.partedmagic.com/) disk which is live-run and has BOTH GParted and Clonezilla on it(as well as other useful utilities!)

Get [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/) disk which should correct your grub after you've moved your ubuntu to the internal hard drive

(as always, back-up anything you can't afford to lose)

with everything hooked-up and powered-up we'll boot the machine with the live-run Parted magic disk and first play around with the Erase Disk function to give that hard drive a nice secure erasing.

then you'll check that drive with GParted to see exactly how much room it's got on it(just write down the number/size shown as unallocated)

then I'm assuming your ubuntu partition is the whole 250gb external drive so you'll need to resize that to whatever that number was from above

so now we should have a 160gb space to do a partition to partition cloning

here you'll start clonezilla and clone "local partition to local partition"
(note: you do NOT want "image" selections!!! Just direct clones)

it's really quite self-explanatory and intuitive

just take it slowly and make notes as necessary and you should be fine

once you've got the clone on HDD-1 then you can unplug the external drive and reboot with the super grub disk in and it will sort things out for you

I also attached a screen shot of one of my multi-partition multi-distro hard drives just for reference

---

### Post by oldfred on 2009-06-25
Lew,
Is there some reason you have 3 swap partitions? My understanding is only one swap is used regardless of which Linux is booted including a live CD. I do put a swap on each hard drive only for future use in case I disconnect a drive.

---

### Post by LewRockwell on 2009-06-25
> **oldfred said:**
> Lew,
Is there some reason you have 3 swap partitions? My understanding is only one swap is used regardless of which Linux is booted including a live CD. I do put a swap on each hard drive only for future use in case I disconnect a drive.

**For the benefit of present AND future visitors to this thread and post**

There were several factors taken into consideration when this drive was partitioned. As you can see from one of the links included, in some instances multiple swaps were mandatory since each one could only be 2GB and subject machine had 4GB of ram.

These are just some of them:

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

[http://www.bolthole.com/solaris/raid1andswap.txt](http://www.bolthole.com/solaris/raid1andswap.txt)

[http://kerneltrap.org/node/5247](http://kerneltrap.org/node/5247)

[http://forums13.itrc.hp.com/service/forums/questionanswer.do?admit=109447627+1245962038735+28353475&threadId=987511](http://forums13.itrc.hp.com/service/forums/questionanswer.do?admit=109447627+1245962038735+28353475&threadId=987511)

[http://tldp.org/HOWTO/Partition/requirements.html#SwapSize](http://tldp.org/HOWTO/Partition/requirements.html#SwapSize)

---

### Post by Ciril on 2009-06-25
Thank you to everyone who responded.

Mr. Rockwell, I will try to follow your suggestion to the best of my ability.

Ciril.

---


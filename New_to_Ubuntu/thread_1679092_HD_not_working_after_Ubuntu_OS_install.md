---
title: "HD not working after Ubuntu OS install"
date: 2011-01-31
forum: New to Ubuntu
---

### Post by unforgetable on 2011-01-31
Last night I downloaded Ubuntu in Windows 7, installed it via USB drive and was playing around with it for 30mins before going to bed. I woke up this morning, packed my stuff up, came to school, come into the library, boot up my laptop and get a "No Operating System detected." message. 

During my install/partition process, I was very careful when I set aside the 100gb partition for Ubuntu and made sure my other OS (Win7) was going to still be there. In fact, when I rebooted one of the times while setting up Ubuntu, I hit my partition select screen and had Ubuntu, Win7 and Win Vista (recovery partition, I'm assuming), all to choose from. 

Also, my computer is BRAND NEW. Brand new as in just over a month old. It is a Lenovo Y560. I tried going into BIOS and Boot Order and there is no hard drive being detected. 

Please help, I really don't understand how installing a OS could make my HD not work, but there is no other logical explanation.

---

### Post by TeoBigusGeekus on 2011-01-31
> **unforgetable said:**
> Please help, I really don't understand how installing a OS could make my HD not work, but there is no other logical explanation.
Me neither...:-k
I don't believe it has something to do with ubuntu; perhaps physical damage to the laptop?
Ubuntu could mess up your pc - trashing windows, for example - but I don't think it can make a hd disappear.

---

### Post by unforgetable on 2011-01-31
It was sitting on my coffee table all night, there is no possibility of physical damage.

---

### Post by TeoBigusGeekus on 2011-01-31
Think hard...
Perhaps while traveling to school or perhaps did a friend of yours borrowed it for a while or something...
I can't thing of a way that ubuntu could make a hd disappear. Even if ubuntu formatted your entire disk, it would still show up in your bios.

---

### Post by QLee on 2011-01-31
[QUOTE=unforgetable]...In fact, when I rebooted one of the times while setting up Ubuntu, I hit my partition select screen and had Ubuntu, Win7 and Win Vista (recovery partition, I'm assuming), all to choose from. [/QUOTE]

Well, Ubuntu is not like Windows, you don't reboot multiple times when installing the system, so what do you mean, "one of the times"?

What do you mean by "partition select screen" 

[QUOTE=unforgetable] Please help, I really don't understand how installing a OS could make my HD not work, but there is no other logical explanation.[/QUOTE]

That is not a logical explanation either.

To give a good representation of the current state of your system please download and follow the directions for the boot info script from this page. [Edit] I forgot to add, run this from a live version of Ubuntu.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Although if the BIOS doesn't see the drive that isn't going to work. I agree with TeoBigusGeekus that installation of Ubuntu isn't going to make a HDD disappear.

---

### Post by irv on 2011-01-31
> During my install/partition process, I was very careful when I set aside the 100gb partition for Ubuntu and made sure my other OS (Win7) was going to still be there. In fact, when I rebooted one of the times while setting up Ubuntu, I hit my partition select screen and had Ubuntu, Win7 and Win Vista (recovery partition, I'm assuming), all to choose from.
From this statement I am assuming you are referring to the Grub menu at boot time. if this is the case it was seeing your HD.

> Also, my computer is BRAND NEW. Brand new as in just over a month old. It is a Lenovo Y560. I tried going into BIOS and Boot Order and there is no hard drive being detected.
Looks like a nice laptop. What I would do at this point seeing you install it from the USB drive. I would put the drive back in the laptop boot from it but this time go to the live OS and run it off the USB drive. Go to the system> Administration> and run gparted. This should tell you if all your partitions are in tack.
This is the best place to start from.

> Please help, I really don't understand how installing a OS could make my HD not work, but there is no other logical explanation.

The installing of a OS should not have anything to do with destroying your HD. I am not sure what is going on, but try what I said above.

---

### Post by Rubi1200 on 2011-01-31
+1 to the boot script

If you want us to help you, please do as QLee asked and run the script.

By the way, did you install using the Windows installer Wubi?

---

### Post by unforgetable on 2011-01-31
After I installed Ubuntu I updated some things that required me to reboot. To clarify, I meant the Operating System select screen where I can choose what OS I want to boot into. And yes, it was seeing my hard drive last night before I went to sleep.

Currently, running Ubuntu off my USB drive.

```
ubuntu@ubuntu:~$ sudo bash ~/Desktop/boot_info_script*.sh
Identifying MBRs...
Computing Partition Table of /dev/sda...
Searching sda1 for information... 
no block devices found
Finished. The results are in the file RESULTS.txt located in /home/ubuntu/Desktop

```As you might have guessed, this didn't work because my computer is no longer recognising a hard drive.

No one has touched my computer since last night, so I can 100% guarantee this wasn't due to physical damage.

Through Grep, I'm only seeing my USB drive and when I try to pull down the drop down menu in the upper right, only the USB drive shows up.

This really sucks, I have a feeling I'm going to have to send this back to Lenovo a week into school starting in order to get a warranty replacement. I know it isn't logical to blame Ubuntu for it, but with the laptop being as new as it is and that being the only thing that was significantly done yesterday to it, I'm just at a loss of what it could have been.

I don't know what a Wubi is, but I just went to the Ubuntu home page, downloaded the OS and picked the option to show me how to install from an USB.

---

### Post by mharrison on 2011-01-31
I agree with everyone else that Ubuntu is not capable of stopping the BIOS from seeing the hard drive.  Is it possible for you to remove the hard drive from the laptop and reinsert it to make sure it is connected. 

It is possible that on your trip to school that the drive could have come unhooked internally....odd as it may seem, I have had vibration from walking/car/bus trips loosen a hard drive even though it seemed like it was mounted properly.

---

### Post by irv on 2011-01-31
One thing to understand about HD is that fact if a HD is going to fail, I will happen very quickly. I sold computer for awhile and I have had HD fail within weeks of sale. This is nothing new. I believe the timing with the install of Unbutu was just untimely. 
Yes I would also agree about the HD coming loose in the laptop. My granddaughter's did and all I had to do was take the drive out and put it back in and everything worked. It had a bad connection.

---

### Post by Rubi1200 on 2011-02-01
I know this is a long shot, but I have one more suggestion.

Download, burn to CD, and try running Slax.
[http://distrowatch.com/table.php?distribution=slax](http://distrowatch.com/table.php?distribution=slax)

Use it to see if there is anything there and save what you can.

---

### Post by tpprynn on 2011-02-01
A number of times when I installed Ubuntu or various other distros on an Acer netbook I had, the BIOS somehow became corrupted and had to be re-flashed, simple enough if you read up on the process for a particular computer. I imagine a BIOS won't always be messed up in the same way I saw.

Is it possible that this re-flashing might help, or as the BIOS is working to a greater extent, choose the option to reset its defaults?

---


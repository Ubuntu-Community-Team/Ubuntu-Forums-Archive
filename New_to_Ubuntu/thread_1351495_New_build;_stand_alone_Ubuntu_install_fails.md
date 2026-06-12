---
title: "New build; stand alone Ubuntu install fails"
date: 2009-12-10
forum: New to Ubuntu
---

### Post by PFree on 2009-12-10
Hello Ubuntu Forums!

I just built a new system: Intel DQ45CB mobo with a Intel Q8200 Core 2 Quad. All I have on it right now is a DVD/CD +RW,  a monitor, a USB/floppy, and 2 160gb Seagate drives that I swiped from my old box.

I tried installing Ubuntu 9.10 twice and it goes great (94%) installed. Then, I get the following error message: **The 'GRUB' package failed to install into /target/. Without the GRUB boot loader, the installed system will not boot.**

The first time I tried the install I had the HDD's setup as a RAID 0.

Second time, I deleted the RAID array and changed my drive setting from RAID to IDE. I got the same error.

Another thing I don't understand is the partitioning screen that comes up when installing. It's there, but it won't let me create any partitions.

Any ideas about what I'm doing wrong?

Thanks.
Paul

---

### Post by PFree on 2009-12-10
Anybody out there?

---

### Post by PFree on 2009-12-10
LOL! Guess I should have named my post "newbie nothing works".

---

### Post by nwadams on 2009-12-10
hi

I read it through. Are you using the alternate install cd to set up raid? If so I know nothing about raid and am not familiar enough with the alternate install cd to help you through it. I suggest using the live-cd installer if you have never installed ubuntu before. Only disadvantage is no raid. 

hope that helps

---

### Post by daniell59 on 2009-12-10
Being a newbie my suggestion may not mean anything. I had a problem installing Ubuntu or Windows. It turned out that the memory was the problem. I upped the voltage and changed the timings. After that everything worked.

---

### Post by PFree on 2009-12-10
> **nwadams said:**
> hi

I read it through. Are you using the alternate install cd to set up raid? If so I know nothing about raid and am not familiar enough with the alternate install cd to help you through it. I suggest using the live-cd installer if you have never installed ubuntu before. Only disadvantage is no raid. 

hope that helps

Thanks for the reply nwadams!

I setup RAID in BIOS, then CTRL/I during system boot to setup the RAID 0 array. When the GRUB had a problem, which give me no 'outs' to correct, I deleted the RAID array, changed my BIOS to IDE HDD's, and reinstalled Ubuntu. I caught the same error regarding GRUB failed to install.

I downloaded Ububtu from the Ububtu website, and burned it to CD.

Also, thank you daniell59, for the reply.

Memory tests fine. In fact, after the mem test, I reduced memory from 4gb to 2gb. The GRUB Bootloader just isn't installing. I've been doing some research and apparently I'm not the only one having a problem with GRUB. Unfortunately, I haven't found a solution.

---

### Post by daniell59 on 2009-12-11
> **PFree said:**
> Thanks for the reply nwadams!

I setup RAID in BIOS, then CTRL/I during system boot to setup the RAID 0 array. When the GRUB had a problem, which give me no 'outs' to correct, I deleted the RAID array, changed my BIOS to IDE HDD's, and reinstalled Ubuntu. I caught the same error regarding GRUB failed to install.

I downloaded Ububtu from the Ububtu website, and burned it to CD.

Also, thank you daniell59, for the reply.

Memory tests fine. In fact, after the mem test, I reduced memory from 4gb to 2gb. The GRUB Bootloader just isn't installing. I've been doing some research and apparently I'm not the only one having a problem with GRUB. Unfortunately, I haven't found a solution.

My memory also tested fine. I checked the specs for the memory. The timing and voltage was way off.

---

### Post by egalvan on 2009-12-11
> **PFree said:**
> 
Memory tests fine. In fact, after the mem test, I reduced memory from 4gb to 2gb. 


Have you run a test on the media itself?
(run the "check CD for errors" option on the LiveCD boot screen)

What did you use to test RAM?
(memtest from the LiveCD boot screen is recommended)

Why did you remove 2Gb of RAM?

---

### Post by AgentZ86 on 2009-12-11
Will it boot to (try Ubuntu)

Or do you just select Install everytime.

I had a similar topic recently which I could not just hit install, but could (try ubuntu) and then install from there.

For some reason simply selecting install would not find my partition at the point where it was going to install it, so I could not go any further.

But the (try ubuntu) came up and then I could use the install ubuntu feature from that desktop, and it worked I don't know why or what.

But I also had some other stranges topics going on not related to anything but a video card problem too:

See my strange problem, it's not directly related to yours but it could be since I had not real way of telling either.

[http://ubuntuforums.org/showthread.php?t=1350404](http://ubuntuforums.org/showthread.php?t=1350404)


Anyhow, my post may not be of much help but I was wondering if you tried installing it that way, just to see if there is any difference.

Happy Hacking.

---

### Post by PFree on 2009-12-13
Hi People,

> **daniell59 said:**
> My memory also tested fine. I checked the specs for the memory. The timing and voltage was way off.

Thanks, daniell59, good idea. I'll take a look at timing/voltage tomorrow.

> **egalvan said:**
> Have you run a test on the media itself?
(run the "check CD for errors" option on the LiveCD boot screen)

What did you use to test RAM?
(memtest from the LiveCD boot screen is recommended)

Why did you remove 2Gb of RAM?

Yes, egalvan. I ran the CD check and memtest from LiveCD. Pulling the mem stick was just a shot in the dark. I read somewhere recently that XP don't like to install with 4+ gb of memory, so I was just groping on that one.

> **AgentZ86 said:**
> Will it boot to (try Ubuntu)

Or do you just select Install every time.

Happy Hacking. 

Never saw a 'try ubuntu' option so I've been reinstalling every time. Regarding that, I've been deleting/recreating the raid array before trying to reinstall.

I'll check out your thread tomorrow, AgentZ86. I need to leave that box alone for the rest of the night before I wind up throwing it out a window! 

I posted on the Intel board (at the time I thought the OS wasn't seeing my HDD's) and the guy who replied indicated that ubuntu might not even be able run using a ICH10R controller, but I haven't been able to verify that. I just happen to have a new SCSI raid controller that was was going to use for another array that I can't afford to loose so I popped that in the box and tried installing from there. I got the same results.

I'm starting to think my install disks might be dated. I've been downloading a from Georgia Tech mirror @ [http://www.gtlib.gatech.edu/pub/ubuntu-releases/](http://www.gtlib.gatech.edu/pub/ubuntu-releases/) because downloading from the ubuntu.org site takes forever.

I'm about ready to reformat my drives, clear the CMOS, unplug everything in the box except the necessary stuff, and start from scratch, only because all the hardware I'm using is new and untested (except the HDD's).

Thanks for all the replies.

Regards.
Paul

---

### Post by Fcon_Vpro on 2009-12-13
Im not entirely sure why your install isnt completing, but what I can tell you is that the raid built into your motherboard wont work with ubuntu. Well you can get it to work but its complex and not worth it.
If you want to run your OS on a raid array, its quite a complex setup. If you are just wanting to have a storage raid setup then mdadm is awesome.
Check out this link for some help with os raid configs in ubuntu: [https://help](https://help).**ubuntu**.com/community/**FakeRaid**Howto

---

### Post by oldfred on 2009-12-13
Raid hides some settings on the drives that interfere with installing if now you do not want raid.

Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb

---

### Post by PFree on 2009-12-14
Finally got ubuntu Jaunty Jackalope installed! Had to give up on version 9.10, it just would NOT install.

MANY thanks to **begoogled** for the detailed installation instructions, which can be found here: **[RE: Installing Ubuntu 9.04 RAID0]("http://ubuntuforums.org/showpost.php?p=7874462&postcount=9") **!!!

---


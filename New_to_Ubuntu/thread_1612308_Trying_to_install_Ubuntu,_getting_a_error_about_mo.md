---
title: "Trying to install Ubuntu, getting a error about mounting a file system"
date: 2010-11-03
forum: New to Ubuntu
---

### Post by Ima2k on 2010-11-03
I have a 500gb Hdd, I want to install Ubuntu on it THEN install Windows 7 on it.
  How do I set it up? I've gone through with Use entire disk. Then I made a 8000 MB Primary / Beginning Partition for Swap and a 50 GB  EXT4 (prim/beginning) with drive mount '/' and left the rest unused.
  Then used /dev/sda/ ATA WDC as the boot loader. Then I click go and I get this error :


  The attempt to mount a file system with type swap in SCSI1 (0,0,0), partition #1 (sda) at none failed.


  what does that mean and what do I do? It asks if I want to continue.

---

### Post by Clever_Username on 2010-11-03
Speaking from experience, if you are wanting to run a dual boot of Windows and any other OS, I would strongly recommend installing Windows first.

---

### Post by Ima2k on 2010-11-03
Yeah. I know but, that is what I thought this morning, Windows decided to install 3 partitions. 1 100gb (which I specified), 1 100mb (which I didn't want), and 1 1mb drive which is the boot drive?

So that is 3 out of 4 partitions, and Ubuntu  uses 2? partitions I think swap/install.

So I think I may as well just install Ubuntu and the Swap partitions and then install windows after and use Grub.

---

### Post by anewguy on 2010-11-03
As Clever_Username (you gotta love that one!) said and a lot of us found out the hard way, the easiest way to do things is Windows 1st, Linux 2nd (in installation only ;) ).  Now for the bad news - I'm not sure off the top of my head what is giving you the error, and I doubt that goes away simply by installing Windows first (but PLEASE do!).

After installing Windows, I think I would:

(1) delete the existing Linux partitions
(2) reinstall Ubuntu, but don't say use entire disk.  Instead take the advanced option so you can specify your own partitions and mount points. 

Dave ;)

---

### Post by Ima2k on 2010-11-03
> **anewguy said:**
> As Clever_Username (you gotta love that one!) said and a lot of us found out the hard way, the easiest way to do things is Windows 1st, Linux 2nd (in installation only ;) ).  Now for the bad news - I'm not sure off the top of my head what is giving you the error, and I doubt that goes away simply by installing Windows first (but PLEASE do!).

After installing Windows, I think I would:

(1) delete the existing Linux partitions
(2) reinstall Ubuntu, but don't say use entire disk.  Instead take the advanced option so you can specify your own partitions and mount points. 

Dave ;)

Alright. But like I currently have or did until a few minutes ago (same errors before and after) with windows installed. 

as for 1) I  can't delete the Linux Partitions as I can't make them, I don't think, I'm not sure, It's giving me errors, I can't install Ubuntu, and going back to installing windows will just put me back in square one.

The only options I can think of that might help is if I could just make the partitions I need right now, install windows on one of those partitions and then use the rest.

If I go back to installing windows it's going to install 3 unneeded partitions.

Thanks for your reply and help.

edit - unrelated but I am having trouble getting GParted started aswell, it just freezes and then asks if I want to send a crash  report.

---

### Post by GrantStoner on 2010-11-03
Best option, install Window$, and then download Wubi. It will install Ubuntu from inside windows. It's an ".exe" file. And it gives you the different setup options from within Window$. You'll have the choice then at startup to boot into whatever you want.

---

### Post by Ima2k on 2010-11-03
> **GrantStoner said:**
> Best option, install Window$, and then download Wubi. It will install Ubuntu from inside windows. It's an ".exe" file. And it gives you the different setup options from within Window$. You'll have the choice then at startup to boot into whatever you want.

Alright thanks a lot, I'll give it a try; can I use a Live CD? I don't have the bandwidth to download an .Iso.

Also, when installing through that, how would I set up the partitions under windows? 100gb for windows, rest unused and Wubi would  use the unused?  

Thanks a lot.

---

### Post by GrantStoner on 2010-11-03
You don't need a disk at all. You just double-click "wubi.exe" or whatever it comes as now, and tell it how much space you want it to take up. No manually editing partitions or anything. Just a nice and easy point-click-install setup. When you install Window$, tell it to take up the whole disk as normal - you don't need unallocated space or anything. Then just tell Wubi how much space to take up. It doesn't require you to resize partitions because it installs inside of Window$.

---

### Post by Ima2k on 2010-11-03
> **GrantStoner said:**
> You don't need a disk at all. You just double-click "wubi.exe" or whatever it comes as now, and tell it how much space you want it to take up. No manually editing partitions or anything. Just a nice and easy point-click-install setup.


I'm under the impression I need to download the .iso through that program; I only have the disk from shipit.ubuntu.com, I don't have / can't afford the bandwidth, I am on a really low bandwidth plan which costs if I go over it. 

Thanks for your help.

---

### Post by GrantStoner on 2010-11-03
If I recall right, it does download some stuff that took about a half hour for me. I don't think it needs the whole .iso though - maybe it does. It's been a while since I've had anything to do with Window$; Linux is 100% of all my drives. But if you can't afford what Wubi wants to install, you should think about asking either a neighbor or friend if you can borrow their connection (ethernet so they don't have to share their wifi password) just for 30min or so. If you don't have any neighbors or friends, the public library would be more than happy to allow you to use their bandwith. :)

---

### Post by GrantStoner on 2010-11-03
Oh, and I almost forgot, your swap partition is almost always never #1. Plus, if you're only having trouble with swap, just don't use it. It's not required - just recommended.

---

### Post by Ima2k on 2010-11-03
> **GrantStoner said:**
> If I recall right, it does download some  stuff that took about a half hour for me. I don't think it needs the  whole .iso though - maybe it does. It's been a while since I've had  anything to do with Window$; Linux is 100% of all my drives. But if you  can't afford what Wubi wants to install, you should think about asking  either a neighbor or friend if you can borrow their connection (ethernet  so they don't have to share their wifi password) just for 30min or so.  If you don't have any neighbors or friends, the public library would be  more than happy to allow you to use their bandwith. :smile:

Heh, I'm pretty rural (hence the bandwidth), and I don't have neighbours for quite a ways. I don't think the Library allow me to bring in a desktop either ;)

> **GrantStoner said:**
> Oh, and I almost forgot, your swap partition is almost always never #1. Plus, if you're only having trouble with swap, just don't use it. It's not required - just recommended.

I'll try this. I only need the one partition for Linux? I heard something about one for /root/ as well or something.

Can I get by without the swap? I have 6Gb of ram. Thanks for your help.

---

### Post by Elfy on 2010-11-03
I'd not install wubi if you knew you were going to be using it for sure - it's good to have a look at ubuntu.>  Wubi actually wasn&#8217;t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)

As far as the partitioning goes - I would create an extended partition large enough to contain swap and any other linux partitions you need - then windows can create it's 3 partitions. If you do that before starting the win install it won't be able to create anymore than 3 primary partitions.

/ is the root :)

I would also create the extended towards the end of the drive so that windows can use the beginning. 

You can use get wubi to use the iso you already downloaded.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://wiki.ubuntu.com/WubiGuide#How%20can%20I%20use%20a%20manually%20downloaded%20ISO?](https://wiki.ubuntu.com/WubiGuide#How%20can%20I%20use%20a%20manually%20downloaded%20ISO?)

---

### Post by GrantStoner on 2010-11-03
Oh, yes, they may not appreciate you bringing in a desktop system. Haha. Didn't even give it a thought; figured you were on a laptop. Your root partition is simply "/" not "/root/". And your partitions depend on what you have installed first - Window$ or Ubuntu. If Ubuntu first, then you'll need at least "/boot" and your root partition "/" - you can leave swap out. If if you have Window$ first, then you'll install the bootloader wherever, and won't necessarily need a "/boot" partition for Ubuntu because you'll can install the bootloader wherever the other one is. Keep in mind "/" will be your root partition. If you have something like "/root" or "/root/" - the word "root" would be a folder called root. / is like your C:\ drive, but without "C:". Likewise "/root" is like C:\root, where "root" is the folder name.

---

### Post by Elfy on 2010-11-03
One more thing - if you want to hibernate you will need swap. 

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by GrantStoner on 2010-11-03
> **forestpiskie said:**
> One more thing - if you want to hibernate you will need swap. 

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

But not if you want to put it in sleep mode right? Or do you need it for both? Just wondering cause I was able to put Back|Track in sleep mode while it was in forensics mode (no swap).

---

### Post by Elfy on 2010-11-03
Not sure to be honest - I always have swap anyway so I've neever needed to worry about it :)I would assume not and I have no idea what Back|Track is but I assume sleep mode equates to suspend.

---

### Post by Ima2k on 2010-11-03
> **forestpiskie said:**
> I'd not install wubi if you knew you were going to be using it for sure - it's good to have a look at ubuntu.[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)

As far as the partitioning goes - I would create an extended partition large enough to contain swap and any other linux partitions you need - then windows can create it's 3 partitions. If you do that before starting the win install it won't be able to create anymore than 3 primary partitions.

/ is the root :)

I would also create the extended towards the end of the drive so that windows can use the beginning. 

You can use get wubi to use the iso you already downloaded.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://wiki.ubuntu.com/WubiGuide#How%20can%20I%20use%20a%20manually%20downloaded%20ISO?](https://wiki.ubuntu.com/WubiGuide#How%20can%20I%20use%20a%20manually%20downloaded%20ISO?)

Alright, well I'll pass on the Wubi.

I just installed Ubuntu, haven't got Windows installed at the moment, I used a 8gig Logical Partition with location  being end of Drive, and a 50gb Primary/Beginning Partition, I'll install Windows tomorrow, is it simple to just install windows after and use grub to do the loader?

Thanks for your help.

And, Thanks again Grantstoner.

---

### Post by Elfy on 2010-11-03
After you have installed windows you will need to reinstall grub.

Not sure why you used a logical and a primary - if windows does actually need 3 partitions it's going to complain. I always use logicals for all of my linux partitions - personal choice though.

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showpost.php?p=6391959&postcount=1](http://ubuntuforums.org/showpost.php?p=6391959&postcount=1)

---

### Post by GrantStoner on 2010-11-03
And you'll have to setup grub as well. Window$ should only need 2 partitions. And you're welcome. Forums are a place for information. ^_^ It's our job as members to either ask questions, or answer questions. I'm always happy to be of service.

---

### Post by GrantStoner on 2010-11-03
One question though, why do you need to dual boot with Window$ in the first place? Do you need to boot into Window$ to do something that can't be done through a virtual machine? It may be easier to just install Ubuntu using the whole drive, and then installing Window$ to VirtualBox or VMware or something. Or visa-versa and have Ubuntu in the virtual machine.

---

### Post by Elfy on 2010-11-03
> **GrantStoner said:**
> One question though, why do you need to dual boot with Window$ in the first place? Do you need to boot into Window$ to do something that can't be done through a virtual machine? It may be easier to just install Ubuntu using the whole drive, and then installing Window$ to VirtualBox or VMware or something. Or visa-versa and have Ubuntu in the virtual machine.

I assume you mean Windows - you have something wrong with your keyboard, sometimes the S looks like a $. Please do not do it - > Attacks and derogatory terms of any kind are not welcome. This includes references to other operating systems and the companies that produce them.

---

### Post by GrantStoner on 2010-11-03
Oops, sorry, didn't know it was a violation of any kind. It's not an attack, and it's certainly not derogatory. Windows is mainly proprietary software, stuff you have to pay to use, that's why I incorporate the dollar sign. If my keyboard had an anti-dollar sign I'd incorporate it into "Linux". More of an observation than anything.

Noted: No more unnecessary silly symbols. :)

---

### Post by Ima2k on 2010-11-03
> **GrantStoner said:**
> One question though, why do you need to dual boot with Window$ in the first place? Do you need to boot into Window$ to do something that can't be done through a virtual machine? It may be easier to just install Ubuntu using the whole drive, and then installing Window$ to VirtualBox or VMware or something. Or visa-versa and have Ubuntu in the virtual machine.


Well, Direct x games, syncing an ipod (craptunes), and 15 years of experience and familiarity with  an OS isn't hard to just pack up and leave, maybe later, maybe not.

As for the topic, I finally got it working, I did Windows first, then Ubuntu, I was able to delete the second windows partition when it was in the windows installer partition area.

Thanks for your help everyone. Now  onto other problems heh.

---


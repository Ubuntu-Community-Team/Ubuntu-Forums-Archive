---
title: "Trying to understand partitions and get it right the second time"
date: 2009-08-19
forum: New to Ubuntu
---

### Post by fatgreta on 2009-08-19
Hi,
 
I'm starting the Windows - Linux conversion (I hope). I have a brand new desktop with an AMD 9650 CPU, 4GB of 667 DDR? (2 I think) RAM, a 1GB ATI Radeon 4650 GPU and a 500 GB hardrive. I have Windows XP home installed and updated. I installed Ubuntu once, and ended up with too small a partition, so I can't load the first set of updates. Since I've just begun, and following advice in another post, I'm going to reinstall Ubuntu (I missed the sliders that allow me to set the size for each partition). Before I do this, I want to make sure I'm on the right track about a few things.
 
Looking over other forum posts about partitions, there is a general consensus that anywhere from 10 - 20 GB is plenty of space for the Ubuntu partition (at least in the threads I've found in my searches). I don't have as clear an idea about the Windows partition, but I've read that in the 20 GB range should work fine. Do those figures sound right?
 
This is where I start to get fuzzy on things. If I have 2 20GB partitions, one for Windows and one for Ubuntu, where are the other 460GB? I've read people recommending making a "home" partition, for file storage, etc. If I do that:
 
1) Can I create it during installation, or must I do so later?
2) Can I store both Windows and Linux files there, and will either OS be able to access them if I boot into (Windows or Linux)?
3) If at install I must choose to make only the Ubuntu and the Windows partitions, should I make one take up all the extra space (say 50GB for Windows, 450GB for Ubuntu), or does that not matter?
 
When I ran df -h from my terminal, I got the following information:
 
Filesystem            Size  Used Avail Use% Mounted on
**/dev/sda5             2.3G  2.2G   32M  99% /**
tmpfs                 2.0G     0  2.0G   0% /lib/init/rw
varrun                2.0G  104K  2.0G   1% /var/run
varlock               2.0G     0  2.0G   0% /var/lock
udev                  2.0G  144K  2.0G   1% /dev
tmpfs                 2.0G  480K  2.0G   1% /dev/shm
lrm                   2.0G  2.7M  2.0G   1% /lib/modules/2.6.28-11-generic/volatile
/dev/sda1             464G   44G  421G  10% /media/disk
 
Another user wrote that the bold part was my problem, so I'm guessing that is the Ubuntu partition as things are now set on my system. What are the other figures? Where is Windows currently? If it's the /dev/sda1 partition, that makes me think I need more than 20GB for the windows partition, since I currently have a bunch of files stored there. If I move those files to an as yet uncreated "home" partition, can I then resize the Windows partition?
 
Other than those specific questions, I want to try to make sure that I'm setting myself up for success as I learn and become more familiar with Ubuntu. If I set up a Windows, an Ubuntu and a home partition now, will I regret that later (will I want another partition, etc.)? Is there anything I should do looking forward to prevent having to redo a bunch of stuff in the future? Does that even make sense?
 
Well, any help will be appreciated. Less than 24 hours ago I was pretty sure I'd never get this and I'd just stick with Windows, but the fog is already lifting and I'm getting kind of psyched to learn more about Linux.
 
Thanks,
 
Chris
 
PS - Can anyone tell me what the number of beans listed next to my name in my posts means?

---

### Post by LewRockwell on 2009-08-19
beans equals posts

.

---

### Post by mapes12 on 2009-08-19
> I have a brand new desktop with an AMD 9650 CPU, 4GB of 667 DDR? (2 I think) RAM, a 1GB ATI Radeon 4650 GPU and a 500 GB hardrive. I have Windows XP home installed and updated.Impressive spec. Do you still have your old desktop base unit to hand? If so then I would run my first Ubu install on that. I learnt a lot more by doing the install this way and didn't mess up any old windoze stuff.

---

### Post by LewRockwell on 2009-08-19
here's a screenshot of my partition editor showing my current seven operating systems:

XP
Ubuntu
Puppy Linux
Moblin Beta
EasyLFS
Mandriva
GoBoLinux

with one reserved partition and three separate swap partitions(just to be different)

actually the separate swap partitions were necessary for some experimentation and research

.

---

### Post by SuperSonic4 on 2009-08-19
I would get ubuntu 64bit with those specs and use the live cd to ensure everything works.
Read the red bit for what I would do assuming the 20gb windows could not be altered

[COLOR="Red"][list]
[*]20GiB for Windows (ntfs)
[*]20GiB for / (ext4)
[*]50GiB for /home (ext4)
[*]310Gib for data (ntfs)
[/list][/COLOR]


> **fatgreta said:**
> Hi,Looking over other forum posts about partitions, there is a general consensus that anywhere from 10 - 20 GB is plenty of space for the Ubuntu partition (at least in the threads I've found in my searches). I don't have as clear an idea about the Windows partition, but I've read that in the 20 GB range should work fine. Do those figures sound right?

That's more of a minimum working level - I would have around 50GiB altogether, more if you keep data on the same partition. Personally I have 350GiB but then I've got room to burn
 
> This is where I start to get fuzzy on things. If I have 2 20GB partitions, one for Windows and one for Ubuntu, where are the other 460GB? I've read people recommending making a "home" partition, for file storage, etc. If I do that:

That's empty space, you can use it for whatever you like. My recommendation would be to allocate **60GiB** for /home, **20GiB** for / , **20GiB** for windows and the rest for data (like music, docs, pics etc. 
 
> 1) Can I create it during installation, or must I do so later?

You may create partitions either before or during installation. If you want to do it beforehand use gparted from the live cd.

> 2) Can I store both Windows and Linux files there, and will either OS be able to access them if I boot into (Windows or Linux)?

Windows can't access extX natively at the moment (where X=2,3,4) although a fix exists for ext2 and ext3. This is why I'd recommend a data partition with ntfs which can be accessed from both OSes.

> 3) If at install I must choose to make only the Ubuntu and the Windows partitions, should I make one take up all the extra space (say 50GB for Windows, 450GB for Ubuntu), or does that not matter?

That doesn't matter although it's easier in the future if you leave some empty space. I don't think you should take up all the memory.
 
> When I ran df -h from my terminal, I got the following information:
 
Filesystem            Size  Used Avail Use% Mounted on
**/dev/sda5             2.3G  2.2G   32M  99% /**
tmpfs                 2.0G     0  2.0G   0% /lib/init/rw
varrun                2.0G  104K  2.0G   1% /var/run
varlock               2.0G     0  2.0G   0% /var/lock
udev                  2.0G  144K  2.0G   1% /dev
tmpfs                 2.0G  480K  2.0G   1% /dev/shm
lrm                   2.0G  2.7M  2.0G   1% /lib/modules/2.6.28-11-generic/volatile
/dev/sda1             464G   44G  421G  10% /media/disk
 
Another user wrote that the bold part was my problem, so I'm guessing that is the Ubuntu partition as things are now set on my system. What are the other figures? Where is Windows currently? If it's the /dev/sda1 partition, that makes me think I need more than 20GB for the windows partition, since I currently have a bunch of files stored there. If I move those files to an as yet uncreated "home" partition, can I then resize the Windows partition?

The top one is your root partition and is where everything else is under (like branches off a tree) and everything gets installed here. It's telling you there is no room left to install.
 
> Other than those specific questions, I want to try to make sure that I'm setting myself up for success as I learn and become more familiar with Ubuntu. If I set up a Windows, an Ubuntu and a home partition now, will I regret that later (will I want another partition, etc.)? Is there anything I should do looking forward to prevent having to redo a bunch of stuff in the future? Does that even make sense?

A separate /home makes it easier to reinstall/upgrade because program settings and user documents should not be affected. I like it but it's personal preference.
 
> PS - Can anyone tell me what the number of beans listed next to my name in my posts means?

The number of beans relates to post count

---

### Post by LewRockwell on 2009-08-19
and that's on a 120GB hard drive inside an Acer Aspire 8.9in Netbook

.

---

### Post by LewRockwell on 2009-08-19
.
[http://ubuntuforums.org/showpost.php?p=7786220&postcount=14](http://ubuntuforums.org/showpost.php?p=7786220&postcount=14)

.

---

### Post by mapes12 on 2009-08-19
Hello Chris

A lot of medals to other posters on very comprehensive install configs......nice!

Coming back to your objective. As I mentioned on my previous post if you have a spare base unit then that's what I would use to get acquainted with Ubu. 

If you have to use the windoze box and if it's running XP then I would do the following:

1. Boot from a GParted Live CD (or an UBU Live CD but I find the application CD easier) and make enough space for windoze (too the left) then the rest free space (to the right for Ubu). Make a note of the partition names e.g. sda(digit).

2. Boot from the Ubu installation CD. Follow the prompts. When you get to the Partitioning section select the partition you selected in stage one and then "Guided - use all free space" (that's how I remember it). Don't wory about sizes for /home and all that just now. The objective is to get Ubu installed and operational to play around with.

3. What many windoze converts sometimes forget is that you can install Ubu as many times as you like without being hounded by the MS "You must activate your key now or be shot at dawn" message. Once you get comfortable with the install routine and take a look at the automatic sizes the installer gives to "/" /home and swap you can then think about doing this manually yourself and giving /home its own partition.

---

### Post by Penguin Guy on 2009-08-19
Since you are new to Ubuntu, don't worry about making home partitions and stuff like that. If you have 500GBs _use it_. Splitting it 50/50 is probably best. [COLOR="Red"]Before you partition anything you should defrag Windows or you may delete your stuff.[/COLOR]

Also, when you come to delete Ubuntu, you can't just delete it, you need to set the **M**aster **B**oot **R**ecord back to Windows first or your system will not boot - use google to find out how.

---

### Post by mapes12 on 2009-08-19
> Also, when you come to delete Ubuntu, you can't just delete itStruggling to see why you would want to do this unless to become acquainted with UBU and try a different approach. Then once happy delete MS.

---

### Post by drs305 on 2009-08-19
fatgreta,

Ending up with a 2.3GB partition is a result of an install gone wrong - you aren't the first to suffer from the current installation design. In Step 4 of the partitioning process if you choose "side by side with Windows" you have to go to the bottom bar and slide the partitioning bar. If you don't, you will end up with a (mostly unusable) 2.3GB Ubuntu partition.

I wrote a guide explaining what happened and how to fix it 'the next time':
[HOWTO: 2.5 GB System Partition - What Went Wrong?]("http://ubuntuforums.org/showthread.php?p=7658271#post7658271")
Be sure to click on the snapshot to see what to do in Step 4.

---

### Post by LewRockwell on 2009-08-19
> **mapes12 said:**
> Struggling to see why you would want to do this unless to become acquainted with UBU and try a different approach. Then once happy delete MS.

yes, that was strange...indeed...

nevertheless, one can easily delete all other operating systems besides windows and then pop a SuperGrubDisk in to fix the ol' MBR

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

.

---

### Post by fatgreta on 2009-08-22
> **Penguin Guy said:**
> Since you are new to Ubuntu, don't worry about making home partitions and stuff like that. If you have 500GBs _use it_. Splitting it 50/50 is probably best. [COLOR=Red]Before you partition anything you should defrag Windows or you may delete your stuff.[/COLOR]

Also, when you come to delete Ubuntu, you can't just delete it, you need to set the **M**aster **B**oot **R**ecord back to Windows first or your system will not boot - use google to find out how.

OK, I thought I was all set to do this, and then read this. I'm not sure if I need to reset the MBR or not (nor am I sure what that means). I didn't think I was going to delete ubuntu, I thought I would boot from my ubuntu CD, and go through the install process again, in able to create a larger ubuntu partition and a third home partition. Do I first need to delet Ubuntu, and then figure out how to reset the MBR?

A related question, what is the G.R.U.B. disk I've had mentioned in this post, and what does it do? I went to the link in another reply, but couldn't find anything that described what it is, does, etc.

Finally, not exactly related, how do I mark a thread solved? I've got a bunch of old threads here, that I'd be happy to mark (and this one, when I finally figure this stuff out), but I don't know how that's done.

Thanks again,

Chris

---

### Post by Bartender on 2009-08-22
GRUB is short for Grand Unified Bootloader.  The typical dual-boot installation to a single HDD (which is what you're talking about) involves allowing GRUB to write a very small bit of information to the Windows Master Boot Record.  When a Windows PC starts up, the MBR is the first piece of data to be accessed.  

The GRUB tweak to the MBR tells the PC to go find GRUB Stage 1.5, which is stored in the Linux partition.  At that point you either pick an OS, or after waiting a few seconds, GRUB will tell the PC to proceed to the default OS, which can be set as either Windows or Linux by the operator.

If you remove Ubuntu later, you have to reset the Windows MBR (there are about a million posts on the subject) back to the way it was.  Otherwise that little scrap of GRUB data is still there telling the PC to go to GRUB Stage 1.5, but GRUB Stage 1.5 isn't there anymore and you get an error message.

Don't let that stop you from installing Ubuntu.

EDIT:  Super GRUB Disc is a download that you burn to a bootable CD that gives you a bunch of tools for repairing GRUB or the Windows MBR.

---

### Post by hugh v. angle on 2009-08-22
hi
I had a similar problem.

I installed ubunta a second time--bad move. On the first
installation, I failed to specify enough partition space.
I had read that ubunta takes a good percentage of Vista's
storage (my system has 500 GB); instead, it only allocated 2
GB on /mnt/sda5.  In the second installation, I reserved
250 GB. The boot table showed three OSs (two ubuntas & one
vista). Both ubunta systems showed (fdisk -l) that the device 
boot was sda5 (2 GB). As such, the system was hardly usable
with this limited space. I also noticed that sda7 had approximately
250 GB but was unmounted. When mounted, it showed that it
had the root directory along with the root's subdirectories
and files. In reading, I discovered /etc/fstab controls what
sda partition is mounted at the root.  I took the chance of
switching sda7 for sda5. I found the UUID of sda7 using
vol_id -u /mnt/sda7 (fstab uses the UUID rather than the sda7
label).  It seems to work. I now have sufficient storage space.

I knew I was going to encounter a problem with the second
installation.  However, my search of how to un-instal ubunta was
not fruitful, so I went ahead with the second installation
hoping for the best. I an curious as to why removing ubunta  
is not supported by the ubunta disk?  In my search, I encounter
a few users who had troubles removing the system. 
   
Hugh Angle

---

### Post by SuperSonic4 on 2009-08-22
Is there any reason you don't use a whole line Hugh?

fstab can use labels or it can use direct devices (such as sda1). For example
```
/dev/sda1       /mnt/Videos     ext4    defaults 0 0
``` is a perfectly acceptable line

I would not worry about the bootloader if you reinstall ubuntu, it will install grub again and all will be fine

---

### Post by fatgreta on 2009-08-22
> **Bartender said:**
> GRUB is short for Grand Unified Bootloader.  The typical dual-boot installation to a single HDD (which is what you're talking about) involves allowing GRUB to write a very small bit of information to the Windows Master Boot Record.  When a Windows PC starts up, the MBR is the first piece of data to be accessed.  

The GRUB tweak to the MBR tells the PC to go find GRUB Stage 1.5, which is stored in the Linux partition.  At that point you either pick an OS, or after waiting a few seconds, GRUB will tell the PC to proceed to the default OS, which can be set as either Windows or Linux by the operator.

If you remove Ubuntu later, you have to reset the Windows MBR (there are about a million posts on the subject) back to the way it was.  Otherwise that little scrap of GRUB data is still there telling the PC to go to GRUB Stage 1.5, but GRUB Stage 1.5 isn't there anymore and you get an error message.

Don't let that stop you from installing Ubuntu.

EDIT:  Super GRUB Disc is a download that you burn to a bootable CD that gives you a bunch of tools for repairing GRUB or the Windows MBR.

If I read this correctly, I do not need to uninstall Ubuntu, I can just boot from the Ubuntu CD and reinstall it with different partition sizes? Is this correct?

Thanks,

Chris

---

### Post by Bartender on 2009-08-22
Chris - 
I didn't understand your question.

What is your situation right now?  Do you want to remove Ubuntu?  Is it even installed?  Or are you wondering what happens sometime in the future if you want to get rid of Ubuntu?

BTW, with a 500 GB HDD, wow, I'd give Windows at least 50GB of space, and Ubuntu at least 50GB, then you could make one huge data partition.

If you have Ubuntu installed, and have decided you want to move it around a little, I'd download GParted LiveCD and burn the download to a CD just like you did the Ubuntu CD.  GParted LiveCD is my partitioner of choice.  If I'm going to install Ubuntu, I boot from a GParted LiveCD first, set up all my partitions, then when I go in with the Ubuntu install CD I just mount / and /home and swap to the partitions I already created in GParted LiveCD.

You'll run into trouble with Windows not booting if you remove Ubuntu completely, and even then fixing MBR isn't that hard.

If you move or resize the Ubuntu partitions you should be OK.  Unless you get radical and change the partitions or add some - then I'm pretty sure you'd have to manually edit grub, which could get very hairy.

If you remove Ubuntu entirely, then go right back in with Ubuntu installer CD and move partitions, then reinstall, then I'm 99% sure that you'd be OK when you're done and Windows would boot for you because GRUB would also reinstall itself.

---

### Post by fatgreta on 2009-08-22
> **Bartender said:**
> Chris - 
I didn't understand your question.

What is your situation right now?  Do you want to remove Ubuntu?  Is it even installed?  Or are you wondering what happens sometime in the future if you want to get rid of Ubuntu?

BTW, with a 500 GB HDD, wow, I'd give Windows at least 50GB of space, and Ubuntu at least 50GB, then you could make one huge data partition.

If you have Ubuntu installed, and have decided you want to move it around a little, I'd download GParted LiveCD and burn the download to a CD just like you did the Ubuntu CD.  GParted LiveCD is my partitioner of choice.  If I'm going to install Ubuntu, I boot from a GParted LiveCD first, set up all my partitions, then when I go in with the Ubuntu install CD I just mount / and /home and swap to the partitions I already created in GParted LiveCD.

You'll run into trouble with Windows not booting if you remove Ubuntu completely, and even then fixing MBR isn't that hard.

If you move or resize the Ubuntu partitions you should be OK.  Unless you get radical and change the partitions or add some - then I'm pretty sure you'd have to manually edit grub, which could get very hairy.

If you remove Ubuntu entirely, then go right back in with Ubuntu installer CD and move partitions, then reinstall, then I'm 99% sure that you'd be OK when you're done and Windows would boot for you because GRUB would also reinstall itself.

Thanks for this reply, it's getting clearer. I do have Ubuntu installed, but it is installed in too small a partition right now. I was going to simply boot from the Ubuntu CD and reinstall it, but now I understand that won't work. What I hope to do is create one more partition (a /home partition I've heard it called, for storing files and programs and such), and also enlarge the Ubuntu partition, while making the Windows partition something like 50 - 75GB.

Other things I'm confused about:


[LIST]
[*]What does it mean to "mount" a partition?
[*]What are "/" and "/home" and "swap"? I'm assuming they're partitions? Is the "/" partition the root partition, the windows partition, none of the above?
[*]If I'm going to go ahead and do this, should I make four partitions, for use as I become more familiar with Ubuntu?
[*]Are you suggesting that I uninstall ubuntu entirely, then do as you suggested with GParted, etc.? If so, how do I do the uninstall ubuntu?
[*]If I try to uninstall ubuntu and mess something up, if I have a G.R.U.B. (or Super GRUB?) CD ready, will that help me fix the problem, or will I have to reinstall windows as well?
[/LIST]
Thanks again,

Chris

---

### Post by Bartender on 2009-08-24
> **fatgreta said:**
> 
[*]What does it mean to "mount" a partition?
[*]What are "/" and "/home" and "swap"? I'm assuming they're partitions? Is the "/" partition the root partition, the windows partition, none of the above?
[*]If I'm going to go ahead and do this, should I make four partitions, for use as I become more familiar with Ubuntu?
[*]Are you suggesting that I uninstall ubuntu entirely, then do as you suggested with GParted, etc.? If so, how do I do the uninstall ubuntu?
[*]If I try to uninstall ubuntu and mess something up, if I have a G.R.U.B. (or Super GRUB?) CD ready, will that help me fix the problem, or will I have to reinstall windows as well?
[/LIST]
Thanks again,

Chris

Search "linux mount" in google for technical description.  I can tell you my own goofy understanding.  Once I can picture something in my head I can make progress toward using the information.  The picture doesn't have to be 100% accurate, it just has to work well enough so I don't screw things up.  Do you know what I mean?  When I'm installing Ubuntu and I get to that "mounting" stuff, I just think "Put It Right There".  In other words, I've already created a partition for the Linux OS, another one for swap, and a third one for /home.  So now I'm in the partitioner.  All I have to do is go to the first partition, and in the "Mount" section, I look for /.  Click on that, and / will be mounted in that first partition.  I then "mount" swap in the appropriate partition, and I "mount" /home in the third partition.  Although the picture in my mind is horribly inaccurate from a technical standpoint, "Put It Right There" works to get Linux installed in the right places.

/ = Linux OS.  That's how I think of it.  If you just let Ubuntu auto-install, everything but swap partition goes into /.  It's kind of like C: in Windows.  Kind of. :)  Formatted as ext3 or ext4.

"swap" is - well, swap is swap.  It's a virtual memory partition, similar to Windows page file.  I'm going to stick to a very simple suggestion - make it a little bit bigger than your physical memory as long as you have more than 2GB, so you can use suspend.  It's formatted as "swap" and you don't have to worry much about it.  I've never seen the Ubuntu installer fail to format it correctly as long as it's either installing automatically or you mount the partition as swap.

/home = your personal data home base.  If you manually create a partition, then mount it as /home, then your personal data will go to that partition.  If you don't manually create and mount it, /home is incorporated into /.  Once you have Ubuntu installed and you're at your desktop, you'd have to do some digging to see the difference.  You'll have a "Home" folder either way, it behaves the same, etc.  Formatted as ext3 or 4.

Tell you what, the easiest way to install Ubuntu is just create some space and let it auto-install.  You can always back up your data to an external device, and create a separate /home partition when you install the next version, or even create a /home folder later, as described in aysiu's "psychocats" website.  So it's really up to you.

As to your last questions, I think Ubuntu is installed, but to an area that's too small, right?

If you think you can push Windows over some, I'd just go right back with the Ubuntu install CD and auto-install.  I recommend that because it just sounds to me like you're not ready to try manual partitioning yet.  When you get to the partitioner, click on the existing Ubuntu partition and push it to the left.  Don't get carried away.  The further you push into Windows territory the more chance something will screw up.  Ubuntu will re-write the GRUB thing and you should be fine.

---


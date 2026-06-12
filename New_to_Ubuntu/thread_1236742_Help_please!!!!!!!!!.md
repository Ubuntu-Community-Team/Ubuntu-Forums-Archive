---
title: "Help please!!!!!!!!!"
date: 2009-08-10
forum: New to Ubuntu
---

### Post by melinda on 2009-08-10
I am frantic, I was installing updates and apparently my computer stalled, so my my husband turned it off.  Now it will not start up again.  I keep getting the message that "Ubuntu is running in low graphics mode, you may need to update your configuration to solve this" then it has a list of errors.  After this message appears I can't do anything with the computer, the cursor doesn't move and the mouse is frozen so I have to turn it off and start it up again only to get the same message loop over and over again.  I am freaking out because I have some important information and pictures on the computer that I haven't backed up yet!  What can I do? HELP!!

---

### Post by LowSky on 2009-08-10
please dont use title saying "Help Please", give a description of the problem so other who know of it can help and people with the same issue can use your post as a guide to fix if possible.

Boot into recovery mode press escape during boot to go to GRUB and choose a recovery mode of the first kernel. choose to boot to prompt, sign in then run this command 

```
sudo apt-get update && sudo apt-get upgrade
```

if it says an error let us know

---

### Post by doas777 on 2009-08-10
recovery mode is a good bet. just reboot, and right after the bios page (before anything ubuntu comes up), you should see a message to "press esc to enter grub menu". do so.
then select the option for your current kernel's "Recovery mode"
once you get to a command prompt, use the command lowsky posted. then reboot with 
```
sudo reboot
```
after that, hopefully all will be well.

---

### Post by mapes12 on 2009-08-10
Out typed!

---

### Post by melinda on 2009-08-10
> **LowSky said:**
> please dont use title saying "Help Please", give a description of the problem so other who know of it can help and people with the same issue can use your post as a guide to fix if possible.

Boot into recovery mode press escape during boot to go to GRUB and choose a recovery mode of the first kernel. choose to boot to prompt, sign in then run this command 

```
sudo apt-get update && sudo apt-get upgrade
```

if it says an error let us know



I tried it and got the same thing, as soon as the page with the prompt starts scrolling, the screen blinks on and off and then I get the same error message.This is what the list of errors say:

(EE)GARTInit: Unable to open/dev/agpgart (No such file or directory)
(EE)[drm]drmOpen failed.
(EE)intel(0): [dri]DRIScreenInit failed. Disabling DRI. VideoRAM set too low?
(EE)Intel(0): Failed to allocate framebuffer.  Is your VideoRAM set too low?
(EE)Intel(0): Couldn't allow video memory

---

### Post by halitech on 2009-08-10
first step, step back, grab a coffee/tea/smoke whatever and relax for 15 minutes. 

second, boot up the live cd and start moving things over to a thumbdrive while repeating the mantra "I will make backups" ;)

third. reboot the computer again, select recovery mode and use the xfix option to see if it can restore xorg and allow you to boot.

I'm hoping this will work and put a smile on your face at the same time to try and relieve the stress.

---

### Post by melinda on 2009-08-10
Sorry, I am a real beginner, and the last person trying to help me chewed me out for not being up with the new "millenium"  but you have to start somewhere right?  If someone has the patience with me then I can learn.  Okay...How can I type in a command if the systyem keeps blinking on and off.  I can reboot, select the recovery, then while it is running through all the commands it begins to blink and I goes to the error message before I can type anything...does that make sense?

---

### Post by melinda on 2009-08-10
Tried it and got an error again...computer won't stop blinking on and off while rebooting...

---

### Post by mapes12 on 2009-08-10
> while repeating the mantra "I will make backups"Something that should be a Ubu screensaver by default =D>

---

### Post by hysteresis on 2009-08-10
You might be better off loading your livecd and using it to access your hard drive and copy your personal files to a usb flash drive and then reloading ubuntu on your hard drive.

---

### Post by mapes12 on 2009-08-10
Can you get to a Console like this Alt+Ctrl+F3? We can help you from there.

---

### Post by lisati on 2009-08-10
+1 on (a) using a "Live CD" (you know, the one with the option "try Ubuntu without installing" option) to make a backup of important data, (b) using recovery mode to see if xfix helps, and (c) considering a fresh install if (b) doesn't work.

---

### Post by melinda on 2009-08-10
Okay...I might be so stupid, but how do I get into my hard drive while using my live cd?  I attempted it and came up empty!

---

### Post by lisati on 2009-08-10
> **melinda said:**
> Okay...I might be so stupid, but how do I get into my hard drive while using my live cd?  I attempted it and came up empty!

Don't be too hard on yourself, you're not stupid.

You should be able to access your hard drive from the Places menu.

---

### Post by hysteresis on 2009-08-10
Your drive may not be mounted because of a corrupt file system. Linux needs to mount a drive before it can see the files. It usually does this automatically. When you attempted to read your drive in the places menu and it came up empty, did an icon representing your drive appear on the desktop? If so, right click on the icon and select "mount volume". Hope this helps.

---

### Post by Elswood on 2009-08-10
When you finally figure out how to access your hard drive using your Live CD, copy all your important files onto your external USB hard drive (if you have one). Then, if all the wonderful advice given above doesn't work, re-install your Ubuntu system from your LIVE CD onto your hard drive and start fresh.  If your LIVE CD is an older version of Ubuntu (like 8.10) you must do updates (without letting your husband become impatient and re-boot unless directed to do so by the installation process) and then do a version upgrade to the latest Ubuntu (9.4).  This will take some time to do.  Also, I highly recommend you buy some basic Ubuntu books so that you can look up the procedures and jargon in the index.  And please come back to the forum with any other problems, and let us know how everything works out!:popcorn:

---

### Post by doas777 on 2009-08-10
that sucks! if your system is too hosed to go into recovery mode, then the only real option is to backup your data and reinstall. 
I reccomend creating a sepperate home partition next iteration, so that in future you can reinstall the os without danger to your user data. check out this tutorial on partitioning. it has information on seperate home partitions toward the bottom.
 
good luck

---

### Post by Elswood on 2009-08-10
You forgot to give Melinda the link to setting-up a home partition next time...

---

### Post by LewRockwell on 2009-08-10
> **melinda said:**
> Sorry, I am a real beginner, and the last person trying to help me chewed me out for not being up with the new "millenium"  but you have to start somewhere right?  If someone has the patience with me then I can learn.  Okay...How can I type in a command if the systyem keeps blinking on and off.  I can reboot, select the recovery, then while it is running through all the commands it begins to blink and I goes to the error message before I can type anything...does that make sense?

{{sigh}}

Glad you weren't chewed out on this forum.

We've read this thread and haven't observed where you provide important information about your system.

Hardware and operating system(s) are sometimes more helpful than one might suppose at first blush.

As an added benefit, taking the time to provide this information puts more distance and time between the "oh crap" moment and your further resolution to get through it and past it and hopefully become more knowledgeable and skilled in the process.

If you don't have one already...get an Ubuntu 9.04 Jaunty Jackalope LiveCD downloaded, md5sum checked, and burnt slowly to a CD-R disk.

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

While you are somewhere that this can be done you might also download, md5sum checked, and slowly burn the latest Puppy Linux LiveCD. I have recovered data using Puppy when I could not do so in both windows and ubuntu(just sayin').

[http://www.puppylinux.org/downloads/official-releases/latest-production-release](http://www.puppylinux.org/downloads/official-releases/latest-production-release)

Further, I'd like to note that for the purposes of our recovery efforts, you can't and won't be sure exactly what went wrong and how and where. It is for this reason, and also as a matter of both time considerations and your comfort level with your system, that I strongly recommend rescuing the data(documents, photos, etc) and then committing to a complete fresh installation of Ubuntu.

Also, if you have any problems with booting and the grub set-up then the Super Grub Disk can be a real helper(you might as well download and burn while you're getting Puppy).

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

keep us posted on your progress!

.

---

### Post by melinda on 2009-08-10
> **LewRockwell said:**
> {{sigh}}

Glad you weren't chewed out on this forum.

We've read this thread and haven't observed where you provide important information about your system.

Hardware and operating system(s) are sometimes more helpful than one might suppose at first blush.

As an added benefit, taking the time to provide this information puts more distance and time between the "oh crap" moment and your further resolution to get through it and past it and hopefully become more knowledgeable and skilled in the process.

If you don't have one already...get an Ubuntu 9.04 Jaunty Jackalope LiveCD downloaded, md5sum checked, and burnt slowly to a CD-R disk.

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

While you are somewhere that this can be done you might also download, md5sum checked, and slowly burn the latest Puppy Linux LiveCD. I have recovered data using Puppy when I could not do so in both windows and ubuntu(just sayin').

[http://www.puppylinux.org/downloads/official-releases/latest-production-release](http://www.puppylinux.org/downloads/official-releases/latest-production-release)

Further, I'd like to note that for the purposes of our recovery efforts, you can't and won't be sure exactly what went wrong and how and where. It is for this reason, and also as a matter of both time considerations and your comfort level with your system, that I strongly recommend rescuing the data(documents, photos, etc) and then committing to a complete fresh installation of Ubuntu.

Also, if you have any problems with booting and the grub set-up then the Super Grub Disk can be a real helper(you might as well download and burn while you're getting Puppy).

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

keep us posted on your progress!

.
Thanks, as I was CHEWED out by my uncle who is actually posting things on this thread now (along with all of his name calling, and insults to top it off)

Well I have mounted my drive using a LIVE disk. and was trying to copy my files to an external hard drive.  HOWEVER, I have now run into a big glitch:  
For some reason some of my files - (mainly my picture files which are of upmost importace to me) will not copy over, as they say they are read only, and I do not have permissions to copy or even view them as a "live" user.

Yikes!  When I loaded them to my drive from my camera - it was a copy and paste and nothing else.  So I don't know what to do now.  

Any suggestions? 

Will Puppy recover the data or SuperGrub? Do they work like the live disks?

Dell inspiron 530
Dual Core processor
250 GB HD
purchased 11/08

Ubuntu 8.1 (hardy heron) preinstalled  but upgraded to the latest versions. (was doing an update when this whole problem started  the update was stalled for 3 days, then my husband shut the power off, and now wont reboot)

---

### Post by melinda on 2009-08-10
hi alt + ctrl + f3 ?

do I do this on a live session with disk? 

or right after I boot?

I had to take my computer to my sisters house where I am now here trying to work on it.

She got me to mount my disk on a live session, and try to copy my files over to a external hd. But now I have a problem with that -- my picture files are read only and I cannot copy view nothing without permissions as a live user.  (how this happened is a complete mystery -- as I only copy and pasted them from my camera way back when I put them on to the computer)

someone down the line on this thread suggested I try supergrub?  

I desperately do not want to loose my data like pictures! So perhaps fixing this boot problem is my only hope?  or if I can figure out how to copy the pics and other files blocked as read only...as a live user then I can just reinstall everything.  

Any ideas?

Melinda

---

### Post by sandyd on 2009-08-10
> **melinda said:**
> Thanks, as I was CHEWED out by my uncle who is actually posting things on this thread now (along with all of his name calling, and insults to top it off)

Well I have mounted my drive using a LIVE disk. and was trying to copy my files to an external hard drive.  HOWEVER, I have now run into a big glitch:  
For some reason some of my files - (mainly my picture files which are of upmost importace to me) will not copy over, as they say they are read only, and I do not have permissions to copy or even view them as a "live" user.

Yikes!  When I loaded them to my drive from my camera - it was a copy and paste and nothing else.  So I don't know what to do now.  

Any suggestions? 

Will Puppy recover the data or SuperGrub? Do they work like the live disks?

Dell inspiron 530
Dual Core processor
250 GB HD
purchased 11/08

Ubuntu 8.1 (hardy heron) preinstalled  but upgraded to the latest versions. (was doing an update when this whole problem started  the update was stalled for 3 days, then my husband shut the power off, and now wont reboot)
While in Livecd, open up a terminal and tyle in the following
```
gksudo nautilus
```
and post the output of 
```
sudo fdisk -l 
```
besides, it seems more like a problem with the software / os, not the hd crash so i won't include testdisk tutorials.

---

### Post by Miguellint on 2009-08-10
> **melinda said:**
> But now I have a problem with that -- my picture files are read only and I cannot copy view nothing without permissions as a live user

Just curious....when you right-click on one of your picture files then choose Properties/Permissions who is listed as the owner of the file. Plus who are the group/others.

Also does "root" get a mention anywhere on the permissions page or is it all User#1000 or Ubuntu-Live Session User

FWIW, your files should be recoverable. It's just a permissions thing stopping you at the moment.

Regards

---

### Post by melinda on 2009-08-11
> **carlee said:**
> While in Livecd, open up a terminal and tyle in the following
```
gksudo nautilus
```
and post the output of 
```
sudo fdisk -l 
```
besides, it seems more like a problem with the software / os, not the hd crash so i won't include testdisk tutorials.
gksudo natilus worked to copy my files to my external hd.  
(SIGH...FEW-Y)

I (my sister who is typing now)is just going to reload my OS using a clean Ubuntu 9.4 disk, rather than going back to the preloaded Dell install.  Too old and don't think I want Dell tweaks.

---

### Post by melinda on 2009-08-11
Ok ..so I am installing 9.4 with a disk.  I have a question for anyone who can answer this...

is it best to create partitions now?  before I install...putting my home on a separate partition? 
and is there a reason there is a fat16, and fat32 partition?  and what's with the swap partition?

I know that dell had its own little secret partition that would reinstall the 8.10 version and all its own tweaks all over, I don't think I care about that.

How to I create the new partitions at install.  I am at the install stage:  prepare disk space (Use entire disk)  or specity partitions manually under prepare partitions..but unsure what I am doing here.

(this is Melinda's sister)

---

### Post by WakkiTabakki on 2009-08-11
> **melinda said:**
> Ok ..so I am installing 9.4 with a disk.  I have a question for anyone who can answer this...

is it best to create partitions now?  before I install...putting my home on a separate partition? 

Yes, its definitely best to do that now. Choose to set up partitions manually.
Create one partition for root (i.e the '/'-mount-point) and one partition for the 'home'-mount point. On my laptop (~80Gb disk) I've given 18Gb for '/' and 54 Gb for 'home'.
With a 250Gb disk I'd recommend giving '/' about 50Gb (most of it will probably stay empty, but it's such a hassle if it fills up), and give the rest (save the swap-space, lookie below) to 'home'.

Make them both ext3...

**NOTE!** Just to be perfectly clear: setting up the partitions will hose everything currently on the disk!

> **melinda said:**
> 
and is there a reason there is a fat16, and fat32 partition?  and what's with the swap partition?


Hmm, the fat-filesystems... It may be the Dell:s special secret restore-partition. How big is it?
You should also create a swap-partion roughly the same size as the amount of RAM you've got. The swap is used by the system to temporarily store stuff from the RAM used by inactive programs, freeing up memory for active ones... The swap is also used to store everything in the RAM when system hibernates (thus, you need as much space as there is RAM).


> **melinda said:**
> 
(this is Melinda's sister)

Good luck, Melinda's sister...
/N

---

### Post by mapes12 on 2009-08-11
Out typed

---

### Post by WakkiTabakki on 2009-08-11
> **mapes12 said:**
> Out typed

Well, the early nerd gets the worm :D

---

### Post by desperado665 on 2009-08-11
> **wakkitabakki said:**
> well, the early nerd gets the worm :d

+1

---

### Post by Ji Ruo on 2009-08-11
> **WakkiTabakki said:**
> Well, the early nerd gets the worm :D

Nerds don't get worms 'cos they use linux :p

---

### Post by melinda on 2009-08-11
very cool.  but I need some step by step from you if possible.

I have the current partiotions:
/dev/sda
 /dev/sda1 fat16  49MB      33MB used
 /dev/sda2 fat32  3224MB    1997MB used
 /dev/sda3 ext3   244660MB  27176MB used
 /dev/sda5 swap   2064MB    0MB used


the above table is what I see when I click to partition manually. Do I delete all partitions here and create a new partition table?

---

### Post by LowSky on 2009-08-11
delete them all if you don't need to save anything


the set them up like so
first partition created

give it about 20GB, and mount point is: **/**
yes "**/**" is a mount point

second create your home directory as much space as you like hopefully more than 10GB, but leave about 2000MB set aside
mount point: **/home**

lastly create a **swap **partition out of the rest

note you can create the / (root) partition larger if you like, but I find it unnecessary


hopefully this makes sense, 


oh use EXT3 or EXT4 for the file system, EXT4 is faster, but newer, EXT3 is older and supposedly more reliable.

---

### Post by melinda on 2009-08-11
all partitions are primary right?
and why the first partition 20gb?  first partition is for the OS only? 

I deleted the partitions and now my table says:
/dev/sda
 free space    250000 MB

---

### Post by melinda on 2009-08-11
oh except the swap....that's logical correct?

---

### Post by melinda on 2009-08-11
ok so why are the "/" and "/home" ext3?
and if I create a swap drive of 1.9 GB then what do I do with the rest of the space?

---

### Post by melinda on 2009-08-11
> **LowSky said:**
> delete them all if you don't need to save anything


the set them up like so
first partition created

give it about 20GB, and mount point is: **/**
yes "**/**" is a mount point

second create your home directory as much space as you like hopefully more than 10GB, but leave about 2000MB set aside
mount point: **/home**

lastly create a **swap **partition out of the rest

note you can create the / (root) partition larger if you like, but I find it unnecessary


hopefully this makes sense, 


oh use EXT3 or EXT4 for the file system, EXT4 is faster, but newer, EXT3 is older and supposedly more reliable.
ok....so it made sense, all of this makes sense...except when you said: 
  
second create your **home** directory as much space as you like hopefully more than 10GB, but leave about 2000MB set aside
mount point: /**home**.

using both words HOME threw me for a little loop.

my root partition ("/") I allocated 49.9 GB.
my home partition ("/home") I allocated 181.0 GB
my swap partition I allocated 1.9 GB

here is what my little table says:

/dev/sda
  /dev/sda1  ext3  /        53595 MB
  /dev/sda2  ext3  /home    194396 MB
  /dev/sda5  swap           2006 MB

how is that?

---

### Post by LowSky on 2009-08-11
sorry im at work... and got busy... sounds good to me

---

### Post by LewRockwell on 2009-08-11
> **melinda said:**
> ok....so it made sense, all of this makes sense...except when you said: 
  
second create your **home** directory as much space as you like hopefully more than 10GB, but leave about 2000MB set aside
mount point: /**home**.

using both words HOME threw me for a little loop.

my root partition ("/") I allocated 49.9 GB.
my home partition ("/home") I allocated 181.0 GB
my swap partition I allocated 1.9 GB

here is what my little table says:

/dev/sda
  /dev/sda1  ext3  /        53595 MB
  /dev/sda2  ext3  /home    194396 MB
  /dev/sda5  swap           2006 MB

how is that?

Hi Melinda/Melinda's Sister,

Unfortunately, you will find many different opinions and many different suggestions regarding the proper partitioning of a hard drive

So I'll throw my two cents in and then you won't hear another peep from me unless you specifically desire to partition via these suggestions and need help that others are unable and/or unwilling to offer

Partitioning 101:

Well here we are...just you, me, and this 250GB hard drive...what should we do now?

First we will run a Secure Erase function and then use GSmartControl to check the disk's health via the Parted Magic LiveCD


[http://partedmagic.com/](http://partedmagic.com/)

[http://sourceforge.net/projects/partedmagic/](http://sourceforge.net/projects/partedmagic/)


Ok, assuming that your hard drive is now securely erased and healthy we will now proceed with partitioning

I create the following partitions:

One 30GB Primary Partition at the beginning of the drive

One 20GB Primary Partition right next to the first partition

One Swap Partition equal to your system's MAXIMUM RAM(regardless of whether you're maxed out right now or not...building in future ease of upgrading)

Then you will take all the remaining space left and create one Extended Partition(inside an extended partition you can create/modify/manipulate as many logical partitions as you might desire in the future)

For the time being, if you decide you want a separate Home partition then you can create a logical partition for one in your shiny new extended partition

You're probably wondering about those first two partitions and I'll explain those now to give you some deeper insight as to my partitioning system for my own personal machines as well as the machines I set-up and maintain for others.

The first partition is created on the premise that you(or someone who buys the computer from you) will plop Windows XP/Vista/Seven/etc on it...(while it's vacant you can use it as a playground/sandbox for other stuff/distros/data/whateveryouoryoursistersodesire)

The second partition will get warm and cozy with Ubuntu 9.04 Jaunty Jackalope just as soon as we can get that crazy critter settled in!

The swap partition is set to max ram and while that seems utterly ridiculous today...tomorrow it may seem commonplace...never under-estimate advances in technology and the ever-increasing demand for more space!

The extended partition is where you can play and partition and experiment and such...with a home partition, a photo partition, a data partition, different *nix distros to goof around with...you know...whateveryouandsisterwant...

After you've completed your partitioning then when you get to the installation portion of Ubuntu pertaining to partitions you will need to manually tell it where you want your "/" mount point and your "/Home" mount point if you want them separate

Wheeee, this computin' stuff is fun!

keep us posted on your progress!

.

---

### Post by melinda on 2009-08-11
> **LewRockwell said:**
> Hi Melinda/Melinda's Sister,

Unfortunately, you will find many different opinions and many different suggestions regarding the proper partitioning of a hard drive

So I'll throw my two cents in and then you won't hear another peep from me unless you specifically desire to partition via these suggestions and need help that others are unable and/or unwilling to offer

Partitioning 101:

Well here we are...just you, me, and this 250GB hard drive...what should we do now?

First we will run a Secure Erase function and then use GSmartControl to check the disk's health via the Parted Magic LiveCD


[http://partedmagic.com/](http://partedmagic.com/)

[http://sourceforge.net/projects/partedmagic/](http://sourceforge.net/projects/partedmagic/)


Ok, assuming that your hard drive is now securely erased and healthy we will now proceed with partitioning

I create the following partitions:

One 30GB Primary Partition at the beginning of the drive

One 20GB Primary Partition right next to the first partition

One Swap Partition equal to your system's MAXIMUM RAM(regardless of whether you're maxed out right now or not...building in future ease of upgrading)

Then you will take all the remaining space left and create one Extended Partition(inside an extended partition you can create/modify/manipulate as many logical partitions as you might desire in the future)

For the time being, if you decide you want a separate Home partition then you can create a logical partition for one in your shiny new extended partition

You're probably wondering about those first two partitions and I'll explain those now to give you some deeper insight as to my partitioning system for my own personal machines as well as the machines I set-up and maintain for others.

The first partition is created on the premise that you(or someone who buys the computer from you) will plop Windows XP/Vista/Seven/etc on it...(while it's vacant you can use it as a playground/sandbox for other stuff/distros/data/whateveryouoryoursistersodesire)

The second partition will get warm and cozy with Ubuntu 9.04 Jaunty Jackalope just as soon as we can get that crazy critter settled in!

The swap partition is set to max ram and while that seems utterly ridiculous today...tomorrow it may seem commonplace...never under-estimate advances in technology and the ever-increasing demand for more space!

The extended partition is where you can play and partition and experiment and such...with a home partition, a photo partition, a data partition, different *nix distros to goof around with...you know...whateveryouandsisterwant...

After you've completed your partitioning then when you get to the installation portion of Ubuntu pertaining to partitions you will need to manually tell it where you want your "/" mount point and your "/Home" mount point if you want them separate

Wheeee, this computin' stuff is fun!

keep us posted on your progress!

.
well, I ended up with just the 3 partitions:
/ of 49.9 GB
/home of 181.0 GB
swap of 1.9 GB

and I sent it home with my sista - Melinda.

I did them all ext3 (but swap of course)

I didn't leave any freespace for future whatevers.

**Can Gparted divide up the /home partition later if needed????**  hope so....otherwise I guess we will just start all over again.

I transfered her files back to her computer before she left.  She can download all her extra programs and do the updates.  

I so appreciate all the help on this forum.  I must say I am MIGHTLY impressed!  sheesh ...you type on a Windows forum and it takes DAYS for responses if at all - and good help comes with a price! This is super cool!!  

one last question which may be sort of retarted...but when you create the /home partition -- does Ubuntu by default then place ALL the "home" files under that partition?

The sista Heather

---

### Post by RedRat on 2009-08-11
LewRockwell
That was a very good reply and great information in a very lucid form. Cheers!

---

### Post by WakkiTabakki on 2009-08-12
> **melinda said:**
> well, I ended up with just the 3 partitions:

I didn't leave any freespace for future whatevers.

**Can Gparted divide up the /home partition later if needed????**  hope so....otherwise I guess we will just start all over again.


Yup, you can redistribute the space between root and home while preserving the contents...


/N

---

### Post by Elswood on 2009-08-12
Heather (Melinda's sister) Glad you were able to get the help you needed on this forum so fast! You should join in the Revolution and saddle-up Ubuntu on your computer :) Meanwhile, I'm sure your sister will be calling you for asistance (now that you--at least--know where to look!

Bye-bye for now...

:popcorn:

---

### Post by melinda on 2009-08-12
> **WakkiTabakki said:**
> Yup, you can redistribute the space between root and home while preserving the contents...


/N
THANKS BUNCHES! Too ALL!!

from 
Melinda and her sista Heather!

---

### Post by LewRockwell on 2009-08-12
> **melinda said:**
> THANKS BUNCHES! Too ALL!!

from 
Melinda and her sista Heather!

hey, it's all good!

keep in touch!

.

---


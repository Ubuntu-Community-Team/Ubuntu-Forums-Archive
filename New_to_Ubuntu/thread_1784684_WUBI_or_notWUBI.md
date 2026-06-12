---
title: "WUBI or notWUBI"
date: 2011-06-17
forum: New to Ubuntu
---

### Post by Wray on 2011-06-17
i am confused about which kind of install i have.  WUBI or whatever the other one is called
when i installed ubuntu it was on a clean (from the factory) drive.

At the beginning of the install process i was offered some options  WUBI and a couple of other things that did not make sense to me, so i chose wubi.  I understand that a wubi install runs UNDER windows.
that can't be literally true can it since the drive i installed it on had never seen a windows install?

There was no other drive in the system at the time and ubuntu installed without problems and ran fine
and dual boots fine when i install my Window drive
I suspect it is actually WUBI, after all that is what i chose in the install process!

After reading a bit on this forum, i am unsure what kind of install i have.
Maybe WUBI just sets up dual boot???

what are the implications for WUBI or not WUBI install?

---

### Post by Mark Phelps on 2011-06-17
Wubi installs from inside MS Windows, but contrary to what some folks will tell you, does not actuall run from inside Windows.  However, it does run a little slower than a separate install, primarily because it is piggy-backing off an NTFS file, not running in an Ext3 or Ext4 filesystem.

Also, if your MS Windows filesystem crashes for any reason (i.e., unclean shutdown), you may then NOT be able to boot into Ubuntu.

And finally, the default size allocation is really SMALL -- since it's primary purpose is to give you a chance to become familiar with Ubuntu.  Once you start using it full-time, especially if you start doing big downloads into the Ubuntu space, it will fill up quickly.

The main (and possibly, ONLY) upside is that you don't have to mess around with partitioning -- which, in all fairness, can be a major PAIN if you buy a PC that comes preloaded with Win7 and the usual 4 Primary partitions.

To find out what you have, one way is to open a terminal in Ubuntu and enter "sudo fdisk -lu" (that's a Lowercase L, not a one).  If all you then see is NTFS partitions, and no Linux filesystem partitions, then you have a Wubi install.

---

### Post by Praveen30 on 2011-06-17
well , it is wubi...the others are called --by partition, by virtaul box or vmware

if you want to know more about wubi , see this--

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by computerandu on 2011-06-17
I like the title of the post...

Wubi ot notWUBI...:):lolflag:

---

### Post by _0R10N on 2011-06-17
I haven't try wubi, so I'm not an experienced opinion in this matter, but checking the type of filesystem of your drive partitions wouldn't do the trick?

---

### Post by Wray on 2011-06-17
> **computerandu said:**
> I like the title of the post...

Wubi ot notWUBI...:):lolflag:
My youngest son had a blanket he called his wubi, we couldn't separate it from him.  I thought for a while he would take it with him to university 

My file system is ext4 so, not wubi. Sorry to be such a noob.  I'm just a broken down retired engineer
whose career was pretty much concerned with hardware.  I can mess around a bit with software - can also get into a hell of a lot of trouble doing so!.

This forum is indeed an invaluable resource.  thanks y'all!

---

### Post by blackmail on 2011-06-17
Well WUBI is not an option usually, i mean it runs slower and i have found that it also creates loads of errors...

When you want to have a linux install, you could do the following.

If your computer is dedicated to the Linux installation you have you can just go ahead and install it, remember to set up the install when you select disks, so that you will have a clean install of the root ( / ) on a partition, usually the first and also the /home should be located on a separate partition.

And 10 GB are enough usually for a root partition and also the rest can be soaked up by the /home :D

Also use ext3 or ext4 as a file system, although i used reiser4 and it also worked well.

if you plan on installing a windows7 and a linux distro on the same computer, you should install first the windows system and then the linux system, this is needed because windows is kinda limited in his on cute micro-softie way and will mess up you install if you switch the orders of installation.

Hope this helped a bit.

WUBI actually i think comes from Windows UBuntu Installation

Best Regards

---

### Post by Wray on 2011-06-17
> **blackmail said:**
> Well WUBI is not an option usually, i mean it runs slower and i have found that it also creates loads of errors...

When you want to have a linux install, you could do the following.

If your computer is dedicated to the Linux installation you have you can just go ahead and install it, remember to set up the install when you select disks, so that you will have a clean install of the root ( / ) on a partition, usually the first and also the /home should be located on a separate partition.

And 10 GB are enough usually for a root partition and also the rest can be soaked up by the /home :D

Also use ext3 or ext4 as a file system, although i used reiser4 and it also worked well.

if you plan on installing a windows7 and a linux distro on the same computer, you should install first the windows system and then the linux system, this is needed because windows is kinda limited in his on cute micro-softie way and will mess up you install if you switch the orders of installation.

Hope this helped a bit.

WUBI actually i think comes from Windows UBuntu Installation

Best Regards


Thanks blackmail,
That's not exactly the way i did it
I set up one drive at a time, windows first.  Then i unplugged the windows drive and set up the ubuntu drive.

I don't remember if i had to setup the dual boot process separately, but i think the ubuntu took care of it.
I vaguely remember maybe there was an option in the install process?
iI don't really know, i have done a LOT of messing around in the last few days!

Seems to work fine with one exception - screen savers hang my system.  Also after powerup i have to do a "sudo service udev stop" otherwise i find that both processors run at near 90% capacity.

After the sudo command above it runs at 6-8%.  People on this forum have reported this as a bug

A fine example of the wonderful help available on this forum,  Kudos all!

---

### Post by wildmanne39 on 2011-06-17
> **Wray said:**
> Thanks blackmail,
That's not exactly the way i did it
I set up one drive at a time, windows first.  Then i unplugged the windows drive and set up the ubuntu drive.

I don't remember if i had to setup the dual boot process separately, but i think the ubuntu took care of it.
I vaguely remember maybe there was an option in the install process?
iI don't really know, i have done a LOT of messing around in the last few days!

Seems to work fine with one exception - screen savers hang my system.  Also after powerup i have to do a "sudo service udev stop" otherwise i find that both processors run at near 90% capacity.

After the sudo command above it runs at 6-8%.  People on this forum have reported this as a bug

A fine example of the wonderful help available on this forum,  Kudos all!Hi, yes there is a problem with the screensaver, I had to disable it and power management, also there are some people having trouble with high cpu usage, you can open system monitor and see what is causing it then it might can be fixed, as for wubi or not,post the information from this script so we can see where everything is located:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans

Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read. Then we can look and see how you installed it.

---

### Post by Sergio.G on 2011-06-17
To find out if you have WUBI installed

Boot up Windows OS and then go to:
 
"Control Panel > Add or Remove Programs" for Windows XP or 
"Control Panel > Programs and Features" for Windows Vista or Windows 7

Check if you have an Ubuntu entry in the software list.

Then if you find it there, that means you installed Ubuntu using Wubi

Complications using Wubi?

If you plan to use Ubuntu as a long term solution, then Wubi is not your guy and you should opt for the non-wubi installation (by partition)

I started my adventure in the Ubuntu Realm installing Lucid Lynx 10.04 inside a virtual machine, then I ditched the virtual machine and decided to try Wubi but had a major problem once I updated Ubuntu (using update manager inside Ubuntu) GRUB2 messed up something and I was not able to load Win7 nor Ubuntu.

That is why I switched to the dual boot partition install instead of Wubi option, and to be honest I couldn't be happier

Cheers!

---

### Post by jtarin on 2011-06-17
> **Wray said:**
> My youngest son had a blanket he called his wubi, we couldn't separate it from him.  I thought for a while he would take it with him to university 

And some people entering Linux need a WUBI too!:p

---

### Post by apollothethird on 2011-06-17
> **Wray said:**
> i am confused about which kind of install i have.  WUBI or whatever the other one is called
when i installed ubuntu it was on a clean (from the factory) drive.

At the beginning of the install process i was offered some options  WUBI and a couple of other things that did not make sense to me, so i chose wubi.  I understand that a wubi install runs UNDER windows.
that can't be literally true can it since the drive i installed it on had never seen a windows install?

There was no other drive in the system at the time and ubuntu installed without problems and ran fine
and dual boots fine when i install my Window drive
I suspect it is actually WUBI, after all that is what i chose in the install process!

After reading a bit on this forum, i am unsure what kind of install i have.
Maybe WUBI just sets up dual boot???

what are the implications for WUBI or not WUBI install?

Someone correct me if I'm wrong, but I don't think it's possible to install wubi unless you run the wubi program from inside Windows... Windows has to actually be running when you perform your install.   I don't think it's possible to boot to the Live CD and find a wubi option.

Also, I don't think it's possible to install a full Ubuntu install unless you boot the disk outside of Windows running.

If you can think back and remember for sure whether you run the Live CD from Windows or not, you'd know.

The Wubi installation procedure will give you a full installation option, but that option will let you know that you have to Boot to the Live CD to proceed with a full install.

I could be wrong, but I have never been able to find a different way of getting to the Wubi install except by running the Live CD under Windows.

When I first heard of wubi I searched high and low for the program because I wanted to test it to give support for people asking about wubi.  I eventually discovered what I'm describing here.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

---

### Post by Wray on 2011-06-17
> **apollothethird said:**
> Someone correct me if I'm wrong, but I don't think it's possible to install wubi unless you run the wubi program from inside Windows... Windows has to actually be running when you perform your install.   I don't think it's possible to boot to the Live CD and find a wubi option.

Also, I don't think it's possible to install a full Ubuntu install unless you boot the disk outside of Windows running.

If you can think back and remember for sure whether you run the Live CD from Windows or not, you'd know.

The Wubi installation procedure will give you a full installation option, but that option will let you know that you have to Boot to the Live CD to proceed with a full install.

I could be wrong, but I have never been able to find a different way of getting to the Wubi install except by running the Live CD under Windows.

When I first heard of wubi I searched high and low for the program because I wanted to test it to give support for people asking about wubi.  I eventually discovered what I'm describing here.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")


I think you are right.  My windows was not in the system when i nistalled ubuntu and i see no evidence of ubuntu on my windows drive

Unfortunately both my windows and my ubuntu drives are partitioned into 1 partition.  I cannot see any of the Windows files when running ubuntu.  I thought i would be able to see windows files.
Is that possibly because ubuntu cannot see the windows root partition which is the only one on the disk?

---

### Post by beew on 2011-06-17
So basically it is a standalone Ubuntu install, congratulations!

Instead of swapping hard drives I simply install Ubuntu and a whole bunch of other Linuxes in an external hard drive and boot into it. It is the same thing. 

Instead of Windows I also have Ubuntu installed internally. But the external installation has other Linux distros and also the Ubuntu there is of a different version and I use it for testing. I can also boot from other computers so this is like a portable OS (for that I can't install proprietary graphic drivers)

> Unfortunately both my windows and my ubuntu drives are partitioned into 1  partition.  I cannot see any of the Windows files when running ubuntu.   I thought i would be able to see windows files.
Is that possibly because ubuntu cannot see the windows root partition which is the only one on the disk?

The Ubuntu disk should have 3 partitions (/, /home and swap) If you are running Ubuntu you can simply connect the Win drive like a usb device and Ubuntu should be able to see its content.

---

### Post by wildmanne39 on 2011-06-17
Hi, you should see window files in ubuntu, open file manager and on the left side you should see your windows drive. But the only way that you could have windows and ubuntu on the same partition is a wubi install or install in a virtual machine like with virtualbox. I still think you should run the boot script so we can see what your hard drive look like.
Post the information from this script so we can see where everything is located:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans

Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.

---

### Post by Wray on 2011-06-18
> **Sergio.G said:**
> To find out if you have WUBI installed

Boot up Windows OS and then go to:
 
"Control Panel > Add or Remove Programs" for Windows XP or 
"Control Panel > Programs and Features" for Windows Vista or Windows 7

Check if you have an Ubuntu entry in the software list.

Then if you find it there, that means you installed Ubuntu using Wubi

Complications using Wubi?

If you plan to use Ubuntu as a long term solution, then Wubi is not your guy and you should opt for the non-wubi installation (by partition)

I started my adventure in the Ubuntu Realm installing Lucid Lynx 10.04 inside a virtual machine, then I ditched the virtual machine and decided to try Wubi but had a major problem once I updated Ubuntu (using update manager inside Ubuntu) GRUB2 messed up something and I was not able to load Win7 nor Ubuntu.

That is why I switched to the dual boot partition install instead of Wubi option, and to be honest I couldn't be happier

Cheers!

 Thanks  y'all for all responses thus far.

Here is my situation at this point
I hav e repartitioned my ubuntu disk into  HOME, BOOT, USR, TEMP, SWP partitions
and reinstalled using the ubuntu install disk  The repartition was done as part of the install process

I have noted a vouple of changes from the original    installation referenced in this thread preceding this post, 

1.  Screen savers no longer hang the system.  They stop movement after about 5 minutes,but do not hang the system as before

2. I no longer have the 90% processor usage reported above.  The systen now comes up from cold start  running at about 6-8%

NEW QUESTION:  How do i see what is actually resident in each partition?

---

### Post by wildmanne39 on 2011-06-18
> **Wray said:**
> Thanks  y'all for all responses thus far.

Here is my situation at this point
I hav e repartitioned my ubuntu disk into  HOME, BOOT, USR, TEMP, SWP partitions
and reinstalled using the ubuntu install disk  The repartition was done as part of the install process

I have noted a vouple of changes from the original    installation referenced in this thread preceding this post, 

1.  Screen savers no longer hang the system.  They stop movement after about 5 minutes,but do not hang the system as before

2. I no longer have the 90% processor usage reported above.  The systen now comes up from cold start  running at about 6-8%

NEW QUESTION:  How do i see what is actually resident in each partition?Hi, I am not sure exactly what you are asking but you can look at your partitions with disk utility or gparted just make sure you do not change anything.

---

### Post by apollothethird on 2011-06-18
> **Wray said:**
> Thanks  y'all for all responses thus far.

Here is my situation at this point
I hav e repartitioned my ubuntu disk into  HOME, BOOT, USR, TEMP, SWP partitions
and reinstalled using the ubuntu install disk  The repartition was done as part of the install process

I have noted a vouple of changes from the original    installation referenced in this thread preceding this post, 

1.  Screen savers no longer hang the system.  They stop movement after about 5 minutes,but do not hang the system as before

2. I no longer have the 90% processor usage reported above.  The systen now comes up from cold start  running at about 6-8%

NEW QUESTION:  How do i see what is actually resident in each partition?

Run "gparted".  If it's not installed, run, "sudo apt-get install gparted".

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

---

### Post by Wray on 2011-06-18
How do i post a screen shot from gparted?   I want to post the partition scheme i currently have ubuntu  installed into
and have the good people here tell me what is wrong with it.  It doesn't look right to me, but then i am a total noob

---

### Post by apollothethird on 2011-06-18
> **Wray said:**
> How do i post a screen shot from gparted?   I want to post the partition scheme i currently have ubuntu  installed into
and have the good people here tell me what is wrong with it.  It doesn't look right to me, but then i am a total noob

Someone will probably tell you how to post a screen shot, but I'll tell you something about using gparted and getting information to us.

First off, it's be easier to send us the text from the script of your new environment than trying to send us a bunch of pictures.  We can go over the text with you and tell you how it relates to what you're looking at on gparted.

As far as gparted, when it initially starts it will show you how one drive is partitioned.  You might not initially be looking at the drive that has the information that you're looking for.  Click on the GParted menu item at the top, point to Devices and look at the other devices to get information of how they are partitioned.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

---

### Post by dFlyer on 2011-06-18
My advice is to dual boot with separate OS. One partition for you original OS and one for ubuntu. I've not heard anything good about wubi, except for just testing linux.

---

### Post by Sergio.G on 2011-06-19
> **Wray said:**
> NEW QUESTION: How do i see what is actually resident in each partition?

In Ubuntu there is a graphical utility that allows to analyze disk usage and displays the disk space occupied by every directory on your computer, the name is Disk Usage Analyzer (Baobab) this belongs to the gnome-utils package.

If you don't have it installed go to synaptics and search for baobab or gnome-utils

You could also type the next command using the command line to have a quick overview on the space available on all the current mounted file systems

```
df -Th
```

df: report file system disk space usage
  T: print file system type
  h: print sizes in human readable format (e.g., 1K 234M 2G)

for more info check the man page (man df)

Hope I didn't misunderstand the question :)
Cheers

---

### Post by Wray on 2011-06-19
> **Sergio.G said:**
> In Ubuntu there is a graphical utility that allows to analyze disk usage and displays the disk space occupied by every directory on your computer, the name is Disk Usage Analyzer (Baobab) this belongs to the gnome-utils package.

If you don't have it installed go to synaptics and search for baobab or gnome-utils

You could also type the next command using the command line to have a quick overview on the space available on all the current mounted file systems

```
df -Th
```df: report file system disk space usage
  T: print file system type
  h: print sizes in human readable format (e.g., 1K 234M 2G)

for more info check the man page (man df)

Hope I didn't misunderstand the question :)
Cheers
  Thanks Sergio, i will certainly look at that/those...looks llike there may be some good info there vis vis my linux education.

But what i really wanted is to be able to post a screen shot from terminal
thanks

---

### Post by Sergio.G on 2011-06-19
In Ubuntu there is an application installed by default, depending on the
version you will find it in Applications >> Accessories >> Take Screenshot

This utility is part of the gnome-utils package, if you don't have install this package from synaptics

Alternate Method:
By pressing this key combinations "alt + f2" on your keyboard, it will popup the run application utility

then write this:

```
gnome-screenshot --interactive
```


Hope it helps.
Cheers

---

### Post by shuttleworthwannabe on 2011-06-19
If you can figure how to solve [this]("http://ubuntuforums.org/showpost.php?p=10957151&postcount=1"), i might add my weight against Wubi; best to partition.

---

### Post by apollothethird on 2011-06-19
> **Wray said:**
> Thanks Sergio, i will certainly look at that/those...looks llike there may be some good info there vis vis my linux education.

But what i really wanted is to be able to post a screen shot from terminal
thanks

You might also try hitting the "Print Screen" key.  This snaps a picture of my desktop and bring the screenshot application up with the images for me to decide what to do with it.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

---

### Post by shuttleworthwannabe on 2011-06-27
> **shuttleworthwannabe said:**
> If you can figure how to solve [this]("http://ubuntuforums.org/showpost.php?p=10957151&postcount=1"), i might add my weight against Wubi; best to partition.

And [here is the solution]("http://ubuntuforums.org/showpost.php?p=10961522&postcount=17").

But to get to the topic--There is definately a performance drop if you choose to go WUBI route; but if you just want to test on a machine that is not your own (temporarily, because no partitioning is done on base system) then WUBI is the way to go.

---

### Post by jtarin on 2011-06-27
> **shuttleworthwannabe said:**
> And [here is the solution]("http://ubuntuforums.org/showpost.php?p=10961522&postcount=17").
[That's only part of the solution.]("http://www.howtogeek.com/howto/17903/remove-ubuntu-or-xp-from-the-windows-7-boot-menu/")

---


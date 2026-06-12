---
title: "Need help choosing a Flavor"
date: 2009-08-25
forum: New to Ubuntu
---

### Post by k33bz on 2009-08-25
Ubuntu is obviously my favorite flavor to choose. However in this case. For my son's computer Ubuntu will not be a choice.

Reason being is that I have an extra tower which I will be giving to my son who is 6 yrs old. So the OS needs to be attractive, yet simple and light with a few kids games and learning programs.

Here is the problem though, and why it wont be Ubuntu. This is an old computer, an HP Vectra. I am not sure on how much CPU power it has, but I know it has 272 mb RAM. one 256mb RAM and 4 sticks of 4MB RAM. Really old school sticks of RAM.

So what Flavor of Linux should I choose for this Tower. I was thinking Damn Small Linux, but I didnt see any kid games or learning apps available.

---

### Post by Bachstelze on 2009-08-25
Do a command-line installation of Ubuntu and install XFCE on it. Then you can proceed to installing any game you want, and maybe change the theme or whatnot.

---

### Post by k33bz on 2009-08-25
> **HymnToLife said:**
> Do a command-line installation of Ubuntu and install XFCE on it. Then you can proceed to installing any game you want, and maybe change the theme or whatnot.

ok, sounds easy enough. I know XFCE is very light weight. Question though. Does Ubuntu have a text-base install that fits onto a USB? I dont have a cd-rom on the computer in question.

Only options I have is either via USB, Network, or Floppy Drive.

Any options given to me is greatly appreciated :)

---

### Post by Old_Grey_Wolf on 2009-08-25
**I may be wrong**; however, that computer looks like it has a 486 DX2 processor. The BIOS for those old computers do not have an option for you to boot from a CD or USB. Therefore, it will most likely be very hard or impossible to install a Linux distro or any non-floppy based OS on that machine.

I wouldn't waste my time; however, **if you are up to the challenge** you could give it a try.

Good Luck!

---

### Post by Bachstelze on 2009-08-25
> **Old_Gray_Wolf said:**
> **I may be wrong**; however, that computer looks like it has a 486 DX2 processor.

A 486 with 256MB of RAM? That's unlikely, I don't even know whether they support it.

@OP: yes, the mininmal ISO for Ubuntu is only 11MB and can be put on an USB Flash drive to install from it.

[http://archive.ubuntu.com/ubuntu/dists/jaunty/main/installer-i386/20081029ubuntu34/images/netboot/mini.iso](http://archive.ubuntu.com/ubuntu/dists/jaunty/main/installer-i386/20081029ubuntu34/images/netboot/mini.iso)

Here's how to do it (pasted from [https://help.ubuntu.com/community/Installation/FromUSBStick):](https://help.ubuntu.com/community/Installation/FromUSBStick):)

> - Thanks for the advice guys, it also worked on my laptop: got it installed with 7.10 (and the encrypted LVM partitions I needed). I needed

a) a network link and install mini.iso,

b) a working system with syslinux and mtools (On feisty: apt-get install syslinux).

c) cat /etc/mtab to find out my usb was at /dev/sdb1, mounted as /media/Flashdisk:

    * syslinux -s /dev/sdb1
    * mount -o loop /home/stilus/Desktop/mini.iso /media/cdrom0/
    * cp -r /media/cdrom0/* /media/Flashdisk
    * cd /media/Flashdisk
    * mv isolinux.cfg syslinux.cfg
    * cd /
    * umount /media/Flashdisk 

Plugged this Flashdisk in my to-be-installed system, and that was that: let the netinstall begin!! -- stilus

---

### Post by nhasian on 2009-08-25
your giving your son a 486 computer?  dont you love him?  my cell phone has more processing power than that.  :)

actually there are a lot of packages you can install in ubuntu for young children.  I installed a bunch of learning games to teach abc's, simple arithmetic, memory games, etc.  its all in the repos.

---

### Post by k33bz on 2009-08-25
> **nhasian said:**
> your giving your son a 486 computer?  dont you love him?  my cell phone has more processing power than that.  :)

actually there are a lot of packages you can install in ubuntu for young children.  I installed a bunch of learning games to teach abc's, simple arithmetic, memory games, etc.  its all in the repos.

ya I do, but low on cash, real low. At fo the computers I have left over, that would be the best one. So at this moment in time I dont have much of a choice.

---

### Post by LunaticHiatus on 2009-08-25
xfce might be a little bloated. Do a minimal install (just google ubuntu minimal for the iso) and install it with unetbootin.
I suggest using LXDE as a desktop manager though. Its about as light as you can get without having to go threw massive configuration.

---

### Post by 0faber on 2009-08-25
You might try [http://www.qimo4kids.com]("Qimo") It's based on Xubuntu and comes with software for kids. It might be a little fat though.

---

### Post by Old_Grey_Wolf on 2009-08-25
> **HymnToLife said:**
> A 486 with 256MB of RAM? That's unlikely, I don't even know whether they support it.

@OP: yes, the mininmal ISO for Ubuntu is only 11MB and can be put on an USB Flash drive to install from it.

[http://archive.ubuntu.com/ubuntu/dists/jaunty/main/installer-i386/20081029ubuntu34/images/netboot/mini.iso](http://archive.ubuntu.com/ubuntu/dists/jaunty/main/installer-i386/20081029ubuntu34/images/netboot/mini.iso)

Here's how to do it (pasted from [https://help.ubuntu.com/community/Installation/FromUSBStick):](https://help.ubuntu.com/community/Installation/FromUSBStick):)

The HP Vectra is an old computer. 

What I am trying to point out is that a computer of that vintage may not support booting from CD or USB to install the OS. 

The OP needs to look at the BIOS boot options to determine if it can actually boot from a CD or USB.

---

### Post by R_W322 on 2009-08-25
What model Vectra is it? I can't find any reason with the specs that it wouldn't work fine with a USB stick and Xubuntu? 

RYAN.WDZIECZNY

---

### Post by mlthmp on 2009-08-25
> **Old_Gray_Wolf said:**
> **I may be wrong**; however, that computer looks like it has a 486 DX2 processor. The BIOS for those old computers do not have an option for you to boot from a CD or USB. Therefore, it will most likely be very hard or impossible to install a Linux distro or any non-floppy based OS on that machine.

I wouldn't waste my time; however, **if you are up to the challenge** you could give it a try.

Good Luck!


Question. If this is the case (I still have an old 486 in the closet too, lol) could he possibly use a floppy for bootup.. one that has CD drivers? Is there any way he could do this and install in this manner?

I know when I last used it I installed Windows 95 from CD (blank HD) I used a floppy boot disk with CD drivers enabled. Would the same work for him with a linux install?

Just wondering, im still learning the OS itself, and not quite versed on how everything works lol.

---

### Post by k33bz on 2009-08-25
> **Old_Gray_Wolf said:**
> The HP Vectra is an old computer. 

What I am trying to point out is that a computer of that vintage may not support booting from CD or USB to install the OS. 

The OP needs to look at the BIOS boot options to determine if it can actually boot from a CD or USB.

Actually, you are half right. The Vectra dont support booting from USB, but it can boot from a CD-Rom. I had to borrow a CD-ROM from my parts pile, I have already tried DSL, did not like to much, to much difficulty for a child. 

So now I am currently burning an ISO image of Qimo. Thanks 0faber



R_W322
The Model is HP Vectra VL5/133 Series 5 DT
It wont boot from USB :(

---

### Post by R_W322 on 2009-08-25
What if you just pulled the harddrive and loaded Xubuntu from you're computer? I don't know if there'd be a compatibility issue but it might be something to try?

RYAN.WDZIECZNY

---

### Post by k33bz on 2009-08-25
> **R_W322 said:**
> What if you just pulled the harddrive and loaded Xubuntu from you're computer? I don't know if there'd be a compatibility issue but it might be something to try?

RYAN.WDZIECZNY

Doing it that way I would have to mess with the MBR, and that sometimes can be quite a pain to deal with :)

---

### Post by k33bz on 2009-08-25
> **0faber said:**
> You might try [http://www.qimo4kids.com]("Qimo") It's based on Xubuntu and comes with software for kids. It might be a little fat though.

Seems like it may well be a tad bit fat. Ran the LiveCD, go to the boot menu, and it loads up a window with a table full of letters and numbers. Then drops down to a CLI. SO from there I went ahead and chose to boot directly to a Live Boot. For the last 5 mins now I have been waching the loading bar go back and forth, lol. Not sure if it is installing or not.



UPDATE: Was not able to install Qimo. Which truthfully sucks, Really wanted to get that one for my son. Anyway, I decided to look a little more into it. Had to repeatedly reset the computer so I could read it all. Only gave me like 1.5 seconds to read anything while transeferring from the Vectra Screen to the CMOS and finally to the BIOS screen.

Anyway, this computer actually is only reading out 256 MB RAM, not the 272 that it should of been. And the CPU is only a Pentium Processor 133MHz. I looked around, I dont think I will find a distro that will be suited for my son that will be able to run on this computer. I am not even sure if I will be able to update the CPU from 133MHz to a 400MHz CPU. I know I can find them (socket 7), just am not sure it will work or not. I dont have any specs for this mother board.

---

### Post by k33bz on 2009-08-26
bump

only cause I had to edit my last post

---

### Post by snowpine on 2009-08-26
Deli Linux will run on a Pentium 1:

[http://www.delilinux.de/](http://www.delilinux.de/)

Check out 3rd screenshot... 133mhz just like yours!
[http://www.delilinux.org/wiki/doku.php?id=screenshots](http://www.delilinux.org/wiki/doku.php?id=screenshots)

---

### Post by k33bz on 2009-08-26
> **snowpine said:**
> Deli Linux will run on a Pentium 1:

[http://www.delilinux.de/](http://www.delilinux.de/)

Check out 3rd screenshot... 133mhz just like yours!
[http://www.delilinux.org/wiki/doku.php?id=screenshots](http://www.delilinux.org/wiki/doku.php?id=screenshots)

Ya, I saw that, so I have it already burned. THis is my second attempt to install. keeop getting a L 99 99 99 99 99 LILO Error.

---

### Post by random turnip on 2009-08-26
Well, if Xubuntu won't work (i don't think it will) and you don't like DSL or Puppy Linux, try DeLi.

---

### Post by 0faber on 2009-08-26
Take a look at this [http://kmandla.wordpress.com/2009/03/19/the-k6-2-debian-5-lxde-and-not-qimo/]("http://kmandla.wordpress.com/2009/03/19/the-k6-2-debian-5-lxde-and-not-qimo/") You also might be able to contact kmandla and ask for advice. (Kmandla is or used to be a moderator on the Ubuntu forums, and seems like a really nice person.)

---

### Post by k33bz on 2009-08-26
> **random turnip said:**
> Well, if Xubuntu won't work (i don't think it will) and you don't like DSL or Puppy Linux, try DeLi.

From what I have read, I am loving DeLi. However I am having problems with the Lilo Boot Loader. I need help with that part. I have installed twice so far, each time ending up with this error after I re-boot.

```
L 99 99 99 99 99 99 99 99
```

The 99 keeps repeating itself for a few lines

---

### Post by k33bz on 2009-08-27
Ok, I got that part fixed now. I have DeLi installed on this old computer. Have some other issues right now. But I will be taking those to the forums on DeLi's site. Unless someone here wants to volunteer their help.

Thanks to all that helped.

---

### Post by k33bz on 2009-08-30
> **HymnToLife said:**
> Do a command-line installation of Ubuntu and install XFCE on it. Then you can proceed to installing any game you want, and maybe change the theme or whatnot.

will it work on this machine? Reason I ask is, I do have DeLi installed on it now, but what is available for me to add on to it is very  limited.

---

### Post by halitech on 2009-08-30
if  you are already familiar with Ubuntu, you shouldn't have any issues doing a base Debian install and installing XFCE or LXDE as it will give you more or less the same apps as you are already familiar with

[http://forums.debian.net/viewtopic.php?t=26566](http://forums.debian.net/viewtopic.php?t=26566)

---

### Post by k33bz on 2009-08-31
> **halitech said:**
> if  you are already familiar with Ubuntu, you shouldn't have any issues doing a base Debian install and installing XFCE or LXDE as it will give you more or less the same apps as you are already familiar with

[http://forums.debian.net/viewtopic.php?t=26566](http://forums.debian.net/viewtopic.php?t=26566)

I have done a base install of etch then a distro upgrade to lenny so as to install lxde. Problem is after all this startx does not work. After digging around a bit I saw that I dont have ~/.xinitrc anywhere nor do I even have a directory for X11.

Where have I messed up at?

---

### Post by halitech on 2009-09-01
from here: [http://forums.debian.net/viewtopic.php?f=17&t=44738&hilit=lxde](http://forums.debian.net/viewtopic.php?f=17&t=44738&hilit=lxde)

```
If you don't have an ~/.xinitrc file, you can always just create one that says exec startlxde
```

---

### Post by k33bz on 2009-09-01
> **halitech said:**
> from here: [http://forums.debian.net/viewtopic.php?f=17&t=44738&hilit=lxde](http://forums.debian.net/viewtopic.php?f=17&t=44738&hilit=lxde)

```
If you don't have an ~/.xinitrc file, you can always just create one that says exec startlxde
```

yes that is me from the other site, so as you can see it is more than just missing the .xinitrc file, which was already created and failed to work.

I am actually re-installing, seems to be a botched install

---

### Post by cascade9 on 2009-09-01
> **k33bz said:**
> Anyway, this computer actually is only reading out 256 MB RAM, not the 272 that it should of been. And the CPU is only a Pentium Processor 133MHz. I looked around, I dont think I will find a distro that will be suited for my son that will be able to run on this computer. I am not even sure if I will be able to update the CPU from 133MHz to a 400MHz CPU. I know I can find them (socket 7), just am not sure it will work or not. I dont have any specs for this mother board.

256MB not 272MB is probably from your motherboard not being able to read from both the 72 pin and 168 pin ram. 

I doubt you will get a 400 running on that chipset (its a HX). You might get a 400 running @ 332 or 300 (83mhz or 75mhz FSB x 4). Probably, teh fastest thing you can put into that board without under clocking would be a P200/P233 or maybe a K6-300 (K6-2 300-450 might run as well, but only with an underclock). Maybe. Depends on your motherbaord if the faster AMD chips are even supported.

---

### Post by k33bz on 2009-09-01
Ok here is the update, took along while to install and upgrade the distro this time around. I pretty much have the same problems, but finally I am actually getting an output of information on why it is not working unlike last time.

```
Failed to load module "s3" (Module does not exist,0)
No drivers available

Fatal server error:
no screens found
```

Obviously this is only a partial list, but these are the only errors and or warnings that show.

---

### Post by k33bz on 2009-09-03
This is now working, everything, I had to load the S3 Video Driver. 

This computer is now running Debian with LXDE and Slim.

---


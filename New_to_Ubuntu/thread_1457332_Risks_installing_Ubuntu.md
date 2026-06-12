---
title: "Risks installing Ubuntu"
date: 2010-04-18
forum: New to Ubuntu
---

### Post by MightyDwarf on 2010-04-18
Hi, I'd like to know what are the risks when I install Ubuntu...
Will it affect the speed of my PC? Will it affect the speed of my games and applications as well?
'cause I'm not sure about installing Ubuntu, and I'm actually too chicken to install Ubuntu alone, so I'll ask whether it's easy to install Ubuntu or not. I have already burned an ISO image on a DVD, version 9.10 and 8.XX ... something can't remember. Which Ubuntu should I install.
Can I expect any troubles after installing the OS? I heard you've to download some drivers for your graphics card to see the cool effects of Ubuntu, but I'm scared whether it affects my games and the stability of Windows Vista?
So.. Either i install Ubuntu to see what happens or just leave my Vista (though it's very unstable and uncomfortable to me)?
I know it's many questions, but there are surely people that like to help beginners like me.
Thank you very much.
BTW my graphics card is from ATI, 5670 model with IceQ cooler...
4GB RAM and a Quad Core Q6600, just in case.

---

### Post by -humanaut- on 2010-04-18
If you burned two ISO images on a single DVD you're already going to have trouble.

---

### Post by mgranet on 2010-04-18
Save yourself the fear. Just install Ubuntu in a virtual machine to see if you like it. Since all the hardware will be piped or emulated, you won't have to worry about hardware not working. Or worry about deleting partitions, having bootloader issues...
[http://www.virtualbox.org]("http://www.virtualbox.org")

---

### Post by MightyDwarf on 2010-04-18
> **-humanaut- said:**
> If you burned two ISO images on a single DVD you're already going to have trouble.

Nah, don't worry. I knew it'd be wrong if I'd burn two ISO images, so I burned 2 apart DVDs.

> **mgranet said:**
> Save yourself the fear. Just install Ubuntu in a  virtual machine to see if you like it.
[http://www.virtualbox.org]("http://www.virtualbox.org/")

I already tried it at my gf's house, and I really liked it.

---

### Post by rosswmcgee on 2010-04-18
First reply is correct. Also since the new release is near I would wait. After all that I think you will find a clean install a piece of cake and the system much easier to use and just as fast if not faster.

---

### Post by howefield on 2010-04-18
> **MightyDwarf said:**
> .. so I'll ask whether it's easy to install Ubuntu or not...

You wrote a couple of months ago the following so I guess you already know the answer to that.

> **MightyDwarf said:**
>  My uncle told me about Ubuntu a week ago, so now when I had some time I could install it.
First try Ubuntu 9.10 downloaded, burned onto a CD, installed it (it was soo easy! :) )

---

### Post by barney385 on 2010-04-18
Ubuntu is the best supported OS in the world. Hands down.

If you like playing games, I'd use a dual-boot set-up, as I don't recommend WINE---that's just my preference though.

Ubuntu is 10 fold more secure on the interwebs than any MS product for sure...

---

### Post by Kayden on 2010-04-18
I'd have to say nowadays, so long as your hardware is adequately supported (which it's very unlikely that it *isn't*), Ubuntu is wholly safe to install. Since you've said you've already tried it on another PC and liked it, I don't see how firing up a LiveCD and seeing how it runs on your machine would be a bad idea! I do have to agree, though, that it's probably best to stick it out until Lucid's released.

[quote="barney385"]Ubuntu is the best supported OS in the world. Hands down.

If you like playing games, I'd use a dual-boot set-up, as I don't recommend WINE---that's just my preference though.

Ubuntu is 10 fold more secure on the interwebs than any MS product for sure...[/quote]
I'd keep this in mind, too; if you're a gamer, dual-booting's the way to go. WINE is all right for small applications that just need to have converted API calls to run. Games, however, are often more complex than that sort of software and frequently require advanced configuration to work.

---

### Post by Keiran230 on 2010-04-18
If you want the newest features (like btrfs) Fedora would be better, or if you want speed, maybe SliTaz or something, but if you want a very simple and supported distro, you've picked the right one. It has the smallest chance of user error, so that's not that much of a risk.

The only problem I've ever had with installing drivers is for wifi. Even if you have hardware that only works with proprietary drivers, Ubuntu will normally find them for you (You just have to give Ubuntu permission to install them, for legal reasons). Make sure you have an ethernet connection at first, just in case. Proprietary drivers are NOT bundled automatically with Ubuntu, because Ubuntu is licensed as GPL, not LGPL. It will automatically download them, but they won't just be there already.

If you're really worried about breaking Windows and don't want to use normal VMware like Virtualbox, you can always install it with WUBI, [here]("http://wubi-installer.org/").

Concerning the cool effects, there are basic ones installed in Ubuntu by default, but if you want the more advanced ones, search the package manager for something called Compiz Fusion.

---

### Post by Arand on 2010-04-18
The ubuntu install should under normal circumstances not affect the operation of windows.

If installed in a "Dual-Boot" they will run independently, Ubuntu will take up its chunk of storage space on the harddisk, and windows has it's chunk but they will run independently and not affect the performance of the other at all.

To make media (CD/DVD) from which you can install you will need to (if you have not already) follow the instructions here: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

The Ubuntu installer will guide you through setting up a dual-boot if you choose to install it.

This screecast illustrates the process: [http://screencasts.ubuntu.com/2009/09/02/Ubuntu_Dual_Boot_Install](http://screencasts.ubuntu.com/2009/09/02/Ubuntu_Dual_Boot_Install)

- Arand

---

### Post by Keiran230 on 2010-04-18
This was an afterthought... I'm pretty sure if you install Ubuntu as a dualboot beside Windows by repartitioning it, Windows will now boot from grub as the bootloader, not the original booloader. Therefore, so long as Ubuntu is installed, it will work, but if you delete ubuntu's partition (and thus, the /boot/) Windows will still be present on disk, but your computer won't know where the bootloader is. You will then get a "NTLDR not found" or something like that. I'm pretty sure you can repair this using XP's original install disk though, if you're willing to go through that mess. This is why I tend to be paranoid about dualboot systems.

---

### Post by barney385 on 2010-04-18
> **Keiran230 said:**
> This was an afterthought... I'm pretty sure if you install Ubuntu as a dualboot beside Windows by repartitioning it, Windows will now boot from grub as the bootloader, not the original booloader. Therefore, so long as Ubuntu is installed, it will work, but if you delete ubuntu's partition (and thus, the /boot/) Windows will still be present on disk, but your computer won't know where the bootloader is. You will then get a "NTLDR not found" or something like that. I'm pretty sure you can repair this using XP's original install disk though, if you're willing to go through that mess. This is why I tend to be paranoid about dualboot systems.

Yeah, I can understand that. Windoze needs to be installed first, then if you decide you like it, Ubuntu cans be installed *after* and partitioned accordingly...but that's another thread...


:smile:

---

### Post by Gjallarbru on 2010-04-18
Hope you like to read...

**First the ISO**

Burn only one image to the disc.  If you have 2 files named "something.ISO" on your disk, neither will work.  

Vista has NO ISO BURNING CAPABILITY ON IT'S OWN.  You will need something like ISO Recorder ( [http://isorecorder.alexfeinman.com/isorecorder.htm](http://isorecorder.alexfeinman.com/isorecorder.htm)).  With that, you'll be able to burn your disk properly.

A properly burned imaged should created a disk with many files and folders on it (not just the iso files).  Open your disk and see for yourself.

**Second, the choices**

**1)** You can boot of the CD and try Ubuntu live.  It will be slower than normal (CD-roms are slow), but you can try it without any change to your system.

**2)** Wubi installation:  Install Ubunut on your current filesystem.  The least intrusive choice.  Ubuntu will only take space on your disk, but since it will be using a windows filesystem, it will be slower than a "true" install on Linux native file system.  The advantage is that Ubuntu will be no different than other software on you machine in terms of installing and removal.

**3)** Dual-boot:  Probably the best choice if you are a gamer and wanting Ubuntu to full strength.  With that choice, Ubuntu will need to resize your partitions on your hard disk to make space for itself (unless you have a spare disk).  Resizing is somewhat a long process, but it can be left entirely on automatic during installation.  Back up your data, as things could go wrong (like if you choose to do this without a battery (UPS), in a thunderstorm.  If thunder hits the powerlines while resizing and power goes out, so does your data on the hard disk).

The reason for choice 3 is that it will leave Vista intact and give you ubuntu.  Although many windows games do run on Linux (with wine technology: [www.winehq.com](www.winehq.com)), there's no way to be certain they will run.  So keeping windows around for a serious gamer is not really a choice, it's more of a must.  I'm not much of a gamer these days, but I still have windows for the occasional gaming fix.

**4)** A pure Ubuntu install:  Ubuntu will erase your hard disk and install itself.  If you are a windows gamer, you might regret this one.  There are games for Linux, but they aren't many with "commercial equivalent" in my opinion.

Choices 3 and 4 are in the install menu once you booted with the disk.  Just click the one you want. 

Choice 1, will not change anything to your system.  Choice 2 and 3 will give you the option of booting Windows or Ubuntu.  If you run one, the other will be completely unaffected and run as usual.  You will have to reboot to change OS. 

**The install**

Installing Ubuntu has been entirely painless for me for the last 3 years.  I have a friend who, out of the blue, jumped ship to Ubuntu and is happier for it.  He did the install without my help.  I did help him for some specifics of his personal needs, but not for the install.  That was with Ubuntu 9.10.

The only real question for you is 32 or 64 bits.  32 bits has a few less quirks, but 64 bits is faster on "processor intensive" task.  Both are fine choices, but I chose the 64 bit version. 64 bits is not the default version people download, you have to "choose" it on the website.

The quirks on 64 bits are flash and java...  You have to know what's best to install.  If you choose 64 bits, that can be taken care of, just say so.

Lastly, you should consider waiting until the end of the month.  A new version of Ubuntu will be coming out (10.04, named lucid lynx).  The latest and greatest is surely the better install choice.  I'm using 10.04 since Alpha2 stage, and like it very much.  The final version should be top notch.  There's no point of installing only to upgrade 2 weeks from now unless you are in a terrible hurry.

Also, look into Linux Mint.  It is Ubuntu based, but has all the codecs you'll need right of the bat.  Ubuntu doesn't, and some restricted formats (like mp3, and dvd playback) need extra steps which are, not very complicated, but sometimes cumbersome.

Does that do it for your questions?

---


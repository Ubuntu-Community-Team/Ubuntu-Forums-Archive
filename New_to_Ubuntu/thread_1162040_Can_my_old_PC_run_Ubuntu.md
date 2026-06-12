---
title: "Can my old PC run Ubuntu ?"
date: 2009-05-17
forum: New to Ubuntu
---

### Post by hcchen on 2009-05-17
My 1999 old Notebook PC's CPU is Pentium-II 266M , 100M RAM. 
First partition C: drive has about 2G space. 2'nd partition D: drive has about 3G space. CD-ROM is *almost* broken.  <======= Note!
USB can not boot but works fine with my external USB HDD.

It still works fine with Windows 2000. Just slower.

Can it run Ubuntu and any other suitable Linux? Please advice. Thanks !!

---

### Post by mick222 on 2009-05-17
1oo mb ram is not enough for ubuntu but you could try damn small linux or puppy linux which should happily run on your system.

---

### Post by ugm6hr on 2009-05-17
> **mick222 said:**
> 1oo mb ram is not enough for ubuntu but you could try damn small linux or puppy linux which should happily run on your system.

Probably best to avoid Puppy too... I found it very slow on less than 128MB RAM.

Options:
1. DSL (DamnSmallLinux)
2. DeliLinux

If your CD-ROM is not working, you don't have many options (do you have a floppy drive?)

DSL is a LiveCD, so you can try it out to see if you like it.

---

### Post by guitar_man on 2009-05-17
recently I booted Damn small linux on an old box

Pentium II 400Mghz
64Mb ram
just boot it from the cd rom....

---

### Post by Game Over on 2009-05-17
I've been reading a lot about Damn Small lately, how does it stack up to, say, Ubuntu?

---

### Post by mister_p_1998 on 2009-05-17
If you can get enough ram into it... maybe, Im running Xubuntu Hardy on a P2 500 with 512 mb ram, you might get away with 256.
Steve

---

### Post by Nasaki on 2009-05-17
If you really wanted to, I am sure that you could shove xubuntu onto your machine. I bet that it would be at least as fast, if not faster, then you current windows 2000 install. Although, for speed's sake, I would stick with the recommendations of DSL.

---

### Post by lkraemer on 2009-05-17
DSL or TinyCore 1.4.2 is the best bet.  Both would work fine.
For Tinycore you will need a Wired LAN to download things
like a browser and other software so you can actually do some
meaningful work.

Try out the LiveCD's of both.

TinyCore is only 10Meg.

If you have a floppy, you can make a Boot floppy that will boot from
a USB CDR Drive.  I use that on my old Compaq Presario 1672 AMD K6-2 350MHZ
with 192 Meg RAM and 80 Gig Hard Drive.  I forget what the boot manager
is that I used.  Will have to look later to find out what it is.

lkraemer

---

### Post by kerry_s on 2009-05-17
> **hcchen said:**
> My 1999 old Notebook PC's CPU is Pentium-II 266M , 100M RAM. 
First partition C: drive has about 2G space. 2'nd partition D: drive has about 3G space. CD-ROM is *almost* broken.  <======= Note!
USB can not boot but works fine with my external USB HDD.

It still works fine with Windows 2000. Just slower.

Can it run Ubuntu and any other suitable Linux? Please advice. Thanks !!

nothing will be as fast as win2k on those specs.
dsl ( [http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/) )will be usable but limited, you could run far more things with win2k and it would be more up to date.
dsl runs old things built for the era of old hardware, for instance firefox is like 1.0.7, while on win2k you could run firefox 3 the latest.
i would recommend you just try and clean up win2k or if you can a fresh install.

---

### Post by khelben1979 on 2009-05-17
You can install Debian on that computer and run it without problems, but... don't expect fast performance if you are going to use KDE or Gnome. I have run Debian myself on systems with a lot less memory than 100 MB of RAM.

---

### Post by egalvan on 2009-05-17
From the TinyCore website:


[B]_What are the minimum requirements_?

An *absolute minimum* of RAM is *[COLOR="Red"]32mb[/COLOR]*.
 TC won't boot with anything less,
 no matter how many terabytes of swap you have.
The minimum cpu is i486DX (486 with a math processor).

A _recommended configuration_:
Pentium 2 or better, *128mb* of ram *+ some swap* [/B]

---

### Post by egalvan on 2009-05-17
> **kerry_s said:**
> 
i would recommend you just try and clean up win2k
 or if you can** a fresh install.**

Absolutely +1.

Nothing like a fresh start for Windows to work better...

But watch out for "lost drivers"...

Make SURE of adequate hardware driver support
BEFORE starting the re-installation.

Some manufactures/OEM are no longer hosting Win2K drivers...

Speaking from "Sad Experience" here :mad:

I used to use a package called LitePC.
I believe it is now called XP-Lite, but I may be wrong...
I haven't used it in  while...
It ccould strip down a Windows install to some amazingly small dimensions.

---

### Post by hcchen on 2009-05-18
I found Damn Small Linux - DSL is also Damn Amazing !
The first page pops up so fast that I tried to reboot again to make sure what I have seen.

I also realized that my old notebook's CD drive is fine. It just can't read modern 
Ubuntu 700M CDs LOL

I should have gone to sleep two hours ago but DSL keeps me at the desk with her
for another 30 min and another. I have to say thank you very much to all of you in prior.
Linux is so much fun!!

---

### Post by Wiebelhaus on 2009-05-18
Go With a Ubuntu command line installation and then build to specifically what you need from your operating system ,[ here's a how to]("https://help.ubuntu.com/community/Installation/LowMemorySystems")Don't be intimidated it's very easy! You may just need to experiment and start over a few times but it's allot of fun , if you into learing how things work at a fundamental level.

---

### Post by NHArticleTen on 2009-05-18
> **hcchen said:**
> I found Damn Small Linux - DSL is also Damn Amazing !
The first page pops up so fast that I tried to reboot again to make sure what I have seen.

I also realized that my old notebook's CD drive is fine. It just can't read modern 
Ubuntu 700M CDs LOL

I should have gone to sleep two hours ago but DSL keeps me at the desk with her
for another 30 min and another. I have to say thank you very much to all of you in prior.
Linux is so much fun!!

I'm using a 1997 Gateway 2000 Laptop with a 150mhz processor that I've stacked 224mb of ram into...and I'm using DSL with much pleasure!

enjoy!

---

### Post by hcchen on 2009-05-19
> **Wiebelhaus said:**
> Go With a Ubuntu command line installation and then build to specifically what you need from your operating system ,[ here's a how to]("https://help.ubuntu.com/community/Installation/LowMemorySystems")Don't be intimidated it's very easy! You may just need to experiment and start over a few times but it's allot of fun , if you into learing how things work at a fundamental level.
This is exactly what I was actually looking for. Thank you very much !! For guys you didn't try to click the link, it's an ubuntu official article titled "**How to install Ubuntu on low memory systems  (Pentium III and earlier machines, with 32-192 MB RAM).**"  well well .....

By the way, I appreciate the very nice comment that points out that Windows 2000 is the best OS for my old computer. It's very true. But without paying for an extra Anti-virus I bet it won't be healthy for over just 3 days after connected to the Internet.

---

### Post by kerry_s on 2009-05-19
> **hcchen said:**
> This is exactly what I was actually looking for. Thank you very much !! For guys you didn't try to click the link, it's an ubuntu official article titled "**How to install Ubuntu on low memory systems  (Pentium III and earlier machines, with 32-192 MB RAM).**"  well well .....

By the way, I appreciate the very nice comment that points out that Windows 2000 is the best OS for my old computer. It's very true. But without paying for an extra Anti-virus I bet it won't be healthy for over just 3 days after connected to the Internet.

i used avg on my 2k machine, it's free: [http://free.avg.com/](http://free.avg.com/)

---

### Post by ugm6hr on 2009-05-19
> **hcchen said:**
> This is exactly what I was actually looking for. Thank you very much !! For guys you didn't try to click the link, it's an ubuntu official article titled "**How to install Ubuntu on low memory systems  (Pentium III and earlier machines, with 32-192 MB RAM).**"  well well .....

Report back on how it works with 100MB RAM.  I have installed Ubuntu + LXDE on 128MB with good success, but have my doubts whether 2.6 kernel + X + window manager + Firefox will cope with 100MB.  I suspect there will be plenty of swappiness.

---

### Post by XubuRoxMySox on 2009-05-19
Another excellent alternative is the Ubuntu-based [Crunchbang Linux]("http://crunchbanglinux.org"). I added the ultra lightweight [LXDE]("http://lxde.org") desktop environment to give mine a "Windowsy" familiarity with icons to click on. My family didn't even know they were using Linux instead of Windows until I told them so! Crunchbang works great on older systems and shares all the awesome Ubuntu repositories and stuff.

-Robin

---

### Post by hcchen on 2009-05-31
also in my web page with pictures [http://sites.google.com/site/guitardingdong/install-ubuntu-904-from-hdd](http://sites.google.com/site/guitardingdong/install-ubuntu-904-from-hdd)

My old pc is a Thinkpad notebook with Pentium II CPU , 96M RAM. 10G hard disk. Ubuntu 904 is working fine on VirtualBOX with only 96M RAM on my another modern computer. So I am sure this old notebook PC should be able to run Ubuntu 904. Question is how to install with its very limited peripherials.

The CD-ROM drive is almost broken. I am lucky that it can still boot from DSL CD (Damn Small Linux 4.4) and GRUB CD. But it can't read Ubuntu 700M CD completety (nor any other 700M CD). Due to the old CD drive's poor condition, I can't install Ubuntu from CD-ROM directly. The old computer can't boot from USB drive. About its floppy drive, I don't have any diskette anyway. 

Seems liket that I have to Install Ubuntu 904 from hard disk directly. I have anoter modern compuer and USB hard disk box to do the copy.  Before trying on the old notebook PC, I pracice the 'install Ubunto from hard disk' on VirtualBox virtual machine first. Now I got blocked by an error that says ,

[FONT=courier new][!!] Detect and mount CD-ROM
Incorrect CD-ROM detected
The CD-ROM Drive contains a CD which cannot be used for installation.
Please insert a suitable CD to continue with the installation.
[Continue]
[/FONT]

My detail steps are :
1. Create a 4G hard disk space for the VirtualBox virtual machine.
2. Boot DSL CD , use "DSL 2 toram" boot option so I can change the CD to Ubuntu Alternate CD later. (most people use 'desktop CD' while alternate CD is for people like me. It requires less memory and provides more options)
3. run cfdisk to create 3 partitions. They are,
[FONT=courier new]    hda1. Linux partition 2048Mega reserved to be the target partition. [/FONT]
[FONT=courier new]    hda2.1000Mega ext2 partition to be the installation source. [/FONT]
[FONT=courier new]    hda3. other hundreds Mega spaces reserved for linux swap partition.[/FONT]
3. mkfs -t ext2 /dev/hda2  (If I remember correct)
4. Change CD-ROM to Ubuntu 904 Alternate CD.
4. mount -o loop /dev/cdrom /mnt/cdrom (If I remember correct)
5. mount  /dev/hda2 /mnt/hda2 (If I remember correct)
6. I use DSL built-in file manager 'emelfm' to copy everything includes hidden files from /mnt/cdrom/*.* to /mnt/hda2.
7. Change the CD-ROM to a GRUB CD.
8. Reboot the virtual machine and it boot up to GRUB.
9. use 'c' command to GRUB command line, give 3 command lines, they are
[FONT=courier new]     kernel (hd0,1)/install/vmlinuz[/FONT]
[FONT=courier new]     initrd (hd0,1)/install/initrd.gz[/FONT]
[FONT=courier new]     boot
[/FONT]10. I was so happy to see this works !! 
But the installation got blocked at the error message box mentioned above. 
I think that's normal because hda2 is of course not a CD-ROM. Although I have tried my best to keep the directory structure same as the Ubuntu 904 Alternate CD-ROM. This way works if it's a Windows 2000 , XP install CD besides.

Now please help !!

---

### Post by hcchen on 2009-06-06
I have finally successfully installed Ubuntu 804 on my old computer. It costed me two weeks to walk through all the barriers, shoooo, this is the final workable way ["Install Ubuntu on old pc from hard disk"]("http://ubuntuforums.org/showthread.php?p=7385698#post7385698") . 
You are right. Ubuntu is really very slow on this old pc. DSL's performance is ok but in Taiwan Chinese language is always needed. Over all, Windows 2000 is really the most suitable operation system. However, I enjoy having so much fun on this old compuer. Thank you all, have a good day ~~~~~

---


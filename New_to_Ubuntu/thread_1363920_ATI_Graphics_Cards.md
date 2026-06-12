---
title: "ATI Graphics Cards"
date: 2009-12-25
forum: New to Ubuntu
---

### Post by aley on 2009-12-25
I had A question regarding ati graphics cards, I have a dell laptop with a 512MB ATI Mobility RADEON HD 4570 graphics card, Now do I download the Linux driver for the 4000 series from the amd website or is there a better alternative?

One other question I have is I already have windows 7 installed on the laptop which I want to keep as programs I run have known issues on Ubuntu. is it possible to keep this install of windows and partitition a seperate intsall of Ubuntu without having to reinstall Windows.

Any help would be much apreiciated.

Thanks

Alex

---

### Post by coffeecat on 2009-12-25
> **aley said:**
> I had A question regarding ati graphics cards, I have a dell laptop with a 512MB ATI Mobility RADEON HD 4570 graphics card, Now do I download the Linux driver for the 4000 series from the amd website or is there a better alternative?

ATI is a bit of a lottery depending on the actual card. It will probably work OK out of the box with the open-source radeon driver, but you probably won't get 3d acceleration. Once you've done a hard-drive install, you can install the proprietary fglrx driver from System > Administration > Hardware Drivers. On my Acer laptop with the ATI Mobility Radeon HD 4200 card, performance with the proprietary driver was actually worse than with the open-source driver. And even with the open-source driver I had to create a custom xorg.conf file to make my desktop usable. But you may be luckier.

> **aley said:**
> One other question I have is I already have windows 7 installed on the laptop which I want to keep as programs I run have known issues on Ubuntu. is it possible to keep this install of windows and partitition a seperate intsall of Ubuntu without having to reinstall Windows.

It is entirely possible to keep Windows and install Ubuntu on its own partitions by shrinking the Windows C:\ partition. But it would be a good idea to know the current partition layout first. Windows 7 usually comes on 2 partitions. There will also be some sort of Dell utility partition, and if Dell has included some other sort of partition, and if all those partitions are primary ones, you'll be stuck because there is a limit of 4 primary partitions per hard drive.

Have you tried running Ubuntu live from the CD yet? You can do that without making any changes to the HD and you'll get a chance to see how the ATI graphics work out of the box. If you haven't, download the 9.10 ISO and burn it to CD and boot up with it. Once in the desktop, go to Applications > Accessories > Terminal and post the output of this command:

```
sudo parted -l
```That's a lower-case L at the end. If you can get an internet connection from the live CD, you'd be best copying and pasting that output.

Last thought: have you heard about Wubi? Installing Ubuntu to its own partitions as a dual-boot is better, but Wubi is a good way of trying out Ubuntu. Have a look here:

[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

---

### Post by 3rdalbum on 2009-12-25
> **aley said:**
> I had A question regarding ati graphics cards, I have a dell laptop with a 512MB ATI Mobility RADEON HD 4570 graphics card, Now do I download the Linux driver for the 4000 series from the amd website or is there a better alternative?

There's a better way. Go to System > Administration > Hardware Drivers. You'll be offered a download of an ATI driver that's been well-tested with Ubuntu and is guaranteed to stay in sync with your kernel and Xorg.

If it doesn't appear in the Hardware Drivers program, you might need to reload your package list.

> One other question I have is I already have windows 7 installed on the laptop which I want to keep as programs I run have known issues on Ubuntu. is it possible to keep this install of windows and partitition a seperate intsall of Ubuntu without having to reinstall Windows.

Oh yes. Back up your Windows just in case. Boot the Ubuntu CD and run the installer, and use the "resize" option on the partitioning screen. Drag the handle in the bottom bar graph to the left to allocate some space for Ubuntu.

---

### Post by waspbr on 2009-12-25
never mind

---

### Post by sandyd on 2009-12-25
> **aley said:**
> 1. I had A question regarding ati graphics cards, I have a dell laptop with a 512MB ATI Mobility RADEON HD 4570 graphics card, Now do I download the Linux driver for the 4000 series from the amd website or is there a better alternative?

2. One other question I have is I already have windows 7 installed on the laptop which I want to keep as programs I run have known issues on Ubuntu. is it possible to keep this install of windows and partitition a seperate intsall of Ubuntu without having to reinstall Windows.

Any help would be much apreiciated.

Thanks

Alex
1. Download the driver from the site (or envyng). both comfirmed to be working.
the driver that ubuntu provides in "hardware drivers" is a bit of a memory hog for some people and its still being sorted out.

2.
Go to your windows control panel. administrative tools -> Computer Management -> Disk Management 

shrink your windows partition so that you have free space

when you get to the partitioning part of ubuntu, choose (use largest contineous block of free space)


good luck, and have a great christmas

---

### Post by sandyd on 2009-12-25
> **3rdalbum said:**
> <snip>

Oh yes. Back up your Windows just in case. Boot the Ubuntu CD and run the installer, and use the "resize" option on the partitioning screen. Drag the handle in the bottom bar graph to the left to allocate some space for Ubuntu.
NO.
if you do that, windows will complain on the next reboot and you will have to "repair" windows. which requirs the restore disks if the process seems to go on forever.
resize it using windows disk manager.

---

### Post by coffeecat on 2009-12-25
> **carlee said:**
> NO.

Good advice!

@OP, more details here:

[http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/](http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/)

Although that's about Vista, the same is true for Windows 7. I like the way they blithely say, "... don’t worry, we’ll fix it... Insert your Windows Vista installation dvd...". Most Vista/W7 users don't have a Microsoft installation DVD. The OEM restore utilities that come with most machines with pre-installed Windows are not up to this particular job.

@carlee, I've read about the forums that if you untick the 'round to cylinders' box in the Gparted resize utility, you won't render Windows unbootable. Personally, I wouldn't risk it, but I wondered if you'd come across anything.

---

### Post by sandyd on 2009-12-25
> **coffeecat said:**
> Good advice!

@OP, more details here:

[http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/](http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/)

Although that's about Vista, the same is true for Windows 7. I like the way they blithely say, "... don&#8217;t worry, we&#8217;ll fix it... Insert your Windows Vista installation dvd...". Most Vista/W7 users don't have a Microsoft installation DVD. The OEM restore utilities that come with most machines with pre-installed Windows are not up to this particular job.

@carlee, I've read about the forums that if you untick the 'round to cylinders' box in the Gparted resize utility, you won't render Windows unbootable. Personally, I wouldn't risk it, but I wondered if you'd come across anything.
ive actually tried that before.
no luck though.

p.s. just a refrence for those who made this mistake and never made a restore disk.
you will need......(drum roll please)...: [http://www.google.ca/url?sa=t&source=web&ct=res&cd=2&ved=0CBAQFjAB&url=http%3A%2F%2Fneosmart.net%2Fblog%2F2008%2Fwindows-vista-recovery-disc-download%2F&rct=j&q=windows+vista+recovery+disk&ei=su80S5u3D4qDngfw8cXvCA&usg=AFQjCNH0BZw45r8QvupoJkt-r-E5c8yOmg]("http://www.google.ca/url?sa=t&source=web&ct=res&cd=2&ved=0CBAQFjAB&url=http%3A%2F%2Fneosmart.net%2Fblog%2F2008%2Fwindows-vista-recovery-disc-download%2F&rct=j&q=windows+vista+recovery+disk&ei=su80S5u3D4qDngfw8cXvCA&usg=AFQjCNH0BZw45r8QvupoJkt-r-E5c8yOmg")

and i havent come accross anything, because i only used the safe way (found out about it the hard way after i fried vista and it just sat there "repairing" its partitions)

---

### Post by coffeecat on 2009-12-25
> **carlee said:**
> ive actually tried that before.
no luck though.

Thanks for that. I'm glad to have that confirmed by someone who's tried. I shall continue to advise people not to resize their Vista/W7 C:\ partitions with Gparted. :)

.... **Edit:** and point them in this direction:

[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)

---

### Post by Dvdre on 2009-12-25
> **aley said:**
> I had A question regarding ati graphics cards, I have a dell laptop with a 512MB ATI Mobility RADEON HD 4570 graphics card,

I have the same ATI card in a Sony Vaio laptop. You can easily add the ATI driver if you install Ubuntu 9.04, but you may face big problems if you try to install it on Ubuntu 9.10. I tried twice to put 9.10 on this laptop and both times the result was the Black Screen of Death on booting up, after the ATI driver was installed. 

On 9.04 64-bit, the driver works fine. But not on 9.10. After two tries I gave up and rolled back to 9.04, which works very well on this laptop.

---

### Post by aley on 2009-12-26
Thank you very much for everybody help sorry it took so long to reply xmas day was busy for me :) all the posts were very helpful.

Has there been anyone else out there that has had the same problem as Dvdre as I would really like to use the latest version of Ubuntu if possible.

Thanks

Alex.

---

### Post by aley on 2009-12-26
Also I had on other question Carlee posted this:

1. Download the driver from the site (or envyng). both comfirmed to be working.
the driver that ubuntu provides in "hardware drivers" is a bit of a memory hog for some people and its still being sorted out

but where exactly is this link?

Sorry if this is a blindingly obvious answer :) but I just don't know

Alex

---

### Post by 3rdalbum on 2009-12-26
> **aley said:**
> Also I had on other question Carlee posted this:

1. Download the driver from the site (or envyng). both comfirmed to be working.
the driver that ubuntu provides in "hardware drivers" is a bit of a memory hog for some people and its still being sorted out

but where exactly is this link?

Sorry if this is a blindingly obvious answer :) but I just don't know

Alex

[www.ati.com](www.ati.com) is "the site". EnvyNG is a program in the Ubuntu repositories that can install drivers for you too.

Incidentally, I've resized a Vista partition in the Ubuntu installer with no ill effects.

---

### Post by nishant.singh28 on 2009-12-26
Uhhhh......all the b***s*** about the ati drivers!!! :D Just go to hardware drivers. It will install the latest driver without ANY error. Did that 2 times each on my and a friend's laptops. No problems whatsoever.

---


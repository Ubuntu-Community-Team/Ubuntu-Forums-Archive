---
title: "How to install ubuntu onto external hard drive"
date: 2010-07-22
forum: New to Ubuntu
---

### Post by CJ-1990 on 2010-07-22
I have tried to install Ubuntu 10.04 onto my external hard drive but it won't work, cn anyone give me specific instructions on how to install it?
Btw here are my computer specifications:
 
Microsoft windows XP
Home edition
Version 2002
Service pack 2
Intel(R) Pentium(R) 4 CPU 2.40GHz
1.79GHz, 1.00GB RAM
160GB Hard drive
NVIDIA GeForce MX 440(Microsoft corporation)
 
I am trying to install Ubuntu on a 160gb external hard drive on which I intend to keep 30gb of space free for usage on windows based systems and the rest for Ubuntu
 
Please note that apart from the live cd I don't have anything else to install Ubuntu, if I will need anything else please let me know ^-^

---

### Post by jmszr on 2010-07-22
CJ-1990,

This may be of help: [http://www.ubuntugeek.com/a-much-easier-way-to-install-ubuntu-on-a-usb-device-stick-or-hd.html](http://www.ubuntugeek.com/a-much-easier-way-to-install-ubuntu-on-a-usb-device-stick-or-hd.html) .

You would need to alter the instructions slightly to account for the 30GB NTFS partition.

---

### Post by CJ-1990 on 2010-07-22
Heya Jmszr, thanks for the help, hopefully this will work, I'll try it tonight ^-^

---

### Post by beew on 2010-07-22
You just do it in the same way that you would for an internal hard drive. 

Boot from a live usb (or a live CD) and insert the external drive. Then click install Ubuntu 10.04 on the desktop and go through the usual installation steps, but at step 4(?) click install manually and 
choose your external drive to install Ubuntu to.

Be sure about the name of the external drive so you don't wipe out your internal drive. In the final step choose "advanced" and install the boot loader in your external drive and click install and wait. That's it. 

You don't need to edit anything like they say in the Ubuntu Geek link. I tried that on a 40G hard drive which I removed from an old laptop and use as an external drive as well as a 8 G pendrive. Both work flawlessly.:p

P.S. According to this link you don't need to set aside 30G for ntfs (or FAT32). It says there is a utility for Windows to read ext3 format. I haven't tried that out though.
[URL="http://www.psychocats.net/ubuntu/partitioning"]
http://www.psychocats.net/ubuntu/partitioning[/URL]

I assume that you want the 30 ntfs just so that Windows can assess files in it, since I don't think it is possible to install and run Windows on an external drive.

---

### Post by viking350 on 2010-07-22
now if 10.4 does not work and everything else fails try using 9.10 and if that does not work it probably will not work at all

---

### Post by beew on 2010-07-22
10.04 will work, I am posting this from Ubuntu10.04 installed in a 8 G usb pendrive right now. Plus I do all the kernel and system updates without a problem.  

9.10 I am not sure, seems that there is a lot of work involved from what I read on the net even if it works.

---

### Post by CJ-1990 on 2010-07-22
Thankyou to all who replied to this thread ^-^ Beew, you said to click advanced and install the boot loader onto the external drive, where do I get this boot loader? I don't really know anything about Ubuntu yet lol

---

### Post by beew on 2010-07-22
> **CJ-1990 said:**
> Thankyou to all who replied to this thread ^-^ Beew, you said to click advanced and install the boot loader onto the external drive, where do I get this boot loader? I don't really know anything about Ubuntu yet lol

Hi, see the screenshot for the final step here. The boot loader is in the live CD.

[URL="http://news.softpedia.com/news/Installing-Ubuntu-8-10-97417.shtml"]
http://news.softpedia.com/news/Installing-Ubuntu-8-10-97417.shtml[/URL]

This is for Ubuntu 8.04 but it is the same for 10.04.

However, instead of installing the boot loader into dev/sda1 you should install it in the external hard drive which you can choose from the drop down menu.

Also, for "hard disk partition" choose "manual" and follow the instructions in the Ubuntu Geek link Jmzsr posted earlier. What you see will be somewhat different from the screen shot here because this is for the automatic option:p

Instead you will see a list of drives. Very important! Make sure you know the name of your external drive so you won't wipe out your internal one. Once you identify your external drive you can click "free space" and add new partitions as described in the Ubuntu Geek link.

Some people recommend that you should remove your internal hard disk first in order that you won't get confused and erase it, but I don't think it is necessary and I didn't.

If you are in doubt at any step, just hit "back" to redo it. All steps are reversible until you hit the final "install" button, after that there will be no going back.

Cheers.

Oh, you have to unmount your external drive before you can partition it and install Ubuntu into it. Just right click the disk's desktop icon (which will show up when you plug in the external drive) and choose unmount.

---

### Post by oldfred on 2010-07-22
Grub2 is the boot loader that Ubuntu uses. The advanced button just lets you choose which drive to install the boot loader to. Since it is an external you want to set in BIOS to boot the external first, then the internal. That way grub will boot and give you a menu for both operating system. IF the external is not plugged in then your current windows boot loader in the internal drive will still boot windows.

Shows advanced button:
[http://members.iinet.net/~herman546/p28/032_install-now.png](http://members.iinet.net/~herman546/p28/032_install-now.png)

While for two drives the second can be an external:
Dual boot 2 drives
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

---

### Post by CJ-1990 on 2010-07-23
Heya peeps, installed Ubuntu onto my external hard drive last night and followed the directions you guys gave me but.... when I go into the terminal I get stuck:
 
I typed sudo -i
 
Then media/disk/boot/grub 
 
The terminal then says it's a directory but I don't know where to go from there
 
I was so close on gettin it workin that I could taste the sweet nectar that is Ubuntu haha ^-^
 
Any help on this would be great

---

### Post by oldfred on 2010-07-23
If you got to a terminal you have booted. You may have video issues.

Try recovery mode from the menu. And/or try at the menu to edit the line. Use e to edit and where it says quiet splash replace with nomodeset.

---

### Post by CJ-1990 on 2010-07-23
Oh that's the thing dood, I booted from the live cd, then accessed the external hard drive through the terminal, but when I type what's needed and then type vi for the menu, nothing comes up, no information like what's on the instructions 8(
 
I can follow the instruction up to the terminal bit, but don't know exactly what to type from there aye

---

### Post by oldfred on 2010-07-23
I thought your boot stopped at the terminal from your hard drive.

Post this so we can see where everything is at:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

### Post by CJ-1990 on 2010-07-26
Hey guys, I haven't done the diagnostics thing just yet, I'm thinking it may be me who is at fault here, I don't quite know how to use the ubuntu terminal just yet, only been usin the live cd to see what ubuntu looks like, apart from that not much to do on it, can anybody tell me exactly what to type after installing ubuntu onto my external hard drive from stage 4 of this link? -> [http://www.ubuntugeek.com/a-much-eas...ick-or-hd.html](http://www.ubuntugeek.com/a-much-eas...ick-or-hd.html) 
 
I can get up to stage 4 but I don't really know what to type from there, when I type sudo -i it does let me have root priviledges, then I type media/disk/boot/grub with disk bein the name of my hard drive ubuntu is installed on, but after that when I type vi for the vim menu it does nothing but bring up a menu, no information or anything, and when I type anything on the menu, nothing happens, no lines with information, if anything I think it might be the terminal at fault, or my novice terminal skills lol.

---

### Post by -kg- on 2010-07-26
We're making things way more complicated than they need to be here.

First, the link:

[http://www.ubuntugeek.com/a-much-easier-way-to-install-ubuntu-on-a-usb-device-stick-or-hd.html]("http://www.ubuntugeek.com/a-much-easier-way-to-install-ubuntu-on-a-usb-device-stick-or-hd.html")

...points to an installation guide for Hardy 8.04.  Hardy uses Legacy GRUB and Lucid uses GRUB2 by default.  That is why you can't find the "menu.lst" file they say to edit in the guide.

Have you tried to boot to the installation?  You will need to select booting from the USB device either through the BIOS boot menu (at the bottom of the initial boot-up screen it will say, "Press <certain key, like F2> to enter BIOS" and "Press <certain key, like F12> to enter Boot Menu") or you will need to set the boot sequence in BIOS so that it looks for your external (USB) hard drive before it looks for the hard drive (just like CD or Floppy).

If you installed the boot loader in the MBR of your external drive, the GRUB boot loader menu should come up as as it should, and you should be able to boot to the external device.

---

### Post by oldfred on 2010-07-26
Your link does not work, but I think I know which it was. 

The instructions are for grub legacy and you do not have grub legacy. You should just be able to boot if you have the external set to boot first in BIOS.

---

### Post by CJ-1990 on 2010-07-26
I've reformatted the drive first before installing as told, then installed it, as told before 
 
I set in the advanced options that the boot loader should be set to dev0 to install in there which is the external drive, when I try to boot the drive it doesn't, 
 
I then followed the direction on the link that didn't work (It is also up higher in this post), the link worked for me, I got to the second part of the isntructions and followed till step 4, on which I got stuck since the menu came up but I couldn't find any information that the link explained, as far as the mbr of the drive is concerned I have no idea how to install the grub loader to it, the disk has grub 2 on it as default for ubuntu 10.04, I can follow directions that any give me although you'd probs have to dumb it down a bit, I don't quite know how to work the terminal properly.
 
Also, if this helps the drive is formatted to ext4 when installing, if this is the wrong format than please tell me, I hope that I can become ubuntu soon lol ^-^

---

### Post by oldfred on 2010-07-26
The instructions are for grub not grub2, so they will not work.

So we can see the details:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

this has newer instructions:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive)

---

### Post by beew on 2010-07-26
> **CJ-1990 said:**
> Heya peeps, installed Ubuntu onto my external hard drive last night and followed the directions you guys gave me but.... when I go into the terminal I get stuck:
 
I typed sudo -i
 
Then media/disk/boot/grub 
 
The terminal then says it's a directory but I don't know where to go from there
 
I was so close on gettin it workin that I could taste the sweet nectar that is Ubuntu haha ^-^
 
Any help on this would be great

Sorry, I am not understanding. What are you doing sudo -i for?

May I ask which version of Ubuntu are you trying to install?

Like I said, I have installed Ubuntu 10.04 in two external devices (one 40 external hard disk which I removed from a dead laptop and an 8 G Kingston USB thumb drive) and in no time did I have to go to the terminal. 

I just booted  from a live USB (I assume it is ok if you use a live CD), attach the external device and install just as you would with an internal drive and in the last step put the bootloader in the external device with the advanced option and that was it (all the while being careful about the external device's name). When I plug either of them into a desktop or a laptop configured to boot from usb and switch on the computer I automatically get into the boot screen everything works without a hitch. I read the Ubuntu Geek link, but as I said you don't need to edit anything like they instructed you there, the thing just works after installation. I have been using these devices for a few weeks now, getting all the system as well as application updates and going on the internet, watching movie and playing music (well the 8G one is slow as you would expect).

---

### Post by beew on 2010-07-26
Ok, my drives are formatted to ext3 instead of ext4. That might make a difference though I doubt it. The reason I chose ext3 is simply to avoid possible compatibility issues that might arise somewhere down the road as I figured ext4 was rather new. I could be wrong on that.

---

### Post by CJ-1990 on 2010-07-26
Thanks beew, I know this should work and I did try it, but unfortunately it doesn't work for me, it won't boot, when the computer restarts it goes to that black screen with the boot menu and bios options, I type for the boot menu but it just freezes on the same screen, doesn't boot when the external drive is plugged in, dunno what to do about it aye

---

### Post by beew on 2010-07-26
Are you sure you bios can boot from usb? There are some bios which have the option but somehow it doesn't work.

---

### Post by CJ-1990 on 2010-07-26
Well dunno what version of bios I have, but it was first installed with XP home edition 2002, haven't changed the bios since, maybe that's the problem?

---

### Post by beew on 2010-07-26
I have this SamSung laptop (new!) which just doesn't like to boot from USB. Even though I have configured the bios to boot from USB it just ignores it. I have to always press ESC when it starts up to get to the one time boot menu and reset the boot sequence, but even that doesn't work. Right after Grub2 has started immediately it will abort and the PC will start booting from the hard drive again, so I have to hit ESC again and bring up the boot menu once more to reset it. I have to do this twice in a row every time I try to get it to boot from the usb! I don't have this problem with other computers I plugged my usb into.

---

### Post by beew on 2010-07-26
> **CJ-1990 said:**
> Well dunno what version of bios I have, but it was first installed with XP home edition 2002, haven't changed the bios since, maybe that's the problem?

Is that a really old PC?

---

### Post by CJ-1990 on 2010-07-26
8 years ago so probably yeah aye ^-^

---

### Post by beew on 2010-07-26
Then it probably just doesn't boot from USB.

---

### Post by CJ-1990 on 2010-07-26
How do I get another bios, do I just have to buy another computer?

---

### Post by -kg- on 2010-07-27
Yep, support for booting from USB only came in around 2002-2003 or so.  I'm having the same problem here with a pre-2002 laptop, compounded by the fact that the optical drive is broken and I can't find a replacement.

Something you might want to check out is the [PLoP Bootmanager]("http://www.plop.at/en/bootmanager.html").  You can write this boot manager to HD, CD, or Floppy disk and boot a USB device using that.

---

### Post by CJ-1990 on 2010-07-27
I'm going to reinstall ubuntu on my external drive tonight and see how that goes, but I have heard a few bad things about windows not allowing anything else to boot, as far as I know I have installed grub to the mbr of the external drive, so that shouldn't be a problem, windows seems to be not letting me boot from the external drive, would a dual boot rectify this?, i know that the internal drive has an mbr inside it that the computer normally reads from, then I install another mbr to the external, maybe my computer is getting confused about which one to read from, would a dual boot make this any easier?

---

### Post by beew on 2010-07-28
> i know that the  internal drive has an mbr inside it that the computer normally reads  from, then I install another mbr to the external, maybe my computer is  getting confused about which one to read from, would a dual boot make  this any easier It shouldn't matter as long as the computer you plug your external drive into supports booting from external devices. It is like you can boot from a live CD even if you have windows installed in the hard drive. I mostly plug my portable Ubuntu installation in PCs running windows and it works beautifully.

BTW, I think you should probably upgrade your system, i.e. buy a new computer unless you are really hard up on cash or you are interested in the archeology of technology :p  Otherwise it just isn't worth it to go through the troubles IMHO. Getting a floppy? What is a floppy? I think it is a thing you put your coffee cup on. ;)

Incidentally, even if you cannot boot from the usb you may still be able to install Ubuntu into it. You just have to plug it in someone else's computer to use it. On the other hand, I have the feeling that the Ubuntu live CD will grind to a halt running in a 2002 machine. I tried to install Ubuntu in my roommate's 7 year old laptop. The installation was successful but it was painful to run it.  Finally I have to wipe it and install Lubuntu and it runs in a good speed. Maybe you should consider Lubuntu instead of Ubuntu.

---

### Post by CJ-1990 on 2010-07-28
Defs gonna get a new computer, defs it's turn for an upgrade, then I can scrap the old one and beat the **** out of it for bein so ****ing slow ^-^ probs gonna get another internal drive and put ubuntu onto it, so I can switch from windows to ubuntu at will, and keep the external purely for space ^-^ Thanks for the help everyone, I'll mark this post as solved

---

### Post by MrMarc on 2010-07-31
Curiously, are there any issues in actually using this as a portable OS? 

I wish to have an Ubuntu install on my external hard drive as a kind of backup solution whenever things go wrong but I'd intend to use it across multiple machines. This includes my own netbook, desktop and HTPC, as well as anyone else's machines that may need repairing or accessed in someway if anything goes wrong.

Are there any issues with booting from different machines to those the portable OS was originally installed on? Does GRUB take only those original hard drives into account or can it adapt to new environments?

Kind Regards!

\\:D/

---

### Post by 10.04newbie on 2010-07-31
> **MrMarc said:**
> Curiously, are there any issues in actually using this as a portable OS? 

I wish to have an Ubuntu install on my external hard drive as a kind of backup solution whenever things go wrong but I'd intend to use it across multiple machines. This includes my own netbook, desktop and HTPC, as well as anyone else's machines that may need repairing or accessed in someway if anything goes wrong.

Are there any issues with booting from different machines to those the portable OS was originally installed on? Does GRUB take only those original hard drives into account or can it adapt to new environments?

Kind Regards!

\\:D/

Well, for what it's worth, I can tellyou that I have installed Ubuntu 10.04 remix to an Acer laptop, then subsequently took-out the hard disk and transferred it to a HP netbook. It successfully ran on the HP and all I needed to do was update the wireless network driver by clicking the 'Hardware Drivers' icon, in System. The relevant driver was found quickly enough - I installed and activated it and, Bingo !

---

### Post by BlackRay on 2010-08-29
> Then media/disk/boot/grub

I believe they meant to change directories, ie type: cd media/disk/boot/grub

Hope this helps, plz post if it does cuz I considering it.

---

### Post by sarc on 2010-09-12
Hello:

I have a brand new HP ProBook 6555b with Vista, I use it for work and I must be 100% sure I do not do ANYTHING at all to my notebook internal hard disk - no changes to MBR, Vista loader etc.

Could someone confirm that this method will allow me to boot Ubuntu 10.4 without making ANY changes to my hd0 (notebook internal hard disk) AS LONG AS I CLICK ADVANCED AND TELL THE INSTALLER TO INSTALL GRUB IN THE USB HARD DISK?

p.s. I have experience with installing Ubuntu and manual partition setting.

Thanks!!!

> **beew said:**
> You just do it in the same way that you would for an internal hard drive. 

Boot from a live usb (or a live CD) and insert the external drive. Then click install Ubuntu 10.04 on the desktop and go through the usual installation steps, but at step 4(?) click install manually and 
choose your external drive to install Ubuntu to.

Be sure about the name of the external drive so you don't wipe out your internal drive. In the final step choose "advanced" and install the boot loader in your external drive and click install and wait. That's it. 

You don't need to edit anything like they say in the Ubuntu Geek link. I tried that on a 40G hard drive which I removed from an old laptop and use as an external drive as well as a 8 G pendrive. Both work flawlessly.:p

P.S. According to this link you don't need to set aside 30G for ntfs (or FAT32). It says there is a utility for Windows to read ext3 format. I haven't tried that out though.
[URL="http://www.psychocats.net/ubuntu/partitioning"]
http://www.psychocats.net/ubuntu/partitioning[/URL]

I assume that you want the 30 ntfs just so that Windows can assess files in it, since I don't think it is possible to install and run Windows on an external drive.

---


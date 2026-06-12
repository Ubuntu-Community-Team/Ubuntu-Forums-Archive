---
title: "Installing apps to Ubuntu?"
date: 2009-12-05
forum: New to Ubuntu
---

### Post by jquest68 on 2009-12-05
I've managed to get ubuntu installed and working, but I realized that I didn't do the partition right so I lost my windows 7, thats all right. I was wondering about installing apps to ubuntu. Can I install Photoshop cs3, itunes?

---

### Post by endBc on 2009-12-05
You can't install Windows applications on Linux. Probably the easiest workaround will be Wine ( some kind of an emulator ) but even then, not everything will work.


[LIST]
[*][http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)
[*][https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)
[/LIST]

---

### Post by ed-koala on 2009-12-05
You have several choices, depending on the amount of trouble you want to go through.

1. Reinstall Windows and duel boot
2. Install Wine (some programs may not work)
3. Use native Linux apps instead (has a learning curve)

---

### Post by Defiant Rat on 2009-12-05
If i were you, and i had already paid for windows 7, i would want it back especially if you have paid for Photoshop as well, so dual booting is probably the best option there.

[https://help.ubuntu.com/community/WindowsDualBoot#Installing%20Windows%20After%20Ubuntu](https://help.ubuntu.com/community/WindowsDualBoot#Installing%20Windows%20After%20Ubuntu)

If you arnt bothered about getting windows back you have the option of trying to run the programs in wine (im not sure how well Photoshop and Itunes work in Wine) or using native apps such as Gimp instead of Photoshop and Rhythmbox instead of Itunes. Both should be installed by default.

To add and remove tracks from an ipod with Rhythmbox , this works for me:
[http://www.simplehelp.net/2007/07/03/how-to-manage-your-ipod-using-rhythmbox-in-ubuntu/](http://www.simplehelp.net/2007/07/03/how-to-manage-your-ipod-using-rhythmbox-in-ubuntu/)

I had to enable disk use on the ipod first (which needed Itunes).

Good luck :)

---

### Post by niteshifter on 2009-12-05
> **ed-koala said:**
> You have several choices, depending on the amount of trouble you want to go through.

1. Reinstall Windows and duel boot
2. Install Wine (some programs may not work)
3. Use native Linux apps instead (has a learning curve)

4. Install a virtualization package like VirtualBox, then run Windows as a virtual machine. 

Caveats: 
You need ample RAM. For example a 512MB RAM system can - in theory - support a Win XP install: 256MB for the Linux OS, 256MB for XP. You won't like the performance of either. A 1GB RAM system will do better (even split of RAM). 2GB or more does well.

Not a good choice if you've some specialty internal (PCI card) hardware that you need to use. The hardware won't be visible to the Win virtual machine. USB connected equipment works  - you need the Closed Source Edition aka the PUEL version from Sun, not the Open Source Edition from Ubuntu's repositories.

Not a good choice if 3D (DirectX 10 or higher required) gaming is your thing. Support for such in VBox is minimal.


Benefits:
Software - like Office, for example - works just like it does on a "real" Windows install. From the software's vantage it is running on Windows.

---

### Post by jquest68 on 2009-12-05
all of these ideas I would love to try, but when I bought this laptop it had Vista, and then a friend of mine who's a IT installed Windows 7 but I don't want to bother him because he's always busy. Would my laptop still have Vista in it? or is it lost after I installed Ubuntu?

I'm into creating themes for the iphone and ipod touch and had so many PSD files that got erased but have most of them on my external hard drive. I would love to use it again but I guess I'll try Gimp. but what do I do far as music? if I link my ipod touch my laptop won't read it? I wished I did the partitioning correctly, I thought I did, but I didn't.

any suggestions?

---

### Post by Temposs on 2009-12-05
The iPod Touch is known to not work well with Linux. Basically every other iPod works quite well with Ubuntu, but I don't think you'll get the iPod Touch working well unless you jailbreak it.

---

### Post by Anuovis on 2009-12-05
I have a very general advice: do not rush into Ubuntu. Read some basic things about the system, dual boot for a while and see if it does what you want, if the hardware works. There are many good applications and you might find nice alternatives, maybe even better than in Windows. But you may not.

For example, Gimp is a nice thing but maybe you need some obscure feature of Photoshop that it doesn't have. Photoshop is bigger and heavier but not every user needs such a beast for picture editing. Our needs are very different, you don't know until you try.

Ubuntu also has a learning curve, things are different here and it takes time to get used to that. In my opinion, it is worth it, but you might feel safer if you can boot Windows when need arises. Don't just jump into Ubuntu and expect that it will do everything that you need, it just doesn't work that way. Be patient.

[B]_[Here is a good reading on this forum]("http://ubuntuforums.org/showthread.php?t=63315")_
[Here is another]("http://linux.oneandoneis2.org/LNW.htm")

_[Here is a book about Ubuntu]("http://www.ubuntupocketguide.com/index_main.html")_
_[and some tutorials to start with here]("http://www.psychocats.net/ubuntu/")_
[/B]

---

### Post by The_Pirate_King on 2009-12-05
Most Windows programs can be installed via a program called [WINE]("http://www.winehq.org/").  Many other programs are available through Synaptic Package Manager, in Settings > Administration. 

You can install iTunes using a program called "[PlayOnLinux]("http://playonlinux.com/en/")", but I recommend using a different program as there are a lot of problems with iTunes. 

I have heard that it is very difficult to install Photoshop through WINE, but I have never tried it myself.  As an alternative, I recommend [GIMP]("http://www.gimp.org/"), a free open source program with many of the same features as photoshop.  It's got about all you would need for basic image editing, but it lacks some of the more advanced features provided by photoshop. 



If I might ask, do you know exactly why Windows isn't working? 
It could just be that you have to configure your GRUB bootloader program so that windows will work, which is a fairly easy process described in great detail [here]("https://help.ubuntu.com/community/Grub2").

---

### Post by cael_shadowhunter on 2009-12-05
I connect a second gen ipod nano to my ubuntu partition with a program called amarok ([http://amarok.kde.org/]("http://amarok.kde.org/"))

The touch is likely to be a little more difficult to get working but you might want 2 check out the site.

---

### Post by jquest68 on 2009-12-05
> **The_Pirate_King said:**
> Most Windows programs can be installed via a program called [WINE]("http://www.winehq.org/").  Many other programs are available through Synaptic Package Manager, in Settings > Administration. 

You can install iTunes using a program called "[PlayOnLinux]("http://playonlinux.com/en/")", but I recommend using a different program as there are a lot of problems with iTunes. 

I have heard that it is very difficult to install Photoshop through WINE, but I have never tried it myself.  As an alternative, I recommend [GIMP]("http://www.gimp.org/"), a free open source program with many of the same features as photoshop.  It's got about all you would need for basic image editing, but it lacks some of the more advanced features provided by photoshop. 



If I might ask, do you know exactly why Windows isn't working? 
It could just be that you have to configure your GRUB bootloader program so that windows will work, which is a fairly easy process described in great detail [here]("https://help.ubuntu.com/community/Grub2").

thanks for your advice. Windows isn't working because I loaded Ubuntu and I thought I set the partitions right but I don't have that choice of OS when the laptop is booting up. So, I just let it boot on Ubuntu. I think everything is gone. I have a question can I reboot my system to an actual date like restoring my computer to a certain date, will it go back to windows?

---

### Post by Defiant Rat on 2009-12-06
> **jquest68 said:**
>  Windows isn't working because I loaded Ubuntu and I thought I set the partitions right but I don't have that choice of OS when the laptop is booting up. So, I just let it boot on Ubuntu. I think everything is gone. I have a question can I reboot my system to an actual date like restoring my computer to a certain date, will it go back to windows?

Have you looked to see if the windows partition is still there? It could be that you did set up the partitioning correctly, but grub isnt showing Windows 7, in which case you just need to set up grub to show windows 7, and you can use both:
> **The_Pirate_King said:**
> 
It could just be that you have to configure your GRUB bootloader program so that windows will work, which is a fairly easy process described in great detail [here]("https://help.ubuntu.com/community/Grub2").

Or try [SIZE=2]**[this.]("http://http://erickoo.wordpress.com/2009/06/14/how-to-add-vista-partition-to-grub-2-ubuntu-9-10-karmic-koala/")**[/SIZE]

---

### Post by jquest68 on 2009-12-06
> **Defiant Rat said:**
> Have you looked to see if the windows partition is still there? It could be that you did set up the partitioning correctly, but grub isnt showing Windows 7, in which case you just need to set up grub to show windows 7, and you can use both:


Or try [SIZE=2]**[this.]("http://http://erickoo.wordpress.com/2009/06/14/how-to-add-vista-partition-to-grub-2-ubuntu-9-10-karmic-koala/")**[/SIZE]

How would I check to find out? when its loading I see on the left upper corner of my laptop saying "Grub loader" is that what you mean? how would I check to see if its still installed?

---

### Post by seenthelite on 2009-12-06
> **jquest68 said:**
> How would I check to find out? when its loading I see on the left upper corner of my laptop saying "Grub loader" is that what you mean? how would I check to see if its still installed?

System/administration/disc utility you will see it there if it is still there. But maybe you could get to know Ubuntu and a viable way to use Windows is by using Virtualbox.

---

### Post by JK3mp on 2009-12-06
Either as stated above or with fdisk command. Just be sure Windows is gone b4 giving up hope. Normally setup dual boot in Ubuntu is Uber easy to understand, so perhaps it is just grub being gay, then again I've dual booted several, and both Grub and Lilo detect Windows 7 Partitions just fine, though grub does label it as Windows Vista for some reason beyond me. If it is there you can configure /etc/grub.conf(i think thats right path) file to view it. We can help you through that. Otherwise i'd recommend reinstalling Windows THEN reinstalling Ubuntu correctly for dual boot.(U do have to open freespace up first btw, which could have been your problem, if you do installer will have option to install to freespace, thus avoiding deletion and/or formatting of windows segment of your drive). The reason i say REINSTALL ubuntu is windows generally likes to use all your hard drive and avoid w/e it might overwrite so likely it will delete your Ubuntu. And NO there is no recovery option for Ubuntu to kick back to Windows, BUT you may have a partition (which you'll see with fdisk or setting said above) that is a recovery partition, i know my laptops vista had a partition (sda1) with factory image of Vista that i could restore. Show us results of cmd "fdisk -l" and we'll see your options from there. Sorry for the long read =P.

---

### Post by jquest68 on 2009-12-06
> **JK3mp said:**
> Either as stated above or with fdisk command. Just be sure Windows is gone b4 giving up hope. Normally setup dual boot in Ubuntu is Uber easy to understand, so perhaps it is just grub being gay, then again I've dual booted several, and both Grub and Lilo detect Windows 7 Partitions just fine, though grub does label it as Windows Vista for some reason beyond me. If it is there you can configure /etc/grub.conf(i think thats right path) file to view it. We can help you through that. Otherwise i'd recommend reinstalling Windows THEN reinstalling Ubuntu correctly for dual boot.(U do have to open freespace up first btw, which could have been your problem, if you do installer will have option to install to freespace, thus avoiding deletion and/or formatting of windows segment of your drive). The reason i say REINSTALL ubuntu is windows generally likes to use all your hard drive and avoid w/e it might overwrite so likely it will delete your Ubuntu. And NO there is no recovery option for Ubuntu to kick back to Windows, BUT you may have a partition (which you'll see with fdisk or setting said above) that is a recovery partition, i know my laptops vista had a partition (sda1) with factory image of Vista that i could restore. Show us results of cmd "fdisk -l" and we'll see your options from there. Sorry for the long read =P.

thank you for your help, its a little confusing what you wrote at the end. I like Ubuntu and I want to keep it but its what I had on my desktop with Windows that I'm pretty bummed about. I think I lost it. I had so much PSD files that I worked on very hard and its gone.

this is what I got:

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors

---

### Post by Merk42 on 2009-12-07
> **jquest68 said:**
> thank you for your help, its a little confusing what you wrote at the end. I like Ubuntu and I want to keep it but its what I had on my desktop with Windows that I'm pretty bummed about. I think I lost it. I had so much PSD files that I worked on very hard and its gone.

Basically he's saying your drive may have been sectioned off, but even if it had your PSD files would be gone at the section would only contain things from when you first bought it.

If you really want to try and get those PSDs back you could look into data recovery software.

---

### Post by Defiant Rat on 2009-12-07
> **jquest68 said:**
> 
this is what I got:

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors

You need to run:
```
sudo fdisk -l

```Then post the results


> **JK3mp said:**
>  though grub does label it as Windows Vista for some reason beyond me. 
Weird, i have Vista installed (soon to be removed :D) and it lists it as Windows7

---

### Post by tlcstat on 2009-12-07
Greetings,
Of course it goes without saying, backup, backup, backup! This is even true in Linux. That being said Windows 7 works just fine in Virtualbox. It is easy to setup and also to get Windows 7 installed. Setting up access to underlying media is a bit technical but there is plenty of support available. 
If you want to run Ubuntu, the best thing to do is bite the bullet and don't install a Windows partition. I did that for years and I didn't get anywhere with linux. Thing is it takes time to find appropriate native Linux software. But that was also true with Windows. I went through hundreds of Windows apps just to find that "one" that provided all my needs. Currently I only use four Windows apps, everything else is native linux. I personally feel that I have a much better and safer computer. But I still backup my data. Pendrives are cheap!
tlcstat

---


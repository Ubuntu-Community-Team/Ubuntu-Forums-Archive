---
title: "ubuntu dual boot installation problems"
date: 2010-04-15
forum: New to Ubuntu
---

### Post by mminorhsd on 2010-04-15
I have a windows xp machine that I am trying to get ubuntu to work in  a dual boot situation. I download and burned the 9.10 image to a cd. I booted from that CD, and followed the installation instructions, allowing the ubuntu cd to partition the hard drive and  install ubuntu. I can see the partition that it created, but the machine does not me for which system to boot. I tried the isntallation process a second time and when it got to the partitioning portion of the install, it showed that the machine already has an ubuntu partition.

I can run ubuntu from the cd, but I would really like to run it from the hard drive. I think that would be much faster. I have seen mention of GRUB2 as being the dual boot handler. I suspect that either that did not get installed properly, or in the wrong spot on the disk.

Does anyone have an idea how I can get the dual boot working?

Thank you for you help

Mike

---

### Post by e4uforums on 2010-04-15
What happens when you try to boot without the live cd in the machine?

---

### Post by mminorhsd on 2010-04-15
I've seen references to the "LIVE CD" an many posts. Is that the CD that I burned with the .iso file? If so, when I boot to that cd, I get the menu options to install ubuntu and the option to "try" ubuntu by running it from the CD. The installation will run again. When it get's the part 6, partitioning the hard drive it shows ubuntu is already on the drive.

If I run ubunu directly from the cd, ubuntu boots up and runs, although it is very slow.

Mike

---

### Post by e4uforums on 2010-04-15
Yes.  The Live CD is the disc you burned with the .iso file.  When you boot with this disc in the drive and choose "Try Ubuntu without making any changes to your computer", you are running the Live CD.  It's called this because you have a live operating system on a disc - you can run a complete desktop environment from the CD without making any changes to the computer you're running it on.

Yes again, it is generally very slow to run the OS from the CD.  Also, many of the changes you make while running the live cd are not persistent - they will be reset when you boot the next time.

---

### Post by mminorhsd on 2010-04-15
Does it look like I did something wrong in the installation that prevents the dual boot from taking place?

---

### Post by e4uforums on 2010-04-15
> **e4uforums said:**
> What happens when you try to boot without the live cd in the machine?


What happens when you try to boot _***without ***_the live cd in the machine?

---

### Post by mminorhsd on 2010-04-15
The machine boots straight into Windows XP.....

---

### Post by mminorhsd on 2010-04-15
Sorry that I misread your first post.....

---

### Post by e4uforums on 2010-04-15
That's ok...

It sounds like Ubuntu isn't properly installed OR GRUB is broken.

Go ahead and pop that Live CD back in and boot to that.  Let's choose the same "Try Ubuntu without making any changes to my computer" option so we can get to the Ubuntu desktop.  Once at the desktop, double click the Install icon on in the upper left.  Go through the installer screens until you get to the screen asking you which partition you would like to install to.  Let us know what you see here.  I suspect you'll see just one partition for the XP install and nothing else.

If you have just one partition, then Ubuntu did not install correctly and you should be safe proceeding with partitioning the HDD and installing Ubuntu.

If you have 2 partitions (one for XP and one for Ubuntu), then GRUB is most likely is not installed or it is broken.  Search the forums for "reinstall GRUB" and you should find instructions on installing GRUB from the live cd.

---

### Post by theozzlives on 2010-04-15
please....
what you wanna do is boot the live CD and run
```
fdisk -l
```
not the l is a lowercase L and not a 1.
Soon as you find out your Linux partition (prolly sda2) then run:
```
sudo -i
mount /dev/sda"x" /mnt
grub-install --root-directory=/mnt/ /dev/sda
```
The "x" is symbolic of a number. Then you'll wanna run```
update-grub
``` once you're in Ubuntu.

---

### Post by mminorhsd on 2010-04-21
e4uforums.....I booted to the CD and there are 2 partitions, one showing XP and one showing ubuntu. I've been busy at work andhave not gotten back to trying to fix grub but that will be the next step. Thank you for your help.

---

### Post by mminorhsd on 2010-04-21
e4uforums.....I booted to the CD and there are 2 partitions, one showing  XP and one showing ubuntu. I've been busy at work andhave not gotten  back to trying to fix grub but that will be the next step. Thank you for  your help.

---

### Post by mminorhsd on 2010-04-21
theozzlives....

Thank you for your response. Is this the way to fix grub?

---

### Post by e4uforums on 2010-04-21
First try what theozzlives recommended.  That procedure will fix GRUB, so if you problem is in fact a broken GRUB, this will take care of you.

If that does NOT work.  What you'll want to do is boot to that live cd, and run through another install of Ubuntu.  Be mindful to choose the current Ubuntu partition to install to.  Keep in mind you will loose any data on the current Ubuntu partition when you install again - but this shouldn't be a problem if you just recently installed.

Installing Ubuntu again will also re-install GRUB.  This should discover both OS's and give you the option to boot either.

Let us know how this goes.  Any other questions just fire away...

---

### Post by ChaimaaMer on 2010-04-21
Sorry if I am interrupting , but I have just installed the Ubunto inside windows XP using the WUBI , and I just want to know what is the difference btween that and what mminorhsd is doing.

thx

---

### Post by e4uforums on 2010-04-21
When you use WUBI, Ubuntu actually runs from the Windows file system.  A file is created at C:\Ubuntu\Root that is size of your Ubuntu install and the boot files for Windows are modified to add the Ubuntu instance to the Windows boot menu.  When you boot to Ubuntu, you are actually using a "virtual" disk that is contained in the Windows file system.  If your Windows system becomes un-bootable, you will not be able to boot into Ubuntu.  This method is recommended for only short term testing, this is not recommended for a production system.

When you partition off your drive, both OS get full access to their own separate disk space.  Ubuntu can format it's partition with ext3 or 4 and Windows can stick with NTFS - both are separated and neither depends on the other.  They are completely independent of each other.  Performance will be better using a true dual boot opposed to a WUBI install.

---

### Post by ChaimaaMer on 2010-04-21
I see  .. thanks 4 the explanation :KS

---

### Post by mminorhsd on 2010-04-22
OK...I booted ubuntu from the live cd and tried to open a terminal window to use the procedure that theozzlives recommended. The terminal window failed to open.  I am going to try one more install and see if that makes any difference.

While in ubuntu I noticed some logs. IN one of them it  mentioned being unable to read from the disk. I think this was during the installation from the cd. It is possible that when I burned the cd that something happened. I am going to burn another CD, at a slower speed and see if that makes a difference.....

---

### Post by mminorhsd on 2010-04-23
I created a new live cd and am trying to install ubuntu on the original partition that was corrected for ubuntu the first time I tried the install. When I selected the ubuntu partion I recevied a message that there is no root file system defined and to correct this from the partitioning menu. I think that this menu is accessed by pressing the change button on the screen where you select the partition to load to. I selected the EXT4 from the drop down list and proceeded to try and load ubuntu. It still gave me the message that there is no root file system. 

Now to my question. Should I check the box to format that partition from the change menu? Will that create the root file system???

I refuse to give up on this!

---

### Post by mminorhsd on 2010-04-26
I have come  to believe that the problem is with the CD's I have been burning, or the iso that I downloaded. I tried to install again and got a message that it could not read a aprt of the disk. I have ordered a distro disk and will try again when that comes in. Let's hope that works.....

---

### Post by spydeyrch on 2010-04-26
> **mminorhsd said:**
> I have come  to believe that the problem is with the CD's I have been burning, or the iso that I downloaded. I tried to install again and got a message that it could not read a aprt of the disk. I have ordered a distro disk and will try again when that comes in. Let's hope that works.....

@mminorhsd

Quick question for you, do you happen to have a usb flash drive with at least 2GB of storage on it? I may have a solution to help you. You can still boot into your windows partition, right?

Let me know.

-Spydey:guitar:

---

### Post by mminorhsd on 2010-04-27
Yes, I can still boot into windows, and I do have a USB drive with at least 2 gb of space. What is your suggestion?

---

### Post by spydeyrch on 2010-04-27
My suggestion is that you make a usb live installer. Instead of burning a CD with ubuntu and making a ubuntu live cd, use either [UNetBootin]("http://unetbootin.sourceforge.net/") (creates a non-persistent) or use [Pendrive's installer]("http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/") (creates persistent file)[.]("http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/")

Your computer will have to be able to boot from a usb drive, something you will need to change in your BIOS.

If you would like more info, let me know. :-)

-Spydey:lolflag:

---

### Post by mminorhsd on 2010-04-27
Is a persistent file one that is not able to be removed? Would the USB drive be usable for something else after I get Ubuntu installed? Not that it really matters, but I would purchase a 2gb drive instead of using my 4gb usb drive if it can't be used for anything else.

I will also have to see if the pc I'm using can boot from the USB drive....

---

### Post by spydeyrch on 2010-04-27
Be warned that by using your flash drive and "burning" ubuntu to it, any and all data on your usb flash drive will be formatted and erased. Just wanted to make sure you are aware of that.

What the those two installers do is basically make an make your ubuntu install CD but instead of a CD, it does it on the USB flash drive. This has it's advantages: it is faster, you can erase it if needs be and re-do it and you won't waste a piece of media. If you burn a CD and it is bad. Out the window goes the CD, but with the USB drive, it is still usable.

Also, you can create what is known as a persistent file, if you use the pendrive site's installer (not UNetBootin).

When you boot form the CD and select the "Try ubuntu without changing your existing files" option, you run the entire ubuntu OS from within your RAM. It is called a live session and has no impact on the files located on your HDD. The issue is that when you shutdown/restart, any and all changes that you made during your live session are lost. Which can be an issue sometimes.

So with the usb flash drive, you can still make the installer, just like the CD version. And you can still do the live session, just like the CD version. The difference is that you can make a persistent file. This records and saves any changes that you make to the ubuntu system while in the live session. Any documents you create, and bookmarks you make, any programs you install, etc. Now of course you are limited to the amount of available space on your usb drive. The ubuntu .iso takes up about 700MB (if memory serves me correctly) but this will allow you to install any programs needed to resolve your GRUB issue. Also, it may run better allowing you to do the install again and hopefully fix the GRUB issue automatically.

-Spydey:lolflag:

---

### Post by spydeyrch on 2010-04-27
> **mminorhsd said:**
> Is a persistent file one that is not able to be removed? Would the USB drive be usable for something else after I get Ubuntu installed? Not that it really matters, but I would purchase a 2gb drive instead of using my 4gb usb drive if it can't be used for anything else.

I will also have to see if the pc I'm using can boot from the USB drive....


If you use a USB drive to do what I am suggesting, then you wont be able to use it for anything else unless you get rid of the ubuntu install on the usb drive. Now, there is a work around for that issue but it requires a much larger flash drive. It is actually pretty cool!! I have a 16GB flash drive and it allows me to do some pretty cool things. I can carry an OS with me where ever I go, still have my nessecary files with me, and be free of virii. :popcorn:

If you have multiple 2GB or larger flash drives, choose one to use that doesn't carry any important files. You can always reformat it later once you get the issue fixed. That would allow you to use it for what ever you want later. :KS

Does all that make sense? It also means that you won't have to wait for the CD to come in the mail. :)
Yes, the most critical thing is to check if your BIOS can boot from a USB drive. You might need to set it to boot from the BIOS via boot sequence or boot priority. Also, most BIOSes have a "press XX button to chose boot source" message during POST.

Let me know if you need any help.

I also have one other idea that can get somewhat risky but has always worked for me without negative consequences. But it does have it's risks and involves your Windows partition.

Keep in touch. I check the forums on a regular basis.  :guitar:

-Spydey:lolflag:

---

### Post by mminorhsd on 2010-04-27
It doesn't look like the PC I'm using for ubuntu will let me boot from USB drive....I'll just wait for the distro disk I purchased to arrive. Thanks anyway.....

---

### Post by spydeyrch on 2010-04-27
> **mminorhsd said:**
> It doesn't look like the PC I'm using for ubuntu will let me boot from USB drive....I'll just wait for the distro disk I purchased to arrive. Thanks anyway.....

What is the computer brand? Custom built? What is the motherboard manufacturer and model number? How old is it? Have you tried a BIOS update? Many times a BIOS update will add new features, such as USB booting.

-Spydey:lolflag:

---

### Post by mminorhsd on 2010-04-27
It a dell optiplex i purchased from a re-furbisher locally. Not sure about the bios or board.....

---

### Post by spydeyrch on 2010-04-27
> **mminorhsd said:**
> It a dell optiplex i purchased from a re-furbisher locally. Not sure about the bios or board.....

Do you know what model/number of optiplex it is? :KS 

-Spydey:lolflag:

---

### Post by mminorhsd on 2010-04-27
Optiplex GX 60

---

### Post by Shazaam on 2010-04-27
mminorhsd...
If you haven't made any changes yet try this...
When your pc boots, try hitting your ESC keyboard button before it starts to load Windows. Do you now get the grub O/S choices menu?

---

### Post by spydeyrch on 2010-04-27
> **mminorhsd said:**
> Optiplex GX 60

Ok, I am going to do a little research and see what I can come up with. I will be back soon.

-Spydey:lolflag:

---

### Post by mminorhsd on 2010-04-27
Shazamm - esc during bootup does nothing as far as loading grub. I don't think I ever got a complete system load due to the bad disks I have been trying to use....

Spydey - thank you for all your help!

---

### Post by spydeyrch on 2010-04-27
> **mminorhsd said:**
> Shazamm - esc during bootup does nothing as far as loading grub. I don't think I ever got a complete system load due to the bad disks I have been trying to use....

Spydey - thank you for all your help!

You are welcome.

Oh and guess what..... You can boot from a usb flash drive!!!

[http://support.dell.com/support/edocs/systems/opgx60/en/ug/advfeat.htm#1122512]("http://support.dell.com/support/edocs/systems/opgx60/en/ug/advfeat.htm#1122512")

You may need to upgrade your bios to the most recent available. I don't know though because I don't know what version you are running.

Good news is that you can boot form a usb flash drive. Read the quick guide that I linked above.
:KS:popcorn:

-Spydey:lolflag:

---

### Post by spydeyrch on 2010-04-27
Once you have updated your bios, if you need to to get usb booting possible, then try the live ubuntu usb. If you need help, let me know. :P

-Spydey:lolflag:

---

### Post by mminorhsd on 2010-05-25
THank you everyone for all your help. I finally got Ubuntu 10.4 loaded on the old dell. My son burned a disk on his older computer, and I loaded Ubuntu on the pc. Instead of a dual boot system,I dedicated the entire machine to Ubuntu. I'm now working through getting the network connection to work with my router. But I'm up and running and learning about the system. So far, I like what I see.

Thanks again,

Mikey

---


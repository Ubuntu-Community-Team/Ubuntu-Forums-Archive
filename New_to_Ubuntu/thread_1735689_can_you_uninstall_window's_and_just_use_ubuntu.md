---
title: "can you uninstall window's and just use ubuntu?"
date: 2011-04-21
forum: New to Ubuntu
---

### Post by flagrl on 2011-04-21
I was just wondering if you can uninstall windows and just have ubuntu on it? and if so how?

---

### Post by lisati on 2011-04-21
Yes, you can run Ubuntu on its own without the need to have Windows installed on your computer. The process of removing windows without hurting Ubuntu will depend in part on whether or not you used Wubi to install Ubuntu "within" Windows.

---

### Post by rosencrantz on 2011-04-21
Sure. Just let Ubuntu wipe the Windows partition during the installation and use it for the system. 
But why not live with a dual boot?

---

### Post by flagrl on 2011-04-21
cause i really dont want windows on my computer and i think i used wubi im not 100% thou

---

### Post by lisati on 2011-04-21
> **flagrl said:**
> cause i really dont want windows on my computer and i think i used wubi im not 100% thou

One way of telling if you used wubi is to look on the Windows add/remove programs list on its control panel.

---

### Post by wilee-nilee on 2011-04-21
> **flagrl said:**
> cause i really dont want windows on my computer and i think i used wubi im not 100% thou

If you have a ubuntu cd boot it and either take a screen shot of gparted or run this command in the terminal and post the output.
```
sudo fdisk -l
```

---

### Post by flagrl on 2011-04-21
i dont have cd and i will look at the window's program i dont think its on there though

---

### Post by wilee-nilee on 2011-04-21
> **flagrl said:**
> i dont have cd and i will look at the window's program i dont think its on there though

If it is a wubi install the Ubuntu OS can be transferred to a partition as a regular install, so we just need to confirm what you have.

You can look in the add and remove programs in windows to look for a wubi Ubuntu install.

---

### Post by dazthejunglist on 2011-04-21
> **flagrl said:**
> I was just wondering if you can uninstall windows and just have ubuntu on it? and if so how?

just reformat your hard drive and start over oh sorry does help to down load and burn ubuntu to disk then pop in the disk on boot up the do a complete install of ubuntu might want to copy anything important to mass storage first

---

### Post by Blasphemist on 2011-04-21
> **dazthejunglist said:**
> just reformat your hard drive and start over

Flagrl, the post before this is what you should pay attention to, not the one quoted here given what you've said.

---

### Post by 84_K10Guy on 2011-04-21
As someone else said, just let the Ubuntu installer wipe the windows part of the drive. That's what I did with mine and it works perfectly.

---

### Post by flagrl on 2011-04-21
i dont have wubi. im worried about taking it off and then re instlling it cause when i installed ubuntu this time i had to connect to the internet and install something but im not sure what someone did it for me but if i have to i will do it.

---

### Post by wilee-nilee on 2011-04-21
> **flagrl said:**
> i dont have wubi. im worried about taking it off and then re instlling it cause when i installed ubuntu this time i had to connect to the internet and install something but im not sure what someone did it for me but if i have to i will do it.

So would you consider downloading the ISO for what Ubuntu distro is installed and posting a screenshot of the gparted partition manager on the live cd?

What you may or may not realize is that this ISO is an important part of the tools you may need to make sure you lose nothing, and are prepared for any needed fixes.

---

### Post by flagrl on 2011-04-21
yea i will do that. where would i do that at.

---

### Post by ClientAlive on 2011-04-21
> **wilee-nilee said:**
> So would you consider downloading the ISO for what Ubuntu distro is installed and posting a screenshot of the gparted partition manager on the live cd?

What you may or may not realize is that this ISO is an important part of the tools you may need to make sure you lose nothing, and are prepared for any needed fixes.


+1 on that. You need to have Ubuntu on a disc or usb so if something happens you will have it to turn to.


> **flagrl said:**
> yea i will do that. where would i do that at.


I'm not sure which release of Ubuntu you are wanting to install. I think Ubuntu 10.10 is the latest stable release.

It can be downloaded from this page:  [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

There is also a drop down menu at step one to select 32 or 64 bit system. Do you know if it is a 32 or 64 bit system that you have?

You will be able to run 32 bit on either kind of system and this is what a lot of people go with.

If you click the "Show Me" button in step two it will give you more in the way of instructions on how to burn it.

All you are doing when you burn it is burning the iso image to a disc. There are also many free programs for doing that. I use Magic ISO sometimes and it is simple to use. It runs on Window.

When you download in step one - you might want to select somewhere easy to find it after it is complete (like the desktop).

-------------

One other thing. Sometimes people like to make an additional partition on their hard drive when they install Ubuntu. It is not too hard to do and can save you from possible trouble in the future. If you do want to do that, now is the time to do it - when you first install it. Please let the other guys on here advise you more on it though and whether they think it is a good idea.

Also, make sure you have a back up of all your personal files that you want to keep before beginning.
:)

---

### Post by flagrl on 2011-04-21
ok i downloaded the server addtion on a cd i think so i will try to install that. will that work?

---

### Post by ClientAlive on 2011-04-21
> **flagrl said:**
> ok i downloaded the server addtion on a cd i think so i will try to install that. will that work?


I don't know a lot about the differences; but, are you running a server? Or just a regular computer that you use for personal use? And did you mean: "addition" or "edition"?

Thanks

---

### Post by Blasphemist on 2011-04-21
It will work for a server but no I don't think that is what you want. Desktop is what you want unless you are building a server. For 10.04 or 10.10 use desktop edition, if you install 11.04 beta 2 that is being released out of beta in 1 week, it is just called desktop. If you go with 11.04, natty narwal, the automatic updates will get you to the release without reinstalling.

---

### Post by ClientAlive on 2011-04-21
Are you the one who installed Ubuntu and Windows on your computer before this?

---

### Post by flagrl on 2011-04-22
no i never installed windows on my computer.so i need the desktop edition but wont it just do the same thing and install next to window's?

---

### Post by stealth. on 2011-04-22
**Wait OP, just migrate wubi to another partition. **

[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354) <--Nice guide, I've personally used it before.

---

### Post by flagrl on 2011-04-22
i got to 
mkfs.ext4 [COLOR=Red]/dev/sda5[/COLOR]then i got 
Could not stat /dev/sda5 --- No such file or directory

---

### Post by stealth. on 2011-04-22
> **flagrl said:**
> i got to 
mkfs.ext4 [COLOR=Red]/dev/sda5[/COLOR]then i got 
Could not stat /dev/sda5 --- No such file or directory


[U][B]READ EVERYTHING, UNDERSTAND WHAT YOU ARE DOING

[/B][/U]*[COLOR=Red]Please don't use the manual migration unless you  fully understand what you are doing. The automated migration has many  additional safeguards and will protect you from errors.[/COLOR]*

what is the output of "fdisk -l"

---

### Post by flagrl on 2011-04-22
the output is:

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x80000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14594   117218304    7  HPFS/NTFS

---

### Post by stealth. on 2011-04-22
I'm going to try to help you, I don't have too much time though. 

[FONT=Courier New]/dev/sda1   *           1       14594   117218304    7  HPFS/NTFS [/FONT]<---This is your Windows partition I believe, because that's the only partition there, and you installed from Wubi right?



Your going to need to make 2 more partitions, one for Linux swap space (this is generally around 4gb) and the Ubuntu partition (How ever much space you want/have left). 

Use Ubuntu's Disk Manager to make the partitions, or install Gparted.

---

### Post by flagrl on 2011-04-22
im downloading it again so i can save it on a cd then start the downloading process again once i get the CD done when i reinstall it will it uninstall window's or will it use it side by side again. sorry i'm really new to the whole thing

---

### Post by JKyleOKC on 2011-04-22
The server edition that you downloaded does not have any Windows-like capability; it runs from the command line only. While it's possible to install the Windows-like capabilities afterward, it's much more likely to get you highly confused along the way! For best results at this stage of your learning curve, use the 32-bit Desktop version. It will work with almost any hardware, and usually works "out of the box" with no tweaking required.

Also you need to be aware that doing a complete replacement will wipe out everything that you have stored on the computer, so you need to back up any files that you want to keep onto an external drive or USB stick. This is especially important with regard to pictures that you've stored from your own camera, or any documents you have written on the machine.

And ask here if you have ANY questions, before trying something to see if it works. With Linux, any version of it, it's quite easy to wipe out your entire system by using a wrong command -- so verify anything that you don't understand!

Welcome to the wonderful world of free (as in liberty) computing!

---

### Post by stealth. on 2011-04-22
> **flagrl said:**
> im downloading it again so i can save it on a cd then start the downloading process again once i get the CD done when i reinstall it will it uninstall window's or will it use it side by side again. sorry i'm really new to the whole thing

Yeah, that's probably better. Just re-download the .iso and burn the _**image**_ to the CD. You can install it over Windows (I remember seeing the option, although I haven't done it that way...yet)

Tell it to format /dev/sdb1 (according to fdisk -l is the Windows partition) [B]

Follow the above post if you want to keep anything from Windows, I assumed you would already know this. [/B]

---

### Post by flagrl on 2011-04-22
ok thank you i will tell yall how it goes.

---

### Post by Blasphemist on 2011-04-22
> READ EVERYTHING, UNDERSTAND WHAT YOU ARE DOING

Please don't use the manual migration unless you fully understand what you are doing. The automated migration has many additional safeguards and will protect you from errors.

It is Friday and the week can beat down on us but, everyone should remember that by and large everyone is trying to be smart and safe about what they do. When recommendations are dangerous or while walking step by step through a process that is complicated, it never hurts to include additional warning or instruction. It is very hard for many if not most forum users to fully understand each and every step of what they are doing. That is especially the case because posts are seldom written with the lowest common level of expertise in mind. That is expected. All contributions are welcome and as people use posts, when they can add explanation or reference that helped them, they certainly should.

Using all caps, underlining and bolding seems unduly harsh. I see you are helping now and applaud that. I also see you don't have much time. I'll work on this too and it looks like others are willing.

I also just saw the note on using sdb1. Did I miss something? That would be a second hard drive. I fully concur with Jim Kyle's post. Welcome again flagrl.

---

### Post by stealth. on 2011-04-22
> **flagrl said:**
> ok thank you i will tell yall how it goes.

Alright sweet. I'm about to take Windows off myself. The only thing holding me back was Fl Studio and iTunes. With my shiny new partition I'm going to install Arch Linux. I'm going to have it dual boot into either Ubuntu or Arch Linux(I've never used Arch before)


8-)

---

### Post by stealth. on 2011-04-22
> **Blasphemist said:**
> It is Friday and the week can beat down on us but, everyone should remember that by and large everyone is trying to be smart and safe about what they do. When recommendations are dangerous or while walking step by step through a process that is complicated, it never hurts to include additional warning or instruction. It is very hard for many if not most forum users to fully understand each and every step of what they are doing. That is especially the case because posts are seldom written with the lowest common level of expertise in mind. That is expected. All contributions are welcome and as people use posts, when they can add explanation or reference that helped them, they certainly should.

Using all caps, underlining and bolding seems unduly harsh. I see you are helping now and applaud that. I also see you don't have much time. I'll work on this too and it looks like others are willing.

I also just saw the note on using sdb1. Did I miss something? That would be a second hard drive. I fully concur with Jim Kyle's post. Welcome again flagrl.

I've always thought that /dev/sda is like the main disk, and /dev/sdaX is the partition. 

Sorry about the underlining/bold font I was just trying to make sure he saw what I wrote. Was not trying to be mean.

---

### Post by jramshu on 2011-04-22
I have a HP Desktop I completely removed Window's from and it's now an Ubuntu machine, started out as a desktop, now it's a server. I also have a dual boot HP laptop(currently on). 

Here is my little bit of advice. 
Backup everything you consider important.
Once you have the Desktop ISO, put it in, reboot. 
During installation the set-up will give you options on partitions.
If you don't want window's any more, select the one that says something like "Guided-Use Entire Disk," that will erase window's and automatically set-up the partitions correctly. 
Once you get some more experience using Ubuntu, then you can go back and set-up the partitions anyway you want/need. Usually the default set-up is just fine. 

Here is a fairly good site that shows the graphical install.
[http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml](http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml)

---

### Post by ClientAlive on 2011-04-22
> **JKyleOKC said:**
> The server edition that you downloaded does not have any Windows-like capability; it runs from the command line only. While it's possible to install the Windows-like capabilities afterward, it's much more likely to get you highly confused along the way! For best results at this stage of your learning curve, use the 32-bit Desktop version. It will work with almost any hardware, and usually works "out of the box" with no tweaking required.

Also you need to be aware that doing a complete replacement will wipe out everything that you have stored on the computer, so you need to back up any files that you want to keep onto an external drive or USB stick. This is especially important with regard to pictures that you've stored from your own camera, or any documents you have written on the machine.

And ask here if you have ANY questions, before trying something to see if it works. With Linux, any version of it, it's quite easy to wipe out your entire system by using a wrong command -- so verify anything that you don't understand!

Welcome to the wonderful world of free (as in liberty) computing!


+1  Yes. Abosolutely.


> **stealth. said:**
> Yeah, that's probably better. Just re-download the .iso and burn the _**image**_ to the CD. You can install it over Windows (I remember seeing the option, although I haven't done it that way...yet)

Tell it to format /dev/sdb1 (according to fdisk -l is the Windows partition) [B]

Follow the above post if you want to keep anything from Windows, I assumed you would already know this. [/B]

+1 to that.

Ubuntu is very easy to install from a disc. I think it's even possible to get a free one sent to you in the mail (although I've never done it).

When you put the disc you burned in the cd/ dvd drive and restart you'll be given an option to install. Clicking on that pretty much walks you through the process.

Welcome to Ubuntu flagrl! Hope you enjoy it and enjoy your stay on the forums.

---

### Post by flagrl on 2011-04-23
i uninstalled it and reinstalled it using a cd. at first my computer shutdown during the installitiong process so i had no server nothing but i figured out how to do install ubuntu so now i just have ubuntu :) i even figured out how to get the internet wokring agian and it only took me 20 minutes instead of 20 days :) thank ya'll for yalls help i appreciate it.

---

### Post by ClientAlive on 2011-04-23
> **flagrl said:**
> i uninstalled it and reinstalled it using a cd. at first my computer shutdown during the installitiong process so i had no server nothing but i figured out how to do install ubuntu so now i just have ubuntu :) i even figured out how to get the internet wokring agian and it only took me 20 minutes instead of 20 days :) thank ya'll for yalls help i appreciate it.


That's awesome! Congrats on your new install!

:popcorn:

---


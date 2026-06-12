---
title: "Losing Ubuntu"
date: 2009-08-02
forum: New to Ubuntu
---

### Post by kingofkong on 2009-08-02
I just bought a computer that has Ubuntu 9.04 installed on it. It looks like a cool platform but I'm 100% lost on it.
 
If anybody can tell me or direct me to a tutorial on how to format the drive and install vista instead it would be greatly appreciated as my googling how to do it has come up with nothing.

---

### Post by aysiu on 2009-08-02
Why did you buy a computer with Ubuntu 9.04 on it if you wanted Vista?

Here. This tutorial from Microsoft may help you:
[http://support.microsoft.com/kb/247804](http://support.microsoft.com/kb/247804)

---

### Post by lisati on 2009-08-02
> **kingofkong said:**
> I just bought a computer that has Ubuntu 9.04 installed on it. It looks like a cool platform but I'm 100% lost on it.
 
If anybody can tell me or direct me to a tutorial on how to format the drive and install vista instead it would be greatly appreciated as my googling how to do it has come up with nothing.

That's what the forums are here for: so you can ask questions about using Ubuntu. 

Now what was the Ubuntu-specific question again?

---

### Post by kingofkong on 2009-08-02
> **lisati said:**
> That's what the forums are here for: so you can ask questions about using Ubuntu. 
 
Now what was the Ubuntu-specific question again?
 
I want to format the HDD so I can switch to windows Vista (lost my XP disks >_<) because I can't get it to install the game I want to play (Fiesta)
 
Plus I'm so unfamiliar with Ubuntu that I feel like a monkey hitting the keyboard with a rock lmao.

---

### Post by SunnyRabbiera on 2009-08-02
Well you can try your game with wine, by default Ubuntu cant install .exe but with wine it might work.
Though wine is far from perfect.
If you got enough RAM you can install windows in virtualbox

---

### Post by credobyte on 2009-08-02
Do you have a valid ( licensed ) Windows Vista CD/DVD ? If the answer is yes, boot from it and you'll have a choice, whether you want to delete all existing partitions and create a new one or to install them side-by-side.

---

### Post by kingofkong on 2009-08-02
> **SunnyRabbiera said:**
> Well you can try your game with wine, by default Ubuntu cant install .exe but with wine it might work.
Though wine is far from perfect.
If you got enough RAM you can install windows in virtualbox
 
here's sys specs
AMD Athlon 64 X2 Dual Core 4200+
Gigabyte GA-M55SLI-S4 (Nvidia nForce4 chipset)
4GB DDR2 PC2-6400 RAM
NVIDIA GeForce 8800 GTS 512 (512 MB)
Hiper Modular Power Supply (520W)
Western Digital Raptor 150GB (10000 RPM SATA 3.0Gb/s)
 
I wouldn't mind keeping ubuntu but windows is easier to understand
 
> **credobyte said:**
> Do you have a valid ( licensed ) Windows Vista CD/DVD ? If the answer is yes, boot from it and you'll have a choice, whether you want to delete all existing partitions and create a new one or to install them side-by-side.
 
I do and have tried that. It goes through setup and does fine until it asks me to select a partition. None are formatted to the corect format and when I try to it gives me an error message when I try to just boot disk it.

---

### Post by credobyte on 2009-08-02
> **kingofkong said:**
> 
I do and have tried that. It goes through setup and does fine until it asks me to select a partition. None are formatted to the corect format and when I try to it gives me an error message.

You need to delete it & create a new one, NTFS partition.

---

### Post by Sef on 2009-08-02
>  I wouldn't mind keeping ubuntu but windows is easier to understandIt is easier because you are used to it.   Since I use Ubuntu more, I find it easier to understand and use than Windows.  If you want to keep it, you can dual boot.

---

### Post by kingofkong on 2009-08-02
> **credobyte said:**
> You need to delete it & create a new one, NTFS partition.
 
Ok, could you tell me how to do that? I've used the help feature and it says to go to system>admin tools>gnome partition something, which doesn't seem to be installed unless I missed it. I'm usually good at just puzzling things out on my own but my searches have come up less then satisfying and I've gotten quite frustrated.
 
> **Sef said:**
> It is easier because you are used to it. Since I use Ubuntu more, I find it easier to understand and use than Windows. If you want to keep it, you can dual boot.
 
I'd like to do that so I can putter around with Ubuntu.

---

### Post by credobyte on 2009-08-02
> **kingofkong said:**
> Ok, could you tell me how to do that? I've used the help feature and it says to go to system>admin tools>gnome partition something, which doesn't seem to be installed unless I missed it. I'm usually good at just puzzling things out on my own but my searches have come up less then satisfying and I've gotten quite frustrated.

Well, yes, gParted ( the tool you are talking about ) does not come pre-installed. Tough, I don't see a reason why you would want to install it - you will not be able to delete your partition while it's mounted ( while it's in use ).
Do you have an Ubuntu CD ? If so, boot into a Live session and you'll be able to perform these steps ( delete, create, etc. ).

---

### Post by aysiu on 2009-08-02
You can use the GParted live CD to reformat the drive as FAT32 or NTFS:
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by lotharmat on 2009-08-02
I have found pottering around with ubuntu really good fun. I am a total noob but after a few weeks I think I'm starting to learn something. I now prefer it to Windows! For a start, the amount of free software out there for Ubuntu is mind-blowing. if you do a google search for "dual booting Ubuntu with Windows - Ubuntu installed first" you will probably get a step by step guide with pictures. Give Ubuntu a chance - you will love it!

---

### Post by kingofkong on 2009-08-02
> **credobyte said:**
> Well, yes, gParted ( the tool you are talking about ) does not come pre-installed. Tough, I don't see a reason why you would want to install it - you will not be able to delete your partition while it's mounted ( while it's in use ).
Do you have an Ubuntu CD ? If so, boot into a Live session and you'll be able to perform these steps ( delete, create, etc. ).
 
I don't have a CD, I got the computer 2nd hand with Ubuntu pre-installed. I'm assuming I can get a iso somewhere and burn a CD on the comp I'm using ATM which is no good for much more the internet browsing.
 
Also thanks to you and everybody else that's responded.

---

### Post by slakkie on 2009-08-02
Now why are we helping someone that should call MS support to get Vista installed. All MS installers have fdisk, so he can delete/create partitions with the windows installer.

Download [http://sourceforge.net/projects/gparted/files/gparted-live-stable/](http://sourceforge.net/projects/gparted/files/gparted-live-stable/)
Burn the image
Boot the CD
Remove all partitions
Boot from Vista CD

/thread.

---

### Post by kingofkong on 2009-08-02
> **slakkie said:**
> Now why are we helping someone that should call MS support to get Vista installed. All MS installers have fdisk, so he can delete/create partitions with the windows installer.
 
/thread.
 
cause I've learned through the helpful posts that I can keep Ubuntu and have windows as well which I'd preffer while I learn how to use Ubuntu.
 
Not totally sure hoe to do that yet but I'm catching on, DLing the GParted live CD ISO so I can partition the drive so I can run both hopefully.
 
If you can offer some advice to that respect it would be greatly appreciated
 
*EDIT*
> **slakkie said:**
>  
Download [http://sourceforge.net/projects/gparted/files/gparted-live-stable/](http://sourceforge.net/projects/gparted/files/gparted-live-stable/)
Burn the image
Boot the CD
Remove all partitions
Boot from Vista CD
 
/thread.
 
Thanks, can I also use this to keep Ubuntu and run windows? From what I've read I can, I have enough space and 4 gig of RAM, plus another 1 gig stick I havent put in yet

---

### Post by lotharmat on 2009-08-02
People are helping because they are helpful and the more helpful people are the more likely people are to stick with Ubuntu.

---

### Post by pastalavista on 2009-08-02
Your machine seems to be perfect for Ubuntu. If you'd like to try and fix it, I have a solution that has worked for me a few times. Boot into recovery mode and repair broken packages. Then open a root terminal with networking and enter these commands:
```
sudo apt-get update (to make sure the networking works.. if it doesn't skip the rest)

sudo apt-get purge xserver-xorg

sudo apt-get install xserver-xorg

sudo apt-get dist-upgrade
```

The best thing I like about Ubuntu (I got rid of Windows entirely) is that I CAN fix it. In the early stages, it was perplexing and I had to do a ton of searching for fixes. But I eventually got all the bugs and kinks worked out andd it is now rock-solid. With Windows Vista I (I only had 1 gig of RAM and they said it was "Vista Ready") whenever something broke, all I could do was re-install. It got extremely sluggish if I didn't reboot at least twice a day. Ubuntu would run fine forever if I didn't have to reboot sometimes for kernel updates. Windows doesn't allow you to do anyting system-wise except run its own approved software which usually has monetary expense. Ubuntu is constantly improving daily and I see the benefits right away. I would never go back to Windows now. I'm sorry you're so indoctrinated in Windows dogma. Keep learning Linux. One day you'll be glad you did.

---

### Post by nothingspecial on 2009-08-02
You need to boot from the disk. Adjust the settings in your bios for this.

Then you need to reduce the size of your ubuntu partition and create a new windows one. Then install windows on the new empty partition.

It would actually be easier to install windows over the entire disk and then create a new partition for Ubuntu because windows doesn`t like 2 operating systems so won`t easily let you boot ununtu.

---

### Post by slakkie on 2009-08-02
> **kingofkong said:**
> 
Thanks, can I also use this to keep Ubuntu and run windows? From what I've read I can, I have enough space and 4 gig of RAM, plus another 1 gig stick I havent put in yet

Yes, but don't remove all the partitions, but resize them. You will have to do some grub magic after you've installed windows since the mbr (master boot record) will be overwritten by windows. Normally I would say, install Windows first, then Linux. But since you already have Ubuntu installed this doesn't fly.

Follow this guide for fixing the mbr: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by lotharmat on 2009-08-02
> **slakkie said:**
> Yes, but don't remove all the partitions, but resize them. You will have to do some grub magic after you've installed windows since the mbr (master boot record) will be overwritten by windows. Normally I would say, install Windows first, then Linux. But since you already have Ubuntu installed this doesn't fly.

Follow this guide for fixing the mbr: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Although it could be less painful.

I'm in a similar situation with a Laptop I bought - I plan to format HDD --> install Windows 7 --> re-partition and install Jaunty.

---

### Post by kingofkong on 2009-08-02
> **slakkie said:**
> Yes, but don't remove all the partitions, but resize them. You will have to do some grub magic after you've installed windows since the mbr (master boot record) will be overwritten by windows. Normally I would say, install Windows first, then Linux. But since you already have Ubuntu installed this doesn't fly.
 
Well, Ubuntu is free to DL to reinstall if I just get rid of it (which I'm assuming I can do with GParted as per this you recently posted).
 
> **slakkie said:**
> 
Download [[COLOR=#000000]http://sourceforge.net/projects/gpar...d-live-stable/[/COLOR]]("http://sourceforge.net/projects/gparted/files/gparted-live-stable/")
Burn the image
Boot the CD
Remove all partitions
Boot from Vista CD

 
I'm assuming I can remove and reformat correctly for windows using this proccess? Then reinstall Ubuntu so I can learn it?

---

### Post by lotharmat on 2009-08-02
That's what I'd do.

---

### Post by Katalog on 2009-08-02
May I also direct yur attention to this free book, "[The Ubuntu Pocket Guide and Reference]("http://www.ubuntupocketguide.com/download_main.html")"? It contains instructions on just about everything, including how to set up your computer to dual boot Windows and Ubuntu (it's even in the first chapter, I believe).

---

### Post by slakkie on 2009-08-02
> **kingofkong said:**
> Well, Ubuntu is free to DL to reinstall if I just get rid of it (which I'm assuming I can do with GParted as per this you recently posted).
 

 
I'm assuming I can remove and reformat correctly for windows using this proccess? Then reinstall Ubuntu so I can learn it?

If you are going to do this I would advise to split your disk 50/50 for both Windows and Ubuntu. So yes, the same process applies when you want to reinstall Ubuntu later on.

---


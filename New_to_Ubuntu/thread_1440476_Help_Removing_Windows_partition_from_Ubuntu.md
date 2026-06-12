---
title: "Help Removing Windows partition from Ubuntu"
date: 2010-03-27
forum: New to Ubuntu
---

### Post by Goroman on 2010-03-27
Hi guys, I am really a beginner here, I gave a step coming to Ununtu.
First I installed wubi as a os managed from windows, I have more than a month using it and I am confident and really dont want to go back to windows.

I tried to remove windows at all to install the complete ubuntu as my only OS. I could not do it.
Then I prefered to wubi, now I am on my ubuntu partition but would like get rid off windows at all.

I have added gparted from repository which did not work due to cannot remove partitions in use (Windows at this case).
Then, I downloaded the gparted live cd (gparted-live-0.5.2-1.iso) and burned using brasero disk burner... There I did "burn image" and selected the downloaded iso image from my downloaded places. and burned completely fine.

When I insert the disc I supposed it will run from the very beginning which did not happen, I can only see the files... DID I DO SOMETHING WRONG WHEN BURNING?
I went to System-preferences-preferred applications and there accessibility - mobility - run at start... but nothing happens. I still see the files when I open the cd...

What I am doing wrong?

Please help.

---

### Post by s_ø on 2010-03-27
Hi. The easiest would be to download the ubuntu iso file and burn it. Then boot it and choose 'use entire disk' in the install process. REMEMBER TO BACKUP - you will lose everything on the disk.
I dot know really anything about wubi, but think you run it as a program from windows. So you cant remove windows without removing wubi.

---

### Post by gnometorule on 2010-03-27
Got a little trouble deciphering what you write, but it seems you are still running Ubuntu under Wubi, and want to get rid of Windows. IF that is what you're trying to do, that's not possible. All you need to do is to burn a live CD and take it from there; this can lead to trouble, but that's the way to go to single-install Ubuntu.

But I might well have just not been able to understand what you wrote.

---

### Post by Girya on 2010-03-27
I'm not sure if I understand the question but I think you need to insert the disk in your cd drive (if its not already in there) and reboot the computer.

---

### Post by readycarpenter on 2010-03-27
yes I think he is still running ubuntu through wubi

wubi does not even create a real ubuntu partition, it researves space from your windows partition, wubi ubuntu is on your windows partition.

backup your data, download and burn the ubuntu iso
boot the cd, and install ubuntu
cheers

---

### Post by Goroman on 2010-03-27
Yes, I am using ubuntu through wubi. Where can I download the ubuntu iso? and where can I boot it from? do I have to go to my windows partition or is simply add the ubuntu iso and everything start/

Thanks for helping me.

And sorry for my limited english.

---

### Post by takisan on 2010-03-27
It's at [http://releases.ubuntu.com](http://releases.ubuntu.com)
I'd reccomend [Karmic]("http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-i386.iso") (9.10) but Hardy is on that server as well.

If you want a port, it's at [http://cdimage.ubuntu.com/ports/releases/](http://cdimage.ubuntu.com/ports/releases/)

The Install DVD for Karmic is at [http://cdimage.ubuntu.com/releases/9.10/release/](http://cdimage.ubuntu.com/releases/9.10/release/)

---

### Post by s_ø on 2010-03-27
Download ubuntu here[ http://www.ubuntu.com/getubuntu/download]("http://www.ubuntu.com/getubuntu/download")
Burn it either to a cd, or from your wubi install, use the usb startup creator utility to create a bootable usb stick. 
Start by making backup of your data.
When ready to install, reboot your computer. You can get a boot menu by pressing F12 (on most systems), then select to boot cd or harddisk>usb.

---

### Post by vivek40 on 2010-03-27
The best would be to use a torrent to download the ISO image, burn it at least on three to four CDs(It is always good to have a few of them with you)and then do a fresh install , throw away that windows out of the window<believe me it is a piece of crap>

---

### Post by Goroman on 2010-03-27
OK, downloading...

---

### Post by Goroman on 2010-03-27
Ok, I already downloaded the ubuntu iso, I followed the steps from the installation page. I added the disc, restart the computer and I was directed to the same initial page where I can choose between ubuntu and windows. I choose ubuntu but the disc did not start...

What am I doing wrong?

---

### Post by noobie1 on 2010-03-27
First of all, you didn't mention backup.  You're going to lose anything you have on the hard drive when you do this.

You need to boot from the CD, and may need to change this in the BIOS.  Depending on your computer it might need you to press F2 or Del at startup.  Once you're in change the boot order so that CD is first.

---

### Post by Goroman on 2010-03-27
I already back it up.
I did f12 at startup and take me to the ubuntu screens... I got the options to add language, keyboard and all the menu to start ubuntu... when I did install ubuntu simple did not follow and the actions get frozen. do I have to wait more than 5 minutes? or something went wong? I press the eject and the it take me again to the partitions menu.

Do I have to wait at that process?

---

### Post by s_ø on 2010-03-28
So you booted the livecd and got the menu where you can choose "try ubuntu...", "install.."?
What did you choose?
Where did it freeze? Just after the boot screen or when you have loaded the installer?

Remember when using the livecd you are running ubuntu from the cd/ram, so it can take a long time to load.

---

### Post by Goroman on 2010-03-28
Yes  I booted and I got that menu.
I choose install at first instance nothing happens. Then I removed the cd and inserted again and did try ubuntu and just get frozen. It let me navigate away from the f1, f2, f3, f4 etc menus before I click on the options to run ubuntu.

I know it can take a long time, but I let it yesterday all night and now I come to check it and it is at the same point... frozen..

This is the second cd I burn thinking the first one was burned wrong.

---

### Post by waynefoutz on 2010-03-28
It could be your cd drive. Do you have a USB memory stick? You can pick one up for a few bucks if not.  You can download unetbootin at [http://unetbootin.sourceforge.net/]("http://unetbootin.sourceforge.net/")
and use that to download and install it on a USB memory stick. You probably need to go into your BIOS and set the boot order so it will boot off the USB.

I prefer installing operating systems this way, it's a lot faster than using a cd, plus you can use the USB stick over and over.

---

### Post by theozzlives on 2010-03-28
Don't eject the CD, be patient and wait.

---

### Post by egalvan on 2010-03-28
> **Goroman said:**
> Yes  I booted and I[B] got that menu.
[/B]

This is the second cd I burn **thinking the first one was burned wrong.**

First, if the CD booted and you got that menu, then is was burned OK.

Second, if you want to test the CD (highly recommended), then from that menu, choose "test media" (or some such choice, possibly "test CD", it should be easy to figure out.)
This will run a checksum on the entire contents and **verify that the CD was burned correctly, and that the contents are correct.**
Mark the CD as "tested and verified".
(Obviously, if the check fails, then that CD is a coaster ;))

After this, I (highly) recommend you choose the "test memory" option, and let it run for two to four hours.
If the memcheck does not show any errors in the middle part of it's screen, then your RAM is most likely fine.
 (the errors always show in red, when I run it on 'problematic" machines)

---

### Post by egalvan on 2010-03-28
> **Goroman said:**
> 

I know it can take a long time, but I let it yesterday **all night** and now I come to check it and it is at the same point... **frozen**..

> **theozzlives said:**
> Don't eject the CD, be patient and wait.

Hey Ozz, you're right on the 'patience', but wouldn't "all night" be a little long in that department :)?
I know *I* wouldn't wait *that* long.

Mayhaps the OP has other issues.

Hey **Goroman**, please post the specs on that machine...

these are the most important at this moment...
type and speed of CPU
how much RAM
how big a hard drive, and how much empty space

---

### Post by gnometorule on 2010-03-28
> **waynefoutz said:**
> It could be your cd drive. Do you have a USB memory stick? You can pick one up for a few bucks if not.  You can download unetbootin at [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
and use that to download and install it on a USB memory stick.

Downloaded unetbootin from synaptic. What's next? I would like to make me one of these for KK. Thanks much. (when downloading from link quoted above for 'Linux', i get 'unknown filetype'; but I'd assume that the synaptic download is just as well if not easier in principle).

---

### Post by Goroman on 2010-03-28
Hey Egalvan and Guys, thanks very much for helping me... I appreciate. I am now FREE from windows and happy.

It seems the problem it was the cd I was writting to. I tried with another cd brand and  everything worked fine.

Now I am updating.

Thanks again.
:popcorn:

---


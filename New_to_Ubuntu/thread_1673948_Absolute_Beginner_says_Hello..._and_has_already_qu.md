---
title: "Absolute Beginner says Hello... and has already questions..."
date: 2011-01-23
forum: New to Ubuntu
---

### Post by Alqamar on 2011-01-23
Hello there! I am an Absolute Beginner, so please forgive me if my questions have been asked a thousand times. I have used Ubuntu several times in a Dell Netbook, and I would like to try it on my desktop computer.

I use Windows XP SP3, and would like to install Ubuntu in an external drive, to boot from it, keeping both OS in different drives. 

Is it possible? I've been checking the Forums in [www.ubuntu.com](www.ubuntu.com), but it seems I can't find the information. Or, more likely, it seems like it is possible, but it seems I cannot find any definite answers...

I've found plenty of information on installing Ubuntu from an external drive or an USB stick, as I have already downloaded Ubuntu 10.10 (the ISO file) and burnt it into a DVD.

Would you please help me, or point me in the right direction? 

I've bought this external drive: Toshiba PX1665E - 1HF4. 
I would like to split it, using some space exclusively for Ubuntu, and some other space for both Ubuntu and Windows (to keep files, etc...).

---

### Post by Rubi1200 on 2011-01-23
Hi and welcome to the forums :)

This will hopefully get you going in the right direction:
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

If you have questions, feel free to ask.

---

### Post by hansolo4949 on 2011-01-23
I know it certainly POSSIBLE to install Ubuntu to and External HDD, unless you don't want to boot the computer, you will have to keep the HDD plugged into your computer. The reason for that is that "GRUB" which is the Linux bootloader, is on the External HDD, so if you remove it, and the computer wants to boot, it will generate an error message and abort. I think one possible solution is to boot from a livecd, and install GRUB on you internal HDD, and that way, GRUB is there, and can boot your computer. There are several good tutorials on this, just google "installing GRUB on my internal HDD using a livecd" or something like that.:)

---

### Post by mlentink on 2011-01-23
It is entirely possblie to install ubuntu on an external harddisk and leave your internal harddisk as is. Just make sure to install GRUB on the external (USB)-disk. After makeing the partitioning selesction in the installer (obviously, make sure to use partitions on the external disk) click the advanced button and have GRUB installed on the external disk. 

At boot time, use the BIOS-boot order options (usually F9, or Del, consult your computer's manual) and select the appropriate drive.

---

### Post by Alqamar on 2011-01-24
Thanks for all the replies so far.

I will begin reading the link in Rubi1200's reply. Uhmmm... this looks interesting but difficult. (begins to read....)

---

### Post by Rubi1200 on 2011-01-24
> **Alqamar said:**
> Thanks for all the replies so far.

I will begin reading the link in Rubi1200's reply. Uhmmm... this looks interesting but difficult. (begins to read....)
To be honest, I do not know of an easier way to do it than the method Herman illustrates on his site.

The important thing to do is make backups first, be careful with partitioning, and use the advanced (manual) installation option when you move ahead.

Ask as many questions as you want before you start. We are here to help.

---

### Post by Paqman on 2011-01-24
Another point you may want to bear in mind is that running your OS across a USB connection is likely to be pretty slow. Ubuntu will run much better if you install it to your internal hard drive. However, if you're nervous about partitioning that drive then i'd suggest you go ahead and install to the external one for now, and look at reinstalling to the internal drive once you're a bit more comfortable with the system.

---

### Post by Alqamar on 2011-01-24
> **Paqman said:**
> Another point you may want to bear in mind is that running your OS across a USB connection is likely to be pretty slow. Ubuntu will run much better if you install it to your internal hard drive. However, if you're nervous about partitioning that drive then i'd suggest you go ahead and install to the external one for now, and look at reinstalling to the internal drive once you're a bit more comfortable with the system.

Is that so? Uhmmm...

My internal drive is split into two logical partitions (one is called C:, the other is called D:...) Maybe I should install Ubuntu into D:, formatting it... But is it safe to do so? Won't it affect the other partition? Doubts, doubts...

(Keeps reading)

Thanks for all your replies. I'll return as soon as I have more questions, and will be sure to ask before doing anything (I guess it's safe to boot with the LiveCD and try Ubuntu without installing it...)

---

### Post by Vaphell on 2011-01-24
> Maybe I should install Ubuntu into D:, formatting it... But is it safe to do so? Won't it affect the other partition? Doubts, doubts...

it won't affect your main windows partition but remember that playing with partitions is a serious business so it's wise to back up all things you can't afford to lose, just in case some unlikely glitch, loss of power, human error happens.

If you decide to go on, i suggest manual install with separate home partition, which in the long run makes it a breeze to reinstall ubuntu in case of some screwup that the initial lack of experience may prove hard to fix. People often break things when they are not too familiar with them and starting fresh is often the best choice that saves a lot of grief.

---

### Post by T4M* on 2011-01-24
Hello.  New member here.

Im trying to do the same thing but I went ahead of myself.

I installed ubuntu on an external hardrive and it works fine.  But, on my internal hardrive, I already had Windows Vista installed.

I wanted to have two operating systems but now i just have ubuntu.

Is there anyway to fix this?  here are some pics...

[http://img18.imageshack.us/img18/9494/dsc07108nh.jpg](http://img18.imageshack.us/img18/9494/dsc07108nh.jpg)
[http://img249.imageshack.us/img249/945/dsc07109f.jpg](http://img249.imageshack.us/img249/945/dsc07109f.jpg)
[http://img96.imageshack.us/img96/747/dsc07110d.jpg](http://img96.imageshack.us/img96/747/dsc07110d.jpg)

---

### Post by Alqamar on 2011-01-24
I'm also thinking of buying an additional internal drive, splitting it into Windows space (to store files, sucha as ripped music from my CD collection, not programs) and Ubuntu space, and use it as a safe sand-box enviroment. Uhmm...

---

### Post by Alqamar on 2011-01-24
> **T4M* said:**
> Hello.  New member here.

Im trying to do the same thing but I went ahead of myself.

I installed ubuntu on an external hardrive and it works fine.  But, on my internal hardrive, I already had Windows Vista installed.

I wanted to have two operating systems but now i just have ubuntu.

Is there anyway to fix this?  here are some pics...

[http://img18.imageshack.us/img18/9494/dsc07108nh.jpg](http://img18.imageshack.us/img18/9494/dsc07108nh.jpg)
[http://img249.imageshack.us/img249/945/dsc07109f.jpg](http://img249.imageshack.us/img249/945/dsc07109f.jpg)
[http://img96.imageshack.us/img96/747/dsc07110d.jpg](http://img96.imageshack.us/img96/747/dsc07110d.jpg)

I'm not sure I undestand the pictures... (in fact, I'm sure I don't understand most of what the pictures mean...)

Did you say you wanted to install Ubuntu on the external drive, and installed in on your internal drive, erasing Windows Vista? (by mistake)

Or did you say that you installed Ubuntu on the external drive, and it worked fine, but you -unexplicably- no longer have Windows Vista on your internal drive?

---

### Post by Paqman on 2011-01-25
> **T4M* said:**
> Hello.  New member here.

Im trying to do the same thing but I went ahead of myself.

I installed ubuntu on an external hardrive and it works fine.  But, on my internal hardrive, I already had Windows Vista installed.

I wanted to have two operating systems but now i just have ubuntu.

Is there anyway to fix this?  here are some pics...

[http://img18.imageshack.us/img18/9494/dsc07108nh.jpg](http://img18.imageshack.us/img18/9494/dsc07108nh.jpg)
[http://img249.imageshack.us/img249/945/dsc07109f.jpg](http://img249.imageshack.us/img249/945/dsc07109f.jpg)
[http://img96.imageshack.us/img96/747/dsc07110d.jpg](http://img96.imageshack.us/img96/747/dsc07110d.jpg)

What you've done there is install Grub (the bootloader) to your internal drive. You needed to install it to your external.

You'll can [reinstall Grub]("https://help.ubuntu.com/community/Grub2#Reinstalling GRUB 2") to fix this.

---

### Post by Alqamar on 2011-03-26
I finally installed Ubuntu. Thanks all for your kind help.

---

### Post by Rubi1200 on 2011-03-26
Excellent!!! Really glad you got it sorted out.

Enjoy :D

---


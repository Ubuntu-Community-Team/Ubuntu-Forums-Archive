---
title: "Windows\Linux Rig project questions."
date: 2010-12-22
forum: New to Ubuntu
---

### Post by CP2 on 2010-12-22
Hey all. I am thinking about building a Linux\Windows rig. My main focus is to build a project linux box so I can get more versed in working things from the linux side. But I also want to run windows secondary for games. Should I dual boot or should I run each OS separately with removable hard drives?  Does anyone have any suggestions on hardware and some technical aspects? I know how to build computers and I know how to run windows. I only know a bit out running Linux. I took college classes and did some work on the Linux side for about 2 years. But as far as compatibility issues I know I can look at the list on this site for that.

Any help would be much appreciated. 

Also, how is using an SSD for the windows side possible with a rig like this? Dumb question?

CP

---

### Post by dixonstalbert on 2010-12-22
if you have a newer system and 4 gigs of ram, I would suggest running linux in a virtualbox (virtualbox.org) inside of your windows install.

This way you can switch back and forth instantly instead of re-booting and you do not have to worry about corrupting partitions, boot sectors and other mishaps with dual booting.

---

### Post by chubble10 on 2010-12-22
Hardware wise, Ubuntu will run on pretty much everything that windows will, but faster. OS wise, easier to install Windows first and then add Ubuntu with dual-boot. You can also download all the drivers for the graphics card that you want to get for windows games and then enable the fancy graphics effects in ubuntu too!

---

### Post by amjjawad on 2010-12-22
> **CP2 said:**
> Should I dual boot or should I run each OS separately with removable hard drives?

It's your call. Ubuntu can be installed on USB Drives.

If you need more info about Ubuntu and Dual Booting, please check my signature.

All the best!

---

### Post by natravis on 2010-12-22
You can definitely dual boot. There are plenty of guides out there about how to accomplish this. If you are unsure of Linux, you could use a VM solution within windows (like Virtualbox). Essentially you will install Windows, throw in boot CD/USB, partition drive, install Linux. I do believe there are other things you need to consider when using SSDs, but I'm not aware of what those are as I do not have an SSD.

Using an SSD with Windows 7 should be no problem. I'm unsure of XP, but why would you be going back anyways? ;)

---

### Post by Kirboosy on 2010-12-22
Well it also depends on how much space you need too. If you only need 30 Gb for Ubuntu you can install Ubuntu via Wubi.exe rather than using Grub. Only limitation is you max out at 30 Gb.

The nice thing is if you decide you don't like Ubuntu (And I doubt you will not like it) is you can open up the control panel and simply uninstall Ubuntu from Windows like a normal application. :D

[http://www.ubuntu.com/desktop/get-ubuntu/windows-installer](http://www.ubuntu.com/desktop/get-ubuntu/windows-installer)


Virtualbox is also a good solution IF you have powerful hardware.

---

### Post by CP2 on 2010-12-22
Thanks for all the help guys. As of now I currently have an iMac and I dual boot windows XP as well. being that I already have XP i figured I go XP since I wouldn't use Windows Extensively enough to buy Windows 7. But I should also make that part of my "project" as well....the Window 7 thing. 

So, if I wanted to run a project multimedia server using Ubuntu, then would VMware be suitable enough? I ask this because I ran windows through vmware fusion on my Mac and when it came to games it didn't run right. I know gaming is  a different dimension when it comes to computers (IMO)

---

### Post by amjjawad on 2010-12-22
> **Caboose885 said:**
> Well it also depends on how much space you need too. If you only need 30 Gb for Ubuntu you can install Ubuntu via Wubi.exe rather than using Grub. Only limitation is you max out at 30 Gb.

The nice thing is if you decide you don't like Ubuntu (And I doubt you will not like it) is you can open up the control panel and simply uninstall Ubuntu from Windows like a normal application. :D

[http://www.ubuntu.com/desktop/get-ubuntu/windows-installer](http://www.ubuntu.com/desktop/get-ubuntu/windows-installer)



I installed Ubuntu 10.04 on 4.0GB USB-Drive and I still have 1GB Free Space.

Wubi is not real installation. You'll run it inside Windows. Lots of problems with Wubi that I don't recommend. Dual-Booting is the simplest thing that anyone could do.

---

### Post by chubble10 on 2010-12-22
Also, if you decide to use USB to run ubuntu, you should also make sure that you use a fast stick or even a portable hard drive, as otherwise it will run very slow due to the data transfer speeds.
Also, I wouldn't recommend running windows in virtual ox/vmware for games, as you are going to run out of power (as you are running 2 OSs at once) and you will get lower frame rates due to that.

---

### Post by CP2 on 2010-12-22
> **chubble10 said:**
> Also, if you decide to use USB to run ubuntu, you should also make sure that you use a fast stick or even a portable hard drive, as otherwise it will run very slow due to the data transfer speeds.
Also, I wouldn't recommend running windows in virtual ox/vmware for games, as you are going to run out of power (as you are running 2 OSs at once) and you will get lower frame rates due to that.


Noted about the gaming portion. I ran into this problem before. So Yeah, i think dual booting is in my best interest.

---

### Post by Jerry N on 2010-12-22
I use removable drives because I experiment with a lot of different OS distributions.  My advice is to dual boot on a single drive and to partition the drive using gparted from the Ubuntu live CD or some other partitioning program like PartedMagic.  The first partition should be NTFS for Windows, the second EXT4 or whatever turns you on for Ubuntu, the third a swap partition for Ubuntu, and the fourth and biggest can be an NTFS partition for data.  Install Windows first, then Ubuntu.  Some folks like a separate home partition but I quit doing that a couple of years ago.  If you have a second drive, use it to back up the files on your primary drive.  

Jerry

---

### Post by CP2 on 2010-12-22
> **Jerry N said:**
> I use removable drives because I experiment with a lot of different OS distributions.  My advice is to dual boot on a single drive and to partition the drive using gparted from the Ubuntu live CD or some other partitioning program like PartedMagic.  The first partition should be NTFS for Windows, the second EXT4 or whatever turns you on for Ubuntu, the third a swap partition for Ubuntu, and the fourth and biggest can be an NTFS partition for data.  Install Windows first, then Ubuntu.  Some folks like a separate home partition but I quit doing that a couple of years ago.  If you have a second drive, use it to back up the files on your primary drive.  

Jerry

Do you have a partition layout that you go by? Like Part 1: 20% part 2: 20% part 3: 15% part 4: 45%  Something like that?

---

### Post by amjjawad on 2010-12-22
> **CP2 said:**
> Do you have a partition layout that you go by? Like Part 1: 20% part 2: 20% part 3: 15% part 4: 45%  Something like that?

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

I think it has everything you're looking for.

---

### Post by chubble10 on 2010-12-22
Essentially just install windows and then run the ubuntu installer from the live cd and let ubuntu install alongside windows and then it will automatically make all the necessary partitions for you.

---

### Post by amjjawad on 2010-12-22
> **chubble10 said:**
> Essentially just install windows and then run the ubuntu installer from the live cd and let ubuntu install alongside windows and then it will automatically make all the necessary partitions for you.

I'd recommend Manual Installation :)
I've never chosen otherwise!

---

### Post by ppv on 2010-12-22
Dual booting Ubuntu with Windows will be the only way that real Ubuntu experience will be seen. Others options are good but you may want to only use them if you just want to try Ubuntu. But if you have already done so and want Ubuntu installed then you could dual boot.

---

### Post by chubble10 on 2010-12-22
> **amjjawad said:**
> I'd recommend Manual Installation :)
I've never chosen otherwise!

I always go auto so that I can blame something if it all goes wrong :D And I can always edit the sizes later of I start funning out of space

---

### Post by Kirboosy on 2010-12-22
> **amjjawad said:**
> IWubi is not real installation. You'll run it inside Windows. Lots of problems with Wubi that I don't recommend. Dual-Booting is the simplest thing that anyone could do.


Wubi is a real installation its just not a GRUB installation. Some people don't want to commit to Ubuntu because they don't know if they will like it or understand it. So Wubi is really the safest to start. Then if they like it I always recommend real dual booting.

Grub is just a pain in the butt at times and to save them trouble (especially if I can't be there to help them) I recommend Wubi

---

### Post by amjjawad on 2010-12-22
> **Caboose885 said:**
> Wubi is a real installation its just not a GRUB installation. Some people don't want to commit to Ubuntu because they don't know if they will like it or understand it. So Wubi is really the safest to start. Then if they like it I always recommend real dual booting.

Grub is just a pain in the butt at times and to save them trouble (especially if I can't be there to help them) I recommend Wubi

I do respect your opinion but I tend to disagree.

Today, I wrote a guide to avoid using Wubi. I'm still waiting for the approval. For me, I think it's a personal opinion. Some may like it, some other may don't. I'm from those who never ever used Wubi and will never do :)

[http://en.wikipedia.org/wiki/Wubi_%28Ubuntu_installer%29](http://en.wikipedia.org/wiki/Wubi_%28Ubuntu_installer%29)
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by chubble10 on 2010-12-22
> **amjjawad said:**
> I do respect your opinion but I tend to disagree.

Today, I wrote a guide to avoid using Wubi. I'm still waiting for the approval. For me, I think it's a personal opinion. Some may like it, some other may don't. I'm from those who never ever used Wubi and will never do :)

[http://en.wikipedia.org/wiki/Wubi_%28Ubuntu_installer%29](http://en.wikipedia.org/wiki/Wubi_%28Ubuntu_installer%29)
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

Definitly agree there, I tried wubi briefly and found it was
 A) slow
 B) buggy
 C) annoying
So definatly avoid for me!

---

### Post by Jerry N on 2010-12-22
> **CP2 said:**
> Do you have a partition layout that you go by? Like Part 1: 20% part 2: 20% part 3: 15% part 4: 45%  Something like that?

The swap partition could be 2 to 4 gb.  Other than that, I do it differently every time.  20 to 50 gb is plenty for Ubuntu and 50 to 100 gb for Windows.  The rest for data.

I always partition manually.  The few times I tried WUBI it didn't work and I didn't care enough to fight with it.  I tried VM once (Windows 2000 inside Ubuntu) and while it worked fairly smoothly I felt that the performance loss was quite significant.  Others would argue but I don't see WUBI and VM as real Ubuntu installs.

Jerry

PS:  I am definitely **NOT** an expert on Linux but I do have extensive experience in electronics with Linux being a small subset of that experience.

---

### Post by amjjawad on 2010-12-22
> **chubble10 said:**
> Definitly agree there, I tried wubi briefly and found it was
 A) slow
 B) buggy
 C) annoying
So definatly avoid for me!

Wubi (for me - this is my personal opinion) is trying to help users to user Ubuntu in Windows-Way. Linux is not Windows, period. If I want to try something different, I won't do that in any Windows-Way. Having that said, I would at least create a LiveCD/USB and try Ubuntu, perhaps install it and have fun but will not do it with Wubi.

I also believe in something else. I believe that each program must be run under its native environment. I use Windows to run Office and Photoshop despite there's Wine. That's my opinion.

Anyway, good luck everyone :)

---

### Post by CP2 on 2010-12-22
Wow, this is definitely some good info all. This seems like the first online community that actually responds fast and with serious answers. Period. On other subject matters in other help forums I haven't gotten this much of a response ever. And without all the name calling. Good job guys.

---

### Post by Kirboosy on 2010-12-22
We might disagree on Window Managers and different install methods but we all agree that Ubuntu is awesome. :D

Since everyone on here uses Ubuntu we don't namecall because they were smart enough to get away from the tyranny of Windows ;)

---

### Post by amjjawad on 2010-12-22
> **Caboose885 said:**
> We might disagree on Window Managers and different install methods but we all agree that **Ubuntu is awesome**. :D

AMEN to that :D

> Since everyone on here uses Ubuntu we can't namecall because they were smart enough to get away from the tyranny of Windows ;)That wasn't name calling, that was a discussion or debate :D

Linux For Human Beings ;)

---

### Post by Kirboosy on 2010-12-22
> **amjjawad said:**
> Today, I wrote a guide to avoid using Wubi. I'm still waiting for the approval. For me, I think it's a personal opinion. Some may like it, some other may don't. I'm from those who never ever used Wubi and will never do :)

Let me know when this guide is approved.

I have never used Wubi on my own machines but when introducing Ubuntu to friends I just install Wubi. Only one time I haven't gone back and regular installed it. I've installed it like 25 times and only one friend didn't make the switch and removed Ubuntu...needless to say I'm still constantly fixing their Windows....

---

### Post by BbUiDgZ on 2010-12-22
I dual boot windows 7 and ubuntu 10.04
my windows partition should just be called fallout3 and Football manager as thats all I use it for.

---

### Post by amjjawad on 2010-12-22
> **Caboose885 said:**
> Let me know when this guide is approved.

Sure thing. You'll find it in my signature once it's approved ;)

> 
I have never used Wubi on my own machines but when introducing Ubuntu to friends I just install Wubi. Only one time I haven't gone back and regular installed it. I've installed it like 25 times and only one friend didn't make the switch and removed Ubuntu...needless to say I'm still constantly fixing their Windows....

I'm not going to waste time to convert people to Linux :D if they don't want to move, it's their loss. I always tell people about Linux and how good it's but they keep using what they were using from day 1. Up to them :)
On the time being, I'm investing (not going to say wasting because it's not a waste) my whole time in learning Linux. I installed 8 Distributions on my PC and willing to install more. I'm learning so fast because I'm spending perhaps all the time here or in writing guides, trying new stuff, etc.

Linux has changed my life. Seriously. I just don't understand how? I'm talking about real-life :)

I feel sorry for Microsoft. Windows is not bad but definitely not as good as Linux.
As for games, I saved my time and bought PS2. Funny thing is, I stopped playing the day I installed Ubuntu on my PC and that was in Sept or August this year, can't remember when :)

Sorry to the OP. I know this is way off-topic but I just can't help it :)

---

### Post by CP2 on 2010-12-22
> **amjjawad said:**
> Sure thing. You'll find it in my signature once it's approved ;)



I'm not going to waste time to convert people to Linux :D if they don't want to move, it's their loss. I always tell people about Linux and how good it's but they keep using what they were using from day 1. Up to them :)
On the time being, I'm investing (not going to say wasting because it's not a waste) my whole time in learning Linux. I installed 8 Distributions on my PC and willing to install more. I'm learning so fast because I'm spending perhaps all the time here or in writing guides, trying new stuff, etc.

Linux has changed my life. Seriously. I just don't understand how? I'm talking about real-life :)

I feel sorry for Microsoft. Windows is not bad but definitely not as good as Linux.
As for games, I saved my time and bought PS2. Funny thing is, I stopped playing the day I installed Ubuntu on my PC and that was in Sept or August this year, can't remember when :)

Sorry to the OP. I know this is way off-topic but I just can't help it :)

No worries on that man. I like to hear everyone's take on Linux.  It spells freedom. Especially when you know what you are doing. I'd like to totally convert to Linux but i have one problem. I use Logic pro for my music productions. Other than that I think I'd be ok to make the switch totally. 

With Linux I can:
Manage my ipod
Watch movies
stream movies to my PS3
Use the open office
maintain a multimedia server
Totally customize my desktop
Do specifically tailored backups
Play games (but, i think for a while I still may use windows in dual boot. I love Aion)
Surf the web
Tinker away without totally screwing myself....i think. 
and more.

---

### Post by amjjawad on 2010-12-22
> **CP2 said:**
> No worries on that man. I like to hear everyone's take on Linux.  It spells freedom. Especially when you know what you are doing. I'd like to totally convert to Linux but i have one problem. **I use Logic pro for my music productions**. Other than that I think I'd be ok to make the switch totally. 


Thank you and I always do that :) I mean, trying to find out what others think.

For that problem, you can always Dual-Boot UNLESS you can find the equivalent software.
For me, as I mentioned, I prefer for example to use Photoshop on Windows; that's why I keep Windows XP on an old IDE HDD for these stuff. It's better to run everything on its native environment.

Most likely, you'll find a clone or an equivalent software to Logic Pro. It's a matter then if you'll like the new choice or not? of course only you who will decide that :)

I used to work on Sound Forge a lot in the past. At the moment, I don't have time for all this.

Try to search on google or this forum, hopefully you could find something like Logic Pro :)
If not, again, you could always Dual-Boot. Come on, Windows XP is not that bad ;)

---

### Post by CP2 on 2010-12-22
> **amjjawad said:**
> Thank you and I always do that :) I mean, trying to find out what others think.

For that problem, you can always Dual-Boot UNLESS you can find the equivalent software.
For me, as I mentioned, I prefer for example to use Photoshop on Windows; that's why I keep Windows XP on an old IDE HDD for these stuff. It's better to run everything on its native environment.

Most likely, you'll find a clone or an equivalent software to Logic Pro. It's a matter then if you'll like the new choice or not? of course only you who will decide that :)

I used to work on Sound Forge a lot in the past. At the moment, I don't have time for all this.

Try to search on google or this forum, hopefully you could find something like Logic Pro :)
If not, again, you could always Dual-Boot. Come on, Windows XP is not that bad ;)

There was another guy on a thread saying that he LOVED LMMS. Of course I never tried it, but I doubt it would work with my audio interface. I have an apogee Duet. I'll have to do some research and see if there are any mods to help.

---

### Post by amjjawad on 2010-12-22
> **CP2 said:**
> There was another guy on a thread saying that he LOVED LMMS. Of course I never tried it, but I doubt it would work with my audio interface. I have an apogee Duet. I'll have to do some research and see if there are any mods to help.

I'm really sorry mate because I can't be so much help but I'm sure you'll find what you're looking for. As I mentioned, if you won't, Dual-Boot is not bad idea at all. Don't install too much stuff, if you really want my advice, go for Windows XP with only the applications you need.

If you need anything about Dual-Booting, check my guide and if you have any question, feel free to ask :)

---

### Post by 12apennachi on 2010-12-22
Kind-of off topic, but I am planning on running a bunch of different distros on an external hard drive that is 5400 rpm. Will it run slowly or will it be smooth enough?

---

### Post by ppv on 2010-12-22
> **12apennachi said:**
> Kind-of off topic, but I am planning on running a bunch of different distros on an external hard drive that is 5400 rpm. Will it run slowly or will it be smooth enough?

Once booted they are going to run in a manner as if they were the only ones installed. It may make a difference if you use a hard drive with a different rpm.

---

### Post by CP2 on 2010-12-22
> **ppv said:**
> Once booted they are going to run in a manner as if they were the only ones installed. It may make a difference if you use a hard drive with a different rpm.

Yeah, I was like huh?  5400 rpm??? Go 7200.  These days not pricey at all.

---

### Post by amjjawad on 2010-12-22
I have two IDE HDDs, one is 20GB and the other is 40GB. Both are 5400 rpm. I have no problems with them at all. I mean, I don't have problems with the speed.

---

### Post by Kirboosy on 2010-12-22
> **amjjawad said:**
> I have two IDE HDDs, one is 20GB and the other is 40GB. Both are 5400 rpm. I have no problems with them at all. I mean, I don't have problems with the speed.

Yeah but are you running them off the USB Bus? USB on older drives like that may be kind of slow....to start at least. Once it gets rolling it should be fine.

***Kind-of off topic, but I am planning on running a bunch of different  distros on an external hard drive that is 5400 rpm. Will it run slowly  or will it be smooth enough?***

Really what you could do is rip the enclosure off the drive and then install it like a normal drive. I did that to install a bigger HD in my Xbox original, but thats a different thread. ;)

---

### Post by amjjawad on 2010-12-22
> **Caboose885 said:**
> Yeah but are you running them off the USB Bus? USB on older drives like that may be kind of slow....to start at least. Once it gets rolling it should be fine.


I did that once. I installed Ubuntu on one of them while it was connected through USB to my PC. It was much faster than XP :D

---

### Post by mysteriousdarren on 2010-12-23
Well it would work better with 7200 rpm but 5400 will work. I am guessing you plan on partitioning each one many times to just try each distro? Well exactly how many? and is this for s&g? I would give you some distros to try if you wanted. I have tried almost all the major distros on distrowatch that fit normal archicture.

---

### Post by amjjawad on 2010-12-23
> **Caboose885 said:**
> Let me know when this guide is approved.

It's approved. Check my signature. The last link.

---


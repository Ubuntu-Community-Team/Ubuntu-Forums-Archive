---
title: "Installing Linux on a laptop with no operating system"
date: 2009-04-05
forum: New to Ubuntu
---

### Post by ARom on 2009-04-05
Hi,

I plan on purchasing a laptop with no Operating System to save myself $95 USD on Vista. 

This is a Sager (Clevo) notebook: [http://www.xoticpc.com/sager-np7680-built-clevo-m762tu-p-2412.html](http://www.xoticpc.com/sager-np7680-built-clevo-m762tu-p-2412.html)

I'm thinking I will burn Ubuntu 8.10 to a disc, and then try to get it up and running on the new laptop, how difficult will this be?

How easy will it be to get everything up and running given I probably won't have Windows anywhere near the laptop until perhaps Windows 7 (by everything I mean the drivers, touchpad, webcam) etc...? 

Thanks

---

### Post by lisati on 2009-04-05
I don't have any experience of freespire, so I can't help on that one.
As for the "2009" version of Ubuntu, I wonder what they're getting at with the offer: as far as I know the latest "official" release of Ubuntu is 2008 (version 8.10)

---

### Post by ARom on 2009-04-05
> **lisati said:**
> I don't have any experience of freespire, so I can't help on that one.
As for the "2009" version of Ubuntu, I wonder what they're getting at with the offer: as far as I know the latest "official" release of Ubuntu is 2008 (version 8.10)

Never mind with the eBay link, I think I need to create an installation disc of Ubuntu 8.10, this shouldn't be too hard should it? 

Just mount the files on a CD and access them from the laptop and install?

---

### Post by DarkReaper79 on 2009-04-05
You will need to download and burn a cd/dvd with the iso image.

---

### Post by ShaunG on 2009-04-05
Download the .iso. Burn that to a cd. Many good program out there for that. Pop the cd into your pc and boot from that then bob's your uncle and what not :)

[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

---

### Post by oldos2er on 2009-04-05
I'd be a little concerned about the wireless and built-in camera; you might want to do a little research first about whether they're supported under Linux.

---

### Post by ARom on 2009-04-05
> **oldos2er said:**
> I'd be a little concerned about the wireless and built-in camera; you might want to do a little research first about whether they're supported under Linux.

O.K, I'll ask the Seller & then the guys @ NBR about wireless and the built in camera.

Especially wireless.... but why does my wireless work fine on my current laptop with Vista Premium & Ubuntu 8.10, Ubuntu 8.10 recognized the wireless connection right away, is that because of Vista?

Without Vista, does that mean it will be harder to get wireless up and running in 8.10?

---

### Post by anewguy on 2009-04-05
Actually, Vista has nothing really to do with it.  It's a matter of what chipset is in the wireless adapter.  Unless you are using the same adapter, you will want to research what chipset is in the adapter.  At the vendor site for the laptop, does it have a Windows driver for the wireless?  If so, if worse comes to worse you should be able to get it running with ndiswrapper.

Another potential area of concern is the video.  What model/chipset is the video?  You should research this as well so you will know in advance if people have had any trouble with getting that chipset to work in Linux, and if a work-around was found.  Restricted drivers or such things as Envyng can be a good friend in this area.

Those are 2 things you definitely want to work before you even worrying about things like the webcam (I understand that it sounds important to you, but what good is a webcam if you can't get wireless working or you can't display things on your screen the way you'd like to).

The best place to start is always the manufacturers support site.  Look for wireless drivers and check on video drivers (the video drivers themselves won't be useable, but they can point to the chipset and therefore the Linux driver you'll need).  Be sure to look for a specifications page to see if it lists the detail of which wireless and which video came in the computer.

Dave :)

---

### Post by ARom on 2009-04-05
> **anewguy said:**
> Actually, Vista has nothing really to do with it.  It's a matter of what chipset is in the wireless adapter.  Unless you are using the same adapter, you will want to research what chipset is in the adapter.  At the vendor site for the laptop, does it have a Windows driver for the wireless?  If so, if worse comes to worse you should be able to get it running with ndiswrapper.

Another potential area of concern is the video.  What model/chipset is the video?  You should research this as well so you will know in advance if people have had any trouble with getting that chipset to work in Linux, and if a work-around was found.  Restricted drivers or such things as Envyng can be a good friend in this area.

Those are 2 things you definitely want to work before you even worrying about things like the webcam (I understand that it sounds important to you, but what good is a webcam if you can't get wireless working or you can't display things on your screen the way you'd like to).

The best place to start is always the manufacturers support site.  Look for wireless drivers and check on video drivers (the video drivers themselves won't be useable, but they can point to the chipset and therefore the Linux driver you'll need).  Be sure to look for a specifications page to see if it lists the detail of which wireless and which video came in the computer.

Dave :)

O.K great, thanks guys/gals. 

Any other tips/suggestions are welcome.

---

### Post by ARom on 2009-04-05
I may just get a cheap copy of XP and do the Wubi thing, no?

---

### Post by ShaunG on 2009-04-05
> **ARom said:**
> I may just get a cheap copy of XP and do the Wubi thing, no?

Or a FREE copy of linux distro and try that :P

Worst case scenario, you gotta remove it and install xp in which case then you spend your money.

---

### Post by oldos2er on 2009-04-05
> **ARom said:**
> I may just get a cheap copy of XP and do the Wubi thing, no?
  
 No. I think the point's already been made, but try an Ubuntu LiveCD first. No reason to spend money on Win* unless you know for a certainty you need to.

---

### Post by ARom on 2009-04-05
lol, o.k, o.k sorry. :p

I'll stick with my plan to mount the image of 8.10 and struggle with that for a while. Hopefully I can get all of my hardware and drives working.

---

### Post by kevmitch on 2009-04-05
Looks like they've got Intel wireless chips which are supported in the kernel (i.e., out of the box with no effort on your part). The nvidia chip should also not be too much of a problem as there are both proprietary and open-source drivers. The webcam and the fingerprint reader would be the things that might take some work. I have 0 experience with webcams, but you might take a look at fprint of thinkfinger for the fingerprint reader.

---

### Post by ShaunG on 2009-04-05
Generally there is a way to get almost everything working and running on *nix. It may be easy as 3.14 or it may take years but after struggling to get things to work you'll wonder how you ever did without *nix. (Going on my experiences to date)

---

### Post by ARom on 2009-04-05
> **kevmitch said:**
> Looks like they've got Intel wireless chips which are supported in the kernel (i.e., out of the box with no effort on your part). The nvidia chip should also not be too much of a problem as there are both proprietary and open-source drivers. The webcam and the fingerprint reader would be the things that might take some work. I have 0 experience with webcams, but you might take a look at fprint of thinkfinger for the fingerprint reader.

Thanks for your help

> Generally there is a way to get almost everything working and running on *nix. It may be easy as 3.14 or it may take years but after struggling to get things to work you'll wonder how you ever did without *nix. (Going on my experiences to date)
I was reading on Notebook Review that it may stop working for strange reasons and recovery is not as good as Windows, I will be using this laptop most importantly for summer college correspondence courses, is this a significant problem? I would hate to lose my work and break something afterward... I'm also not a fan of constantly backing up every little thing.

Has Ubuntu ever crashed on you to the point where you cannot recover your files and had to re-install?

---

### Post by sanemanmad on 2009-04-05
> **ShaunG said:**
> Generally there is a way to get almost everything working and running on *nix. It may be easy as 3.14 or it may take years but after struggling to get things to work you'll wonder how you ever did without *nix. (Going on my experiences to date)
I 2nd that...

---

### Post by kevmitch on 2009-04-05
> **ARom said:**
> Thanks for your help

I was reading on Notebook Review that it may stop working for strange reasons and recovery is not as good as Windows, I will be using this laptop most importantly for summer college correspondence courses, is this a significant problem? I would hate to lose my work and break something afterward... I'm also not a fan of constantly backing up every little thing.

Has Ubuntu ever crashed on you to the point where you cannot recover your files and had to re-install?

You should make a habit of backing up regardless of what operating system you are using. You have to EXPECT that your hardisk will fail tomorrow because one day it WILL. They do have a finite lifetime.

That said, Linux has MUCH better backup facilities and it is much easier to automate. Take a look at  [sbackup]("http://www.debianadmin.com/backup-and-restore-your-ubuntu-system-using-sbackup.html") for example.

I believe that the "stop working for strange reasons" is referring to when upgrades don't go smoothly. In 6 years of using Linux I have experienced only once when an upgrade broke my system and I was using Debian unstable, which is well, less stable. Even then I was able to fix it to original condition with a live cd. I think it would be a very rare case where your system would ever be completely hosed and your data unrecoverable.

If you want to reserve the possibility to reinstall without loosing your data, you should consider creating a separate /home partition during the install process. This is a something that really should be standard for all operating systems. This allows you to completely erase your system but keep all your user-level data intact. You can even use the same home directory for different Linux distributions so you can try out a few and keep the same data between them.

---

### Post by anewguy on 2009-04-05
Exactly.  I wasn't trying to frighten you away, just making you aware of some things that it helps to research a little up front so you have some idea of what you doing instead of jumping in with no clue and then feeling lost.

As far as school goes, just check with them to find out if anything that is reliant on Windows (and why) or on Internet Explorer.  Tell them you will be running Linux and just want to be sure there should be no problems.  I can't image there should be any problems, but better to check.

Good luck!

Dave :)

---

### Post by ShaunG on 2009-04-05
> **ARom said:**
> T
I was reading on Notebook Review that it may stop working for strange reasons and recovery is not as good as Windows, I will be using this laptop most importantly for summer college correspondence courses, is this a significant problem? I would hate to lose my work and break something afterward... I'm also not a fan of constantly backing up every little thing.

Has Ubuntu ever crashed on you to the point where you cannot recover your files and had to re-install?

You can try setting up home on a seperate partition (option available when installing ubuntu) and also having another seperate partition for your college work. That way if ubuntu goes bananas up and you need to re-install, you lose very little. You should also back up regularly.

The following is a great how to on backing up your system.
[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

---

### Post by ARom on 2009-04-05
Sounds good.

> As far as school goes, just check with them to find out if anything that is reliant on Windows (and why) or on Internet Explorer. Tell them you will be running Linux and just want to be sure there should be no problems. I can't image there should be any problems, but better to check.
I almost overlooked this, thanks for the reminder

---

### Post by GuitarRocker2562 on 2009-04-05
I would say that the only way you can break a linux system is if you tinker with system files and make a mistake, if you just use it as a windows user uses windows, it's very hard to mess up your system, linux people just tend to be more cautious with their data which is why everyone is telling you to make backups. I would say Ubuntu is less likely to fail then windows.

---

### Post by ARom on 2009-04-07
> **ShaunG said:**
> Or a FREE copy of linux distro and try that :P

Worst case scenario, you gotta remove it and install xp in which case then you spend your money.

I think I may need a cheap copy of Winddows for Microsoft Money :(

Unless I can't get Microsoft Money in Linux :)

---

### Post by ShaunG on 2009-04-07
Try this:

[http://www.gnucash.org/](http://www.gnucash.org/)

---

### Post by ShaunG on 2009-04-07
And this thread

[http://ubuntuforums.org/showthread.php?t=435901](http://ubuntuforums.org/showthread.php?t=435901)

---

### Post by DracoJesi on 2009-04-07
> **ARom said:**
> Never mind with the eBay link, I think I need to create an installation disc of Ubuntu 8.10, this shouldn't be too hard should it? 

Just mount the files on a CD and access them from the laptop and install?

mount the files to the disk? you mean burn don't you?

I downloaded the .iso in a little under an hour and a half, burned it on a disk in 4-5 minutes, and installed it on my Sony Vaio, in 8-10 minutes, the only problem I had was with my built in wireless, but that was only a matter of having the right driver, it was easily fixed, it's been a week and as far as I can tell, there's no other compatibility issues...

and the only prior Linux experience I've had has been with an old distribution of Mandrake  7.2, I can use it comfortably but am in no way an expert,

---

### Post by Yed Ied on 2009-04-07
I just did this, this morning, an a brand new Toshiba Satellite L355, with Vista, and everything worked just fine, as that is what I'm sending this to you with.

Yed Ied

The best things in life............AREN'T THINGS.

---

### Post by lhb1142 on 2009-04-07
> **ARom said:**
> Hi,

I plan on purchasing a laptop with no Operating System to save myself $95 USD on Vista. 

This is a Sager (Clevo) notebook: [http://www.xoticpc.com/sager-np7680-built-clevo-m762tu-p-2412.html](http://www.xoticpc.com/sager-np7680-built-clevo-m762tu-p-2412.html)

I'm thinking I will burn Ubuntu 8.10 to a disc, and then try to get it up and running on the new laptop, how difficult will this be?

How easy will it be to get everything up and running given I probably won't have Windows anywhere near the laptop until perhaps Windows 7 (by everything I mean the drivers, touchpad, webcam) etc...? 

Thanks

:KS It looks like a really nice computer. If I were buying it and planned to install Ubuntu, the first thing I would do is to telephone the company and ask if anyone there has any experience with using Ubuntu and if they have actually tried it on this computer. If the answer is positive in both cases, then you are good to go.

If they seem clueless, you may want to do some research on the web (the forums of course but don't forget Google!). And if they are themselves unable to help you, you may wish to reconsider buying this particular computer in favor of waiting for a "sale" on a Windows computer. I did that last year and I got two Acer Extensa 5620-6419 computers (two different "sales" a month apart at Office Depot) for $499.00 each. I "wiped" Windows off the computers and installed Ubuntu 8.04 (the latest version at the time - now I'm running 8.10).

But hopefully this company will have people who actually know about their product and will be able to reassure you that the computer will function properly and completely with a Ubuntu installation. Certainly if they are selling it without an operating system installed, it must be able to handle anything you can throw at it! At least that's what I would think.

They will also probably be able to recommend certain options to you to make the Ubuntu OS operate to best advantage.

I wish you the very best of luck.

Lawrence ):P

---


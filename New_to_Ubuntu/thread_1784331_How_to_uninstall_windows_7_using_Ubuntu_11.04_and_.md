---
title: "How to uninstall windows 7 using Ubuntu 11.04 and speed up my netbook"
date: 2011-06-16
forum: New to Ubuntu
---

### Post by mem101296 on 2011-06-16
I have an Acer Aspire One D255 and its been going slow. I'm guessing its because of Windows but I'm not sure. Could anyone help me find out why its going slow and how to uninstall windows 7? I'm 14 so could you please try not to confuse me but I do know a lot about computers and Linux Ubuntu.

---

### Post by mister_playboy on 2011-06-16
If you want help with Windows... then you should go to a Windows forum. ;)

I recommend you investigate that before deciding whether you want to install Ubuntu and whether you want to dual-boot or be Linux only.

---

### Post by mem101296 on 2011-06-16
I don't want windows and don't care about windows. I want to get rid of it and speed up my computer. Do you know how to help?

---

### Post by LowSky on 2011-06-16
> **mister_playboy said:**
> If you want help with Windows... then you should go to a Windows forum. ;)

I recommend you investigate that before deciding whether you want to install Ubuntu and whether you want to dual-boot or be Linux only.

Wow... don't be that uncool.

First things first. If you want to install Ubuntu, just go over to Ubuntu.com, go to the download page and do some light reading about installing from a usb drive, as your PC has no CD-ROM drive.

Before you install Ubuntu try it out using the Live option, back up all your data to a flash drive or some other media. We are not responsible for your Data! I really hope this is your PC and not the family's. Many kids now and forever do experiments using things that don't quite belong to them and parents get angry fast. If you need to reinstall Windows make sure you have the media to do so. There is no going back.

Next install Ubuntu make sure your computer can boot a USB drive, some need a special keyboard command, other just do it. if the machine just boots into Windows, reboot again, check out the screen on startup for a line that say something like boot order press F-something-or-other, maybe delete or escape.

then during the install choose full disk if you only want Ubuntu... and go from there. You have the option to install side by side as well if you want to keep Windows. Once its gone its gone... have a backup disk if you ever want to reinstall.

If you already have Ubuntu installed and just want to get rid of Windows, its simple... install gparted, then open it, find the windows partitions (usually 2 of them with Windows 7), usually FAT32 or NTFS file format.

Then open a terminal type

sudo update-grub

things should work fine from there.


remember to please check with your parents. far too often kids jump into things and they bite off more than they can chew. Remember you will loose the ability to do many things in Ubuntu that may have been very important without knowing it in Windows. try running the liveCD/USB for a week or so. go to all your websites, and try out libreoffice and see if it lives up to the standard that MS Office created, for many users it doesn't. Make sure your printer works, test your mp3 player - ipods are tricky.


I recently had my sister come to me with her PC and it was a mess. I installed Ubuntu with her permission and to her annoyance her camera doesn't connect as it did in Windows. She dismissed Ubuntu for that reason alone.

---

### Post by mem101296 on 2011-06-16
Sorry. The problem is that I've already installed Ubuntu and have had it for a while (since 10.04). I like it better than windows and believe windows is slowing down my computer since its almost has as much memory as vista. Do you know how to uninstall Windows 7? Thats what I'm trying to get at.

---

### Post by mem101296 on 2011-06-16
I just read the whole message. Since I'm new to this I cant delete my post. But thanks

---

### Post by mem101296 on 2011-06-16
And don't worrie about me screwing up Ubuntu. My Dad got it for me, but i know more about it than anyone in my family. I'm the computer/computer fixer in the house.

---

### Post by mister_playboy on 2011-06-16
> **mem101296 said:**
> Sorry. The problem is that I've already installed Ubuntu and have had it for a while (since 10.04). I like it better than windows and believe windows is slowing down my computer since its almost has as much memory as vista. Do you know how to uninstall Windows 7? Thats what I'm trying to get at.

OK, your initial post was unclear.  Do you have Ubuntu installed on a separate partition or in Windows via Wubi?

---

### Post by mem101296 on 2011-06-16
Im sorry for the trouble. Its separate partition I checked

---

### Post by LowSky on 2011-06-16
just follow my post

---

### Post by mem101296 on 2011-06-16
Thanks for all your help and tolerance of me.

---

### Post by mister_playboy on 2011-06-16
> **LowSky said:**
> just follow my post

Your post doesn't seem to mention deleting the Windows partition and expanding the Ubuntu partition to fill the empty space.

Also, his stated purpose for removing Windows was to make the "computer faster" and that is not going to happen if he was already running Ubuntu on its own.

---

### Post by mem101296 on 2011-06-16
Im a bit confused now. Is there a certain way to uninstall windows successively so all the space is being used by Ubuntu?

---

### Post by mister_playboy on 2011-06-16
> **mem101296 said:**
> Im a bit confused now. Is there a certain way to uninstall windows successively so all the space is being used by Ubuntu?

There is, but I think I still feel I'm not sure what your goal is.

Removing Windows won't speed anything up because Windows and Ubuntu are separate... they have no effect on each other since only one is running at any time.  Removing Windows will free up hard drive space, but it isn't going to change how the computer runs.

Does the computer seem slow in just Windows, or in both Ubuntu and Windows?

---

### Post by mem101296 on 2011-06-16
In both of them. I don't use windows that one reason I want to get rid of it. But I mostly want to speed up my computer in both gaming and internet

---

### Post by nzjethro on 2011-06-16
> **mem101296 said:**
> In both of them. I don't use windows that one reason I want to get rid of it. But I mostly want to speed up my computer in both gaming and internet

Deleting Win 7 will be an easy matter of deleting that partition. There are programmes out there that can non-destructively merge unallocated space (i.e. what your Win partition will become) with your Ubuntu partition, but this won't make your computer run any faster, it'll just give you more HDD space. What are your system specs? Have you considered one of the "lightweight" Ubuntu versions? I used Xfce (essentially Xubuntu), and I find it fantastic, better than GNOME, and faster. Otherwise, if you run a less resource intensive distro (Puppy Linux or DSL) you may find your performance increasing.

---

### Post by mister_playboy on 2011-06-16
> **mem101296 said:**
> But I mostly want to speed up my computer in both gaming and internet

Removing Windows won't get you want you want, so I don't think you should do it. ;)

Adding more RAM to your netbook is what can make it seem faster, but I would need to know what exact computer you have before I can tell if this is possible.

Netbook's usually have slow processors and there is no way to change that, I'm afraid.

Like nzjethro said, using LXDE or XFCE instead of Gnome can help make Ubuntu seem faster.

---

### Post by mem101296 on 2011-06-16
Does any of the smaller Linux operating systems have the same interface as Ubuntu. I mean does any of them have the launcher bar on the side? What do you need to know about my net book?

---

### Post by mister_playboy on 2011-06-16
> **mem101296 said:**
> Does any of the smaller Linux operating systems have the same interface as Ubuntu. I mean does any of them have the launcher bar on the side? What do you need to know about my net book?

You can do a similar setup, moving the panel to side like it is in Unity... it won't look as pretty, but it will run faster.  That's the tradeoff you have to make.

I just need to know the name and model of your netbook... this information is often just below the screen or above the keyboard.  A company name and then some numbers/letters.

If we know the specification of your computer, then we can do a better job of picking a setup that will run well on it.

---

### Post by dFlyer on 2011-06-16
Removing windows 7 or Vista will not speed up your computer, it will only give you more hd space. Have you looked at adding more memory? Maybe getting a faster processor or using a lighter version of Ubuntu!

---

### Post by wildmanne39 on 2011-06-16
Hi, also you said for playing games, if you want to play windows games you might not be happy with out windows, you can not play just any windows game you want too on ubuntu or any linux distribution. You will need to check the games you want to play with the games you can play in wine. Also everyone is right is system is not going to be faster removing windows.

---

### Post by mem101296 on 2011-06-17
> **mister_playboy said:**
> You can do a similar setup, moving the panel to side like it is in Unity... it won't look as pretty, but it will run faster.  That's the tradeoff you have to make.

I just need to know the name and model of your netbook... this information is often just below the screen or above the keyboard.  A company name and then some numbers/letters.

If we know the specification of your computer, then we can do a better job of picking a setup that will run well on it.
Ok I got a Acer Aspire One D55

---

### Post by mem101296 on 2011-06-17
The game I like to play is called mine craft made for both Linux and Windows but goes better for me on Linux and is still not that great.

---

### Post by steve7777777 on 2011-06-17
> **mem101296 said:**
> Ok I got a Acer Aspire One D55

The D55 is a very decent Netbook. Ubuntu should run just fine. 

I would back up your home and etc directories to an external USB drive, then do a fresh install of Ubuntu 64. Start from scratch and ditch the Windows if you can get by 100% without it. One thing - 2GB of Ram will make a difference if you only have 1GB installed.

---

### Post by mem101296 on 2011-06-17
Thanks but I got 32 bit on my flash drive is that just as good?

---

### Post by One Eye Lucky on 2012-04-18
> **LowSky said:**
> Wow... don't be that uncool.

You're The Man. Thanks for the lengthy and detailed answer, it really helped more than intended. :-)

---

### Post by howefield on 2012-04-18
Old thread closed.

---


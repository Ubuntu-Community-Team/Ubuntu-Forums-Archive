---
title: "Completely new to Ubuntu, but willing to try it. Need help."
date: 2009-01-18
forum: New to Ubuntu
---

### Post by Cherick on 2009-01-18
First of all, I just started searching for info on Ubuntu, so I'm just starting from zero here.
I'm curious about this OS and I'm willing to try it, but I don't know all the steps that I need to take. So I'm gonna try to describe my scenario as good as possible and see if I can get some help here. Thanks in advance.


I have a Dell XPS M140 laptop. Windows XP SP3 Media Center. The disk properties say it has 49.7GB total size. 504MB ram. 
So, I pretty much have copies of all my pics, documents, etc. on a desktop computer, because a few days ago I had to do the Dell PC restore thing because there's something wrong with the CPU overheating and I thought that would fix it, but didn't. The thing is that I started transferring stuff back to the laptop, but now that I'm thinking of trying Ubuntu, here are a few of my questions:

-I want to have both XP and Ubuntu. How do I do the partitions on the disk, if I already have Windows XP on it and I DONT have an XP boot CD since this Dell uses the PC Restore utility. Should I Restore it again and then do partitions? That way I have a "fresh" XP. 

-So basically I want an XP partition, an Ubuntu, and a shared one for all my programs to use with both OSs, is that possible?

-Can the desktop be customized with themes, fonts, etc. in Ubuntu?

-What if I don't like it, how do I go to uninstall and put it all back up the way it was, without the disk partitions, etc. I know I can try it first, but I mean, if I installed and later I decide to uninstall it.

I may have some more questions, but these can get me started. Thanks in advance for the help.

---

### Post by Montblanc_Kupo on 2009-01-18
> **Cherick said:**
> 
-I want to have both XP and Ubuntu. How do I do the partitions on the disk, if I already have Windows XP on it and I DONT have an XP boot CD since this Dell uses the PC Restore utility. Should I Restore it again and then do partitions? That way I have a "fresh" XP. 

Restore disks are so freakin' stupid. sigh. I remember when they HAD to provide a way to just install the OS. Oh well. I can't say 100% on this because you never know with restore disks.. but I'm thinking if you use a ubuntu live cd to partition the drive into chunks... one chunk for windows... and another for linux... then use the system restore disks on the first chunk... it should work. But no guarantees. ymmv.

> -So basically I want an XP partition, an Ubuntu, and a shared one for all my programs to use with both OSs, is that possible?

This sounds like a recipe for disaster to Me... it might be theoretically possible... but windows doesn't like anything that isn't windows... will be a pain to even get it to read the linux file structure (although linux won't have any issue reading ntfs really)... and I'm thinking it would be really easy for it to mess up and corrupt things.

> -Can the desktop be customized with themes, fonts, etc. in Ubuntu?

More than your wildest dreams. Each distro comes with it's own windows manager... or you can replace most of them with compiz fusion and emerald if you like... which has tons of customizations and themes. Icon sets and windows themes are a drag and drop away. It's groovy baby... groovy. hehe

> -What if I don't like it, how do I go to uninstall and put it all back up the way it was, without the disk partitions, etc. I know I can try it first, but I mean, if I installed and later I decide to uninstall it.

Well... you can always try the live cd first... play with it a bunch and install later without any risk to your hard drive install. If you want to remove it later... just use the Live CD to repartition the drive so that it's one big chunk of unpartitioned space and reinstall windows back into it.

---

### Post by MockY on 2009-01-18
You could give Wubi a shot. That way you can try Ubuntu out without having to do any partitioning and it is easily removed if it comes to that.

[http://wubi-installer.org/](http://wubi-installer.org/)

---

### Post by talsemgeest on 2009-01-18
> **Cherick said:**
> -Can the desktop be customized with themes, fonts, etc. in Ubuntu?
You have no idea. You can customize ubuntu to look like absolutely anything you want! Make it a Mac OS/X clone, Vista clone, Xp clone, or anything out of your imagination. One of the best resource sites for changing the look of ubuntu is [gnome look](http://gnome-look.org).

---

### Post by Leo Dragonheart on 2009-01-18
Thats the way I would go just duel boot till you decide if you like it or not. I was going to do the partitioning thing but it took so long that I just wiped the drive and installed Ubuntu...I did save all my folders I wanted to keep to a second drive first, then just transfered them when it was done...Instilation took 15 minutes from disk insertion to being back online...

Try duel booting first to see if you like Ubuntu...

---

### Post by talsemgeest on 2009-01-18
Try installing Ubuntu using wubi first. Wubi installs ubuntu onto a file on your windows drive, so there is no partitioning necessary.

---

### Post by glennlad on 2009-01-18
> **talsemgeest said:**
> You have no idea. You can customize ubuntu to look like absolutely anything you want! Make it a Mac OS/X clone, Vista clone, Xp clone, or anything out of your imagination. One of the best resource sites for changing the look of ubuntu is [gnome look](http://gnome-look.org).

really? wicked =)

---

### Post by talsemgeest on 2009-01-18
Yep, it really is very cool. Just take a look at this months [screenshot thread](http://ubuntuforums.org/showthread.php?t=1027196) and see the kind of things people have done with their desktop.

---

### Post by Sef on 2009-01-18
> First of all, I just started searching for info on Ubuntu, so I'm just starting from zero here.
I'm curious about this OS and I'm willing to try it, but I don't know all the steps that I need to take. So I'm gonna try to describe my scenario as good as possible and see if I can get some help here. Thanks in advance.Please ask any question.


> I have a Dell XPS M140 laptop. Windows XP SP3 Media Center. The disk properties say it has 49.7GB total size. 504MB ram. 
So, I pretty much have copies of all my pics, documents, etc. on a desktop computer, because a few days ago I had to do the Dell PC restore thing because there's something wrong with the CPU overheating and I thought that would fix it, but didn't. The thing is that I started transferring stuff back to the laptop, but now that I'm thinking of trying Ubuntu, here are a few of my questions:Your specs are fine.

> -I want to have both XP and Ubuntu. How do I do the partitions on the disk, if I already have Windows XP on it and I DONT have an XP boot CD since this Dell uses the PC Restore utility. Should I Restore it again and then do partitions? That way I have a "fresh" XP. Read [Psychocats]("http://psychocats.net/ubuntu").  No, you don't have to restore XP.

> -So basically I want an XP partition, an Ubuntu, and a shared one for all my programs to use with both OSs, is that possible?Yes, it is.  Psychocats explains how to do that.

> -Can the desktop be customized with themes, fonts, etc. in Ubuntu?

Yes.

> -What if I don't like it, how do I go to uninstall and put it all back up the way it was, without the disk partitions, etc. I know I can try it first, but I mean, if I installed and later I decide to uninstall it.I'd have to research that question to give you good advice.

> I may have some more questions, but these can get me started. Thanks in advance for the help.Please ask any question that you have.

Download and burn the LIve CD, then run it for a while.   If there are any problems with the Live CD, then almost always they will occur upon install.

---

### Post by Cherick on 2009-01-18
Thanks for the replies!
I tried the live cd last night. I could not connect to the internet, I use wireless network. And also I want to use the files and programs I have already on my computer and I could not access "C:"

Also it asked me for a password when it was starting up, and gave me error messages about invalid username or password. I don't use password to get into Windows so I don't know why I was getting those messages.

---

### Post by talsemgeest on 2009-01-18
> **Cherick said:**
> Thanks for the replies!
I tried the live cd last night. I could not connect to the internet, I use wireless network. And also I want to use the files and programs I have already on my computer and I could not access "C:"

Also it asked me for a password when it was starting up, and gave me error messages about invalid username or password. I don't use password to get into Windows so I don't know why I was getting those messages.
Wireless networks can sometimes give a bit of trouble. Once you have installed ubuntu we can work through it and find the problem. As for trying to access "C:\", there is no "C" in ubuntu, just the one big file system where you might be able to access your old files. But don't forget that programs made for windows will not work without something like [wine.](http://www.winehq.org/)

---

### Post by kansasnoob on 2009-01-18
> **Cherick said:**
> First of all, I just started searching for info on Ubuntu, so I'm just starting from zero here.
I'm curious about this OS and I'm willing to try it, but I don't know all the steps that I need to take. So I'm gonna try to describe my scenario as good as possible and see if I can get some help here. Thanks in advance.


I have a Dell XPS M140 laptop. Windows XP SP3 Media Center. The disk properties say it has 49.7GB total size. 504MB ram. 
So, I pretty much have copies of all my pics, documents, etc. on a desktop computer, because a few days ago I had to do the Dell PC restore thing because there's something wrong with the CPU overheating and I thought that would fix it, but didn't. The thing is that I started transferring stuff back to the laptop, but now that I'm thinking of trying Ubuntu, here are a few of my questions:

-I want to have both XP and Ubuntu. How do I do the partitions on the disk, if I already have Windows XP on it and I DONT have an XP boot CD since this Dell uses the PC Restore utility. Should I Restore it again and then do partitions? That way I have a "fresh" XP. 

-So basically I want an XP partition, an Ubuntu, and a shared one for all my programs to use with both OSs, is that possible?

-Can the desktop be customized with themes, fonts, etc. in Ubuntu?

-What if I don't like it, how do I go to uninstall and put it all back up the way it was, without the disk partitions, etc. I know I can try it first, but I mean, if I installed and later I decide to uninstall it.

I may have some more questions, but these can get me started. Thanks in advance for the help.

First and foremost you need to troubleshoot this:

> because a few days ago I had to do the Dell PC restore thing because there's something wrong with the CPU overheating and I thought that would fix it, but didn't.

A new OS is not going to fix an overheating problem!

It could be "dust bunnies", a failing cpu fan, etc!

Installing software is labor intensive for a CPU so if you have a heat problem you need to troubleshoot that and fix it!!!!!!!!!!!!!!

---

### Post by snova on 2009-01-18
> **Cherick said:**
> -So basically I want an XP partition, an Ubuntu, and a shared one for all my programs to use with both OSs, is that possible?

Kinda. Windows programs will not run on Ubuntu, at least not natively. There is a program called Wine that can run most Windows programs, but it's not perfect.

> And also I want to use the files and programs I have already on my computer and I could not access "C:"

There are no "drives", the way you are used to. The system is very different...

But you should still be able to access your files. Look under the Places menu, Computer.

---

### Post by Cherick on 2009-01-20
Ok, I tried the Live CD first, then I wanted to try the Virtual Box and I couldn't even install it since it was painfully slow.
So now I'm trying Wubi. Installed it, but I still don't have my wireless internet. I need help. Can someone tell me what steps I need to take, or what commands do you need the outputs of, since I have seen that recommendation in some other threads. If I need to paste command outputs here please tell me how do I copy from Ubuntu and bring them with me to Windows so I can paste them here.

edit: oops. Just in case, my wireless card is Dell Wireless 1370 WLAN mini-PCI.

---


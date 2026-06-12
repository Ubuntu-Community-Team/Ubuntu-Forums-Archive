---
title: "Deleting Ubuntu"
date: 2009-01-09
forum: New to Ubuntu
---

### Post by beatrice on 2009-01-09
First, I don't even know if I used the right term. Deleting, uninstalling, formatting, getting rid of it... Pick one that suits you best. :P 
Second- sorry for my poor English.

So. I've been using Ubuntu for about 3 weeks and I really like it. I had quite a few problems and while trying to solve them, I typed all kind of things into terminal, installed different programs, changed many settings and so on... I was experimenting. Now I know exactly what to do and how to do it to make it work the way I want (or at least I think so) but Ubuntu is ruined by this point. The poor guy is reporting about a lot of errors, only wireless work, sometimes it won't shut down,etc. So, I want to uninstall/delete/remove it and install it again. 

Don't laugh if that seems stupid, I'm not familiar with computers.
And I'm a woman. It's a hell good excuse.

However, all I found on internet was how to remove it if you have it double-booted with Windows. Which I do not have and am not going to have. So, what should I do? Live CD? Live CD I used when installing Ubuntu? Gparted? Something else? 

P.S. I have Ubuntu 8.10

---

### Post by thegreenblob on 2009-01-09
If ubuntu is all you have on the machine right now and you just wanna remove it and install it again, the easiest way would be to run the live cd installer again and at the partitioning option choose "Guided - Use entire disk". Which will completely format the hard drive and install a fresh ubuntu on it.

---

### Post by Terl on 2009-01-09
Everyone does as you are doing!  I have reinstalled before as well.  It is part of learning.  All you have to do is put your Ubuntu disk in, start the pc, and install right over what you have.  It will reformat everything for you and you can start fresh.

---

### Post by qyot27 on 2009-01-09
If you use the Live CD there should be an option to format the drive and install fresh.  It's there on the page with the partitioning options, but it isn't the default.  Someone else that knows the actual terminology on the page will probably answer with the specifics, but it is there on the Live CD.

EDIT: Ok, it's already been answered.

---

### Post by beatrice on 2009-01-09
Seriously? It's THAT easy? I knew there was a reason I chose Ubuntu. :KS So that would erase everything I have on my coumputer now? There won't be any files left behind to take up disc space? It will be just as I would be installing it for the first time, when I got a brand new coumputer?

---

### Post by bailbath on 2009-01-09
Sounds like you need to reinstall with the Live cd. Do you have any files you don't want to lose? Put them on a usb pen drive to back them up first. Then use the live cd to start again then update straight after from the system-admin-update manager. Do what you want to get the install to how you like it then restore your files from the pendrive. I use Simple Backup to do a backup of the optimal setting of my system so I can always restore to that point. Simple backup is available from the package manager system-admin-synaptic do a search to find it within synaptic.
Ian

---

### Post by thegreenblob on 2009-01-09
> **beatrice said:**
> Seriously? It's THAT easy? I knew there was a reason I chose Ubuntu. :KS So that would erase everything I have on my coumputer now? There won't be any files left behind to take up disc space? It will be just as I would be installing it for the first time, when I got a brand new coumputer?

Yeah pretty much. :)

---

### Post by -grubby on 2009-01-09
You should back up your files (to a flash drive, CD, whatever) before you reinstall though.

---

### Post by mkvnmtr on 2009-01-09
Yes it's that easy. I have done it maybe 30 times when I messed up something. Later remember that you can probably fix anything you can messup but at first it is easier to reinstall. If you have only Ubuntu on your machine just do the same as when you installed the first time. If you are dual booting choose manual install and go back in the same partitions.

---

### Post by beatrice on 2009-01-09
Don't you worry about me, everything is backed up and waiting to be restored. :D So... Thanks to everyone, I'm quite shocked for I expected all kinds of codes, codes, strange geek words I do not understand, etc. :D I'll be back when something doesn't work :D And now it's time for me to bring my poor OS back to life. :KS
Thanks again. 
And... Happy New Year. Better later than never.

---

### Post by Dedoimedo on 2009-01-09
Hi there,
Actually, it's the same for any operating system :) You format or delete the partitions and old data is gone.
Dedoimedo

---

### Post by ajgreeny on 2009-01-09
If you haven't actually done it yet, and you want to reinstall all of the programs and updates you added to ubuntu without having to download them all again, perhaps because of download limits by your ISP, copy all the files in your */var/cache/apt/archives* folder as well as your home files, etc etc and all your updates and added apps will be available for you to use againby copying them back to the new */var/cache/apt/archives* folder with the sudo cp command, or even using the file browser nautilus as root ```
gksudo nautilus
```Be very careful using this last suggestion, as you can easily damage your system by moving, or removing system files that you should not touch.

---

### Post by beatrice on 2009-01-21
I know this might be a stupid question but still.... If you reinstall the operating system (is reinstall the right expression?), well, is it in any way bad for your computer? You know, like you're reinstalling for the forth time or so, will it work more slowly or anything like that? ;)

---

### Post by perlluver on 2009-01-21
> **beatrice said:**
> I know this might be a stupid question but still.... If you reinstall the operating system (is reinstall the right expression?), well, is it in any way bad for your computer? You know, like you're reinstalling for the forth time or so, will it work more slowly or anything like that? ;)

I have re-installed about 30 times, after all that time, my hard drive might be a little slower, but other than that, everything is still the same for me.

---


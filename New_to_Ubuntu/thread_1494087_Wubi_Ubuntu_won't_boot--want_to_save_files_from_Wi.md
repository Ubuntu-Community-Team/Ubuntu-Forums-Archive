---
title: "Wubi Ubuntu won't boot--want to save files from Windows"
date: 2010-05-26
forum: New to Ubuntu
---

### Post by ggriffis on 2010-05-26
My wubi installed ubuntu won't boot anymore but I'd like to save my  ubuntu files.  I heard that you could access ubuntu files from the  windows sector so I tried downloading and installing these programs: #   [http://www.chrysocome.net/explore2fs](http://www.chrysocome.net/explore2fs) #  [http://www.fs-driver.org/](http://www.fs-driver.org/)   However, after installing, I don't know how to access these programs in  order to find my files.  How do I access them?

---

### Post by bcbc on 2010-05-26
The easiest way (I know of) is to use an ubuntu live cd (install cd). Then you can loopmount the wubi virtual disks containing your data. The virtual disk you are interested in is c:\ubuntu\disks\root.disk

So you'd boot the cd, select 'try without any changs', then mount your windows partition that contains the ubuntu files. After that your partition is mounted under /media/xxxx (where xxxx is the label or uuid)

Then you can loopmount the wubi root.disk from terminal:```
sudo mount -o loop /media/xxxx/ubuntu/disks/root.disk /mnt
```

After that all your data files are under /mnt/home/userx and you can copy them to your windows partition under /media/xxxx

See this for more info (it also describes the above): [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

By the way, if you've got a 9.10 wubi install and haven't done so already, replace the wubildr file (it's a known bug that may have caused your wubi not to boot):[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

---

### Post by bodhi.zazen on 2010-05-26
> **ggriffis said:**
> My wubi installed ubuntu won't boot anymore but I'd like to save my  ubuntu files.  I heard that you could access ubuntu files from the  windows sector so I tried downloading and installing these programs: #   [http://www.chrysocome.net/explore2fs](http://www.chrysocome.net/explore2fs) #  [http://www.fs-driver.org/](http://www.fs-driver.org/)   However, after installing, I don't know how to access these programs in  order to find my files.  How do I access them?

use Ext2read :

[http://sourceforge.net/projects/ext2read/files/](http://sourceforge.net/projects/ext2read/files/)

Ir runs like "Explorer" , your files are in C:\ubuntu\disks\ 


[img]http://i.imgur.com/RCy0C.jpg[/img]

---

### Post by ggriffis on 2010-05-27
Thank you both so much!  In that case, maybe you could help me with trying to fix the original problem so that I won't have to reinstall Ubuntu.  Here's what happened--I installed Ubuntu via Wubi a few weeks ago.  Great, working fine.  Then I finally agreed with the pop-up to allow it to install the 60 or so updates it was suggesting.  Then next time I tried to boot into Ubuntu instead of Windows, it came up with a grub> prompt.  I googled that and found some instructions for trying to get it to boot to the "most recent kernel": [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2).  I followed the Wubi-specific instructions and typed in the following commands:

set root=(loop0)
(worked fine)

linux /vmlinuz root=/dev/sdXY loop =/ubuntu/disks/root.disk ro
(except I'm supposed to substitute something for sdXY and wasn't sure what--attached are files that are in that dev directory, thanks to you guys--can you help me figure out what file I should plug in there, if any will work?)  I tried a couple but kept getting "file not found"  Any help or insight would be appreciated.  I'd rather not have to reinstall Ubuntu because I had already configured a bunch of things to get my development environment working.  Again, thanks so much.  I'm amazed that their are people like you out there willing to look at someone else's problem and try to help out.

---

### Post by bodhi.zazen on 2010-05-27
Honestly, IMO, wubi is to take Ubuntu for a spin. If you like it I advise you back up yout data and perform a standard installation.

There are a few "tricky" issues with wubi, such as the loop mount, and it is easier to maintain a standard installation.

Alternately you can "convert" a wubi installation to a more standard installation, but that will take more effort then a fresh install.

With Linux, fresh installs are easy, and most people either make a separate /home or /data partition to store data.

---

### Post by bcbc on 2010-05-27
I'm going to have to agree with bodhi.zazen on this. I've run a few wubi installs on 10.04 and both have been broken by standard updates. With 9.10 it seemed more stable, except for the annoying wubildr bug.

Having said that, if you want to try and repair, these are your options.
First:
1. back up all the virtual disks in *x*:\ubuntu\disks\ to another folder (not under \ubuntu) 
2. uninstall and reinstall wubi
3. copy over the new virtual disks with your backups.
NOTE: this will only work if the problem is to do with the booting mechanism, not within the virtual disks themselves.

Second:
if you can mount your wubi, you can try chroot'ing into it and then running updates. If you want I can give you instructions.

But IMO, since you installed it only a few weeks ago, and you can recover your actual data, I'd say, just reinstall - and do it dual boot.

---

### Post by ggriffis on 2010-05-27
I'm a little confused.  I thought I already had it set up as a dual boot.

---

### Post by ggriffis on 2010-05-27
Also, if I take the route of backing up my virtual disks, uninstalling, and reinstalling ubuntu via Wubi, do I just copy the old disks over top of the newly created ones?  And will it have all the additional software I installed?  Sorry, I'm pretty new to all this.  Thanks.

---

### Post by bodhi.zazen on 2010-05-27
> **ggriffis said:**
> I'm a little confused.  I thought I already had it set up as a dual boot.

Yes, wubi is a dual boot, ie you boot either windows or ubuntu.

BUT wubi is not a "Standard" install of Ubuntu and it uses several "tricks" to install Ubuntu as if it were an application in Windows.

First it uses teh Windows boot loader to boot Ubuntu, not Grub.

Second with wubi you do not re partition your HD, rather you install ubuntu into a file within the windows partition which is then loop mounted.

So although you have a dual boot system, it is not a standard installation and, IMO, is more error prone and problematic then a standard install.

IMO, if you are going to use Ubuntu long term, remove wubi and install Ubuntu proper.

---

### Post by bcbc on 2010-05-27
> **ggriffis said:**
> Also, if I take the route of backing up my virtual disks, uninstalling, and reinstalling ubuntu via Wubi, do I just copy the old disks over top of the newly created ones?  And will it have all the additional software I installed?  Sorry, I'm pretty new to all this.  Thanks.

Yes - it will be identical, because the root.disk contains the entire file system that ubuntu is installed on including os files, applications, and your data. 

That's why I said, if the problems you are having are actually on your ubuntu installation itself, then doing the above won't help. Because we haven't really gotten to the bottom of why wubi isn't booting.

---

### Post by ggriffis on 2010-05-27
Thanks a MILLION to all who replied.  May you all be blessed a million times over.  The fix to the wubildr file outlined in one of the replies above fixed my issue and now I can boot into Ubuntu again:  [http://sourceforge.net/apps/mediawik...lems:Wubi_9.10]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10").

---

### Post by bcbc on 2010-05-27
> **ggriffis said:**
> Thanks a MILLION to all who replied.  May you all be blessed a million times over.  The fix to the wubildr file outlined in one of the replies above fixed my issue and now I can boot into Ubuntu again:  [http://sourceforge.net/apps/mediawik...lems:Wubi_9.10]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10").

Cool. Glad that's all sorted.

Remember to backup the root.disk file - that makes it easy to recover if you have problems. 

Consider not upgrading to 10.04 as I've had a bunch of problems with wubi 10.04 test installs. 
If you do upgrade, do NOT install grub2 anywhere (even though it suggests to install it everywhere if not sure). And if it gets in a loop during "Preparing memtest86+", then click on the details, you see 'found image linux 2.6.xxx' repeating. CTRL+C breaks this loop.

---


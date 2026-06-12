---
title: "Triple booting XP, 7, and Ubuntu?"
date: 2009-10-15
forum: New to Ubuntu
---

### Post by djm227 on 2009-10-15
I have never dual installed OSs before, let alone triple.  So some guidance would be greatly appreciated.

Right now I have an 80gb internal, which has XP on it.  I recently used Wubi to install Ubuntu, which I am running now.....but I love it so much I want to uninstall it in order to do a full install.

Basically what I am looking to do is leave XP on my 80gb.  Then I will order a 160gb, make two partitions of 80, and install Windows 7 and Ubuntu on that one.  I wasn't going to get 7, but students get it for only $30, so I couldn't pass that up.  I also have 500gb external and 300gb internal I use for storage, so that won't be a problem.

So is there anything I need to know before I do this, or is it pretty straight forward?  Some people were telling me to make sure to install Linux last....still not sure why that is.  Also, I love how Wubi lets me choose which OS to start at startup.  Will that be the same for the triple install?

Side question:  The student Windows 7 is labeled as "upgrade".  Yet on the download page it has links to how to install it from scratch.  Even though it is labeled as "Upgrade", can I still use it on a fresh hard drive?

Thanks for the help!

---

### Post by LewRockwell on 2009-10-15
do the appropriate back-ups/clones to protect your valuable data and then you can partition the 80GB for multi-partition/multi-boot...no need to buy yet another drive, especially since you can use your other drives for storage of back-ups and clones

-----------------------------

We've posted regarding partitioning many times previously, both here and other places as well

However, these might help a little:

[http://ubuntuforums.org/showthread.php?t=1222961](http://ubuntuforums.org/showthread.php?t=1222961)


[http://ubuntuforums.org/showthread.php?t=1252042](http://ubuntuforums.org/showthread.php?t=1252042)


[http://www.justlinux.com/forum/showthread.php?t=147959](http://www.justlinux.com/forum/showthread.php?t=147959)

-----------------------------

Then there are always these alternatives as well:

[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

.

---

### Post by Merk42 on 2009-10-15
If you're getting Windows 7 why even keep XP?
I've been using Windows 7 since beta and I haven't run into any problems.

---

### Post by LewRockwell on 2009-10-15
> **Merk42 said:**
> If you're getting Windows 7 why even keep XP?
I've been using Windows 7 since beta and I haven't run into any problems.

yes, a clone could be made of current XP operating system/partition/drive/etc. for safekeeping and then you could do whatever...

.

---

### Post by kayvortex on 2009-10-15
You'll want to install Ubuntu last because it will install the GRUB boot loader at the MBR (Master Boot Record), which will allow you to pick what OS to boot up. Windows, on the other hand, never checks to make sure you have another OS installed (haven't installed Windows 7 yet, but I doubt it'll be any different) and just boots straight into Windows. (So, for example, if you install Windows 7 last, when you start your computer it will just load Windows 7 straight away without even asking you if you want to boot something else.)

If your Win7 disk is for upgrade, this will destroy your XP install (I've never done a Windows upgrade, so somebody confirm this, please). So, unless you have an XP disk too, then you'll only have a dual-boot set-up. It *should* say somewhere that the win7 disc is *only* for upgrade (and it sounds like it is for only $30), so try to read up and find out.

If the Win7 disc is for upgrade only, and you really want to keep an XP installation, then you're going to need an XP install disc, or else I *think* you can make an image of the XP install and reinstall it on another partition (I'll need to check that for sure).

Let me know what you want to do (try for a triple-boot, or settle for a dual-boot), and I'll get back to you.

---

### Post by djm227 on 2009-10-15
> **kayvortex said:**
> You'll want to install Ubuntu last because it will install the GRUB boot loader at the MBR (Master Boot Record), which will allow you to pick what OS to boot up. Windows, on the other hand, never checks to make sure you have another OS installed (haven't installed Windows 7 yet, but I doubt it'll be any different) and just boots straight into Windows. (So, for example, if you install Windows 7 last, when you start your computer it will just load Windows 7 straight away without even asking you if you want to boot something else.)

If your Win7 disk is for upgrade, this will destroy your XP install (I've never done a Windows upgrade, so somebody confirm this, please). So, unless you have an XP disk too, then you'll only have a dual-boot set-up. It *should* say somewhere that the win7 disc is *only* for upgrade (and it sounds like it is for only $30), so try to read up and find out.

If the Win7 disc is for upgrade only, and you really want to keep an XP installation, then you're going to need an XP install disc, or else I *think* you can make an image of the XP install and reinstall it on another partition (I'll need to check that for sure).

Let me know what you want to do (try for a triple-boot, or settle for a dual-boot), and I'll get back to you.

I do have an XP disc, but I didn't really want to upgrade from XP to 7 because I have a lot of documents/music/etc on that hard drive that I don't have room for on my externals for back up.  Because of this, I was hoping I could just leave that hard drive and XP as is....but it's looking like I can't do that.  I've been trying to contact Microsoft to make sure the 7 is "upgrade only", but they're support page is awful....they don't even have a help option for 7 home edition yet.  Although I did make a post on their forums, so we'll see what kind of responses I get.

Another reason I would rather keep my installation then upgrade is because, although 7 is supposed to be different, I do not want to have the game/software/hardware incompatibility that so many of my friends did with vista.  Also, according to the website for students...the upgrade is only from Vista anyways...so I'm at a little bit of a loss.   They definitely make it sound like [on this page]("http://windows.microsoft.com/en-us/windows7/Installing-and-reinstalling-Windows") that the one disc does it all...but I don't want to take any chances.

---

### Post by Merk42 on 2009-10-15
> **djm227 said:**
> I do have an XP disc, but I didn't really want to upgrade from XP to 7 because I have a lot of documents/music/etc on that hard drive that I don't have room for on my externals for back up.  Because of this, I was hoping I could just leave that hard drive and XP as is....
Then do so and don't even worry about it being bootable.  
You'd still be able to access your documents music/etc from your old XP 80GB Drive in both Windows 7 and Ubuntu even if you can't actually boot into it.


> **djm227 said:**
> Another reason I would rather keep my installation then upgrade is because, although 7 is supposed to be different, I do not want to have the game/software/hardware incompatibility that so many of my friends did with vista.
I really doubt this will be a problem.  A lot of the hardware problems were because of the higher kernel number and have since been fixed.  The higher kernel number won't be a problem with 7 since it's listed as 6.1.  If you'd like to list what software you're running I'll try and check.

---

### Post by djm227 on 2009-10-15
Well windows support got back to me.  The only way I can install the 7 upgrade on my computer is to clean install from XP......I'll just have to find a way to make some room on my external or something for backups.

So I guess I'm gonna be doing a duel boot.  Thats alright though, if I ever need XP I still have the disc.

Thanks for the help everyone.

---

### Post by kayvortex on 2009-10-15
> Well windows support got back to me. The only way I can install the 7 upgrade on my computer is to clean install from XP......I'll just have to find a way to make some room on my external or something for backups.

So I guess I'm gonna be doing a duel boot. Thats alright though, if I ever need XP I still have the disc.

If you're going to buy another HD, then I think it's technically possible to clone your first HD over to the other one, and then do a clean Win7 install from it. I say, "I think", because I've never actually done it (I've never needed to); but it's not too difficult to clone a HD, and I don't expect Windows 7 or XP to be able to spot this and prevent it.
Basically, qualitatively, what you can do is this:
[LIST=1]
[*]Hook the second HD up to the motherboard.
[*]Put an Ubuntu LiveCD in, boot off it, and clone (i.e. completely copy) the first HD to the second one (a fairly simple operation in Linux thanks to dd). You should then have two identical copies of Windows XP.
[*]Detach the first HD, put your XP CD in and repair the MBR (again, not too hard a thing to do). Reboot your system. If your XP system boots up OK, then your cloned OS works fine. If not, then no harm: you can just detach the second HD, reattach the first one, and then upgrade XP to Windows 7 like you were planning to do as before.
[*]If your cloned XP OS boots OK, then simply do the Win7 upgrade on the cloned system.
[*]When the Win7 installation finishes, then simply attach the first HD back in again, and you now have your original XP system on the first one, and Win7 on the second. (DON'T attach the first HD until AFTER the Win7 install, otherwise you will have problems with drive letters: i.e. your Win7 installation will be on D: instead of C:, and this can cause problems when you install software).
[*]Finally, put the Ubuntu LiveCD in, boot off it, and install Ubuntu. Ubuntu will find your Windows installations and take care of all of the booting issues.
[/LIST]

Your data won't technically be at risk at any stage (unless you miss-type the dd command), but computers have a track record of screwing you over, so I'd still recommend doing a backup of your data. Even if Windows blows a fit and stops you from booting, you can still boot Linux and access and copy your files to an external HD and reinstall Windows, so you don't need to worry there.

It's up to you if you're comfortable with attaching hard drives, issuing Linux commands like dd, and installing and doing some minor repairing of OS's. There's lots of guides here, and on the internet about doing it, but it depends on how comfortable you are with it. If not, then dual-booting is not so difficult. Just make sure you know what partitions are, and how to do it. If you're not sure about anything, I'll be happy to answer any questions you have.

---

### Post by Mark Phelps on 2009-10-17
Unless you're in a real big hurry, suggest you wait on the Windows 7 "upgrade" because LapLink has announced that they're going to offer a version of their PC Mover software that WILL support an in-place upgrade to Windows 7 from XP.

---

### Post by Jose Catre-Vandis on 2009-10-17
If it helps, I have done just as you requested, but all on a single drive.

1. Partitioning:

/hda1     30GB (XP)
/hda2     30GB (7 - RC)
/hda3     30GB (Ubuntu)
/hda4    100GB (DATA)
/hda5      1GB (SWAP)

2. Installation

XP first
7 next
Ubuntu last

3. Notes

When you install 7, it places its boot loader files and information on the XP partition under C:\, so you then boot XP from the 7 bootloader. Once you install Ubuntu, you can only call the 7 bootloader from grub, and then select XP from there. (I belive there is a way round this, but have not bothered on my machine)

---

### Post by djm227 on 2009-10-17
I think that I'm going to end up just trashing XP once I get 7.  According to you guys, and the reviews, there's really nothing I need to worry about as far as compatibility goes.  Someone else made a good point.....XP is an 8 year old OS, and is COMPLETELY outdated. We had some good times, but it's time to let her go.  I fell like I was smart to wait until 7 and not get vista, but it's now time to get this old OS out of my machine.  Anyways,  I always have the disc if I absolutely need it.

When it all comes down to it, I want to start using Ubuntu as my main OS anyways.  So in my opinion, the less Microsoft in my machine the better.

---

### Post by jakejake678 on 2009-10-17
personally, if your keen on Windows XP and 7, and since not having ubuntu is out of the question :D, why dont you find yourself a windows 7 iso (legally obtained of course :)) and running a virtual machine? and also, Wubi is pretty close to a full install of Ubuntu, the only things that it doesnt add are small things you'll never notice, so... you should be fine...

---

### Post by djm227 on 2009-10-18
> **jakejake678 said:**
> personally, if your keen on Windows XP and 7, and since not having ubuntu is out of the question :D, why dont you find yourself a windows 7 iso (legally obtained of course :)) and running a virtual machine? and also, Wubi is pretty close to a full install of Ubuntu, the only things that it doesnt add are small things you'll never notice, so... you should be fine...

Honestly, Wubi has been pretty unstable for me.  I don't know what it is, because I have only been on it for a couple weeks, but it has frozen up at least 3 times to a point where I have not been able to undo it.  In fact, today it was so bad that I was forced to do a hard reboot....and now I can not even get Ubuntu to start.  I love the platform, but I'm hoping a full install will get rid of some of these problems.  It's not like I was stressing it to hard or anything...just basic stuff.

---


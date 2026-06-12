---
title: "Reinstate GRUB menu following Windows install"
date: 2009-08-21
forum: New to Ubuntu
---

### Post by SuaSwe on 2009-08-21
[COLOR="Red"]Edit: After having a look round I'm suddenly feeling a bit nervous over here. Would be eternally grateful to anyone willing to scroll down to post #4 and respond to my plea for help![/COLOR]

Just a very quick one: I know there is loads of info on this but I was hoping one of you genii could tip me off about the swiftest and smoothest way to do it.

In essence, my neighbour's dual-booting XP/Ubuntu and has just had to reinstall XP because it's fallen over (again), and of course the GRUB menu is now gone. So what would you guys say is the quickest, safest way of getting it back?

---

### Post by rbc on 2009-08-21
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by SuaSwe on 2009-08-21
Lucky, as my trusty laptop is refusing to make anything bootable for some reason.

---

### Post by SuaSwe on 2009-08-21
Having had a read-around, this is all looking a little bit more complicated than I had hoped.

If I outline here what I'm going to try with this computer - which after all is not mine! - it'd be brilliant if someone could tell me if it's likely to work or not.

The computer is a HP Pavillion (unsure of model number; it's a few years old) with two hard drives, one with XP and one with Ubuntu (Ubuntu was working when XP wasn't; now that XP's been reinstalled and is working fine GRUB obviously won't let us into Ubuntu anymore). I intend to follow the advice given [[COLOR="Blue"]here[/COLOR]]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows"), before the "Preserving Windows Bootloader" subsection.

So in a nutshell find the location with fdisk -l, mount into folder, reinstall GRUB, check menu.lst for obvious errors, reboot and hopefully be happy. Is there any reason to believe that this may not work, say because the PC uses two hard drives? 

Any help gratefully received!

---

### Post by SuaSwe on 2009-08-22
Anyone?

---

### Post by LewRockwell on 2009-08-22
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

the grub is always your friend and trusted companion

learn the grub

[http://art.ubuntuforums.org/showpost.php?p=7813498&postcount=9](http://art.ubuntuforums.org/showpost.php?p=7813498&postcount=9)

here are some links to grub info:

[http://ubuntuforums.org/showpost.php...67&postcount=2](http://ubuntuforums.org/showpost.php...67&postcount=2)

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

[http://en.wikipedia.org/wiki/GNU_GRUB](http://en.wikipedia.org/wiki/GNU_GRUB)


also, we would like to note that learning to edit the grub menu file is fun, rewarding, and educational

you'll learn not only how to effectively administer the grub menu but you might also have some fun adding famous quotations and notes to yourself and/or others/loved-ones

.

---

### Post by philinux on 2009-08-22
+1 for supergrub.

---

### Post by bacardiandwatermelon on 2009-08-22
> **rbc said:**
> [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Did this not work? This thread has saved my *** before :-)

Edit: *** I can't say ***?!?

---

### Post by SuaSwe on 2009-08-22
For some reason the Super Grub ISO's I've found have all failed to become bootable when burnt to disk. Also, the tutorial about making a bootable USB with Super Grub mentions that one should "copy-paste the boot folder" but there is none in the archive available for download on the website. :'(

Gonna try without Super Grub first and see what happens!

---

### Post by SuaSwe on 2009-08-22
OK, getting desperate now! I tried the advice given in the article I linked (basically mounting root and doing grub-install), to no avail. It didn't error so I expect the problem is that the PC is dual-booting from two separate hard drives instead of two partitions. 

I have burnt Super Grub in Ubuntu via Brasero and PowerISO in Windows; the Brasero product isn't bootable and the Windows one simply hangs on 'Loading stage2...' during boot. As mentioned previously, the bootable USB file available on Super Grub's website doesn't contain a "boot" folder when extracted, which apparently it should do.

My neighbour tried wiring up the hard drive in the opposite order (with Ubuntu as master) - with no result, Windows just kept going as usual - and once moved back, the Ubuntu drive isn't recognised at all! Ran my trusty LiveCD again and whereas before it was showing the Ubuntu partitions, it's now showing the Windows ones instead. *sweating* Could this have been a result of doing grub-install? I mounted the correct root partition (checked via ls -l) and installed as instructed; might that have somehow wiped the drive? 

What should I do, guys? Hang myself? :'(

---

### Post by bacardiandwatermelon on 2009-08-25
I suggest putting the drives back, Windows likes being the first drive.. I really have no experience with supergrub, but when you tried to rebuild grub from a live cd, did it give you any errors at all? Failing that you could always just backup your home folder, bite the bullet, and reinstall ubuntu?

---

### Post by pedro3005 on 2009-08-25
I don't know the answer but I know you should have no problem dual-booting from two HDs - I do it myself!

---


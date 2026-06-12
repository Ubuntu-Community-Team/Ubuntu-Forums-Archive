---
title: "Removing Ubuntu's disk partition WITHOUT Vista disks?"
date: 2009-04-10
forum: New to Ubuntu
---

### Post by Noise... on 2009-04-10
I'm looking at setting up a dual-boot with Vista and Ubuntu Studio. 

I posted here a couple weeks ago, and everyone said removal was easy, as long as I had the Vista boot disk. 

The problem is that I don't. Vista came preinstalled on my notebook, with no disks at all. 

Will I still be able to remove Ubuntu if it's not compatible with my computer, or if I just don't like it?

---

### Post by taurus on 2009-04-10
I suppose when you install Ubuntu, you also install GRUB to MBR so you can boot Ubuntu and windows.  So when you remove Ubuntu, GRUB won't be able to boot anymore because it will look for /boot/grub/menu.lst which is gone when you remove Ubuntu.  That's why people said you need a windows CD so you can boot from it and fix the MBR.  You can also use Super GRUB Disk too if you won't have a bootable windows CD.

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by Noise... on 2009-04-10
So, basically, If I would want to remove it I just download the Super Grub disk, burn it to a CD, and use that to repair it before uninstalling Ubuntu?

---

### Post by doas777 on 2009-04-10
is your problem that you can't run fixmbr without a vista disk?

you can get an equivalent to fixmbr with ms-sys. check out bodhi.zazen's adivce on this thread: [http://ubuntuforums.org/showthread.php?t=740221](http://ubuntuforums.org/showthread.php?t=740221) 

oh, BTW, ms-sys was removed from teh repos with hardy because it is a little unclean from an oss perspecfive. you can find it here: [http://ms-sys.sourceforge.net/#Download](http://ms-sys.sourceforge.net/#Download)

good luck,
franklin

---

### Post by AXeS on 2009-04-10
n0t to l0ng ag0,i had intrepid/xp dual b0ot (partitioned drive) and when i removed it (because i installed ubuntu on my new 80gig HD) i had t0 restore my MBR so i used the live 8.10 cd and manually install ms-sys used it and restored my MBR to the windows bootloader.

only found out about supergrub later.

sitting with the boot problem tho but thats n0t imp0rtant right now.

---

### Post by Noise... on 2009-04-10
> **doas777 said:**
> is your problem that you can't run fixmbr without a vista disk?

you can get an equivalent to fixmbr with ms-sys. check out bodhi.zazen's adivce on this thread: [http://ubuntuforums.org/showthread.php?t=740221](http://ubuntuforums.org/showthread.php?t=740221) 

oh, BTW, ms-sys was removed from teh repos with hardy because it is a little unclean from an oss perspecfive. you can find it here: [http://ms-sys.sourceforge.net/#Download](http://ms-sys.sourceforge.net/#Download)

good luck,
franklin

I actually don't have a problem yet. I just want to make sure I have a backup plan before installing Ubuntu Studio. As long as everything goes right, I'll probably become an Ubuntu user. Especially if most of my Windows stuff works through WINE.

---

### Post by Yvan300 on 2009-04-10
What you should have done when installing ubuntu was to install grub to your ubuntu partition instead of the start of your whole hard drive. You could have used a program called EasyBcd which would allow you to add ubuntu to vista's boot loader, making everything simpler. Well to fix your problem, just keep ubuntu, you could decrease the partition size of ubuntu so that it does not take up a lot of space or you could just borrow someone else's  installation disk. A lot of people have one :)

---

### Post by AXeS on 2009-04-10
so thats why i had to look for it... thanx doas777.

so it was unclean,did they make a new prog similar n easy besides manually burning a supergrub disk? only if you know,dont have to answer.

---

### Post by Noise... on 2009-04-10
> **Yvan300 said:**
> What you should have done when installing ubuntu was to install grub to your ubuntu partition instead of the start of your whole hard drive. You could have used a program called EasyBcd which would allow you to add ubuntu to vista's boot loader, making everything simpler. Well to fix your problem, just keep ubuntu, you could decrease the partition size of ubuntu so that it does not take up a lot of space or you could just borrow someone else's  installation disk. A lot of people have one :)

It's not installed yet. Like I said above, before I go to install it, I just want to make sure I'm covered if there's a compatibility issue with my computer, or if it's not for me.

---

### Post by taurus on 2009-04-10
If you want to check for compatibility, run Ubuntu from the LiveCD.  Just remember that it would be a little slow so don't judge the speed with Ubuntu LiveCD though.

---

### Post by AXeS on 2009-04-10
Noise... if i may ask,what you going to use UBUNTU STUDIO for mainly?

---

### Post by Noise... on 2009-04-10
> **taurus said:**
> If you want to check for compatibility, run Ubuntu from the LiveCD.  Just remember that it would be a little slow so don't judge the speed with Ubuntu LiveCD though.

My only disk is the Ubuntu Studio version, which unfortunately lacks that feature. I download standard Ubuntu, but I'm on Mobile Broadband, so I only have 5GB of data usage a month.

---

### Post by doas777 on 2009-04-10
> **Noise... said:**
> I actually don't have a problem yet. I just want to make sure I have a backup plan before installing Ubuntu Studio. As long as everything goes right, I'll probably become an Ubuntu user. Especially if most of my Windows stuff works through WINE.

in that case, check to see if you can burn off backup media from vista. most laptop manufacturers have an option to do so anymore, instead of shipping media. if thats not an option, I would spend the 15$ to have your laptop vendor ship you a disk. once the order is placed you can at least be assured that a backup plan is coming your way over fedex, and breath easy.
just be careful to backup your user data before proceeding. if you do restore, it will likely reformat your partitions.

---

### Post by Noise... on 2009-04-10
> **AXeS said:**
> Noise... if i may ask,what you going to use UBUNTU STUDIO for mainly?

Audio recording and maybe some digital art (photoshop type stuff).

Primarily audio work though.

---

### Post by Noise... on 2009-04-10
> **doas777 said:**
> in that case, check to see if you can burn off backup media from vista. most laptop manufacturers have an option to do so anymore, instead of shipping media. if thats not an option, I would spend the 15$ to have your laptop vendor ship you a disk. once the order is placed you can at least be assured that a backup plan is coming your way over fedex, and breath easy.
just be careful to backup your user data before proceeding.

There's a hidden recovery drive for Vista that will restore back to factory settings.

Will that work as a worst case scenario?

---

### Post by AXeS on 2009-04-10
> **Noise... said:**
> Audio recording and maybe some digital art (photoshop type stuff).

Primarily audio work though.


im into audio, digital composing more like it, i go back to windows just for PROPELLERHEAD REASON 4.
i installed ROSEGARDEN but i have a problem,it doesnt start when i click to start it. i installed it in GNOME but ima try on KDE soon as i get the install.Hope you come right, thats the only tie i have with MS at the mo n it kinda sux.

---

### Post by doas777 on 2009-04-10
> **Noise... said:**
> There's a hidden recovery drive for Vista that will restore back to factory settings.

Will that work as a worst case scenario?

unfourtunatly, no, but it is for the second-to-worst. If you do have a recovery partition, you most likely have an option in your vendors software to burn a set of recovery disks.

heres the worry (though you sound like you understand already).
os installers usually have clumbsy or confusing partitioning controls, which often default to destroying all existing partitions on the first physical disk, and writing their own partition table. the key to doing dual boots (or formatting a system partition, while leaving a data partition), is to not delete the wrong partition. in the worst case, your entire drive would be wiped.

if this does happen, all is not lost. shutdown immediately, and get yourself a copy of the ubuntu rescue remix livecd (from whatever internet connection you can find), and use testdisk to recover the partiton. 

good luck,
franklin

---

### Post by anewguy on 2009-04-10
The recovery partition should work, but check your laptop for some sort of option from the manufacturer to create recovery disks as well.  My old Gateway I had until a year ago let you make one set of recovery CD's, so that even if you lost the recovery partition you could still get Windows back.

If you are concerned about it, I did write a how-to for removing Ubuntu and going back to Windows in this forum:  

[go back to Windows and remove Ubuntu]("http://ubuntuforums.org/showthread.php?t=508927")

The easiest thing to do is in Windows just download mbrfix - it is a free program.  When you want to get rid of Ubuntu, just run mbrfix fix in Windows, then boot using a Livecd and completely remove your Ubuntu partition(s) so it just shows as free space.  You should then be able to use Vista to extend the file system into the free space.

I really hope, since you are going with dual-boot, that you won't need to get rid of Ubuntu, but it is all just personal preference.

Dave :)

---


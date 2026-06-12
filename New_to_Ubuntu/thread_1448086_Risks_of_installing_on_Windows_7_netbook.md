---
title: "Risks of installing on Windows 7 netbook"
date: 2010-04-06
forum: New to Ubuntu
---

### Post by fedira on 2010-04-06
Hi all,

I've been running Ubuntu for years now, and I'd like to help a friend install it on her new netbook, which is currently running Windows 7 Starter Edition.

I thought Wubi might be the easiest way, but I immediately encountered an error that no one seems to have any answers for. (Some suggested manually downloading the ISO and putting it in the same folder; it's currently downloading.)

But this scary-looking error made me worry a little, and I have some questions.

1. What's riskier -- installing Ubuntu from a bootable flash drive or via Wubi? Are there different risks associated with each? Clearly, an error that aborts the installation is merely an annoyance, but an error that messes up booting or something is a serious problem.

2. Is it a bad idea to try to install Ubuntu on a netbook without a CD drive, where there's no way to just reinstall Windows if something goes wrong? What should my backup plan be, in case of major errors?

3. Is the current version of Ubuntu relatively stable, or has it been especially buggy? Should I wait for the next LTS version?

4. Any problem with running regular Ubuntu instead of Netbook Remix on a netbook?

5. Any known problems specifically with Windows 7 or Windows 7 Starter Edition?

This forum has always been a lifesaver -- thanks in advance for any help!

---

### Post by Paqman on 2010-04-06
> **fedira said:**
> 
1. What's riskier -- installing Ubuntu from a bootable flash drive or via Wubi? Are there different risks associated with each? Clearly, an error that aborts the installation is merely an annoyance, but an error that messes up booting or something is a serious problem.


Wubi is great, but if you're confident with installing to a proper partition, then that's the way to go. Wubi does have some limitations that a proper install doesn't have.

I wouldn't install to a USB flash drive, it'd prety slow. You only need to carve 6GB out of the internal drive to install.

> 2. Is it a bad idea to try to install Ubuntu on a netbook without a CD drive, where there's no way to just reinstall Windows if something goes wrong? What should my backup plan be, in case of major errors?

You don't have to get rid of Windows. If you've got space, dual-boot. Plus you could always use a USB CD drive to reinstall Windows. You can get a caddy that converts an IDE drive out of the desktop into a USB device for pretty minimal cash.

> 3. Is the current version of Ubuntu relatively stable, or has it been especially buggy? Should I wait for the next LTS version?

LTS releases aren't any more stable, they're just supported for longer. Karmic is great, but the new version is out in a few weeks.

> 4. Any problem with running regular Ubuntu instead of Netbook Remix on a netbook?

No, it's just personal preference.

> 5. Any known problems specifically with Windows 7 or Windows 7 Starter Edition?

Starter Edition is pretty crippled, you'll find Ubuntu is a much more capable system.

---

### Post by Kakers on 2010-04-06
> 1. What's riskier -- installing Ubuntu from a bootable flash drive or via Wubi? Are there different risks associated with each? Clearly, an error that aborts the installation is merely an annoyance, but an error that messes up booting or something is a serious problem.

If the problem is anything like I encountered, it would not boot into ubuntu and turns out it was just replacing one of the Wubi files listed in the C drive. I believe the file was wubildr found on C drive. Installing Wubi is a lot safer and can be removed at any time.

> 2. Is it a bad idea to try to install Ubuntu on a netbook without a CD drive, where there's no way to just reinstall Windows if something goes wrong? What should my backup plan be, in case of major errors?

Not really, you can always back it up using an external HDD or getting an external dvd drive to make backup cds.

> 3. Is the current version of Ubuntu relatively stable, or has it been especially buggy? Should I wait for the next LTS version?

Releases of Ubuntu if they are "buggy" tends to be around the first few weeks of release, I have been using 9.10 for some time and not had any major problems. Compatibility will be better in 10.04 but the biggest thing is just being supported for 2 years until the next LTS

> 4. Any problem with running regular Ubuntu instead of Netbook Remix on a netbook?

Not always, the main advantage of Remix is it is cut down version which would run faster but we install the normal version of Ubuntu on our laptops at work with no problems.

> 5. Any known problems specifically with Windows 7 or Windows 7 Starter Edition?

None that I know of, other than it being windows... :p

---

### Post by J V on 2010-04-06
> 1. What's riskier -- installing Ubuntu from a bootable flash drive or via Wubi? Are there different risks associated with each? Clearly, an error that aborts the installation is merely an annoyance, but an error that messes up booting or something is a serious problem.Depends on the machine...

> 2. Is it a bad idea to try to install Ubuntu on a netbook without a CD drive, where there's no way to just reinstall Windows if something goes wrong? What should my backup plan be, in case of major errors?I'd hook it to another computer via lan and use clonezilla to make a copy of the HD first

> 3. Is the current version of Ubuntu relatively stable, or has it been especially buggy? Should I wait for the next LTS version?More buggy than usual, but it has stablized.

> 4. Any problem with running regular Ubuntu instead of Netbook Remix on a netbook?Nope, but I advice UNR because its VERY good with available screen realestate

> 5. Any known problems specifically with Windows 7 or Windows 7 Starter Edition?Its windows :)

---

### Post by clive littlewood on 2010-04-06
Hi

I have 9.10 installed on my netbook side by side with winblows 7 without any problems.

Dual boot is easy to install ubuntu from a USB stick and you get a truer experience going this way.

You should have a backup of winblows 7 on a recovery partition.

Clive

---

### Post by Mark Phelps on 2010-04-06
You've already received a lot of responses, so I'll only add a couple of things.

Before you do anything else, see if the Win7 Backup function will allow you make a Recovery "CD" on a USB stick.  If so, I would set that aside as it will come in useful later if you ever need to repair or restore the Win7 boot loader.

Also, at the risk of getting beaten up AGAIN, if you're going to dual-boot instead of using Wubi (which I recommend), I would strongly suggest that you do not allow the Ubuntu installer to shrink the Win7 OS partition -- as that sometimes results in corruption of that partition.  Instead, use the Win7 Disk Management utility to shrink the OS partition and leave the new space unformatted.  Then, install to the largest free space using the Ubuntu installer.

If, after you install, you don't get a menu selection for Win7, open a terminal and enter "sudo update-grub".  That should add the Win7 entry to the GRUB menu for you.

---

### Post by mastablasta on 2010-04-06
> **clive littlewood said:**
> Hi
You should have a backup of winblows 7 on a recovery partition.

 
This was the first thing i though of. Do not delete this partiton (!) unless you previously created a recovery CD (or DVD or whatever they have nowadays).

---

### Post by warfacegod on 2010-04-06
> **Kakers said:**
> Not always, the main advantage of Remix is it is cut down version which would run faster but we install the normal version of Ubuntu on our laptops at work with no problems.

The .iso's for 9.10 Karmic and 9.10 UNR are almost the same size. They also install at about 2.2 GB. UNR isn't meant to be cut down or run faster than 9.10 Karmic.

---

### Post by DarkStar786 on 2010-04-06
I was previously running Ubuntu 8.04 and Windows 7 Ultimate, works just fine for me, though i didn't use Wubi, i prefer separating the partition... but thats just preference..

---

### Post by fedira on 2010-04-07
Thanks all for the helpful responses! A few follow-up questions:

> **Paqman said:**
> Wubi is great, but if you're confident with installing to a proper partition, then that's the way to go. Wubi does have some limitations that a proper install doesn't have.

I wouldn't install to a USB flash drive, it'd prety slow. You only need to carve 6GB out of the internal drive to install.

Can you point me to a guide that shows how to install from the internal hard drive? I didn't even know this was possible -- what's the best way to do it? 

I'd love to use Wubi, as it just seems a little simpler (also simpler to remove, in case of any problems), but it really just refuses to work.

> **Paqman said:**
> You don't have to get rid of Windows. If you've got space, dual-boot. Plus you could always use a USB CD drive to reinstall Windows. You can get a caddy that converts an IDE drive out of the desktop into a USB device for pretty minimal cash.

I don't even have a Windows CD though. Assuming I don't get rid of Windows -- is there any way the Windows partition could be damaged by installing Ubuntu, either via Wubi or on a real separate partition? This is what I was worried about. Or should we be able to boot into Windows no matter what, even if the Ubuntu install goes totally haywire?

---

### Post by mastablasta on 2010-04-07
> **fedira said:**
>  
Can you point me to a guide that shows how to install from the internal hard drive? I didn't even know this was possible -- what's the best way to do it? 
 
I'd love to use Wubi, as it just seems a little simpler (also simpler to remove, in case of any problems), but it really just refuses to work.
 
 
Wubi is virtualization of some sort. It's more ment sort of to try it out but it will never be the same as normal install.
 
How to install with dual boot. Download this free e-book here: [[COLOR=#444444]http://www.ubuntupocketguide.com/[/COLOR]]("http://www.ubuntupocketguide.com/")
 
It's for 8.10 but the instalation process is more or less the same. And installing and partitionaing is extremely easy. in fact ubuntu does most things for you (with recomended settings) but you can slide the slider to give it less space for start.
 
> 
I don't even have a Windows CD though. Assuming I don't get rid of Windows -- is there any way the Windows partition could be damaged by installing Ubuntu, either via Wubi or on a real separate partition? This is what I was worried about. Or should we be able to boot into Windows no matter what, even if the Ubuntu install goes totally haywire?
 
Wubi basically creates a large file on your disk as i understand it and puts the os in it. (someone can correct me on this).
 
If you follow the guide (it really is a great guide) and prepare the disk propperly before doing the partiitoning then you will split the disk. Whatever happens on one partition doesn't affect the other partition. That's why it's always good to have a system partition and data partition (even on Windows). that way if something goes wrong you can delete/format the whole system partition while your prescious data will be safe.
 
You do not have a windows CD because windows are stored on a part of the disk in some backup files. You will have to search the net for informaiton on how to create recovery CD from those files. Each notebook has this done in a different way. Again if you do not ruin this paritition the data will remain there. the recovery CD is just as backup, so that you are safe in case something happens. I also think recovery CD should be available at the company that put these windows on computer.
 
 
Basically partitions are like having separate hard disk. Only in this case your one hard disk is divided into more "pieces" (with software). Each of these pieces is managed separately in a way.

---

### Post by fedira on 2010-04-07
Hi there,

Thanks for your reply. 

I've installed Ubuntu before (I'm running it right now). I was specifically asking about installing Ubuntu from the hard drive (not with Wubi, but creating an actual partition), which someone mentioned was possible if a CD drive is not present and a flash drive is not possible.

So, my question really is:
I've downloaded the Ubuntu ISO. Without burning it onto a CD or a flash drive, how can I install it? Or is this in fact not possible without creating a virtual partition with Wubi?

If it's not possible, I'll go ahead and try to figure out how to make the flash drive work using the guide on the main Ubuntu site.

Thanks again!

---

### Post by marshmallow1304 on 2010-04-07
> **mastablasta said:**
> Wubi is virtualization of some sort.
Not really.  But you are correct that there is slight performance degradation.
> **http://wubi-installer.org/faq.php]Is this running Ubuntu within a virtual environment or something similar?

No. This is a real installation, the only difference is that Ubuntu is installed within a file as opposed to being installed within its own partition.[/QUOTE]


[QUOTE=fedira said:**
> I've installed Ubuntu before (I'm running it right now). I was specifically asking about installing Ubuntu from the hard drive (not with Wubi, but creating an actual partition), which someone mentioned was possible if a CD drive is not present and a flash drive is not possible.


I think that poster meant that it's generally not a great idea to install *to* an external flash drive.  It's perfectly fine to install *from* an external flash drive.

> **fedira said:**
> 
So, my question really is:
I've downloaded the Ubuntu ISO. Without burning it onto a CD or a flash drive, how can I install it? Or is this in fact not possible without creating a virtual partition with Wubi?

You could use [netboot]("https://help.ubuntu.com/community/Installation/Netboot"), but it's much easier to install via USB flash drive.

---


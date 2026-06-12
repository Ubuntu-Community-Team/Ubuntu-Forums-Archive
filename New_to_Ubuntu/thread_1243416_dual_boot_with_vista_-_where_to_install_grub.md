---
title: "dual boot with vista - where to install grub?"
date: 2009-08-18
forum: New to Ubuntu
---

### Post by alpage2 on 2009-08-18
I have dual booted with XP before, but this is my first attempt to dual boot with a pre-installed version of vista, on a recent Dell laptop, and the partitions are different. I seem to have:

/dev/sda1 125.5 MB
/dev/sda2 10.0 GB - corresponding to the D: drive, containing the factory restore files
/dev/sda3 138.9 GB - corresponding to the C: drive, and labelled by the ubuntu disk partitioner as Windows Vista (loader)

Where is the correct place to install grub, to provide me with a dual boot menu on start-up.

I am assuming that the tiny first partition is the vista boot loader? I am just looking for reassurance that installing grup there will still permit grub to recognise the vista partiton, and still be able to boot vista without any unexpected problems.

Many thanks in anticipation.
Alan

---

### Post by Penguin Guy on 2009-08-18
As a rule; **never** delete something if you're not sure what it is. Please run [COLOR="Green"]sudo fdisk -l[/COLOR] and post back the results. Also if you look in [COLOR="Green"]Places -> 125MB Media[/COLOR] it should show you the contents of your 125MB partition.

---

### Post by jacklinux on 2009-08-18
> **Penguin Guy said:**
> As a rule; **never** delete something if you're not sure what it is. Please run [COLOR=Green]sudo fdisk -l[/COLOR] and post back the results. Also if you look in [COLOR=Green]Places -> 125MB Media[/COLOR] it should show you the contents of your 125MB partition.

Wouldn't he/she be able to install Via Wubi? then it would more or less be automatic?

---

### Post by Penguin Guy on 2009-08-18
> **jacklinux said:**
> Wouldn't he/she be able to install Via Wubi? then it would more or less be automatic?
Installing via Wubi is another option, but that is a workaround rather than a solution, most people prefer to only use workarounds if no solution can be found. Nonetheless, if the original poster is interested [[COLOR="Blue"]here is a link where they can read more about it[/COLOR]]("http://wubi-installer.org/").

---

### Post by Arand on 2009-08-18
When I got my dell (xps1530) these partitions were as follows:

sda1: DOS-based partition, presumably meant for booting into Dell factory restore mode. This is as far as I know NOT where the vista bootloader is contained, and NOT where you should install grub.
sda2: Contains factory restore IMAGE, presumably accessed by booting sda1.
sda3: Vista as usual, BCD, the default vista bootloader, is also contained here (in file \bootmgr and folder  \Boot\*)
If you have MediaDirect functionality you may also have a dedicated sda4 partition for that.

The mbr (first 512bytes of the whole sda disk) contains "BCD" as well, or basically just a pointer to sda3 where the "full" BCD will be loaded. (not sure if it first loads the vbr of sda3 or jumps right into executing \bootmbr?)

To dual-boot this:
EITHER:
So what you'll need to do is make a partition for ubuntu which will contain the "full" grub (/boot/grub/*), and then setup grub to the mbr so that it can point to grub on the ubuntu partition, which in turn can load either ubuntu, or chainload BCD and -> vista.

This will be done pretty much automatically by the ubuntu install, if you choose the "side by side" option, or manually create the ubuntu partition.
:DONE

OR:
Alternatively, you could let BCD keep control of the mbr and use a tool like EasyBCD to edit BCD to contain a link to grub. In this case you will have to go into "advanced", in the last confirmation screen in the installer and choose to install grub to sda# (# is your ubuntu partition) instead of hd0 (which is the mbr; interchangable with "sda")
At this point you will have to boot into vista, get hold of and install EasyBCD (or use the bcdedit command line tool already present [rather complicated though]) and then use it to add an entry for grub on your ubuntu partition, in the BCD loader.
:DONE

Not sure if that made perfect sense, happy to explain of anything is unclear.

- Arand

---

### Post by alpage2 on 2009-08-18
Thanks everyone - quality information.

It may take me a while to get to the next step - I am now running into a hardware problem. I was just running CHKDSK in Vista, in preparation for partitioning the drive, when CHKDSK hung up. In setting CHKDSK to run prior to vista booting up, I am left with a hung machine, which, if I pull the plug and restart it, it insists on running CHKDSK from the beginning again, and hanging at the same place. Effectively, I am now locked out of vista.

Ho-hum - off to a vista forum to fix this, unless anyone knows the answer?

Would the 9.04 install disk contain disk tools that could fix this?

CHKDSK reported no file problems, and I am left on screen with:

> 
CHKDSK is verifying free space (stage 5 of 5)
80% complete. (19588657 of 25114620 free clusters processed)


Thanks again
Alan

---

### Post by Arand on 2009-08-18
I would guess that the vista dvd/recovery media would have chkdsk included, so it would be possible to run it "from the outside" on the partiton, which might work better. Maybe?
I've heard GNU/Linux tends to lack in repairing ntfs. 
- Arand

---

### Post by stinger30au on 2009-08-18
> **alpage2 said:**
> I have dual booted with XP before, but this is my first attempt to dual boot with a pre-installed version of vista, on a recent Dell laptop, and the partitions are different. I seem to have:

/dev/sda1 125.5 MB
/dev/sda2 10.0 GB - corresponding to the D: drive, containing the factory restore files
/dev/sda3 138.9 GB - corresponding to the C: drive, and labelled by the ubuntu disk partitioner as Windows Vista (loader)
Alan

125 meg is the windows boot partition
this is the bit u want grub 2 install 2

when u put in the ubuntu 9.04 install cd when the splash screen comes up and asks what to do tell it to install

click thru the options till u find theres a screen that comes up to tell it where to install ad how

there sould be a green bar up the to that says viasta and %100 disc useage

the lower bar will also be green and in right corner a slide bar

click n drag the slide bar to the left a bit and give ubuntu say 15 or 20 gig maybe more if u have the free space

let it install

it will auto add the grub installer and when u next boot u can pick between ubuntu / vista

i highly reccomend u first run the create recovery option on u laptop to make the few dvds required for vista recovery partition to be backed up to dvd first incase it all goes wrong

---

### Post by Arand on 2009-08-18
@stinger30au
Apart from the partitioning instructions, I have to claim you wrong.

sda1 of 125mb is a most likely a dell diagnostics partition (see [http://www.goodells.net/dellutility/index.htm](http://www.goodells.net/dellutility/index.htm) ). This is NOT where the vista bootloader resides, NOR where to install the grub bootloader.

Furthermore, and to my knowledge, Dell does NOT do restoration DVDs, everything you need for a factory restore is on the sda2 restoration partition.
- Arand

---

### Post by alpage2 on 2009-08-19
Thanks Arand

That seems to agree with what I am seeing in the partitions, and the instructions for a factory restore.

I'm still working through the hard drive problem, which will need some diagnostic software from the manufacturer - Hitachi.

Regards
Alan

---

### Post by philinux on 2009-08-19
With vista you can also use easybcd as the bootloader to boot both vista and ubuntu. I installed ubuntu of GF's laptop. At the last stage I clicked advanced and told it to install grub to the ubuntu partition. This way it did not overwrite the mbr with grub.

[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

---

### Post by Bartender on 2009-08-19
Not sure about this, but I wonder if it would make any difference if you booted into Safe Mode and ran CHKDSK from there?

Also, did you make recovery DVD's?  If you reinstall Windows from recovery discs, the recovery partition might go away, leaving you more options for installing Ubuntu.

I don't know how Dell does it, but that's what happened with my Acer - running the discs removed Acer's confusing snarl of four primary partitions and left me with just one partition.

---


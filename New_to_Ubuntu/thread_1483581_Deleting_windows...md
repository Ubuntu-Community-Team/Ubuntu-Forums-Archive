---
title: "Deleting windows.."
date: 2010-05-14
forum: New to Ubuntu
---

### Post by Kafubie on 2010-05-14
How can I do it?
I'm on my netbook and 70 GBs go to windows and 70 to ubuntu.
I feel that Ubuntu is all I need.

How can I do it?

Will I get a grub error or anything If I delete it?
HELP!

---

### Post by jakupl on 2010-05-14
> **Kafubie said:**
> How can I do it?
I'm on my netbook and 70 GBs go to windows and 70 to ubuntu.
I feel that Ubuntu is all I need.

How can I do it?

Will I get a grub error or anything If I delete it?
HELP!

It should be as easy as, booting an ubuntu live cd, go to System --> administration --> Gparted, delete the windows partition and resize the ubuntu partition.

You should not get any grub error.

---

### Post by tmette on 2010-05-14
Can't you use gparted to restore the netbook to a single partition HDD without deleting Ubuntu?

---

### Post by jakupl on 2010-05-14
> **tmette said:**
> Can't you use gparted to restore the netbook to a single partition HDD without deleting Ubuntu?

What?

---

### Post by Kafubie on 2010-05-14
Ok, I deleted the windows thing.
I think It still has the 2 spaces leftover 

One says system
second says recovery
both are NTFS..
isn't that windows?

Also How can I use the unalloted spaces and add to ubuntu?

---

### Post by 2hot6ft2 on 2010-05-14
A screenshot of what you see in gparted would help us to better advise you on how to do it right. This is how to re-install grub keep it you may need it.

Using 9.10 or 10.04 livecd

Here assuming the Ubuntu partition is sda8,and /boot partition is sda6 (if you have a separate /boot partition).

Boot up ubuntu from the livecd,open terminal and run:
```
sudo -i
```
To find out you partitions run
```
fdisk -l
```
Use that info for the following
```
mount /dev/sda8 /mnt
```
```
mount /dev/sda6 /mnt/boot  #skip this one if you don't have a separate /boot partition
```
You'll want to install grub to the drive that is first in the boot order in the BIOS
```
grub-install --root-directory=/mnt/ /dev/sda
```
Reboot removing the livecd in the process and once you're back in ubuntu run
```
sudo update-grub
```

---

### Post by ubunterooster on 2010-05-14
Or go into Gparted  while in live CD and "resize" the existing Ubuntu Partition

---

### Post by Kafubie on 2010-05-14
I have a netbook... (no optical drive)
Soooo.  I can't use the live cd.

Good thing I didn't deleted the partition.
I'm afraid if I do some sort of fresh install that my internet for my netbook wont work.

Is there any alternatives???!?!

---

### Post by ubunterooster on 2010-05-14
Go to system>administation>startup Disk Creator

Edit: sorry, 2hot6ft2, was not trying to steal your post

---

### Post by 2hot6ft2 on 2010-05-14
> **Kafubie said:**
> I have a netbook... (no optical drive)
Soooo.  I can't use the live cd.

Good thing I didn't deleted the partition.
I'm afraid if I do some sort of fresh install that my internet for my netbook wont work.

Is there any alternatives???!?!
You can create and use a usb startup disk just like a livecd.
System > Administration > USB Startup Disk Creator
You'll need the livecd iso to create it.
And a USB Flash drive to put it on as well as setting it up to boot from it in the BIOS if it doesn't do it already it's just a matter of changing the bootup priority (order).

---

### Post by 2hot6ft2 on 2010-05-14
> **ubunterooster said:**
> Go to system>administation>startup Disk Creator

Edit: sorry, 2hot6ft2, was not trying to steal your post
:lolflag: No problem we're all trying to help.

---

### Post by oldfred on 2010-05-14
You should set up several boot USB's to be your liveCd's.

I have one that boots grub2 and directly loads most ISOs. I can just copy the ISO to the flash drive and edit grub.cfg and boot it.

MultiBoot USB with Grub2 (boot directly from iso files)
[http://www.panticz.de/MultiBootUSB](http://www.panticz.de/MultiBootUSB)
 HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2 
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1288604](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1288604)
[http://ubuntuforums.org/showthread.php?t=1451184](http://ubuntuforums.org/showthread.php?t=1451184)
[http://members.iinet.net/~herman546/p20/GRUB2%20CLI%20Mode%20Commands.html#cli_loopback]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20CLI%20Mode%20Commands.html#cli_loopback")
[http://ubuntuforums.org/showthread.php?t=1224417](http://ubuntuforums.org/showthread.php?t=1224417)


I also have a syslinx based install but plan on converting a large flash drive to a full install.
Standard full install to flash or SSD:
Ubuntu Karmic Koala Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html]("http://members.iinet.net/%7Eherman546/p19.html")

I would convert the old windows partition to a /home if you do not have one. It would make good use of the space. I do not like moving boot partitions to the left, only expand to the right. Moving to the left requires total rewriting of everything which is higher risk than other changes. Of course with everything partition editing based you should have good backups first.

---

### Post by Rasa1111 on 2010-05-14
> **Kafubie said:**
> I have a netbook... (no optical drive)
Soooo.  I can't use the live cd.

Good thing I didn't deleted the partition.
I'm afraid if I do some sort of fresh install that my internet for my netbook wont work.

Is there any alternatives???!?!

Hit Alt F4- just do it. lol  :rolleyes:
you should change yer sig..
this forum is for helping others,
not trying to ef them up.

---

### Post by Kafubie on 2010-05-14
I am downloading it now.
Just tell me what to do now, I already know how to boot up into it.
This is what it looks like when I am log'd into ubuntu.
[http://img39.imageshack.us/i/thish.png/](http://img39.imageshack.us/i/thish.png/)
Tell me what is ok to delete.

---

### Post by 2hot6ft2 on 2010-05-14
> **oldfred said:**
> I do not like moving boot partitions to the left, only expand to the right. Moving to the left requires total rewriting of everything which is higher risk than other changes. Of course with everything partition editing based you should have good backups first.

oldfred makes a very good point here. expanding to the right is much safer.
:popcorn:

---

### Post by 2hot6ft2 on 2010-05-14
> **Kafubie said:**
> I am downloading it now.
Just tell me what to do now, I already know how to boot up into it.
This is what it looks like when I am log'd into ubuntu.
[http://img39.imageshack.us/i/thish.png/](http://img39.imageshack.us/i/thish.png/)
Tell me what is ok to delete.
If it was me and I wanted to get rid of windows completely.

I would delete all of those partitions and make a clean start setting it up from scratch. It would be so much faster. Minutes as opposed to several hours and much safer. You may even want to go with a separate /home partition since this is a LTS release like oldfred said.

When you boot to the liveusb you will need to right click on the swap partition and select swapoff.
Then right click on anything else with keys next to it and select unmount.
Then you will be able to make changes.

Backup anything you want to keep and copy it back after re-installing.

While it is downloading think about how much space you want where and for what. Plan ahead.
:popcorn:

---

### Post by ubunterooster on 2010-05-14
I'd leave sda5 and enlarge it.

Edit: sda5? I thought numbers over 4 were virtual partitions?

---

### Post by ubunterooster on 2010-05-14
> **Rasa1111 said:**
> Hit Alt F4- just do it. lol  :rolleyes:
you should change yer sig..
this forum is for helping others,
not trying to ef them up.

Ever PM before complaining in public?

---

### Post by 2hot6ft2 on 2010-05-14
> **ubunterooster said:**
> I'd leave sda5 and enlarge it.

Edit: sda5? I thought numbers over 4 were virtual partitions?
You can only have 4 primary partitions, an extended partition counts as a primary partition and can contain a lot of logical partitions.

Nothing virtual about them they are real partitions. Or should I say they're no more virtual than any other partition.

---

### Post by ubunterooster on 2010-05-14
> **2hot6ft2 said:**
> You can only have 4 primary partitions, an extended partition counts as a primary partition and can contain a lot of logical partitions.

Nothing virtual about them they are real partitions.
Okay thanks. I'll go Inform myself some more about this on Scroogle

---

### Post by 2hot6ft2 on 2010-05-14
> **ubunterooster said:**
> Okay thanks. I'll go Inform myself some more about this on Scroogle
[http://en.wikipedia.org/wiki/Disk_partitioning](http://en.wikipedia.org/wiki/Disk_partitioning)

---

### Post by ubunterooster on 2010-05-14
Oooh! I get it! :D

---

### Post by anewguy on 2010-05-14
I would do something first, before moving into deleting/resizing partitions:

- you say you want to get rid of Windows.  You also mentioned a recovery partition.  I would *strongly* suggest you read through the documentation for your PC to see what the procedure is for using the recovery partition. If it can be used stand-alone (that is, no need for boot/recovery CD's to use with it), I would leave it there.  If it requires boot/recovery CD's or USB flash drives, I would create those as well.

This may seem crazy to some, but why not know that *if* the time comes you desparately need something from Windows you can - including restoring Windows if needed (perhaps a program that just won't run in Linux and for which the equivalent either doesn't exist or isn't up to your standards).

I'm all for Linux and Ubuntu, but I'm also not an operating system bigot.  If it was me, I would be sure I can restore Windows if the need were to ever arise.

just my 2 cents worth.

Dave ;)

---

### Post by 2hot6ft2 on 2010-05-14
> **anewguy said:**
> 
just my 2 cents worth.

Dave ;)
Awe come on now that was worth more than 2 cents...=D>

Definitely create the recovery cd/dvd's if you haven't already. It's the very first thing I do that way if it fails I can take it back and say it failed give me recovery discs or my money back.
Comes in handy if you every decide to sell the pc.
:)

---

### Post by Kafubie on 2010-05-14
I just re-installed everything.
I got my wireless working again.
Tough day.
Installed ubuntu 2 times today.
This netbook and my desktop....  I FEEL ACCOMPLISHED!!!!:popcorn:

---

### Post by ubunterooster on 2010-05-14
[COLOR=Red][size=7]c[/COLOR][COLOR=Olive]o[COLOR=RoyalBlue]n[/COLOR][/COLOR]g[COLOR=Green]r[/COLOR]at[COLOR=Red]s[/COLOR]![/size]

---


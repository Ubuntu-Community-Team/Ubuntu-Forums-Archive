---
title: "Help with removing Win 7 in Dual Boot"
date: 2011-03-05
forum: New to Ubuntu
---

### Post by duranl on 2011-03-05
I have a machine with Win 7 and Ubuntu.  I would like to remove WIn 7.  I read posts saying that I have to delete the Win 7 partition in order to remove Windows.  When I open my partition manager, I can't tell the difference between the Linux and Windows partitions.  I have provided a snapshot of what I see:

[IMG]http://i62.photobucket.com/albums/h111/durancm/Screenshot.png[/IMG]

sda2 is the recovery partition with Windows Vista. Vista came with the computer; I upgraded to Win 7.
sda3 seems like it has both Win 7 and Ubuntu???

This is confusing me.

Can anyone provide a guidance?  I used the WUBU installer to install Ubuntu.

Thanks in advance :)

---

### Post by beew on 2011-03-05
Well it doesn't look like you have a Unbuntu partition. In other words you don't have Ubuntu installed.

Did you "install" Ubuntu via WUBI?

---

### Post by sandyd on 2011-03-05
> **duranl said:**
> I have a machine with Win 7 and Ubuntu.  I would like to remove WIn 7.  I read posts saying that I have to delete the Win 7 partition in order to remove Windows.  When I open my partition manager, I can't tell the difference between the Linux and Windows partitions.  I have provided a snapshot of what I see:

[IMG]http://i62.photobucket.com/albums/h111/durancm/Screenshot.png[/IMG]

sda2 is the recovery partition with Windows Vista. Vista came with the computer; I upgraded to Win 7.
sda3 seems like it has both Win 7 and Ubuntu???

This is confusing me.

Can anyone provide a guidance?  **I used the WUBU installer to install Ubuntu.**

Thanks in advance :)

> **beew said:**
> Well it doesn't look like you have a Unbuntu partition. In other words you don't have Ubuntu installed.

Did you "install" Ubuntu via WUBI?
When you install wubi, ubuntu is installed in a "virtual disk" file inside windows. Therefore, it is not a true dual boot.

In order to remove windows, you would have to back up all the things in your ubuntu partition, and make recovery discs for windows using the dell recovery thingy. If you have the dell win7 upgrade disc because you formerly had vista on your computer, then you don't need a recovery disc. You can use the upgrade disc as an OEM disc to install Win7 again if complications arise (at least mine does, check if you can boot from the upgrade disc).

Then, just burn a copy of the Ubuntu ISO to disk, and choose "use entire disc".

---

### Post by fabricator4 on 2011-03-05
> **duranl said:**
> 
Can anyone provide a guidance?  I used the WUBU installer to install Ubuntu.

Thanks in advance :)

Because you installed Ubuntu as a WUBI install, it is running under the windows partition.  You can't remove the windows partition without removing the Wubi Ubuntu as well.

I suggest you backup all your data, then boot off the live CD, and install Ubuntu that way.  It will boot faster once you have a native install.

I recommend you don't get rid of the Windows recovery partition.  You might want to re-install it at some point, such as to sell the computer, for someone else's use, or to run a windows program that has no Linux equivalent.  If you tell the install to use "the entire drive" then it will indeed get rid of all the existing partions, include the recovery partition.

I also recommend that when you do the partitioning manually you set up two partitions for Ubuntu: The first one of about 30 Gb for the boot drive (mounts as '/'), and the rest of the free space to be mounted as /home.  With home containing all your data and configuration on a separate partition it makes upgrading and repairs a lot easier later.

Chris.

---

### Post by sandyd on 2011-03-05
> **fabricator4 said:**
> Because you installed Ubuntu as a WUBI install, it is running under the windows partition.  You can't remove the windows partition without removing the Wubi Ubuntu as well.

I suggest you backup all your data, then boot off the live CD, and install Ubuntu that way.  It will boot faster once you have a native install.

I recommend you don't get rid of the Windows recovery partition.  You might want to re-install it at some point, such as to sell the computer, for someone else's use, or to run a windows program that has no Linux equivalent.  If you tell the install to use "the entire drive" then it will indeed get rid of all the existing partions, include the recovery partition.

I also recommend that when you do the partitioning manually you set up two partitions for Ubuntu: The first one of about 30 Gb for the boot drive (mounts as '/'), and the rest of the free space to be mounted as /home.  With home containing all your data and configuration on a separate partition it makes upgrading and repairs a lot easier later.

Chris.
thats what the recovery/oem discs are for. Theirs no reason to use space on your hard drive when you might never use it anyways.

---

### Post by fabricator4 on 2011-03-05
> **sandyd said:**
> thats what the recovery/oem discs are for. Theirs no reason to use space on your hard drive when you might never use it anyways.

These days you don't usually get the OEM disks, just the recovery partition and a license label stuck to the machine.

They figure there's no point using perfectly good CDs when they can just give you  a recovery partion and a Windows utility to burn your own.  Of course the sales people never stress just _how_ important it is to actually use this utility, or to verify that the burn was good.  The OEM's will send you a copy of the OEM disks for that model if you ask for it...  At roughly the same price you paid for the license the first time around (at least).

Chris.

---

### Post by GWBouge on 2011-03-05
> **fabricator4 said:**
> These days you don't usually get the OEM disks, just the recovery partition and a license label stuck to the machine.

Dell is actually pretty good at sending out the discs for whatever software they include.  Mine actually came with the 'Dell Only' Windows disc, a driver/utility disc, Adobe SoundBooth, and Adobe PhotoShop and Premier Elements.  Which is great, since the OS comes preinstalled with so much stuff (and I believe the Recovery partition includes all of this), the best thing to do is just wipe the slate clean and install from scratch, lol.

At any rate, yeah, since it's a Wubi install, all you can really do is backup your /home and start over.  If you have the OEM CD's, you should be OK to repartition and get rid of the Recovery and DellUtility areas.

---

### Post by bcbc on 2011-03-05
If you have spent a lot of time and effort customising your wubi install you can migrate it: [http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

If not, I'd insert an Ubuntu CD and install it - either dual boot - or just overwrite what you've got. If you think you might want to reinstall Windows, save yourself the trouble and dual boot. Don't rely on the recovery partition - these probably won't work anyway (some rely on a custom bootloader to boot into, and some check the partition table and won't work if it's changed from the factory install (probably not all but that was true of my dell)).

---

### Post by sandyd on 2011-03-06
> **fabricator4 said:**
> These days you don't usually get the OEM disks, just the recovery partition and a license label stuck to the machine.

They figure there's no point using perfectly good CDs when they can just give you  a recovery partion and a Windows utility to burn your own.  Of course the sales people never stress just _how_ important it is to actually use this utility, or to verify that the burn was good.  The OEM's will send you a copy of the OEM disks for that model if you ask for it...  At roughly the same price you paid for the license the first time around (at least).

Chris.
Not for Dell.
[[IMG]http://img816.imageshack.us/img816/5268/0306011110.th.jpg[/IMG]](http://img816.imageshack.us/i/0306011110.jpg/)
What im holding is an OEM disk. Even though it says upgrade.
Which is why I asked if he/she initially had vista.
Because if you did, you get one of these babies. The upgrade code works for the oem install as well for convince so that windows can easily be installed from scratch if needed.

---

### Post by duranl on 2011-03-06
Thanks everyone.  I had used the WUBI installer for the dual boot.

I downloaded the Ubuntu image, burned it to a cd, and installed it from scratch.  Now, I only have Ubuntu :)
so far, it seems to work much better like this than using the WUBI steup.  For example, the resolution is finer.

---


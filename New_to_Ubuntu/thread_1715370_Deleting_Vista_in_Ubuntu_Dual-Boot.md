---
title: "Deleting Vista in Ubuntu Dual-Boot"
date: 2011-03-26
forum: New to Ubuntu
---

### Post by zenawenliang on 2011-03-26
Ok so I have a duel boot that was setup from the livedisk, and now I dont even want windows so I was wondering on how to remove windows so I can have just linux, here is my hardrive now from gparted

[IMG]http://i56.tinypic.com/2zxzb7l.png[/IMG]

---

### Post by el_koraco on 2011-03-26
you obviously don't have many files in your linux partition, and it doesn't seem like it's been installed a long time ago. the easiest, although not necessarily the option you want would be to make a fresh install. when you do, you'll get the option to specify partitions manually. you'd be best to make a 20 or 30 GB root partition (mountpoint /), a swap partition the size of your ram or double that, and allocate the rest to the home partition (mountpoint /home). 

the installer also presents an option of using the entire disk and doing its own install. in that case it creates a primary partiton with root, and an extended one with swap as the logical parirition on there. 

it really depends on what you want7need to acomplish.

---

### Post by zenawenliang on 2011-03-26
Ok How Would I Do a Backup, because I really dont wana redo the 500mb of updates

---

### Post by fabricator4 on 2011-03-26
> **zenawenliang said:**
> Ok How Would I Do a Backup, because I really dont wana redo the 500mb of updates


Just copy all the .deb files in /var/cache/apt/archives.  This will copy the installation files for all the updates and all the programs you have installed.

You'll still have to run the updates and install the programs, but at least you will not have to download it all over again.

While you are there, copy everything in /home/username including the hidden files.  This will copy all your work and all the application setup that you've done so far.

Chris

---

### Post by kroq-gar78 on 2011-03-26
Or you could just delete the "NTFS" partition (that's where windows is), though I'm not sure what the possible consequences might be if you do so, so don't do it yet (wait till someone who knows more about this says so too).

AFAIK, there's no way to "Copy" updates from one install to another, so if you DO end up doing the clean install, you'll have to redo them (or wait unitl ubuntu 11.04 comes in a month so you won't have to do the UPDATES, but you'll have to download a 700MB file).

Hope it helps

---

### Post by alegomaster on 2011-03-26
You can just format the vista partition, and use it like a second hardrive.(Maybe for a small back up withen the computer if you ever get a virus on the Ubuntu partition)

---

### Post by beew on 2011-03-26
> **kroq-gar78 said:**
> 
AFAIK, there's no way to "Copy" updates from one install to another, so if you DO end up doing the clean install, you'll have to redo them (or wait unitl ubuntu 11.04 comes in a month so you won't have to do the UPDATES, but you'll have to download a 700MB file).

Hope it helps

If sydbat's method works it could. Though I haven't tried it out.

[http://ubuntuforums.org/showthread.php?t=1689961](http://ubuntuforums.org/showthread.php?t=1689961)

@OP,

The mods are going to give you warnings for starting multiple threads on the same topic. :)

---

### Post by zenawenliang on 2011-03-26
Well Im not getting replies.

---

### Post by zenawenliang on 2011-03-26
Alright this idea is bad, dont wanna redo updates, So could I get help with this? [http://ubuntuforums.org/showthread.php?t=1715383](http://ubuntuforums.org/showthread.php?t=1715383)

---

### Post by Hedgehog1 on 2011-03-26
> **zenawenliang said:**
> Ok so I have a duel boot that was setup from the livedisk, and now I dont even want windows so I was wondering on how to remove windows so I can have just linux, here is my hardrive now from gparted

[IMG]http://i56.tinypic.com/2zxzb7l.png[/IMG]

This is not hard to do.  But you do have a few steps to follow.

The basic flow of it is this:

Running in Ubuntu from the disk:
1) Delete ONLY /dev/sda2 using gparted
2) do a "sudo update-grub" in the terminal to remove windows from the boot menu.

3) boot off the LiveCD/LiveUSB
4) run gparted
5) right click on the swap partition, and select 'swapoff' if it is there.
6) move/resize the /dev/sda3 extended partition to fill all available space.
7) move/resize the /dev/sda5 to use all avaiable space inside /dev/sda3

You can reboot after that, with every thing still installed.

Please backup your documents as a safety measure.

***The Hedge***

:KS

---


---
title: "installation failed! wtf!!! (pardon my french)"
date: 2010-07-27
forum: New to Ubuntu
---

### Post by rocka120 on 2010-07-27
i put Ubuntu on my hard disk using Unetbootin and i tried to install it, but everytime i try it says " installation failed. the installer encountered an unrecoverable error. a desktop session will now be run so that you may invetigate the problem or try installing again." then i try to install it from the desktop session and i get to step 4, the part where you partition the hard drive and when i click on forward a message pops up and says "no root file system is defined. please correct this from the partitioning menu" can someone help me fix it?

---

### Post by k3lt01 on 2010-07-27
Why are you using unetbootin? Do you have a cd drive? download and burn a cd instead that way all your files are on the cd whereas unetbootin needs to pull the files from an outside source which, from memory, you need to define.

---

### Post by adamjkok on 2010-07-27
> **rocka120 said:**
> i put Ubuntu on my hard disk using Unetbootin and i tried to install it, but everytime i try it says " installation failed. the installer encountered an unrecoverable error. a desktop session will now be run so that you may invetigate the problem or try installing again." then i try to install it from the desktop session and i get to step 4, the part where you partition the hard drive and when i click on forward a message pops up and says "no root file system is defined. please correct this from the partitioning menu" can someone help me fix it?
So here's my proposed fix:

[LIST]
[*]Reinstall Ubuntu
[*]Set up your partitions manually as follows:
[LIST]
[*]**Ext4** with a least 8 GB.
[LIST]
[*]Mount point should be a lone forward slash (/). This represents the "root" in Linux
[*]Format this partition
[/LIST]
[*]**SWAP** (optional - you can choose how much you want, this is just virtual memory, but the more the merrier ;)).
[LIST]
[*]Leave the extra settings alone.
[/LIST]
[/LIST]
[/LIST]
[COLOR=Red]You may lose data, so I'm just giving you fair warning so this post isn't removed/jailed. I advise using USB drives (flash/HDD) and/or cloud services such as Dropbox to store important data. I'm assuming you don't have anything on your disk right now anyway, just sayin'...[/COLOR]

Lemme know if you run into trouble.

---

### Post by rocka120 on 2010-07-27
i tried to boot from the cd for three days and it would always go to the desktop background and just freeze. so i downloaded the desktop torrent, and used Unetbootin to put it on my harddisk.

---

### Post by rocka120 on 2010-07-27
thank you so much adamjkok. its a 80GB HDD, so i put 16GB in the Ext4 and the rest in the swap area :)

---

### Post by k3lt01 on 2010-07-27
> **rocka120 said:**
> thank you so much adamjkok. its a 80GB HDD, so i put 16GB in the Ext4 and the rest in the swap area :)
Whoa, wait a little bit before you waste so much space.
10gb to 20 gb (20 gb at the most) for / (root)
2gb for SWAP
the rest, in your case, 68gb (approximately) for /home. This is where you will store your files like music and documents.

---

### Post by unteer on 2010-07-27
Partitioning is a tricky thing to teach an individual, especially if they are coming over from the windows world.  The windows philosophy is to partition hard drives because a lot of times viruses would destroy system folders, but at least your personal data would be safe.

With 'nix based systems, partitioning was performed to allow system administrators to perform in place software updates without needing to reformat entire computers.  And in general, partitioning and mount points can help with other tasks, such as spreading out an OS across multiple physical hard drives.

But in this day and age, with plenty of computer resources, external hard drives and constant software updating, it can become tricky to know how to partition.

Here are some tips:
[LIST]
Placing the /boot folder on its own partition can help with massive kernel errors, and it can remain at a relatively fixed size, as the /boot folder rarely grows much larger than the initial kernel load image.
[/LIST]
[LIST]
Your Swap partition should be about twice the size of your RAM.  If you have 1 gigabytes of ram, your swap partition should be about 2 gigabytes.  However, eventually increasing swap does not grant a performance boost, so usually no more than 4 gigabytes of swap area is needed.
[/LIST]
[LIST]
Separating your /home mount point and your / mount can be tricky.  It is true that your /home mount point is where all the "big data" will go, such as music collections, movies and pictures.  But the / mount point contains all other OS necessities, and is also where your new applications and libraries will go.  Thus, it is good to know if your computer will have lots of new applications and whatnot, or if that is not the case.  You can get away with a fixed size partition for / mount point, but remember to include space for applications and other things you may install on your system.
[/LIST]

For more a better understanding of the Linux Directory Structure, and why partitioning and mount points can matter, check out this link:

[http://www.tuxfiles.org/linuxhelp/linuxdir.html](http://www.tuxfiles.org/linuxhelp/linuxdir.html)

---

### Post by rocka120 on 2010-07-27
ok. i changed all of my partitions. 14GB is Ext4 at "/", 2GB is swap, and the rest is at "/home".  and i continued with the install. in the last step a message popped up that says "ERROR!!!. Error informing the kernal about modifications to partition /dev/sda1 -- Device or resource busy. This means linux won't know about any changes you made to /dev/sda1 until you reboot so you shouldn't mount it or use it in anyway before rebooting." Is there someway to unmount it?

---

### Post by rocka120 on 2010-07-27
im trying to unmount the HDD and its saying that "the daemon is inhibited"

---

### Post by k3lt01 on 2010-07-27
I bet sda1 is where your unetbootin is stored. If that is the case then no you cant unmount it as you need it to install the system. You really need to have the disks and/or partitions you are working on unmounted and th only way to do that is to not use them for the install process.

Have you tried a flash drive install or an AlternateCD install?

---

### Post by rocka120 on 2010-07-27
i havent tried the flashdrive yet.
ill do that now if i can.

---

### Post by k3lt01 on 2010-07-27
I would advise you to have [a read of this]("http://www.makeuseof.com/tag/install-linux-with-ease-using-unetbootin/") before you do anything else.

---


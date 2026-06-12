---
title: "Installing Windows on VirtualBox"
date: 2009-05-04
forum: New to Ubuntu
---

### Post by fsanchezcv on 2009-05-04
I have read a guide on how to install windows on ubuntu using virtualbox, but I have a technical question about doing it.

I use a HP NX6325 Laptop that came with Windows XP Pro preinstalled, and no installation cds. However, I used the preinstalled software to create backup DVDs which I tried before and worked great to restart my system to factory settings. 

However, I want to re-format my whole HD to install Jaunty (I know I can just upgrade, but I got my reasons to do this), but I still need to use some Windows sometimes. My question is: **Does Anybody know if I can install XP via VirtualBox using the backup DVDs that I created with the HP software??** They are boot DVDs that install XP Pro formating the partition in which one chooses to install windows, and they also create a new partition for backup files.

If someone has used this kind of CD/DVD to install windows on VirtualBox, please let me know how it went. Many thanks beforehand

---

### Post by shakma on 2009-05-04
I don't see any reason it *wouldn't* work.  I just did an XP install through virtualbox last night.  If you have room now... can you try it quick first?  I mean, do you have room to try the install ***within*** your current install?  Virtualbox is pretty awesome and will let you install just about anything.  Also, you don't need a ton of space if you use the dynamic harddrive option.  I'd recommend downloading the latest version from the sun website rather than the "open source edition" for your particular case though.  It's more forgiving I've found...

---

### Post by wizard10000 on 2009-05-04
Can't speak specifically to HP but I have tried installing to a VM with OEM restore discs and haven't had much luck with Dell or Gateway.

Another thing you might want to remember is that almost all the hardware in a VM is virtualized so the drivers that come with your factory restore discs won't work.

---

### Post by akoskm on 2009-05-04
The possibility that the installation finishes without any problem is small. The DVD backup what you've created is an image from your laptop while the XP is sitting on it. Now you are trying to restore that hardware configuration in a completely different machine. This installation have three possible results: totally fails or you can boot into XP but with wrong drivers (it's the dead end for XP), or you can boot into XP - maybe in failsafe mode or something similar. In this case I suggest you to remove every driver from Device Manager what belongs to your old installation.
Good luck.

---

### Post by lkraemer on 2009-05-04
fsanchezcv,
In your specific case I'd think it would be best for you to do as I have
done on my Compaq CQ50-139NR.

It originally came with a 250 Gig Hard drive with Vista preloaded.  The 
hard drive had two partitions.  A 10 Gig RECOVERY Partition, that is at
the end of your Hard Drive, and the remaining space was the Vista Partition.

There is a MAXIMUM of 4 Primary Partitions that can be used on any single
PHYSICAL Hard Drive.  You can make, and use Extended Partitions, but I
haven't elected to do this.  So, if your XP or Vista Partition is LARGE
say ~200 Gig, and your RECOVERY Partition is ~10 Gig, you still have two
Primary Partitions available....... (Root /  and Linux-Swap ) that can be
used for Ubuntu.

I elected to make my Vista Partition ~80 Gig, becasue I don't ever plan on
using it, then I moved the ~10 Gig RECOVERY Partition right next to
the Vista Partition, and Created the ROOT and Linux-Swap Partitions for
Ubuntu 8.04 LTS, becasue I wanted support until 2011 with as few changes
and updates that the Leading Edge products have.  My Linux-Swap was two
times my RAM (~4 Gig), and the remainder is a Ubuntu EXT3 partition.


You need to go download the SuperGrub ISO and burn the LiveCD, becasue
at some point you will need it.
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

I also keep gparted handy:
[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

The absolute best Dual Boot site is located here:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

Another option is to purchase a new 250 Gig Drive and install it in your
computer and just install the Distro of your choice.  That is the most
fool proof way, keeping your original drive as a backup, or making the new
drive a Dual Boot drive.

To Clone your Drive use Clonezilla:
[http://clonezilla.org/](http://clonezilla.org/)
Disk to Disk, Partition to Partition, Disk to Server, Partition to Server,
Server to Disk, Server to partition......

That should do it for you.

lkraemer

---

### Post by Mark Phelps on 2009-05-04
> **fsanchezcv said:**
> My question is: **Does Anybody know if I can install XP via VirtualBox using the backup DVDs that I created with the HP software??** They are boot DVDs that install XP Pro formating the partition in which one chooses to install windows, and they also create a new partition for backup files.

Don't see any reason why this WOULD work!  After all, as you said, they're boot disks.  So, you're going to launch virtualbox and then boot from a CD? Isn't that going to restart the machine (as in "reboot"), and then, whatever you do after that will affect the whole "real" machine, not the "virtual" machine.

Or, maybe I'm missing something in what you're trying to do ...

---

### Post by Insanity01 on 2009-05-04
> **Mark Phelps said:**
> Don't see any reason why this WOULD work!  After all, as you said, they're boot disks.  So, you're going to launch virtualbox and then boot from a CD? Isn't that going to restart the machine (as in "reboot"), and then, whatever you do after that will affect the whole "real" machine, not the "virtual" machine.

Or, maybe I'm missing something in what you're trying to do ...

no i didn't think it would, in Vmware u select where u want to install from, ISO / DVD drive, just pick DVD drive and it should be fine O.o

---

### Post by Marvin666 on 2009-05-04
If I installed AOL under virtualbox with windows, could it access my laptop's modem?

---

### Post by Insanity01 on 2009-05-04
> **Marvin666 said:**
> If I installed AOL under virtualbox with windows, could it access my laptop's modem?

If you configured virtualbox right, then it should

---

### Post by fsanchezcv on 2009-05-05
Thanks for the insights. I think Im just gonna give it a go, and then let you know how it went. I really dont mind not being able to use some of the features on my computer while using XP inside a VB, I just need windows to run a couple of programs I cant do without.

---


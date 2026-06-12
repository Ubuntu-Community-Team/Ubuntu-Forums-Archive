---
title: "Print Server"
date: 2008-12-12
forum: New to Ubuntu
---

### Post by WillT87 on 2008-12-12
I have an old celeron 800mhz pc with 192mb ram and 40gb hdd

I tried to install ubuntu 8.10 desktop version and got an error about not enough RAM apparently you need 256mb or installation will not work. I ignored the error and it crashed on installation twice. I tried to use ubuntu 8.10 server edition. Not very user friendly. Ive tried tutorials but failed miserably 

  I need this print server to work with windows XP and Vista

  Is there a better verison of ubuntu that would work with this pc

Problems
 I have 12 partions some how 

I really just want to format my disk and start over

---

### Post by binbash on 2008-12-12
you can try linux mint fluxbox edition

---

### Post by starcannon on 2008-12-12
You can try the alternate install cd: [http://www.ubuntu.com/getubuntu/downloadmirrors#alternate](http://www.ubuntu.com/getubuntu/downloadmirrors#alternate)
or a lighter version of ubuntu, like xubuntu: [http://xubuntu.com/](http://xubuntu.com/)
or even do a minimal install and just grab what you need for a printserver: [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

If your new to Ubuntu or Linux in general, I would likely recommend the xubuntu option for your hardware specifications.

GL and have fun

---

### Post by WillT87 on 2008-12-12
Are there any commands in ubuntu 8.10 server edition to clean out my hdd so I can start over

---

### Post by TJCIB on 2008-12-12
Maybe even Puppy Linux as a print server.  that would be fun...and it will bark at you every time it starts up!

It would fly on your machine too...

but the Xubuntu is probably good.

---

### Post by WillT87 on 2008-12-12
Are there any tutorials for this?

---

### Post by TJCIB on 2008-12-12
Sorry, missed your last post...

Are you installing 8.10 on the whole HDD?
If so just use the "guided" option and "use entire disk".  That will reformat the entire partition.

If you have tons of partitions, you will want to delete them and make one big partition.  That can be tricky through the text-based installer, but not impossible.

If you wanted, there are other lightweight options for repartitioning that don't require the use of an ubunutu LiveCD.
You could use the gParted live cd, or pop in a puppy linux cd and it has gparted built into it.  That would give you a graphical tool.

---

### Post by WillT87 on 2008-12-12
What do you think my best option is?

would it be possible to turn this into a mini file server with only one hdd

---

### Post by TJCIB on 2008-12-12
Assuming you want only Xubuntu on your hard drive with no other partitions

Go here:
[http://puppylinux.org/downloads/official-releases](http://puppylinux.org/downloads/official-releases)

Download the latest Puppy Linux .iso
Burn it to a CD
Put it in the drive and reboot
load up puppy, it has some prompts the first time
Run GParted (it is in one of the menus at the top, like system or setup or something, I can't remember which off the top of my head)
When in GParted, delete all of your partitions except the first one
Then "resize" your remaining partition to be all but about 512MB of the disk.  Be sure you set it as an "ext3" file system type
In the remaining ~512MB of space, create a new partition that is a "swap" file system partition taking up the rest of the space.

Then reboot with the xubuntu alternate install CD and install in text mode.
When you get to the partitioning section, just select your first partition as the root "/"

---

### Post by WillT87 on 2008-12-12
so use the gparted tool on puppy then use an xubuntu iso and install?

Im posting in this section for a reason :D

---

### Post by TJCIB on 2008-12-12
Exactly

Your computer will be either really slow or impossible to run an *ubuntu LiveCD.  Puppy solves that because it can run on just about anything and it has the tool you need.

Once you're done getting your partitions sorted out, just continue with a text-mode install from the xubuntu iso that you burned.

---

### Post by WillT87 on 2008-12-12
great... i only have one cd left :(

---

### Post by rlogan on 2008-12-13
I installed the Ubuntu Server edition on a similar spec machine (slightly more ram) and then installed the xfce-desktop package.

Worked fairly well considering it was a 500Mhz machine, maybe worth a try

Cheers

---

### Post by TJCIB on 2008-12-13
you can install Puppy to a USB Pen Drive =)

Not sure if you need the CD or just the .iso though

---

### Post by WillT87 on 2008-12-13
I dont think my bios will support it anyway to change that?

---


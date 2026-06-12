---
title: "Need help deleting Ubuntu OS"
date: 2009-05-05
forum: New to Ubuntu
---

### Post by Varg_Gorgon on 2009-05-05
First off, I'm a true newbie so any step by step info would be greatly appreciate it. 
Secondly, the problem is I have Ubuntu installed twice on my labtop (grub had the start up error so I installed Ubuntu a second time and now my labtop works). Problem is, my disk is at 99% so I cannot install anything (like I have an update right now, and it won't work 'cause there's not enough space). Now, when I start up my computer I choose the option at the top, it says that this Ubuntu 9.04 (hd0,7) ext.3. I have Partition Editor, and I understand I can expand a partition, but I don't know how. 

Partition editor tells me that:

[LEFT] partition: /dev/sda1                       file system: ext3  size: 66.85 gb                           used: 2.87 gb                                             unused: 63.98 gb flags:                                           boot
partition: /dev/sda2                file system: extended                                                                                                                                 size: 7.68 gb used:                                            --                                                                               unused: --
partition:    /dev/sda8                    file system: ext3                                                                       mount point: /                                                                       size: 2.33 gb                                 used: 2.20 gb                                         unused: 127.69 mb
   partition: /dev/sda9              file system: linux-swap                                                                                                                  size: 172.54 mb used:              --                                                                                     unused:--
    partition: /dev/sda6                  file system: ext3                                                                                                                                                    size: 2.33 gb                                  used: 2.02 gb                                           unused: 319.16 mb
   partition: /dev/sda7             file system: linux-swap                                                                                                                     size: 172.54 mb                                  used: --                                                                           unused: --
    partition: /dev/sda5                 file system: linux-swap                                                                                                                              size: 2.33 gb                                         used: --                                                                             unused: --

Sorry for the editing, I don't know how to copy-paste the results from Gparted. 


[/LEFT]

---

### Post by zvacet on 2009-05-05
```
sudo fdisk -l
```
Post output here.

 You can delete one Ubuntu partition with [Gparted live CD.]("http://gparted.sourceforge.net/")You can also delete one swap and after all this you will maybe need to reinstall grub.Read [this]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") instructions.

---

### Post by laithbsoul on 2009-05-05
i'd say just install ubuntu over them both and start fresh back any thing you truly need to a flash drive

---

### Post by Bölvaður on 2009-05-05
you do not uninstall an OS unless if it is installed in a weird manner like with Wubi (you do not seem to be using that so you're in luck). All you need to do is delete the partitions the OS was on and expand the one you want.


If you just installed few moments ago and havent done much changes to settings I would advice you to install ubuntu from scratch (as installing takes very short time and moving data on harddisk when resizing partitions does not take as short time).

1. Prepare partitions

Depending on if you want to use Ubuntu for a long time or you are just checking it out. If you are going to check it out, then ignor everything I will say about data partition. But if you are going to use ubuntu in the long term and even considering to use other distributions, then I hope you'll have a special data partition to make your life easier in the long run.

a. Take pen and paper, draw the size of the partions you want to use.
  i) first partition is for Ubuntu. It doesnt need more than 15 GiB, place it at front of the disk.
  ii) if you have a laptop have a swap partition of equal size of your RAM, if you have desktop you will only need 150MiB swap partition... but you can have it 250 just to be safe. Have it at the other end of the disk.
  iii) Your data partition takes the rest of the space in between those two

b. Take backups of all your data (and configs if you want)

c. Boot from your live cd
  i) Launch Gparted
  ii) Delete all partitions
  iii) Create all the partitions according to your plan

d. Install Ubuntu
  i) Go through the normal process
  ii) Choose MANUAL when you are supposed to do the partitions
  iii) select the big partition and have "/data" as mount point with ext3 as filesystem
       have the smaller partition as "/" and have ext3 also as filesystem.
You can have ext4, but I cannot guarantee it will never fail you, but it is faster and better than ext3... but then again, ext3 is stable and trouble free.
The swap partition is automatically mounted correctly.
   iv) Continue the installation process

e. Setting up Ubuntu
  i) Linking your data partition to your home folder. (GUI version... because people with lower than 50 posts are scared of the terminal ;) even though it is easier)
press Alt+F2 and type ```
gksu nautilus /
```
  ii) right click on the directory named data
click properties &#8594; permissions. Change owner and group to your user name.
Change Access to "Read and Write" for owner, group (and perhaps others so everyone can access the data on there, but try avoid this for now. no real gain for your situation at the moment).
now close nautilus (file manager), as we do not want to do the next steps as super user (root)
  iii) cut the important directories in your home folder (video, documents, music and pictures) and paste them the new /data partition. If you cannot do that you did the permissions in the previous step incorrectly.
  iv) high light the directories and right click on them. Select "Make Links"
  v) cut the links into your home partition and rename them exactly like their counterparts in /data. **These will work like shortcuts so your ~/Documents will now actually be located in /data/Documents**

If Im not mistaken you are done now....

---

### Post by Didius Falco on 2009-05-05
Varg,

Personally, I'd recommend wiping the whole drive and starting fresh. If you have things you need to keep, back those up from your now-working version.

Then wipe the whole hard drive from the Live CD and make 3 or 4 partitions. The / partition, which is going to be the root of your system. a /Home partition, which will be a separate partition to keep your configuration files  and your own data in (Ubuntu will see it and seamlessly add it in - from within Ubuntu, it'll look like its on the same partition), and a swap partition.

The 4th, optional partition, is a Data partition (name it whatever you want, the name isn't important) to store your own files in. I did this at the recommendation of one of the long-time linux users and it has worked out very well for me.

I'd recommend that the / partition be 15-20 Gigs

The /Home partition 25-30 Gigs

The Swap file should be the same size as however much ram you have, unless you plan on editing huge files.

The Data partition size, if you decide to do that, is up to you. Only you know what kind of data and how much there will be.

The reason I say it'd be easier, by the way, is that you are going to have to edit a couple of files (menu.lst and fstab) and get your Grub fixed in order to get everything back in order.

It's up to you, of course and many here will help you achieve whatever path you decide to take, but that is my .02 on it.

Regard,

Didius

On Edit: depending on your disk space the / and /Home partitions can be smaller. I've got a lot of room to play with, so I tend to go pretty large...

---

### Post by Varg_Gorgon on 2009-05-05
Hi [zvacet]("http://ubuntuforums.org/member.php?u=79320") this is what I got from sudo fdisk -l: 

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4d384d37

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8727    70099596   83  Linux
/dev/sda2            8728        9729     8048565    5  Extended
/dev/sda5            9380        9729     2811343+  82  Linux swap / Solaris
/dev/sda6            9054        9357     2441817   83  Linux
/dev/sda7            9358        9379      176683+  82  Linux swap / Solaris
/dev/sda8            8728        9031     2441817   83  Linux
/dev/sda9            9032        9053      176683+  82  Linux swap / Solaris

Partition table entries are not in disk order

- [Bölvaður]("http://ubuntuforums.org/member.php?u=338535") I don't really understand what you meant by "data partition." I don't have any data I wanna save, though. I'm using Ubuntu as my sole OS at the moment.

---

### Post by Bölvaður on 2009-05-05
> **Varg_Gorgon said:**
> 
- [Bölvaður]("http://ubuntuforums.org/member.php?u=338535") I don't really understand what you meant by "data partition." I don't have any data I wanna save, though. I'm using Ubuntu as my sole OS at the moment.

What I am suggesting is to have your personal data on a single partition, so every time you want to format the ubuntu partition, you will not touch your data. And you will be able to mount that partition right onto your new install or any other time when you set up any distribution. It will save you some work in the long run.


The simple way is just having 2 partitions. One small swap file and the rest is ext3 or ext4 (or reiser which is quite good filesystem). But then you'll have to back up all your data if you are going to do anything with the ubuntu partition. And it will be annoying to dual boot with 2 distros accessing that same data... really annoying.

---

### Post by Varg_Gorgon on 2009-05-06
Hey guys, just wanted to say that everything  is working just fine. I especially wanted to thank [Bölvaður]("http://ubuntuforums.org/member.php?u=338535") and [Didius Falco]("http://ubuntuforums.org/member.php?u=802278") for their detailed instructions and all that. Thanks a lot guys!!
Ps. Ubuntu rocks!

---

### Post by Didius Falco on 2009-05-06
Glad it all went smooth. Enjoy!!

If you would, please, mark this thread as solved. Instructions in my Sig.

Regards,

Didius

---


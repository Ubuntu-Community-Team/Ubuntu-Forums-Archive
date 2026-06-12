---
title: "modify size File System"
date: 2009-10-29
forum: New to Ubuntu
---

### Post by shaheru on 2009-10-29
Hello,
I have a dual boot linux/windows shared as following:

sda6 / (file_system)   79GB
sda7 /home            79GB 

sda1 /media/disk corresponding to windows partition 68GB

I would like to give more space to my home directory from the sda6 and would appreciate to have some input about the size that is really needed for the file_system, and also if there is some command to do this partition without the need of a cd.

Thank you for your clarifications!

---

### Post by Bölvaður on 2009-10-29
You have to use the live cd to do changes to your root partition. I'll show you why.

I just tried
> The partition could not be unmounted from the following mount points:

/

Most likely other partitions are also mounted on these mount points. You are advised to unmount them manually.

So that would mean if you could unmount your /home this would be no problem... but now see this.

> umount: /home: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))



I'm currently using 6 GiB out of 25 GiB on a not so old system, so I have few programs installed.
The more programs you install the more will be added to your root partition. You should have** 20 &#8594; 30 GiB** depending on for how long you are going to go without going to a newer version of ubuntu and how much you download from synaptic.
By cleaning out downloaded .deb packages via the command ```
sudo apt-get clean
```
you should get considerable space freed up (depending on how much stuff you downloaded).

*added*
you will not want to run out of space. As things get _very_ weird when it happens.

---

### Post by ibizatunes on 2009-10-29
The / partition, you need a maximum of 10GB unless you have a huge application, or a database
the rest can be  /home

You can change it with the GPARTED Live CD, or the version that is built into Ubuntu live disc, its up to you!!

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

A new version of Ubuntu is out today, so maybe backup your data, clean rebuild your PC with the new partition table size, killing two birds with one stone!!

Up to you!

---

### Post by shaheru on 2009-10-29
Ok, thank you both,
As I am processing huge datasets (more than 5GB each run) I would need also to reduce the windows part. In this case what is the best way to resize all partitions?

---


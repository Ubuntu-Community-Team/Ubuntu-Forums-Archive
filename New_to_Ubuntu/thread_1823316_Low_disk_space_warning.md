---
title: "Low disk space warning"
date: 2011-08-11
forum: New to Ubuntu
---

### Post by bradlees on 2011-08-11
I am getting a low disk space, only 60 mb warning. I thought that I had partitioned plenty of space for ubuntu. Its a toshiba satellite laptop with two 125 gb hdds, windows 7 on one, ubuntu the other. I may be incorrect, but there should be plenty of space?

Also, now, after selecting ubuntu from the bootloader, I get four linux options where before I only got two. 2.6.38-10 an 2.6.38-8 generic and their recovery options. The -10 doesnt work, and the -8 now has a sidebar with icons and doesnt have the top bar options it previously did.

What am I missing?

Thanks for any help.

---

### Post by Toz on 2011-08-11
> **bradlees said:**
> I am getting a low disk space, only 60 mb warning. I thought that I had partitioned plenty of space for ubuntu. Its a toshiba satellite laptop with two 125 gb hdds, windows 7 on one, ubuntu the other. I may be incorrect, but there should be plenty of space?
Lets see how you're partitioned and what the usage is. Open a terminal window, type in the following and post back the results:
```
df -h
```

> Also, now, after selecting ubuntu from the bootloader, I get four linux options where before I only got two. 2.6.38-10 an 2.6.38-8 generic and their recovery options. The -10 doesnt work, and the -8 now has a sidebar with icons and doesnt have the top bar options it previously did.
Installing the -10 kernel does this. If the -10 kernel doesn't work (as it doesn't work for me either), just go to the software manager and remove it. Everything should be reset to the way it was.

---

### Post by bradlees on 2011-08-11
> **Toz said:**
> Lets see how you're partitioned and what the usage is. Open a terminal window, type in the following and post back the results:
```
df -h
```
Installing the -10 kernel does this. If the -10 kernel doesn't work (as it doesn't work for me either), just go to the software manager and remove it. Everything should be reset to the way it was.

here is what I got:
Filesystem            Size  Used Avail Use% Mounted on
/dev/loop0             17G   16G   58M 100% /
none                  999M  672K  999M   1% /dev
none                 1006M  1.5M 1004M   1% /dev/shm
none                 1006M  224K 1006M   1% /var/run
none                 1006M     0 1006M   0% /var/lock
/dev/sdb2             112G   18G   95G  16% /host

---

### Post by jerrrys on 2011-08-11
sudo apt-get clean

sudo apt-get autoclean

sudo apt-get autoremove

that will free up some space

---

### Post by idoitprone on 2011-08-11
> **bradlees said:**
> here is what I got:
Filesystem            Size  Used Avail Use% Mounted on
/dev/loop0             17G   16G   58M 100% /
none                  999M  672K  999M   1% /dev
none                 1006M  1.5M 1004M   1% /dev/shm
none                 1006M  224K 1006M   1% /var/run
none                 1006M     0 1006M   0% /var/lock
/dev/sdb2             112G   18G   95G  16% /host

you have a pretty small system. It is only 17 gb. Try to uninstall excess kernels and remove some files.

You can try to move ubuntu on its own partition. Either way, wubi is not a long term solution and you dont have space anymore

---

### Post by Toz on 2011-08-11
> /dev/loop0 17G 16G 58M 100% /
Well its full. You've got 2 partitions, the root is 17GB and /client is 112GB. Is this some sort of persistent usb install? As jerrys points out above, you're going to need to clean out some space from your root (/). You may also have to look at uninstalling some applications. The other alternative is to resize the existing partitions and move some space from /client to /.

EDIT: Ahhhh, wubi.

---

### Post by bradlees on 2011-08-11
So I am using the wubi and not a full install? I would gladly resize the partition if that's what it takes. I would use that whole 125gb hd for ubuntu.

Any tips on doing this? SHould I start with a live cd install?

Also, what of the usb thing? I keep getting a message about an unrecognized device or something and nothing is connected.

---

### Post by Paqman on 2011-08-11
> **bradlees said:**
> So I am using the wubi and not a full install?

Yes, you can tell from the way you have /host in your filesystem.

You'll need to reinstall from scratch using the LiveCD or a USB if you want more space. In the meantime the command jerrys gave you, and the advice to uninstall any unused kernels will give you some room to play with.

If you take a backup of your home folder (including hidden folders, hit Ctrl-H to see those) then you can copy it back into your new system and it'll preserve your application settings. You could also use [apt-clone](apt:apt-clone) or a bit of [old-school dpkg trickery]("http://ubuntuforums.org/showthread.php?t=261366") to reinstall all your apps.

---

### Post by bradlees on 2011-08-12
There really isn't anything I care too much about preserving on the current system.
Should I reformat the drive I am using and overwrite the existing linux kernels?

---

### Post by -kg- on 2011-08-12
> **bradlees said:**
> There really isn't anything I care too much about preserving on the current system.
Should I reformat the drive I am using and overwrite the existing linux kernels?

If you reformat the partitions on your current drive, you are in effect erasing everything on those partitions, including any existing kernels.

Since you express interest in wiping everything and installing only Ubuntu, my suggestion to you would be to save anything you have on your partitions presently that you want to save.  Then you want to make ***absolutely sure*** that Ubuntu will run on your computer by running a Live CD (or USB) and checking out all the functions.

I say that because I'm not exactly sure how WUBI works.  I don't know whether it uses some Windows drivers to communicate with the hardware, or whether those functions are independent.  If it all works satisfactorily, then...

Run the Installation portion of the Live CD/USB.  When you come to the partitioning section, select "Use Whole Disk" and you'll be good to go.  The installer will delete the old partitions, create the required new partitions and install Ubuntu into them.

---

### Post by bradlees on 2011-08-12
sweet avatar, max:guitar:

---

### Post by -kg- on 2011-08-13
Thanks!  Max is my hero, my fashion advisor/coordinator, and my golf instructor.  :biggrin:

Oh, and he knows a bit about computers, too, considering he's a computer animation and all... :D

---

### Post by pjstock on 2012-03-24
> **Toz said:**
> Lets see how you're partitioned and what the usage is. Open a terminal window, type in the following and post back the results:
```
df -h
```



could I interject and ask help with this same problem?
I am completely befuddled by my Low Disk Space problems

Here's what I get with df -h

julie@julie-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              19G   18G   64K 100% /
none                  750M  284K  750M   1% /dev
none                  754M  352K  754M   1% /dev/shm
none                  754M  332K  754M   1% /var/run
none                  754M     0  754M   0% /var/lock
none                  754M     0  754M   0% /lib/init/rw
/dev/sdb1             228G  185G   32G  86% /media/e0275508-079c-4be0-84f0-3919816ce305

> **jerrrys said:**
> sudo apt-get clean

sudo apt-get autoclean

sudo apt-get autoremove

that will free up some space

I tried these steps but don't seem to have freed up any space. What am I doing wrong? results before and after and steps here:

/dev/sda1              19G   18G   64K 100% /
none                  750M  284K  750M   1% /dev
none                  754M  352K  754M   1% /dev/shm
none                  754M  332K  754M   1% /var/run
none                  754M     0  754M   0% /var/lock
none                  754M     0  754M   0% /lib/init/rw
/dev/sdb1             228G  185G   32G  86% /media/e0275508-079c-4be0-84f0-3919816ce305
julie@julie-desktop:~$ ^C
julie@julie-desktop:~$ sudo apt-get clean
[sudo] password for julie: 


Sorry, try again.
[sudo] password for julie: 
julie@julie-desktop:~$ sudo apt-get autoclean
Reading package lists... Done
Building dependency tree       
Reading state information... Done
julie@julie-desktop:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  acroread-common wine1.2-gecko
0 upgraded, 0 newly installed, 2 to remove and 10 not upgraded.
After this operation, 8,278kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 257041 files and directories currently installed.)
Removing acroread-common ...
Removing wine1.2-gecko ...
julie@julie-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              19G   18G  7.9M 100% /
none                  750M  284K  750M   1% /dev
none                  754M  388K  754M   1% /dev/shm
none                  754M  332K  754M   1% /var/run
none                  754M     0  754M   0% /var/lock
none                  754M     0  754M   0% /lib/init/rw
/dev/sdb1             228G  185G   32G  86% /media/e0275508-079c-4be0-84f0-3919816ce305
julie@julie-desktop:~$ ^C
julie@julie-desktop:~$

---

### Post by Toz on 2012-03-24
@pjstock, the main partition of your main hard drive is full:
> /dev/sda1 19G 18G 7.9M 100% /

You need to find out where the disk space is being used and try to free some up by deleting unneeded data and/or removing unnecessary programs (the previous commands didn't free up much space).

As a first step, try running the following command from a terminal window:
```
du -mscx ~/*
```
...this will show you how the disk space is being used within your profile.

If there is more than 1 account on this computer, you can try:
```
sudo du -mscx /home/*
```
...to show how the disk space is being allocated among all of the users, and:

```
sudo du -mscx /*
```
...to see how the space is allocated among system files on the whole drive (note: this will take time to complete).

This one might also be interesting (checks your log files):
```
sudo du -mscx /var/log/*
```

Note: All results are displayed in megabytes.

---


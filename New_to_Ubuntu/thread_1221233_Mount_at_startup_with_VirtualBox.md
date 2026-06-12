---
title: "Mount at startup with VirtualBox"
date: 2009-07-23
forum: New to Ubuntu
---

### Post by JPHespanha on 2009-07-23
Hi!

I have recently installed Ubuntu 9.04 Desktop using Sun's VirtualBox. My host system is Windows XP. I managed to get a virtual disk, a CD and a USB device installed on startup, but the share folder must be mounted every time I start up the system.

This share allows me to exchange files between the two OSs. The command I use is:
mount -t vboxsf [HostOS Share Name] [Ubuntu Mount Point]

I have read some posts telling to modify the /etc/fstab file, but I am unsure if this is the right way to do it using a virtual machine...:confused:

---

### Post by andrew.46 on 2009-07-23
Hi JPHespanha,

> **JPHespanha said:**
>  The command I use is:

```
mount -t vboxsf [HostOS Share Name] [Ubuntu Mount Point]
```


On my own Ubuntu guest system I add the following to the /etc/fstab:

```
share	/home/andrew/Desktop/share	vboxsf	uid=andrew,gid=users	0	0
```

with */home/andrew/Desktop/share* being the shared folder and *andrew* being the user.

All the best,

Andrew

---

### Post by JPHespanha on 2009-07-24
Hi Andrew!

I have tested this (after spending a while to manage to edit the /etc/fstab with a```

sudo gedit
```) and it did not work.

Here is the command I have used:
```
share    /home/jph/PartilhaUbuntu_XP    vboxsf    uid=jph,gid=admin    0  0
```

However, as I am _really_ an absolute beginner, I do not know how to check what was gone wrong. Any commands or logs to run or check? :)

---

### Post by andrew.46 on 2009-07-24
Hi JPHespanha,

> **JPHespanha said:**
> 
I have tested this (after spending a while to manage to edit the /etc/fstab with a

```
sudo gedit
```) 

and it did not work.


My apologies I should have broken it all down a little more :-). Strictly speaking to edit fstab you are best to make a backup first:

```
sudo cp /etc/fstab /etc/fstab_bak
```

and then edit the original by first pressing Alt + F2 and typing in:

```
gksudo gedit /etc/fstab
```

The backup is just in case things go horribly wrong :-).

> Here is the command I have used:

```
share    /home/jph/PartilhaUbuntu_XP    vboxsf    uid=jph,gid=admin    0  0
```

However, as I am _really_ an absolute beginner, I do not know how to check what was gone wrong. 

A few small things could be wrong. The folder /home/jph/PartilhaUbuntu_XP must exist as the system will not create it for you. Have a look at:

```
ls -ld /home/jph/PartilhaUbuntu_XP
```

My own shared folder reads:

```
andrew@skamandros~/Desktop$ ls -ld share/
drwxr-xr-x 3 andrew users 4096 2009-07-25 10:43 share/
```

Anoher thing is your use of *gid=admin* which I am not sure about. Try the setting that I used which is *gid=users* or match it with the permissions of your shared folder (as i have demonstrated above). It could very well be *gid=jph* I have just realised on Ubuntu.

All the best,

Andrew

---

### Post by JPHespanha on 2009-07-28
Andrew:

First of all, thanks for the patience and the detailed explanations. I am learning a few things about Ubuntu in the process, which is good. However, it seems this new share command is having no effect (is this possible?) in the configuration of the system.

As you suspected, my folder settings were different from what I was guessing:

```
jph@jph-casa:~$ ls -ld /home/jph/PartilhaUbuntu_XP
drwxr-xr-x 2 jph jph 4096 2009-07-23 03:32 /home/jph/PartilhaUbuntu_XP
```

I assumed that gid would be the group my user is attached to, which is Admin, but things are not so linear. There is also a jph group, but is not attached to any user, so I guess Ubuntu is taking care of those aspects.

Anyway, the share had no effects. The fstab has other two devices, as follows:
```
    13    /dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
    14    /dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

I am not configuring a floppy through VirtualBox, so naturally I get a "Error opening device" when I do a:
```
sudo vol_id --uuid /dev/fd0
```

But for the CD-ROM (in fact an ISO image) I do get a UUID:
```
jph@jph-casa:~$ sudo vol_id --uuid /dev/sda1
1bdc9e60-4d9a-4c29-8bf4-7f3e6b318dd5
```

So, apparently, fstab is working fine, except for the share...

Regards,
JP Hespanha

---

### Post by andrew.46 on 2009-07-29
Hi JP Hespanha,

I confess that I am a little stumped. It would not hurt to have a quick look at your virtualbox settings to make sure the shared folder settings are correct. I have attached a screenshot to this post showing my own successful settings.

If this is all correct not all is lost. I would suggest you could post a similar query in the following thread:

How to fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

Bodhi-zazen who wrote this guide is not only very knowledgeable about fstab but also virtualbox and will have more of an idea than me about the problem.

All the best,

Andrew

---

### Post by JPHespanha on 2009-07-31
Hi, Andrew!

From your VBox settings, I understand there is a fundamental difference between our configurations: you are running a Ubuntu host and I am running a XP host! Is that so?

Because otherwise I can not specify a Ubuntu mount point from the VBox share folder settings, which can only browse the host file system.

That is certainly the answer to my system being unable to share the folder at startup.

Anyway, thanks for the reference to "How to fstab"; I will read it with care.

Regards,
JP Hespanha

---

### Post by andrew.46 on 2009-07-31
Hi JPHespanha,

> **JPHespanha said:**
> From your VBox settings, I understand there is a fundamental difference between our configurations: you are running a Ubuntu host and I am running a XP host! Is that so?  Because otherwise I can not specify a Ubuntu mount point from the VBox share folder settings, which can only browse the host file system.

Not quite. I am running a Slackware host with Ubuntu and Windows XP guests. But certainly perhaps a difference is that i am not running a *Windows* host.

> Anyway, thanks for the reference to "How to fstab"; I will read it with care.

I am sorry I could not assist you to solve this issue :(.

Andrew

---


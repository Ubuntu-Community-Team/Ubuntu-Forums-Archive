---
title: "Virtual Box placement"
date: 2009-04-10
forum: New to Ubuntu
---

### Post by nml on 2009-04-10
Hey All..

Current partition setup:

sda1     Ubuntu
sda2     XPpro
sda3     formatted ext3, is only being used for storage
sda4     extended  (only used for swap right now) and is very small (3 gigs)

I want to mess with a virtual machine or two, but want to install Virtual Box on my unused sda3 partition......when I installed it through Ubuntu, is installed on sda1.

Is there a way to put Virtual Box on my sda3, or at least put the virtual machines on sda3

thanks,

Mick

---

### Post by howefield on 2009-04-10
Install Virtualbox on sda1 but install your virtual machine on sda3 when you create the hard disk for it.

Simple.

---

### Post by nml on 2009-04-10
> but install your virtual machine on sda3 when you create the hard disk for it.

I'll keep reading, but this is where my problems seem to begin...I have VB on sda1, but I can't seem to find an option that will let me see or write/create anything on sda3.  I've mounted sda3 on my Ubunut desktop (which is on sda1) but I don't know how to navigate to sda3 from within the VB wizard.

sorry to be so dense..

Mick

---

### Post by Xispa on 2009-04-10
You should know where is the sda3 mount point. 
To list the mounted file systems, type in terminal

```
mount
```

and locate the line for sda3. It should be something like:

```
/dev/sda3 on /home type ext3 (rw,relatime)
```

As you can see, in the example, sda3 partition mount point is /home: if you want to put virtual machine on sda3, save the harddisk for virtual box in any place located into mount point file system for sda3. In this example, folder and subfolders of /home.

---

### Post by nml on 2009-04-10
> As you can see, in the example, sda3 partition mount point is /home: if you want to put virtual machine on sda3, save the harddisk for virtual box in any place located into mount point file system for sda3. In this example, folder and subfolders of /home.

cool, I'll give that a try....

seems my 'mount point' is listed under 'media' in /home folder....

From another post, I apparently can change the write permissions for this mount by the following command

> sudo chown -R yellow:yellow /media/disk
ls -la /media

(after changing 'yellow' to my log in name)

not sure if that helps me, but will try both..

thanks

Mick

---

### Post by Xispa on 2009-04-10
with the command
```
sudo chown -R yellow:yellow /media/disk
```
you will assign yellow user and yellow usergroup as the owners of /media/disk folder. With the parameter -R the changes will be made recursively. 
After this, you can change the read/write settings in a graphical way by right-clicking on folder and selecting properties > privileges.

You can view the help of chown command by typing
```
chown --help
```
or the complete manual with
```
man chown
```

Jordi

---


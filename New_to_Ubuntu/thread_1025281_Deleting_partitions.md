---
title: "Deleting partitions"
date: 2008-12-29
forum: New to Ubuntu
---

### Post by linkmaster03 on 2008-12-29
I'm planning on deleting two partitions at the beginning of my drive. (some bloatware windows recovery partition, and windows itself) First of all, is this going to cause any problems with there not being a primary partition or something? This is how my partitions are currently setup, shown in gparted:

[img]http://img367.imageshack.us/img367/6182/29decmon2245qi2.png[/img]

Secondly, where will I have to renumber my drives? I know I will have to shift everything back two partitions in /boot/grub/menu.lst, and /etc/fstab. Where else?

Thanks guys.

---

### Post by handydan918 on 2008-12-29
You are not trying to do anything impossible. 
However...
ALL partitioning operations are inherently hazardous. never partition without backing up.

Before you partition, and after you back up, do this; it reads all the packages you have installed on your system and prints it to a file called softwarelist.


```
sudo dpkg --get-selections > softwarelist
```


That list contains every piece of software required to reproduce the state your PC is currently in.
So, if you have a backup of your documents (such as your /home directory) AND this softwarelist, then this is all you need to do a full backup and restore.
Like this:

```
sudo dpkg --set-selections < softwarelist

```
This prepares everything, but does not install the various programs in the softwarelist file.
For that you need to run 

```
sudo apt-get dselect-upgrade
```

This will ensure that all the packages on the softwarelist are installed.

Have fun.

---

### Post by 67GTA on 2008-12-29
The only two places to update are /boot/grub/menu.lst and /etc/fstab.

---

### Post by deltadave on 2008-12-30
i just repartitioned my new computer similar to what you are talking about and had no problems.  I left the two beginning partitions though because they are vista and a vista recovery but resized the vista partition so I could put linux on it.  It doesn't look like you have any files on there since it doesn't show any space being used on sda2.  From my (**limited**) experience it looks like you could combine all the first partitions and then resize sda3 to take up all that space.

Another package I found tonight that may be helpful is "aptoncd" and it copies all your installed packages to a cd/dvd so you put them on a different computer and have all the same packages installed.  In my case I just put it on my usb drive and I'll "install" the packages on the new computer from the usb drive.

---

### Post by linkmaster03 on 2008-12-30
Thanks 67GTA and others. :D

---

### Post by sydbat on 2009-02-02
> **handydan918 said:**
> You are not trying to do anything impossible. 
However...
ALL partitioning operations are inherently hazardous. never partition without backing up.

Before you partition, and after you back up, do this; it reads all the packages you have installed on your system and prints it to a file called softwarelist.


```
sudo dpkg --get-selections > softwarelist
```


That list contains every piece of software required to reproduce the state your PC is currently in.
So, if you have a backup of your documents (such as your /home directory) AND this softwarelist, then this is all you need to do a full backup and restore.
Like this:

```
sudo dpkg --set-selections < softwarelist

```
This prepares everything, but does not install the various programs in the softwarelist file.
For that you need to run 

```
sudo apt-get dselect-upgrade
```

This will ensure that all the packages on the softwarelist are installed.

Have fun.Will this allow for a complete reinstall of 8.04.2? What I mean is, can I do a full system reinstall, put my backup of /home into it's new partition, then run this script to install all my apps? If so, very cool. If not...

Also, do I delete fstab, or its contents, so that the new install will find everything properly?

---


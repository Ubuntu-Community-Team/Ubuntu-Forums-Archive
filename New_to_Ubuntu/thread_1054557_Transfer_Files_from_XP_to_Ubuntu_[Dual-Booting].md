---
title: "Transfer Files from XP to Ubuntu [Dual-Booting]"
date: 2009-01-29
forum: New to Ubuntu
---

### Post by UnknownFear on 2009-01-29
I am dual-booting Windows XP and Ubuntu 8.10. Now, I can access my Windows XP harddrive in My Computer, however, I can't access Ubuntu from Windows XP. Seeing as how I can't use my iPod Touch on Ubuntu, is there a quick way to get a folder of all my songs from Windows XP to Ubuntu?

---

### Post by emarkd on 2009-01-29
I've never used it, but there's an ext filesystem driver for XP that should allow you to access your Ubuntu partition.  A google search turns up this:

[http://linuxhelp.blogspot.com/2007/03/mount-ext2-or-ext3-partition-in-windows.html]("http://linuxhelp.blogspot.com/2007/03/mount-ext2-or-ext3-partition-in-windows.html")

I also, don't have an ipod, but I think there's utilities for Linux that support them.  gtkpod comes to mind.  I'm sure it's in the repositories.

---

### Post by UnknownFear on 2009-01-29
Ok. I installed it and I addigned my Linux partition a letter. When I click on it to go into it, it says the driver is not formatted and asks me if I want to format it. I said no. Any help with this?

---

### Post by emarkd on 2009-01-29
Sorry.  Like I said I've never used it.  Maybe somebody will come along with some experience on the issue.

---

### Post by UnknownFear on 2009-01-29
Ok. I'm not going to format it incase it will wipe out my Linux OS, than I'll have to reinstall it. Ugh..

---

### Post by oyroy on 2009-01-29
From what I understand you want the music files you use on your iPod Touch on Windows to be accessible when running Ubuntu? As you can access you Win-drive from Ubuntu, does it not work to locate your iTunes-archive when on Ubuntu? (I cant remember where it is by default), or if you only have your songs on your Touch, browse it from windows, using «View hidden folders and files» option in folderoptions, and make a copy of all the music on the Touch to a folder in Windows, and then access it from Ubuntu the way you access any other file on your win-drive.

---

### Post by UnknownFear on 2009-01-29
I'll try this. I am just transfering all my songs from my iPod to my computer in Windows.

---

### Post by oyroy on 2009-01-29
Good luck!

Im not sure about the iPod Touch, but on my iPod Nano 3rd-gen, my songs are renamed into cryptic names, which makes it difficult to sort. Kinda crappy of Apple, but if you just load them all to a folder, most music-players should load out the tags, and sort the music correctly. Might even use a renaming-prog to fix the names once you have it on your HD, for easier copying and stuff if you just want certain files.

Tho, you really should give gtkpod a go and see if you can access the iPod Touch directly from Ubuntu :)

---

### Post by egalvan on 2009-01-29
> **UnknownFear said:**
> Ok. I installed it and I addigned my Linux partition a letter. When I click on it to go into it,** it says the driver is not formatted and asks me if I want to format it**. I said no. Any help with this?

Unfortunately, this is a problem with the driver. It hasn't caught up to the newest Linux file systems.

from the web site:

[I] Large inodes
The current version of Ext2 IFS only mounts volumes with an inode size of 128 like old Linux kernels have.

Some very new Linux distributions create an Ext3 file systems with inodes of 256 bytes. Ext2 IFS 1.11 is not able to access them.

Currently there is only one workaround: Please back up the files and create the Ext3 file system again. Give the mkfs.ext3 tool the -I 128 switch. Finally, restore all files with the backup.
[/I]

---


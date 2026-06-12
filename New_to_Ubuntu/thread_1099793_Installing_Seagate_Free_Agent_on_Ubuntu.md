---
title: "Installing Seagate Free Agent on Ubuntu"
date: 2009-03-18
forum: New to Ubuntu
---

### Post by willsc on 2009-03-18
Hello everyone!
I am brand new to Linux and using Ubuntu.  I am using a HP Compaq nx7400 and trying to install my external 1 TB drive so I can access files that I have on it from a previous computer.

I have tried to search the forums but nothing is in there that I can find about this.

Any help is appreciated!  I have also looked on Seagate's site and they don't have any drivers that I can see for Linux. 

Thank you for your help!

CW

---

### Post by BDNiner on 2009-03-18
I don't think that you need drivers to install the drive. Does it connect using USB, Firewire, LAN, eSATA? What happens when you plug it in?

---

### Post by willsc on 2009-03-18
When I plug it in it says:

Unable to mount the drive "Free Agent Drive".  DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

When I had Windows it would autoplay and then be a drive I could access.  I must be missing a file or some setting.

---

### Post by willsc on 2009-03-18
USB connection to this laptop....don't have eSATA or Firewire....

---

### Post by BDNiner on 2009-03-18
Is that the entire error message. Have you installed the ntfs-3g package? I think this is all you need.

---

### Post by presence1960 on 2009-03-18
I don't know how recent this is but there are 2 workarounds. I remember reading about the Free Agent's power management being the problem.  [http://news.softpedia.com/news/Workaround-Released-for-Seagate-Free-Agent-73528.shtml](http://news.softpedia.com/news/Workaround-Released-for-Seagate-Free-Agent-73528.shtml)

I see you used this on another computer. Was it windows? Did you have a clean shutdown? If not you can get back into windows and shut it down cleanly. Then you should be able to access it provided this is the problem of course.

---

### Post by Kareeser on 2009-03-18
You may need to forcefully mount it... it **should** work properly after that, even after unplugging.

I don't know the command off-hand, so I'll let someone else answer.

---

### Post by LowSky on 2009-03-18
well lets see if we can see it

please post the output of these commands

```
lsusb

sudo fdisk -l


```

---

### Post by basketcase on 2009-03-18
My 500GB Free agent worked with either eSATA or USB right out of the box with a base install of 8.10.

How is it connected?

---

### Post by willsc on 2009-03-18
Wow I appreciate all of the tips!  I am so new to this that I don't know what some of this means. 

I do learn fast so bear with me.  I did disconnect it from Windows the right way.  My mother board fried on my computer that I am running Ubuntu on.  I had a friend of mine help put some low end parts to make it an internet/ email computer for home and that is about it.  

The external has everything Windows based from my laptop saved and backed up to it.  It has files that I would like to use and get off with this computer if possible.

I use a USB cord to connect it.  My laptop doesn't have eSATA or firewire.

I will go through all of these and see what I can do to get you more information.

Thank you!

---

### Post by ashwat on 2009-03-18
> **willsc said:**
> Wow I appreciate all of the tips!  I am so new to this that I don't know what some of this means. 

I do learn fast so bear with me.  I did disconnect it from Windows the right way.  My mother board fried on my computer that I am running Ubuntu on.  I had a friend of mine help put some low end parts to make it an internet/ email computer for home and that is about it.  

The external has everything Windows based from my laptop saved and backed up to it.  It has files that I would like to use and get off with this computer if possible.

I use a USB cord to connect it.  My laptop doesn't have eSATA or firewire.

I will go through all of these and see what I can do to get you more information.

Thank you!

Apart from all what everyone tells you to do, the first and foremost thing you need to do would be, connect your drive to a Windows system and rename it without any spaces. That did the trick for me.

---

### Post by stchman on 2009-03-18
> **willsc said:**
> Hello everyone!
I am brand new to Linux and using Ubuntu.  I am using a HP Compaq nx7400 and trying to install my external 1 TB drive so I can access files that I have on it from a previous computer.

I have tried to search the forums but nothing is in there that I can find about this.

Any help is appreciated!  I have also looked on Seagate's site and they don't have any drivers that I can see for Linux. 

Thank you for your help!

CW

Ubuntu supports USB hard drives.  Apparently Seagate put some BS cr@p program on the hdd.  Fire up gparted and delete the entire drive and all partition.

I am going to assume this drive is new.

Once you have deleted the entire drive (big gray space) you can then repartition the hdd.

I do most of my external drives in FAT32 as this will be compatible with all PCs out there.  If you go EXT2/3 you will limit your self to an OS that supports EXT file system.

---

### Post by jblackwe on 2009-06-10
Is there any need to install the software that comes with the Seagate? I am able to use it with no problems. I am only interested in the automatic syncing, is there a better way in Ubuntu to have my data automatically synced to my external hard disk? Thanks! 

jb

---

### Post by k3lt01 on 2009-06-10
The programs on your Seagate are for Windows PCs so if the drive is exclusively for an Ubuntu system there is no use in them at all. I have a Seagate 500gb drive also and the Seagate programs are only on it because my sister has a Windows machine and we both use the Seagate for storing photos.

---

### Post by scearley on 2009-06-13
I can't access the FreeAgent on Ubuntu.

In fact, when the drive is plugged in, I can't access any other USB drive.

If I try to access it (the drive does show up in the file structure, but nothing below the sdb1/ level in the tree) the error I get is 
```
TODO: have to rethink extra options
```

What kind of error is this?

---

### Post by Mark Phelps on 2009-06-14
From what I've read, this is a new problem plaguing quite a few of the Linx distros, not just Ubuntu.  There was one thread about hand-patching the HAL source code, and then patching the kernel, that did appear to fix it in SOME cases -- but this is not something that should generally be done as you run the risk of completely crippling your machine in the process.

---


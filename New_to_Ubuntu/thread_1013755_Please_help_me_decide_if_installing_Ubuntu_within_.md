---
title: "Please help me decide if installing Ubuntu within windows gives me what I want"
date: 2008-12-17
forum: New to Ubuntu
---

### Post by dgg9879 on 2008-12-17
Firstly, what I want to know is whether surfing the internet from Ubuntu when Ubuntu is running through windows is as secure as surfing the internet through Ubuntu as a standalone operating system. That is, can internet malware such as spyware and trojans that is only designed for windows get onto my pc if I'm surfing the internet from Ubuntu within windows?

Secondly, I'd like to know if there would be much noticeable difference in performance between Ubuntu and Ubuntu within windows.

If using Ubuntu within windows doesn't protect me than would using Ubuntu through a virtual machine be better?

My main reason for wanting access to Ubuntu on my pc is for surfing the internet. I have anti-spyware software for Windows XP but I believe most spyware is written for windows and so surfing the internet should be more secure this way.

I did not understand the need to partition drives as EXT3 filesystem for dual booting when I first set up my dual boot and was disappointed that substantial diskspace "dissappeared" in windows as a result. Shortly after I accidentally installed a program with a virus but fortunately I used macrium to make a ghost image of my basic windows xp setup beforehand so I'm back to square one without ubuntu but my windows system is running fine.

I've read on the internet about using Gnome Partition Editor from the Ubuntu cd to create partitions but the only options I get from my Ubuntu 8.04 cd are to do a full install or install within windows. 

So I'm a bit nervous about setting up partitions for Linux since I'm still not sure how and not sure how to install Linux to such partitions once they are set up (If I choose the manual install when installing ubuntu is it stratightforward?)

There has to be a swap file partition and the ubuntu operating system partition. Does the manual install instruct you to choose which part goes to which partition? Once you've created the partitions is it easy to tell which ones are the linux ones and which ones are the existing ones?

---

### Post by Pjotrovitz on 2008-12-17
Well, strictly you don't need more than one partition to run Ubuntu, but if you are only going to use it to surf safely on the web I would recommend running it inside a virtual machine instead.

---

### Post by lametike on 2008-12-17
no need swap if it is not a old machine

---

### Post by PartisanEntity on 2008-12-17
> **dgg9879 said:**
> Firstly, what I want to know is whether surfing the internet from Ubuntu when Ubuntu is running through windows is as secure as surfing the internet through Ubuntu as a standalone operating system. That is, can internet malware such as spyware and trojans that is only designed for windows get onto my pc if I'm surfing the internet from Ubuntu within windows?

Ubuntu running inside Windows will act like any other application. While no viruses or trojans will enter Ubuntu, your Windows system has its own security holes and vulnerabilities that will remain open if your computer is connected to the internet. Running Ubuntu inside Windows will not close Windows security holes.

> **dgg9879 said:**
> Secondly, I'd like to know if there would be much noticeable difference in performance between Ubuntu and Ubuntu within windows.

Yes, big differences. Operating systems tend to function slower in virtualisation.

> **dgg9879 said:**
> If using Ubuntu within windows doesn't protect me than would using Ubuntu through a virtual machine be better?

No, again, Ubuntu does not close Windows security holes. Only Microsoft can do that.

> **dgg9879 said:**
> My main reason for wanting access to Ubuntu on my pc is for surfing the internet. I have anti-spyware software for Windows XP but I believe most spyware is written for windows and so surfing the internet should be more secure this way.

I would install Windows inside a virtual machine inside a native installation of Ubuntu, keeping personal and work files in Ubuntu. That's safer.

> **dgg9879 said:**
> I did not understand the need to partition drives as EXT3 filesystem for dual booting when I first set up my dual boot and was disappointed that substantial diskspace "dissappeared" in windows as a result. Shortly after I accidentally installed a program with a virus but fortunately I used macrium to make a ghost image of my basic windows xp setup beforehand so I'm back to square one without ubuntu but my windows system is running fine.

Different operating systems use different filsystems. Windows uses FAT or NTFS, Ubuntu can use a multitude including Ext2 and Ext3, OS X uses HFS+.

Creating a new partition obviously means taking that space from an existing partition.

> **dgg9879 said:**
> I've read on the internet about using Gnome Partition Editor from the Ubuntu cd to create partitions but the only options I get from my Ubuntu 8.04 cd are to do a full install or install within windows. 

Is this Wubi you are talking about?

> **dgg9879 said:**
> So I'm a bit nervous about setting up partitions for Linux since I'm still not sure how and not sure how to install Linux to such partitions once they are set up (If I choose the manual install when installing ubuntu is it stratightforward?)

There has to be a swap file partition and the ubuntu operating system partition. Does the manual install instruct you to choose which part goes to which partition? Once you've created the partitions is it easy to tell which ones are the linux ones and which ones are the existing ones?

Linux is quite easy to install once you grasp the basics.

In the manual install it is up to you to decide where to mount parts of the OS.

The root / should be mounted on the largest partition you have made for Ubuntu.

Swap partition should be at least equal to your ram size and you can select 'swap' from the drop down menu, in the partition editor, to mount it there.

Hope this helps

---

### Post by philinux on 2008-12-17
There is a lot of fud surrounding wubi. The best info is direct from the faq's.

[http://wubi-installer.org/faq.php#requirements](http://wubi-installer.org/faq.php#requirements)

---

### Post by eldragon on 2008-12-17
i think the OP is talking about a wubi install vs a regular partition your drives install.

if this is the case:

when running ubuntu from the wubi install, your windows partition is safe.
when running windows...well, nothing changes.


about performance, im not sure, never used wubi.

if you choose to install through wubi, you will not need to partition your drive. the setup will act as another windows program, and can be removed from the add/remove program list.

if you choose to do the regular install, the installer will guide you quite well. but its always recommended to backup all your important data just to be safe. make sure you know how to restore from the windows install disc in case something goes terribly wrong. these are not only guidelines to installing a new operating system, they should be applied to life too :D

after doing the regular installer, you will be able to access window's partitions but not the other way arround (linux partitions will not show up under windows).

---

### Post by philinux on 2008-12-17
From the faq's


> What is the performance?

The performance is identical to a standard installation, except for hard-disk access which is slightly slower than an installation to a dedicated partition. If your hard disk is very fragmented the performance will degenerate.


---


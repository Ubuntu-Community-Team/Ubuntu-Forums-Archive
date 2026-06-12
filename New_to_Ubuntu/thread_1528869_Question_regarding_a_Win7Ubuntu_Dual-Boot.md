---
title: "Question regarding a Win7/Ubuntu Dual-Boot"
date: 2010-07-11
forum: New to Ubuntu
---

### Post by spartanreborn on 2010-07-11
Hello, I have been meaning to test out and learn how to use Linux for quite some time now. I grew up on Windows generally, and as such, I consider myself a fairly competent Windows user, but I want to see what all the buzz is about with this whole Linux thing (I installed Ubuntu a couple years ago, but shortly after doing that, that computer bricked and I never got around to trying it out again). So I decided that a good way is to set up a dual boot, so that I can use Linux most of the time, and when I encounter something that Linux has issues with (I hear that gaming can be difficult on Linux) or something I can't figure out how to do, I can switch to Windows.

From what I gather, Ubuntu is one of the more popular and easier to set up distributions out there, so I have gone ahead and downloaded the latest version off their site, but before I go ahead and begin installing everything, I have a question concerning how I should partition my HDD.

I have a 300 GB HDD, and a smaller 180 GB external drive that I use for backing up my important stuff (mostly schoolwork and music). If I had files on one OS, would I be able to access those files on the other OS? For example, I have some music (or movies, documents, pictures, whatever) on Ubuntu, but I happen to have Windows open at the moment. Would I be able to access the partition that the other OS is on, and access the documents stored on it (perhaps even copy documents and such from one OS's partition to the other OS's partition, say if I was running out of space on one partition), or would I need to keep an extra partition available for general storage?

Basically, should I just split my HDD 50/50 for the two OS's, or should I set up enough room on each partition for the two OS's , say 20-30 GB's for each OS, and dedicate the rest of my HDD to a general storage drive?


Any other general suggestions that I should keep in mind?
Thanks for any input.

---

### Post by cj.surrusco on 2010-07-11
> **spartanreborn said:**
> 
Basically, should I just split my HDD 50/50 for the two OS's, or should I set up enough room on each partition for the two OS's , say 20-30 GB's for each OS, and dedicate the rest of my HDD to a general storage drive?


Any other general suggestions that I should keep in mind?
Thanks for any input.

I would set up a partition in NTFS as a data partition to keep all of your files, while allowing each OS about 20GiB in two seperate partitions.   

You WILL be able to access files from your Windows partition in Ubuntu. However, it will not work the other way around. You can transfer files between the two file systems, but only from Ubuntu.

---

### Post by Mark Phelps on 2010-07-11
Just for some extra room, I would give Win7 30GB.  Winows OSs get very picky about NOT having extra space.

Also, second the idea of a large, shared NTFS partition for your data.

Finally, it would be better to install Win7 first, and to do that, allocated a 30GB NTFS drive on your partition, and install to that.

---

### Post by tmack2 on 2010-07-11
Hey, welcome to Ubuntu!
There are a few way's to experience Ubuntu and Windows on the same machine.
#1 Install Windows then install Ubuntu in a dual boot configuration using the Ubuntu boot manager.

#2 Install Windows and then install Ubuntu inside Windows using Windows boot loader.

#3 Install Ubuntu and install Windows in Ubuntu by way of VirtualBox./

I have computers set up all 3 ways.

If you choose option #3, you will be able to share a folder the same way as on a Windows network as well as some abilities of copy&paste. Not to mention you will be running both OS's at the same time.

Option 2 & 1 will allow you to boot to windows or Ubuntu. you will be able to pull files from the Windows partition and push files to the Windows partition.

If you choose option #1, you Will install Windows. Once Windows is installed and set up, Install Ubuntu by booting to the live disk. Once you are booted to the disk, choose install.
The Ubuntu installer will allow you to install the 2 OS's side by side. You will be able to choose the size of the partitions during this process.

If you choose option #2, you will Install Windows. Once Windows is set up, insert the Ubuntu disk in the cd/dvd rom and click jon the wobiexe file and it will install Ubuntu in your Windows OS as though it were a program.

If you choose option #3, you will Install Ubuntu by booting to the live cd and installing using the entire disk space. Once you are set up and have run the update manager, you will install, "VirtualBox" and then install Windows in VirtualBox.

 Go to this link to get VirtualBox. The version available in Ubuntu will not allow you to use USB devises.    [http://www.virtualbox.org/](http://www.virtualbox.org/)

After that, go to Medibuntu and install everything you will need to play DVD's.

There is much much more you can do to Ubuntu to get everything working as though you were using Windows.

---

### Post by tmack2 on 2010-07-11
One more thing. Use a journaling 4 file system. it is the fastest. There are explanations on google.

---

### Post by oldfred on 2010-07-11
For the first few years of Ubuntu I had just the XP, Ubuntu and a small shared NTFS partition for photos, firefox & thunderbird profiles. With all the data separate you only need 10-20GB for / (root). You may still want a separate /home as that will still have your user settings mostly in hidden files & folders.

[http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting](http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting)

Now very little data needs access from windows as I am almost converted so I now have large /data partition for Ubuntu only data.

---

### Post by techunit on 2010-07-11
Actually yes you can access your windows files from Ubuntu if you do a full dualboot not a WUBI install. but you won't be able to access the Ubuntu partition from Windows. You could create another partition to hold thta but you are going to run in to a few problems.

Problem 1 Shrinking the Windows Partition! if you don't do this in Windows Using windows Disk Manager then you will brick windows

Problem 2 you can only have 4 primary partitions on a Hard-drive so you are limited. If you computer was factory made then your going to have to many partitions to install ubuntu successfully with an extra partition for file swapping. Ubuntu by default uses 2 primary partitions. You can get around this by creating an extended partition and then putting the ubuntu partitions in side of the extended partition.

Problem three: I foresee questions that you are going to have after this post so I would gladly help you with them.

---

### Post by techunit on 2010-07-11
> **tmack2 said:**
> Hey, welcome to Ubuntu!
There are a few way's to experience Ubuntu and Windows on the same machine.
#1 Install Windows then install Ubuntu in a dual boot configuration using the Ubuntu boot manager.

#2 Install Windows and then install Ubuntu inside Windows using Windows boot loader.

#3 Install Ubuntu and install Windows in Ubuntu by way of VirtualBox./

I have computers set up all 3 ways.

If you choose option #3, you will be able to share a folder the same way as on a Windows network as well as some abilities of copy&paste. Not to mention you will be running both OS's at the same time.

Option 2 & 1 will allow you to boot to windows or Ubuntu. you will be able to pull files from the Windows partition and push files to the Windows partition.

If you choose option #1, you Will install Windows. Once Windows is installed and set up, Install Ubuntu by booting to the live disk. Once you are booted to the disk, choose install.
The Ubuntu installer will allow you to install the 2 OS's side by side. You will be able to choose the size of the partitions during this process.

If you choose option #2, you will Install Windows. Once Windows is set up, insert the Ubuntu disk in the cd/dvd rom and click jon the wobiexe file and it will install Ubuntu in your Windows OS as though it were a program.

If you choose option #3, you will Install Ubuntu by booting to the live cd and installing using the entire disk space. Once you are set up and have run the update manager, you will install, "VirtualBox" and then install Windows in VirtualBox.

 Go to this link to get VirtualBox. The version available in Ubuntu will not allow you to use USB devises.    [http://www.virtualbox.org/](http://www.virtualbox.org/)

After that, go to Medibuntu and install everything you will need to play DVD's.

There is much much more you can do to Ubuntu to get everything working as though you were using Windows.
For virtual box you can use USB devices! I have done it several times.

---

### Post by Paqman on 2010-07-11
> **techunit said:**
> For virtual box you can use USB devices! I have done it several times.

You can with the version from the Virtualbox website, but not with the virtualbox-ose package in the Ubuntu repos.

---

### Post by spartanreborn on 2010-07-11
> **oldfred said:**
> [http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting](http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting)
In this article, it states that Linux uses two partitions, one for itself, and another for it's swap space. What is this swap space?
> **cj.surrusco said:**
> I would set up a partition in NTFS as a data partition to keep all of your files, while allowing each OS about 20GiB in two seperate partitions.   

You WILL be able to access files from your Windows partition in Ubuntu. However, it will not work the other way around. You can transfer files between the two file systems, but only from Ubuntu.
But if I stored files on the shared drive from Ubuntu, I would be able to access those files in Windows?


> **techunit said:**
> Problem 1 Shrinking the Windows Partition! if you don't do this in Windows Using windows Disk Manager then you will brick windows

Problem 2 you can only have 4 primary partitions on a Hard-drive so you are limited. If you computer was factory made then your going to have to many partitions to install ubuntu successfully with an extra partition for file swapping. Ubuntu by default uses 2 primary partitions. You can get around this by creating an extended partition and then putting the ubuntu partitions in side of the extended partition.

I plan on wiping my hard drive, so I won't need to worry about this, at least I don't think I will.

---

### Post by oldfred on 2010-07-11
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

swap is for memory overflow. When you had only 256MB of memory you often need more and it used the hard drive. With over 2GB of RAM you will rarely use swap, but it is still used for hibernation.

Both windows & Ubuntu will read & write data on a NTFS partition. I store my firefox & thunderbird profiles on NTFS shared and firefox has all the same settings (except a few addins) in both system.

---


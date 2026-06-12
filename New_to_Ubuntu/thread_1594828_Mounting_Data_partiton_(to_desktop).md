---
title: "Mounting /Data partiton (to desktop)"
date: 2010-10-12
forum: New to Ubuntu
---

### Post by William-Ubu on 2010-10-12
Hello everyone, Hopefully I didn't start off on the wrong foot posting this question. I've done a bit of reading, but unfortunately I also had to work while trying to figure this out, so I have data everywhere.

I have a 160GB hard drive. I created:

 a 11GB boot/home partition. (sda1)
a 143GB FAT /Data partition (sda3)
and what looks like 6.5GB swap partition (sda5) with a "extended" 6.5 (sda2) on top of that.

Originally I wanted the dedicated /home partition for easy installs, and the a seperate data and page file partition. I couldn't mount it correctly it seems, so now when saving I have to specifiy to save to the /Data partition. If I forget, it gets save to my limited space /home partition. In fact, while trying to figure out Virtualbox for my XP installation, it seems I installed it to my /home partition, eating up another 5GB or so.  
*Because I must have done something incorrectly, when booting the PC, i get an error mssage at the Ubuntu splash screen stating there was an error mounting, and gives me the option of pressing "S" to skip.


So at this point, what can I do to link my desktop and virtualbox to /Data? I was afraid to try anything else, lest I lose my work for the past month or so (I've now backed up as much as I could, based on what was most important) 

Either way, thanks to everyone in this Community. I've learned so much about Linux in general very quickly.

---

### Post by emoguitarist06 on 2010-10-12
Well I can't help with you actual question however if you're willing to re do the partitions I would recommend having:
**"/"** [COLOR="Red"]this is your root/boot partitions less than 10gbs is more than enough[/COLOR]
**"/home"** [COLOR="Red"]obviously as you have experienced this is where everything is saved and should be majority of your harddrive so like 140-145GBs[/COLOR]
**"swap"** [COLOR="Red"]most people recommend double of your ram so if you have 2gbs of ram than 4gbs is more than enough[/COLOR]
This way also allows you to do a fresh install of Ubuntu if you ever needed too without losing your personal files or settings (including any virtual harddrives you've made) and you'll just have to reinstall the programs you had

---

### Post by coffeecat on 2010-10-12
> **William-Ubu said:**
> I have a 160GB hard drive. I created:

 a 11GB boot/home partition. (sda1)
a 143GB FAT /Data partition (sda3)
and what looks like 6.5GB swap partition (sda5) with a "extended" 6.5 (sda2) on top of that.

If the 160GB drive is your only one, this can't be right. If it is, sda1 must be your root (/) partition which contains boot, home and the whole system. An extended partition (your sda2) is simply a "container" for any number of logicals - in this case one only: sda5, your swap partition. You can tell sda5 is a logical partition because logicals are numbered from 5. Primaries (and your one allowed extended) are numbered 1-4.

Using a FAT formatted partition is a bad idea if you do not have Windows. Windows in a virtual machine doesn't count because that can access a Linux filesystem though the Linux host. The reason FAT is a bad idea is because you can only store data on it - no apps, system files or anything like that. FAT doesn't support Linux permissions. Besides, it is an ancient and fragile filesystem.

You are getting a mounting error when you bootup. That is because of an entry in /etc/fstab which refers to a non-existent partition. So - post the contents of /etc/fstab. Also, open a terminal and post the output of:

```
sudo fdisk -lu
```That will give us more information about your partition layout.

---

### Post by William-Ubu on 2010-10-12
Ok, now I see. That makes alot of sense. My setup would be for someone trying to do a dual-boot with windows, right? Not an emulated one. That must be why I chose FAT...but I couldn't have been thinking because of FATs 4gb limit.  Although this now means I'd have to learn how to set up the host thing in virtualbox.

Here are my results from the command:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c5d95

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    20991999    10494976   83  Linux
/dev/sda2       299810814   312580095     6384641    5  Extended
/dev/sda3        20992000   299810358   139409179+   b  W95 FAT32
/dev/sda5       299810816   312580095     6384640   82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by mikodo on 2010-10-12
Hi, when the guys finish helping you out with the re-partitioning, I suggest you then change, where your Virtual Machines mount. Mine go to a separate media partition. Then my /home doesn't fill up with vm's.   In terminal, here is what I followed from GrammatonCleric, on this forum, to set up my mounting of virtual machines outside of /home, to /media:
```

mikodo@mikodo-desktop:~$ sudo mkdir /media/virtualmachines

mikodo@mikodo-desktop:~$ sudo mount /dev/sda9 /media/virtualmachines

mikodo@mikodo-desktop:~$ sudo chown -R mikodo:mikodo /media/virtualmachines

mikodo@mikodo-desktop:~$ sudo chmod -R 700   /media/virtualmachines
```Of course you would user your username and group instead of mine (mikodo).

Mike

---

### Post by William-Ubu on 2010-10-12
> **mikodo said:**
> Hi, when the guys finish helping you out with the re-partitioning, I suggest you then change, where your Virtual Machines mount. Mine go to a separate media partition. Then my /home doesn't fill up with vm's.   In terminal, here is what I followed from GrammatonCleric, on this forum, to set up my mounting of virtual machines outside of /home, to /media:
```

mikodo@mikodo-desktop:~$ sudo mkdir /media/virtualmachines

mikodo@mikodo-desktop:~$ sudo mount /dev/sda9 /media/virtualmachines

mikodo@mikodo-desktop:~$ sudo chown -R mikodo:mikodo /media/virtualmachines

mikodo@mikodo-desktop:~$ sudo chmod -R 700   /media/virtualmachines
```Of course you would user your username and group instead of mine (mikodo).

Mike

Thanks for this tip mike. So, is there any way to move my current Virtualbox to my data partition or do I have to delete it first? Its starting to sound more and more I have to format everything and start over...

---

### Post by mikodo on 2010-10-12
Hi, I would wait until some guru(s), give it an expert's attempt here to straighten you out with the partitioning, before re-installing. I am not one of them however, and sorry I cannot help you with a way out of the situation you are in.   Maybe for now, in preparation for the partition changing work, or new install, backup your backup data nice and tight. Partitioning work can be dangerous and nothing is a guarantee with computers, especially with partitioning.   My two cents worth!  Mike

---

### Post by William-Ubu on 2010-10-13
Hey Mike, I just appreciate everyone taking the time out to assist me. I  will back up what I can for now, unfortunately I have limited storage.  Afterwards I will read and await more advice

---

### Post by coffeecat on 2010-10-13
Good morning, All. Sorry about the delay. Needed some beauty sleep! :wink:

> **William-Ubu said:**
> So, is there any way to move my current Virtualbox to my data partition or do I have to delete it first? Its starting to sound more and more I have to format everything and start over...

I would certainly recommend formatting everything and starting over, except if you've spent some time setting up your Windows XP virtual machine, there's an easy way of backing up and restoring the virtual machine. Have a look in /home/yourusername/.VirtualBox/HardDisks/. In a Nautilus window, press ctrl-H or View > show hidden to reveal the hidden folder .VirtualBox. (In Linux - and MacOS - hidden files and folders are prefaced with a fullstop.) In the HardDisks folder you will find the .vdi file for your virtual XP, plus any other VDIs you might have made. Simply copy/backup this to somewhere - if you have enough storage; I note your comment about limited capacity. Then, when you have reinstalled the OS and reinstalled VirtualBox, you can copy the VDI back into the new HardDisks folder, create a new virtual XP machine in VirtualBox, but instead of creating a new virtual HD, point VirtualBox to the existing VDI file.

> **mikodo said:**
> Hi, when the guys finish helping you out with the re-partitioning, I suggest you then change, where your Virtual Machines mount. Mine go to a separate media partition. Then my /home doesn't fill up with vm's.

@William-Ubu, this makes a lot of sense. It's similar to what I have done. I have set up a multiboot with several partitions and put my Windows VDIs on a dedicated partition which I mount to ~/.VirtualBox/HardDisks/. But if you want to keep things simple, this suggestion is good:

> **emoguitarist06 said:**
> Well I can't help with you actual question however if you're willing to re do the partitions I would recommend having:
**"/"** [COLOR=Red]this is your root/boot partitions less than 10gbs is more than enough[/COLOR]
**"/home"** [COLOR=Red]obviously as you have experienced this is where everything is saved and should be majority of your harddrive so like 140-145GBs[/COLOR]
**"swap"** [COLOR=Red]most people recommend double of your ram so if you have 2gbs of ram than 4gbs is more than enough[/COLOR]

You'd have a big enough /home partition for your needs and since the VDIs normally go in /home you wouldn't need to mess about editing fstab to automount your VDI partition. Personally, I'd go for a minimum of 10GB for the root partition for breathing room.

Just to add to that comment about swap, I noticed your 6GB swap partition. I would think that's overly big. The traditional advice to have a swap twice your RAM goes back to the days when RAM was smaller - say 512MB. I have 4GB in my main machine and my swap gets used hardly at all. You need a swap the same size as your RAM if you need to hibernate, but apart from that, the more RAM you have the less you use your swap. How much RAM have you?

Last thing. I think I mentioned this, but Windows in a VirtualBox virtual machine can access a Linux filesystem if you set up shared folders. No need for a Microsoft fileystem if you don't have Windows running in a normal installation. I have separate data partitions formatted ext4 with Vista running (I mean ambling :wink:) in a VirtualBox machine. I've set up the two data partitions as shared folders in the virtualised Vista and it can read and write to them just fine - simply because it's Ubuntu that's doing the reading and writing.

---

### Post by mikodo on 2010-10-13
Give us an update tomorrow on where you are at. Maybe somebody, that hasn't seen your requests for help, and is qualified to give you assistance, may have the time, to sort this out for you then.  Good Luck!

---

### Post by coffeecat on 2010-10-13
> **mikodo said:**
> Maybe somebody, that hasn't seen your requests for help, and is qualified to give you assistance, may have the time,

That's a bit of a slap in the face. :confused:

---

### Post by William-Ubu on 2010-10-13
I don't think he meant that to be taken that way at all CC. In fact, i think he may have made the post before logging out, right around when you were making yours.

I have about 2.3 GB of Ram on this machine, so perhaps a 2-3gm swap file? I have not seen it used much at all since using Ubuntu. But, I haven't tried anything fun like gaming or video editing yet either.  

Your suggestions is originally what I was aiming for:

/home (The installation by itself, around 10 GB. Would have been great for this very moment)
/Data  (All files and programs) 
/Swap (6gb is likely too much here, thanks for pointing that out)

And a separate partition is recommended for the virtual machines, not /Data? After some more backup , I'll check back before the reformat. Something had to go wrong during my fstab. It should be easy to link the desktop and everything else to the /data partition, right?

---

### Post by Vaphell on 2010-10-13
you can create 'shortcuts' for directories that point to some other location and work just like the real thing. There are 2 kinds of them, hard links and symbolic links and symlinks are used more often

they are created with the command ln, -s is added to create symlink (ln -s)
ln --help to see available options.

once you create Data and mount it properly so it's accessible you can simply redirect your hidden virtualbox directory with virtual machine files to some dir located in /media/Data/ (assuming data is mounted in media, but you can plug it in anywhere) by simply replacing it with link with the same name and moving the content to targeted dir, along the lines of
ln -s /media/data/Vbox ~/.VirtualBox


are you going to have separate home? because your list is somewhat confusing
/home is only for user specific data, installation by itself goes to /

---

### Post by coffeecat on 2010-10-13
> **Vaphell said:**
> are you going to have separate home? because your list is somewhat confusing
/home is only for user specific data, installation by itself goes to /

Agreed.

> **William-Ubu said:**
> Your suggestions is originally what I was aiming for:

/home (The installation by itself, around 10 GB. Would have been great for this very moment)
/Data  (All files and programs) 
/Swap (6gb is likely too much here, thanks for pointing that out)

I think you are being influenced by Windows ways of thinking. Your root (/) partition is where the OS goes - all the system files and installed applications. The root partition only needs to be about 10GB simply because Linux  takes up far less room than Windows. I have an installation with a lot  of extra apps installed and it still only takes up about 5GB.

You can have your /home folder included in the root partition - this is the simplest of all arrangements - but there are good arguments  for having a separate /home partition. The /home partition needs to be as big as all your data needs. So having a /home partition of 100GB+ makes sense. Then you would have room for all your personal files as well as the virtual machine files, which is where they normally go. Then you wouldn't have the complication of putting the VDIs on a separate partition and the need for having this mounted.

---

### Post by William-Ubu on 2010-10-13
> **coffeecat said:**
> 
You can have your /home folder included in the root partition - this is the simplest of all arrangements - but there are good arguments  for having a separate /home partition. The /home partition needs to be as big as all your data needs. So having a /home partition of 100GB+ makes sense. Then you would have room for all your personal files as well as the virtual machine files, which is where they normally go. Then you wouldn't have the complication of putting the VDIs on a separate partition and the need for having this mounted.

Ok, I see where the confusion was. Im mixing "root" and "home" You are correct. I wished to have the root installation, then the "/home" partition separate. Theres no need for me to create one named "/data" 

So when first doing my clean install, my confusion is what messed it all up. It would have installed the OS to "Root" and then everything else @ "/home". For instance, using synaptic to add an application would install it to "/root". But the desktop, downloads and whatever else would go to "/home"? Either that or I'd have to specify location?

---

### Post by coffeecat on 2010-10-13
> **William-Ubu said:**
> So when first doing my clean install, my confusion is what messed it all up. It would have installed the OS to "Root" and then everything else @ "/home". For instance, using synaptic to add an application would install it to "/root". But the desktop, downloads and whatever else would go to "/home"? Either that or I'd have to specify location?

Sorry to nitpick :) but /root is wrong as well. The trouble is, the word root can refer to three things.

1 There's the root partition, which is conventionally referred to as '/'. This can contain the whole shebang, except for the swap partition. Even then you can have a swap file just like in Windows rather than a partition, but let's not go down that road. Having everything in / is the simplest option, but there are advantages to having some things in separate partitions. The most common are /home - which seems a good idea in your case - and some people like a separate /boot, but that's a complication which has no advantages that I can see in your situation.

2 Secondly, root can refer to the root of a filesystem. That's an OS-agnostic term - you can use it in Windows or MacOS. Basically, it means the highest level directory - the actual filesystem itself.

3 Lastly, in Unix-like OSs, 'root' is a separate account - the superuser. Root has its own home directory which happens to be called 'root' which you can find in the root of the filesystem in the root partition. Clear? :p So when you wrote /root, strictly speaking you were actually referring to root's home folder.

Anyway - to the meat of your post. Yes, Synaptic will install apps to the / partition. Executables and other stuff go in /usr and config files in /etc with personal config files in your own home folder. A minority of apps - usually but not always proprietary ones - are installed to /opt. I'm afraid things are not quite as tidy as with Windows with apps going into C:\Program Files, but at least we don't have a registry to [s]mess everything up[/s] complicate things.

And yes, the desktop is basically a folder in your home and you will find a Downloads folder already set up in home as well.

As a general rule of thumb, and unless you have a separate data partition, store everything you need somewhere in your home folder. Consider **everything** else as belonging to the system and the superuser. I remember a thread from someone complaining that they experienced permissions problems every time they tried to use /tmp as a temporary storage space. "It's my computer and the folder is called temp, so why shouldn't I?" seemed to be their attitude. It took about six of us to convince them that it was not a good idea.

---

### Post by William-Ubu on 2010-10-13
Understood. =D> 
 Im actually glad you cleared that up, as minor misconceptions and what not can lead to all kinds of confusion. Especially for someone else who may be reading this thread with the same problem. I did mean "/" and subconsciously knew about "/root" being somewhat our version of windows' "administrator" (learned from using "sudo" command) But I was using it wrong.

I understand alot more, now..especially since I had to to actually look at the way folders and directories are set up here. I found the desktop and VirtualMachine folders. Most of this could have been avoided with more understanding of the file system, I just don't get a whole lot of free time. Not that it's an excuse, just a general ignorance of linux, in which you fine folks are helping me cure. I see how the "/home" folder is a part of "/", which in my case was the 11gb partition. What I actually want is:

"/" - OS root partition. System & Superuser turf.
"/home" Everything not belonging to the system itself, mostly personal files.
"Swap" not gonna be 6GB anymore, but still a separate swap partition

Got one small hangup though. Seems the external drive im using for backup wants to quit on me, so I'll probably have to solder its connectors and clean it good before trying to back up again. Hopefully it works.

Sounds like the /tmp permissions person was also "poisoned"  :lol: ,  with years of Windows usage

---

### Post by cek on 2010-10-13
I generally setup my installs with the following partitions:

/ - root fs where things get installed, ~36GB
/boot - kernel images are placed here, 256MB (this is a left over habit from my gentoo days)
swap - 1GB (my machine has 8GB of RAM, but I don't hibernate)
/home - 16GB, private user data and application settings
/data - "the rest"

The reason I have a seperate /data partition that gets allocated very large is because I have a lot of data (music, pictures, movies, etc.) that I want to have shared between several users on my machine.  Having these in a separate partition/directory structure means they can easily be shared while maintaining private data within each user's /home directory.

On top of that, I setup symlinks within each user's /home directory for ease of use when saving/opening the shared data folders.

Due to the success I've had with this setup, I'm surprised I don't see this (or similar) schemes mentioned more often.  I suppose for a true single user machine (meaning, you only plan to have one user account in place) then a shared data partition is overkill -- maybe that's why it's not as popular.

---

### Post by QLee on 2010-10-13
[QUOTE=William-Ubu]... Most of this could have been avoided with more understanding of the file system, I just don't get a whole lot of free time. 
...[/QUOTE]
When you do get a bit of free time, it might be useful for you to review this document, it will explain a bit about the way the filesystem is structured in operating systems that use the linux kernel. 
[http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/usr.html](http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/usr.html)

You could also read the manual page by entering the command, man hier, in a terminal window.

---

### Post by QLee on 2010-10-13
[QUOTE=cek]...
Due to the success I've had with this setup, I'm surprised I don't see this (or similar) schemes mentioned more often.  I suppose for a true single user machine (meaning, you only plan to have one user account in place) then a shared data partition is overkill -- maybe that's why it's not as popular.[/QUOTE]
Well, you probably don't get to read through the forums as much as I do, it is mentioned often, or some minor deviation of that. However, partitioning suggestions often become emotional.

As a matter of fact, the laptop I'm writing this reply from is setup just like that except I call my data volume "storage" rather than "data" and I only make my OS volumes 10GB.

---

### Post by mikodo on 2010-10-13
> **coffeecat said:**
> That's a bit of a slap in the face. :confused:

Hey man, Sorry... I didn't see your post just previous to mine. I think we posted at the same time. I was trying to encourage William-Ubu to continue to be patient until some help came from people like you. William-Ubu was correct that I meant no intent towards you, as I didn't see your post until now.  Mike

---

### Post by William-Ubu on 2010-10-14
Here's my update: 

MISSION COMPLETE

I backed everything up, and did a clean install. The built in partition system made alot more sense to me this time around, so I made :

/ - 10GB
/Home - 140GB or so
Swap File - 3GB

Now everything has been restored properly, including Guayadeque , firefox and my VirtualBox installation.  Somethings I didnt bother to backup/restore properly are gone, but no worries here.

I thank each and everyone of you for your help with this matter, especially "the Cat". Now I can bumble my way through a Linux conversation halfway!  Now, I can mess around with Wine and other goodies on Linux :guitar:

---


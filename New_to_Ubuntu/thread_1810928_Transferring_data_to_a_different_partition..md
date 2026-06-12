---
title: "Transferring data to a different partition."
date: 2011-07-23
forum: New to Ubuntu
---

### Post by unclecyclops on 2011-07-23
I am dual booting Windows 7 and Ubuntu right now. I want to transfer a folder from my windows 7 partition. To the partition that my Ubuntu is ran on. I would like to avoid having to download it off the internet, or saving it to a disk, as it is a large folder. I have very recently switched, so I have no idea how to do this, and any searches I have done are not helpful. Any help would be appreciated.

I also can't seem to figure out which partition is which. Are there any obvious things that I would notice that would separate the two?

Thanks in advance!:)

Solution: 
With a Wubi installation: Follow the instructions at [http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354) and [http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html).
To transfer the item, go to System Settings > Hardware > Disk Utility. Go to the Device that your partition is on. Click the partition, Mount it (if necessary), click Mount Point. This should display the top location of the folder you want to access. Just click Copy to, and push Root.

---

### Post by wildmanne39 on 2011-07-23
Hi, click on your file manager and on the left side you should see your windows partition just copy the file over but I would not move it sometimes it gets lost.

---

### Post by unclecyclops on 2011-07-23
In the file manager, I see three different drives on the left. "4.0 GB Filesystem", "SYSTEM", and "FACTORY_IMAGE". I installed Ubuntu several months ago, so I can't remember how I set up the partitions. I attached a shot to show you what I see. My USB is the 4 GB, I just don't know about the system and Factory Image.

---

### Post by wildmanne39 on 2011-07-23
Hi, I think system is your windows partition, click on it and see then you can access your documents and other files.

---

### Post by unclecyclops on 2011-07-24
It doesn't seem to be. I can't find any folders for documents or anything similar.

---

### Post by wildmanne39 on 2011-07-24
Hi, did you see the partition with the files on it in disk utility? Is it the large partition? if so click on it in disk utility and see if it is mounted if not then mount it, then open the file manager back up and you should see it there.

---

### Post by -kg- on 2011-07-24
In your Disk Utility image, I didn't notice any partition on your hard drive except for sda1, which is formatted as NTFS.  No partition is listed as formatted to ext3 or ext4.

Did you by chance install Ubuntu under Windows using WUBI?  That would change the measures you'd have to take in order to copy the files over.

---

### Post by amjjawad on 2011-07-24
Is this Wubi installation?

I can't see the folders that you supposed to have?!

---

### Post by unclecyclops on 2011-07-24
This must be installed with Wubi. On the left side of the Disk Utility, under peripheral devices, there is something that says "18 GB File" is this what I am using for Ubuntu?  Is there any way to increase the size of that? I did find the folder that I want to copy over, but I don't have enough space.

Edit: After looking into Wubi some more, is seems that it is a Wubi installation, just from what I see. It looks like I'll have to migrate from Wubi to a normal Dual-boot. Would [http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354) and [http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html) work fine with Natty? It mentions that that the second one is written for 10.10.

---

### Post by oldfred on 2011-07-24
I have not used wubi, but bcbc's instructions are what you need.

I find Herman's instructions to be very complete. Some find them too much. The difference with 11.04 and 10.10 is a few visual looks on screens. I have installed both and not paying close attention do not notice much difference in installers. 

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

It looks like you have only used three of the four primary partitions allowed. So you can use Windows MMC to shrink windows and then use gparted to create an extended partition and put all the Linux partitions in the extended partition. Do not use windows to create additional partitions.

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

---

### Post by unclecyclops on 2011-07-24
Will I need a Windows 7 installation CD? I have read that changing the size of the Windows partition will make it unable to log onto, unless you repair it.

---

### Post by oldfred on 2011-07-24
You need a windows repair CD but changing the size from within windows should not cause any issues. It normally wants to run chkdsk or other fixes automatically after a partition change.

Make your own Windows recoveryCD/repair:
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

You should also create the vendor recovery DVDs which are just an image of your drive as you purchased computer. Or starting all over.

You can also should make full backups of your windows.

---

### Post by unclecyclops on 2011-07-24
> **oldfred said:**
> 
For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

This is the part that confuses me. I am making the extended partition for Ubuntu 100,000 MiB. How many logical partitions should I make, and what size, according to what you said above? Is the /home where all the ubuntu files are?

---

### Post by amjjawad on 2011-07-24
> **unclecyclops said:**
> This is the part that confuses me. I am making the extended partition for Ubuntu 100,000 MiB. How many logical partitions should I make, and what size, according to what you said above? Is the /home where all the ubuntu files are?

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

You need to understand what are the types of partitions, how to partition and how Linux is dealing with partitions, etc.

Good luck!

P.S.
A simple and quick google search will answer such Qs ;)

---

### Post by oldfred on 2011-07-24
Ubuntu is installed in a root partition which is shown as "/". All folders for the system are from /. You can split most of them off but unless running a server you do not really want to do that. 

But /home has all your user settings and all your data. If you want to do a clean install, you can install a entire new version or reinstall by just installing to / and reusing your /home. If /home is inside the / you have to back it up (which you should be doing anyhow) and reinstall it if you do a new install.

I prefer separating system from data both for Ubuntu and for Windows. It makes system slightly more efficient as it does not have files all over hard drive and makes back up a little easier as data is separate from system. Neither are required, you can just install into / (root) and even do not have to have swap if you hae lots of RAM memory. Some create a swap file like windows does, so swap is not in a separate partition. Linux is very flexible on what you do.

---


---
title: "Hard disk problem"
date: 2010-04-12
forum: New to Ubuntu
---

### Post by pike747 on 2010-04-12
I am new to Ubuntu and I installed 10.04 in a dual boot with Windows 7 on separate physical drives. 
My system:
Ubuntu 10.04 Beta AMD64
ProcVersionSignature: Ubuntu 2.6.32-19.28-generic 2.6.32.10+drm33.1
Uname: Linux 2.6.32-19-generic x86_64
NonfreeKernelModules: nvidia
Architecture: amd64
InstallationMedia: Ubuntu 10.04 "Lucid Lynx" - Beta amd64 (20100318)
three physical hard drives, 500GB Win 7, 320GB Ubuntu Linux 10.04, Lucid Lynx, 200 GB Windows storage.

               At first the system would boot straight to Windows.  Then I disconnected the 500GB drive and it booted to Grub2 which showed Ubuntu and Win7 and would load Ubuntu.  I realized that all I needed to do was install Grub2 on the 500GB drive because the Ubuntu installation had placed it on the 320GB drive.
I had read that it was best to install Windows first.  So that drive should be considered the ‘first’ drive.  Ubuntu still considers the drive it is stored on as ‘first’ but as long as Windows thinks it is first I guess I am okay.
I found this link on the Ubuntu forums for installing Grub2 from the live CD:
[http://ubuntuforums.org/showthread.php?t=1014708&highlight=replace+windows+bootloader+grub2I](http://ubuntuforums.org/showthread.php?t=1014708&highlight=replace+windows+bootloader+grub2I) followed the instructions and was able to get my system working the way I want it.
The Linux fdisk command returned this:
[EMAIL="ubuntu@ubuntu:~$"]ubuntu@ubuntu:~$[/EMAIL] sudo fdisk -l
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical / optimal IO): 512 bytes / 512 bytes
Disk identifier: 0x0004ba41
Device Boot Start End Blocks Id System
/dev/sda1 * 1 37692 302754816 83 Linux
/dev/sda2 37692 38914 9814016+ 5 Extended
/dev/sda5 37692 38914 9814016 82 Linux swap / Solaris
Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical / optimal IO): 512 bytes / 512 bytes
Disk identifier: 0x829f813a
Device Boot Start End Blocks Id System
/dev/sdb1 * 1 13 102400 7 HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sdb2 13 60801 488280064 7 HPFS/NTFS
Disk /dev/sdc: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical / optimal IO): 512 bytes / 512 bytes
Disk identifier: 0x6bc67ed0
Device Boot Start End Blocks Id System
/dev/sdc1 1 24793 199146432 42 SFS
Disk /dev/sdd: 18 MB, 18612224 bytes
1 heads, 36 sectors/track, 1009 cylinders
Units = cylinders of 36 * 512 = 18432 bytes
Sector size (logical / optimal IO): 512 bytes / 512 bytes
Disk identifier: 0x6f20736b
Disk /dev/sdd doesn't contain a valid partition table
[EMAIL="ubuntu@ubuntu:~$"]ubuntu@ubuntu:~$[/EMAIL]
I followed the guide and did this:
[EMAIL="ubuntu@ubuntu:~$"]ubuntu@ubuntu:~$[/EMAIL] sudo mkdir /media/sdb1
[EMAIL="ubuntu@ubuntu:~$"]ubuntu@ubuntu:~$[/EMAIL] sudo mount /dev/sdb1 /media/sdb1
[EMAIL="ubuntu@ubuntu:~$"]ubuntu@ubuntu:~$[/EMAIL] sudo grub-install --root-directory=/media/sdb1 /devsdb
/usr/sbin/grub-probe: error: cannot stat `/devsdb'.
Invalid device `/devsdb'.
Try `/usr/sbin/grub-setup --help' for more information.
[EMAIL="ubuntu@ubuntu:~$"]ubuntu@ubuntu:~$[/EMAIL] sudo grub-install --root-directory=/media/sdb1 /dev/sdb
Installation finished. No error reported.
[EMAIL="ubuntu@ubuntu:~$"]ubuntu@ubuntu:~$[/EMAIL]
I made an error on the install command the first time.  Then it worked correctly the second time.
 
Now my current problem: 
I was able to boot to Windows the first time. The next time it did not show up in the Grub2 menu.
I put my Windows disk in the drive and attempted to repair my Windows installation. This attempt failed. It said the drive was corrupted. I could access the drive and it's files from Ubuntu. I copied my persoanl files to the 320 GB drive with Ubuntu on it.
Then I used Seatools to test the drive it tested good on the long and short tests.
Windows still could not do anything with the drive.
I then used Seatools to write zeros to the entire drive. I attempted to install Windows again. It still reports there is no usable partition.
Ubuntu can still access the blank drive.
My question is, does Linux leave something that Seatools cannot overwrite and Windows cannot handle on the drive? If so does anyone have a suggestion for getting this drive working for Windows again. I would love to take it as a sign and be done with Microsoft but I do feel I need a little transition period until magicjack has Linux support and I can find the right tools to replace Adobe CS4.
Any help would be greatly appreciated, thank you
Michael  
P.S I cannot access the 200 GB drive in Linux. Not a big deal if I can get Windows working again.

---

### Post by readycarpenter on 2010-04-12
the thing I have found is Ubutuntu and grub play nice with windows, but not the other way around, I highly suggest always installing all windows oses first as they play nice with one another, 

windows puts a mbr(boot sector) on the first hard drive in your setup, after installing all your win oses,do not change your hd configuration, then boot ubuntu, install, and leave the grub setting to default, it will put grub on the first hd, replacing the windows mbr, and viola triple boot baby, this is the easiest way.

I believe you have grub on a different hd/partition than the windows mbr, this is possible, called chain booting, but not for novice.

like I said grub installs its own boot sector... but grub and config files are (by default) installed to the ubuntu partition.

the way I explained at the top is the simplest, but it does remove the windows mbr, so if you ever delete or format your ubuntu partition you will no longer be able to boot windows, but easy fix using win install disk run fix mbr

cheers

---

### Post by ranch hand on 2010-04-12
OK, first the package testdisk is what you want for testing and recovering disks if that is needed.

If you check the link in my sig you will get a good basic understanding of grub.

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Is the very best in depth info on grub.  It has links to other How Tos on specific grub tasks.

I would try a custom entry for your MS install in your /etc/grub.d/40_custom file and save it as 06_custom.  That way it will be at the top of your menu instead of the bottom and your 40_custom file will be nice and clean if you need it as a template again.  You will need to check the permissions on the 06_custom file to check the box in permissions to enable execution as a program.

---

### Post by pike747 on 2010-04-12
Thank you and I will try your suggetions. To note I did install Ubuntu after Windows. Windows was already on the 500 GB drive. I then installed Ubuntu on the 320 GB. Windows was working for a couple of months prior to installing Ubuntu. When I installed Ubuntu it did include Windows 7 in the grub2 menu but put grub2 on it's own drive. I did not see the Grub2 menu until I disconnected the drive with Win 7. Almost wish I had left it that way. Connecting and disconnecting the hard drive might have forced me to use Linux more :-) I actually found it easier and, so far preferable to install each OS in a separate partition on the same drive. I have this setup running on another computer, the one I am on right now. It has worked very well from the start and through many boots. This has the prior version of Unbuntu, Karmic installed instead of the Beta Lucid.
again thank you, 
Michael

---

### Post by readycarpenter on 2010-04-12
> When I installed Ubuntu it did include Windows 7 in the grub2 menu but put grub2 on it's own drive. I did not see the Grub2 menu until I disconnected the drive with Win 7

is ee exactly your issue.

you installed win on first drive, mbr(boot sector) was also installed there

then you installed ubuntu, and set grub to install on the second drive, also the drive that has ubuntu.

the problem is you pc's bios is set to boot the first drive, which has windows mbr and then boots windows, 

as a workaround you can easily set you pc's bios to boot the second drive, your ubuntu drive that also had grub, listing windows in the menu viola dula boot,

remember your original hd configuration. just change bios to boot second drive

cheers

---

### Post by pike747 on 2010-04-12
Just a quick update. I tried clearing my bios and booting with only the 500GB drive connected. Then I tried again to install Windows. Same message. Then I decided to try installing Ubuntu on that drive and it worked I am working from that installation right now. I suppose that means I need to completely clear this drive using Linux tools? I see above where ranch hand advised me to use the package testdisk to test the drive or can I use the fdisk command from the live CD to remove the Linux partition information? At least I am pretty sure there is nothing wrong with the drive.
Right now I just want to prepare that drive so that windows can use it again. then I will figure out how to get it to play nice with Ubuntu. I do see the mistake I made in haveing Grub2 on both drives. I will follow your instructions for Grub, ranch hand as soon as I can get windows to even install again.

---

### Post by readycarpenter on 2010-04-12
hmmm, you confuse me slightly. so now the problem is no longer.. not booting the proper os, but will not install windows?

to format a drive you can use fdisk, or easier use gparted, it comes on the live disk and has a nice gui.

and as far as clearing your bios, I did not suggest that, I suggested changing your boot order, to boot the second drive instead of the first drive, completely different than clearing the bios

this is very important, when installing mutli os, think about how you want to do it, setup your hd configuration, and don't change it, every-time you take your first drive out, your second drive becomes the first. example: grub is using hd1 becomes hd0. this can create conflicts. 

hope you work it all out
cheers

---

### Post by pike747 on 2010-04-12
Right now I would really love it if someone could just say do this and it is as if the drive were new. Quite frankly I don't comprehend how using the manufacturer's tools to erase the drive does not accomplish this.
I will not totally give up but I need to be able to use windows on my own computer.
I can worry about getting it to do both later. I will leave the 320 GB with Ubuntu disconnected until I can back up my data and start over. That is not feasible at this time because I do not have enough storage.
Thank you all very much for your help and patience,
Michael

---

### Post by ranch hand on 2010-04-12
I have no idea what manufacturers tools you are talking about but most folks who rescue data and sork with partitions use Linux tools to do so.  Why?  You may ask.  Well, they just work better.

I have no idea why you are wiping drives in the first place.  Simply getting a boot loader in the right MBR is all that was required.

---

### Post by egalvan on 2010-04-13
> **pike747 said:**
> I am new to Ubuntu and I installed 10.04 in a dual boot with Windows 7 on separate physical drives. 
My system:
Ubuntu 10.04 Beta AMD64


[B][COLOR="Red"]three physical hard drives[/COLOR],
 500GB Win 7,
 320GB Ubuntu Linux 10.04, Lucid Lynx,
 200 GB Windows storage.[/B]

 sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
Device Boot Start End Blocks Id System
/dev/sda1 * 1 37692 302754816 83 Linux
/dev/sda2 37692 38914 9814016+ 5 Extended
/dev/sda5 37692 38914 9814016 82 Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
Device Boot Start End Blocks Id System
/dev/sdb1 * 1 13 102400 7 HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sdb2 13 60801 488280064 7 HPFS/NTFS

Disk /dev/sdc: 203.9 GB, 203928109056 bytes
Device Boot Start End Blocks Id System
/dev/sdc1 1 24793 199146432 42 SFS

**[COLOR="Red"]Disk /dev/sdd: 18 MB, 18612224 bytes[/COLOR]**
1 heads, 36 sectors/track, 1009 cylinders
Units = cylinders of 36 * 512 = 18432 bytes
Sector size (logical / optimal IO): 512 bytes / 512 bytes
Disk identifier: 0x6f20736b
Disk /dev/sdd doesn't contain a valid partition table

Do you know what that fourth drive (/dev/sdd) is?


> Any help would be greatly appreciated, thank you
Michael  
P.S I cannot access the 200 GB drive in Linux. Not a big deal if I can get Windows working again.

As RanchHand stated, simply recovering the MBR would have returned Windows to a working state.

Also, this seems to be a matter of Microsoft and Linux seeing the drives in different order.

It should have been a simple matter of making the Linux drive the first boot drive (in the BIOS)

At the moment my FireFox has lost it's search engine...
so I cannot Google "sfs", so no joy there.

And Microsoft is notorious for having problems with hard drives if they are not EXACTLY to it's liking.

Me myself and I always use Darik's Boot And Nuke (dban).
It works. Be careful. It **WILL** wipe your drive(s)

---

### Post by pike747 on 2010-04-13
> **ranch hand said:**
> I have no idea what manufacturers tools you are talking about but most folks who rescue data and sork with partitions use Linux tools to do so. Why? You may ask. Well, they just work better.
 
I have no idea why you are wiping drives in the first place. Simply getting a boot loader in the right MBR is all that was required.
 
 
I do not dispute this at all but even the finest tool in an unskilled hand is less than it would be in skilled hands.
I was able to store my personal data on the Ubuntu drive. I have been able to burn it to disks. It is just the fact that I could not get Windows to do anything with that drive that led me to zero it out with Seatools (It is a Seagate drive). I am ignorant of how to do these things in Linux. I am aware that Linux tools are probably the best I just don't know how to use them yet.
You and others have been very patient and helpful. It is too late for getting the boot loader right. I wiped the drive and test-installed Ubuntu on it. 
Quite frankly I wish I could afford to buy the hardware I am typing from right now it is working fantastically with one hard drive partitioned, Windows 7 and Ubuntu. It is my computer I messed up. But don't worry I am a bulldog and I am not going to give up. I believe in open source. It will just take some getting used to.

---

### Post by ranch hand on 2010-04-13
A very helpful, if sometimes extremely boring, tool at your disposal is the man pages.

If, for instance you want to us sfdisk or cfdisk for partitioning for some reason
```

man sfdisk

```
Of gparted or just about anything in Linux has a man page.

Of coarse sometimes it seems a translator would be nice.

Slow down, remember to breath.  Hurry is a thing sure to make a short job longer and harder.

Take my work for it.  I am real good at screwing things over in a rush.

---

### Post by pike747 on 2010-04-13
> **ranch hand said:**
> A very helpful, if sometimes extremely boring, tool at your disposal is the man pages.
 
If, for instance you want to us sfdisk or cfdisk for partitioning for some reason
```

man sfdisk

```
Of gparted or just about anything in Linux has a man page.
 
Of coarse sometimes it seems a translator would be nice.
 
Slow down, remember to breath. Hurry is a thing sure to make a short job longer and harder.
 
Take my work for it. I am real good at screwing things over in a rush.
 
 
Thank you and I think I already proved I am good at messing things up in a hurry. Linux is a big world and I believe it is the real world of computing so I am glad that the person I built this computer for requested it so I will finally get over the hump. 
It is interesting that I recommended Ubuntu to a friend with very little prior knowledge of it because he had genuine disadvantage problems. He tried it and loves it and convinced the person I am building this computer for to use it which, in turn, has finally gotten me to be brave and try something I have been interested in and curious about for 12 years now. All in all, I am very glad I took the plunge. So far the only real loss is some of my time, not data, :~}
Thank you again,
Michael

---

### Post by readycarpenter on 2010-04-13
> As RanchHand stated, simply recovering the MBR would have returned Windows to a working state.

Also, this seems to be a matter of Microsoft and Linux seeing the drives in different order.

It should have been a simple matter of making the Linux drive the first boot drive (in the BIOS)


if you have not formatted any of the drives, I truly believe if you physically connect the hds to your pc, in exactly the order you started, you can be up real fast.

then turn on pc, get into the bios, change it to boot the first drive if it boots windows ok, restart pc

now reset the bios to boot the second drive, do you boot into grub? and is windows on your grub list?

cheers

---

### Post by pike747 on 2010-04-23
[QUOTE=pike747;9112309]I am new to Ubuntu and I installed 10.04 in a dual boot with Windows 7 on separate physical drives. 
My system:
Ubuntu 10.04 Beta AMD64
ProcVersionSignature: Ubuntu 2.6.32-19.28-generic 2.6.32.10+drm33.1
Uname: Linux 2.6.32-19-generic x86_64
NonfreeKernelModules: nvidia
Architecture: amd64
InstallationMedia: Ubuntu 10.04 "Lucid Lynx" - Beta amd64 (20100318)
three physical hard drives, 500GB Win 7, 320GB Ubuntu Linux 10.04, Lucid Lynx, 200 GB Windows storage.  :guitar:

I am trying something new.
I could not get windows to recognize the 500 GB drive no matter what I tried. I could not get DBAN to work because I have a wired microsoft ergonomic keyboard and a cordless logitech. The cordless does not play well with dos type boot programs and the microsoft keyboard has an issue with its F keys until it is in an operating system. I found it hillarious once when I could not get their F8 key to accept their own eula. :lolflag:

I installed Windows7, successfully, on the 320 GB hard drive. The 500 GB is empty, except for whatever is preventing Windows from installing to it. The 200 GB is still for storage only.
I booted to the Ubuntu Cd and began installing it. I will put it on the 500 GB. The install program told me there were no operating systems on this computer. I aborted the install and returned here.
How can I make sure that this works correctly this time? I don't want to let the install program for Ubuntu have it's way when it seems confused. I suppose there is still some confusion about the hard disk boot order.
Thank you all for your help. I took a few steps back to take some breaths and now I have windows again but, I still want Ubuntu! I am learning to love it on the build I put together. I am striving to own that machine and build the customer a new one! Both operating systems seem to work together well on a single physical disk. I have always been under the impression that dual booting worked better on separate physical drives but have been disabused of that notion.

---

### Post by readycarpenter on 2010-04-23
so basically you are trying to get the other 500GB hd recognized in windows-7, and for the ubuntu install to recognize windows.. am I correct? so you can then have dual boot.

are your drive actually sata drives or are they ide? make sure your bios recognizes all 3 hard drives, if they are ide drive you must make sure you have the pins st properly for master and slave

right now you have 3 drives connected, but only 2 drives are recognized in windows, how many show in gparted when you boot the ubuntu live cd?

you can find my im's in my profile, and I'll walk you through a dual boot install if I am around and have time. peace

---

### Post by pike747 on 2010-05-24
First I would Like to thank all of you who helped with this problem. I / we figured out what happened and I now have a dual boot with Windows and Ubuntu with Grub on the correct hard drive.
I noticed during this recent install that there is an advanced tab to install the boot loader. It wanted to default to the wrong drive. After changing this everything went without a hitch. I told it to install to the drive windows is on and now I get a grub boot menu! The original problem was created when it installed to the same drive as Ubuntu. Then it was compounded when I manually installed grub to the Windows drive. I did actually get Windows to access the 500 GB drive that it would not install to through the administrative tools in Windows. I think it would install there now but I am fine with Ubuntu having the larger drive.
It has taken a while because I had a series of personal issues and a move between then and now. As I promised, I did not give up and kept at it until I could use Ubuntu. I look forward to when I can go all open source and it will be sooner rather than later. I have invested a lot of time and effort into learning web design the Windows / Adobe way and I am sure I can learn some open source methods. Text code is text code no matter what. I am already aware that there is an important and marketable technology called Ruby and Ruby on Rails which I look forward to learning.
You, the Ubuntu community have been great and I look forward to corresponding further.
I actually was able to install the Linux ATI drivers on another computer which was a little more difficult than the Nvidia drivers for my own  :smile:

---


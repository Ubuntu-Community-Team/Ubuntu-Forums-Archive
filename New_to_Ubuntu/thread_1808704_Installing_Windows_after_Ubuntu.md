---
title: "Installing Windows after Ubuntu"
date: 2011-07-20
forum: New to Ubuntu
---

### Post by Thrashrokz33 on 2011-07-20
So, for whatever reason I decided to do a fresh install of Ubuntu 11.04, wiping out Windows on my machine. After realizing that Ubuntu didn't have driver support for my video card, and also didn't work with my 3D modeling software, I've decided to dual boot windows on my machine with ubuntu, just for those things. I'm going to follow the instructions in the recommended method at this page: 

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

I just have a few questions before I start this process though (by the way, I'm going to install 32bit Vista, if that makes a difference):

-Will all of my Ubuntu software and settings be left intact after installing windows and recovering the GRUB 2 menu? 

-Will this take BIOS off of my machine? It mentioned somewhere that it replaces the master boot menu, so does that remove BIOS?

-Will dual booting slow down my computer at all?

Thanks in advance!

---

### Post by skatinjj on 2011-07-20
The BIOS will not be removed.

The system should not be any slower.

Your software and settings should stay intact.

---

### Post by skatinjj on 2011-07-20
The BIOS will not be removed.

The system should not be any slower.

Your software and settings should stay intact.

---

### Post by akand074 on 2011-07-20
As long as you don't touch the Ubuntu partition (you don't need to) then everything will remain the same. Your BIOS aren't at the masterboot record. They aren't even on your hard drive they are right on your motherboard. So no, they won't be affected. And lastly, also no. Each OS is completely independent of the other. That is to say, if you are booted in Ubuntu, it's as if all you have is Ubuntu and vice versa. (though you can still mount other partitions as storage).

---

### Post by Thrashrokz33 on 2011-07-20
I've heard that Ubuntu has a "rescue" mode on the CD. Is this an easier technique than the one in the link that I sent?

---

### Post by akand074 on 2011-07-20
> **Thrashrokz33 said:**
> I've heard that Ubuntu has a "rescue" mode on the CD. Is this an easier technique than the one in the link that I sent?

No, I don't believe so. I've always used the LiveCD. I'm not sure if you can even reach rescue mode if grub has been overwritten. Reinstalling grub via liveCD is pretty easy, basically just run a few commands they tell you to in order and you're done.

---

### Post by Thrashrokz33 on 2011-07-20
Thanks! I was looking through a few more forum posts, and it seems like some people ran into trouble with partitions. I'm very inexperienced with that, so I do have one more question (last one I promise.)

My Ubuntu partition is set to around 67gb, while my harddrive has about 250gb on it. Will I have to mess around with partitioning when I install Windows Vista, or will it just automatically create a similarly sized partition, which won't overwrite or screw with Ubuntu? I haven't installed Windows in forever, so I don't know if there's an option to set partition sizes, like the Ubuntu CD nicely includes.

---

### Post by wildmanne39 on 2011-07-20
Hi, here is a guide for installing windows after ubuntu is installed. You will have to reinstall grub from a livecd.
[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm)

I changed it to make it easier so you do not have to scroll down to find how to install vista after ubuntu.

Thank you oldfred, I should have done that in the first place.

---

### Post by oldfred on 2011-07-21
I think wildmanne39 may have given the wrong link. But they have a link on the same page to the correct version - windows after Linux. Basically you do have to create a primary NTFS formated partition with the boot flag for Windows to install.

Also the link is older and you have to plan on reinstalling grub2, not any other boot loader. Ubuntu 9.04 was the last to use grub legacy.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10) - talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)

---

### Post by Thrashrokz33 on 2011-07-21
The article refers to a partition editor that I can't seem to find under the administration tab...

I'm guessing the equivalent for 11.04 would be the "disk utility"? If that is the case, I really have no idea how to make a new partition. When I installed Ubuntu, it automatically selected my whole harddrive as the Ubuntu partition (250gb), and when I go into the disk utility, I see three volumes. One says "246gb ext4" and the other two say "Extended" and "Swap" both being 4.2gb. Clicking edit partition just asks me which type I would like to convert it to, so I'm stuck.

How to I make an NTFS partition, and how big do you recommend it?

---

### Post by wildmanne39 on 2011-07-21
Hi, here is a guide for gparted, not sure you may have to install it first.
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

---

### Post by mastablasta on 2011-07-21
> **wildmanne39 said:**
> Hi, here is a guide for gparted, not sure you may have to install it first.
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
 
gparted is on live disk. you have to use it form live disk so that the disk is not mounted. 
 
you run it by typing
 
gparted
 
in terminal.

---

### Post by akand074 on 2011-07-21
I've installed Windows after Ubuntu several times. I believe right from the install CD I just chose "custom" and then picked the remaining space I had (not dedicated for Ubuntu or anything else) formatted it as NTFS and installed it on that partition and I was done. Just had to reinstall grub after. (Windows 7 is the only one I've done).

---

### Post by oldfred on 2011-07-21
Gparted should also show you how much space you have used. I suggest two NTFS partitions one for the system and one for data. The data can also be in a logical as both Windows & Ubuntu will read a NTFS logical data partition, just that windows will not let the first install of windows be to a logical partition.

Not sure for size of windows as it can grow quickly and NTFS likes 30% or more free space to work well. I have seen minimums of 20GB for XP and 30GB for Vista/7.

It sounds like your extended currently is just swap, that is why you have two partitions of the same size. The extended partition is just a container for logical partitions. After shrinking the Linux partition, I might make one primary using some of the free space and then move the left of the extended into the remaining free space. Then you can create the logical NTFS. That way you  still have a primary partition for future use. Linux will not normally need a primary partiiton but if installing another copy of windows it is much better to use a primary.

---

### Post by Thrashrokz33 on 2011-07-21
I'm having some trouble here. I've shrunk the Linux partition from 246gb to around 150gb, leaving 100gb unallocated space. I used about 80gb of that for the Vista partition that I will be using, and I formatted it as NTFS. Oh, and I made it a primary partition. 

I didn't mess with anything else, because I figured that Vista would have no problem installing on 80gb of space. I put in the reinstallation dvd for windows Vista, and I get to the "custom installation" part. I select the partition that I made with the description "Windows Vista", and I'm pretty sure it's the right one. I selected it as the partition to install vista on, but I get an error message like "no suitable drive found" or something once I try to click the "next" button. Do I need another partition for this or something?

---

### Post by oldfred on 2011-07-21
Did you also put a boot flag on it with gparted. Or from Vista it is called make it the active partition.

---

### Post by tommpogg on 2011-07-21
I recently faced the same problem: i had to install Windows on a PC with Ubuntu 10.10 installed on the whole hard drive (1TB big).

This is what I did:
1) Backup all the data
2) Play a Live CD of Ubuntu 10.10 (in your case 11.04) and use GParted to resize the partition where Ubuntu was installed. IMPORTANT: this is a critical and quite dangerous step: it may cause data loss and harm the system.
3) Use GParted to create two different NTFS partition out of the newly freed space (one for windows and the other to share data between Ubuntu and windows)
4) install Windows
5) follow the steps in the article you cited to restore Grub: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Notice that we have different hardware, configuration and Ubuntu version. So this steps might not work for you

---

### Post by oldos2er on 2011-07-21
> **Thrashrokz33 said:**
> Thanks! I was looking through a few more forum posts, and it seems like some people ran into trouble with partitions. I'm very inexperienced with that

You should back up any and all data you can't afford to lose.

---

### Post by Thrashrokz33 on 2011-07-21
Ok update time. I've successfully installed Windows, and have seemingly recovered the Grub menu (It listed Vista and Ubuntu, and I have yet to attempt to boot Windows through grub, but I'm assuming that it works fine, since I've already booted it once since install.) So, in that aspect, I've accomplished my goal.

However...something strange happened with my Ubuntu installation. When I attempted to log in, my password was different. It was an older password that I had set up, instead of my most recent one. So, I logged on finally to find that everything had been reset to default -- I even have to update like two-hundred things just like I had to a few weeks ago when I first installed Ubuntu.

I would assume that my Ubuntu had been wiped clean...but the thing is I still have all of my files, word docs, etc. I unfortunately do not have any programs that I installed through the software center though, so that's a bummer. I've only been on Ubuntu for a few weeks, so it shouldn't be too hard to get back to where I was...but still this is a bit disappointing, considering that I went to all that trouble just to keep my settings.

---

### Post by akand074 on 2011-07-21
That's very very weird. That shouldn't happen unless you actually particularly did something to cause it on purpose. I didn't even know it was possible to rollback like that in ubuntu :S

---

### Post by Thrashrokz33 on 2011-07-21
Hmm, this seems weird, but I'm not sure if this is normal. I have two "home" folders in different locations now. One home folder is located at "/", which I'm guessing is the main filesystem. This one has the house icon, and on opening it you will find the common music,pictures,documents,etc. The other home folder is located at "/Media/117gb filesystem", and this has all of my old files in it (music,pictures). This does not have a house icon on it. I'm not sure if I booted into the wrong partition or what...but my main filesystem "/" says "volume unknown" now, as opposed to when it said "250gb".

Is it normal to have two home folders, and to have a drive within a drive?

---

### Post by oldfred on 2011-07-21
When you logged in differently it created a new user with new files in /home. But that should have been you standard /home. Is it not able to mount your /home for some reason and then defaulted to something else?

Post this - may be a bit much as we want to see how /home is mounted and if it can be mounted without error:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---


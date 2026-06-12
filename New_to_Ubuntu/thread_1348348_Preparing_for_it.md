---
title: "Preparing for it"
date: 2009-12-07
forum: New to Ubuntu
---

### Post by farkinid on 2009-12-07
Hi there,

I don't know if this is the place to post this given that I haven't even installed Ubuntu yet but I was hoping to get a better picture of what I will be encountering. I've read up on installing and some potential problems but I still don't have a clear picture. I'm hoping I could get some help advice here. This will be a long post so please bear with me. 

Firstly, I am running Windows 7 and XP on a dual boot configuration from 1 single hard disk. I would like to eliminate the XP partition and install Ubuntu on it. The questions for this part are  :-
[LIST=1]
[*]Do I need to format the XP partition with a Windows based tool or can I use the Ubuntu CD which I burned to do it?
[*]What potential problems will I be facing when trying to organize the MBR?
[*]Seriously, how complicated and time consuming is this going to be?
[/LIST]


Secondly, I have an external hard disk with all my media files on it. It is formatted in NTFS. So the questions are :-
[LIST=1]
[*]Will ubuntu recognize that hard disk?
[*]If it won't immediately recognize it, what should I prepare in advance so as to make it operational as soon as possible?
[/LIST]


And finally, later on when I'm more comfortable with Linux, I plan to set up another desktop of mine to store all my media files, work etc. With that in mind, will it be possible to setup that pc to stream videos or sounds bytes over the internet in the event I require it while I am away from that desktop? Is security going to be an issue?

I hope to get an answer before I toast my hard disks tonight. Thank you.

---

### Post by Locke_99GS on 2009-12-07
1.1) The Ubuntu installer can partition and format on its own.

1.2) Ubuntu will install the GRUB2 bootloader over your MBR.
 GRUB2 does a pretty good job at configuring itself by scanning all drives looking for bootable OS's. Usually picks up Windows without issue.     

1.3) Should not be complicated at all, and only take 10-20min.

2.1) Yes, but it won't auto-mount *by default*. It will be accessible from the "Places" menu. 

2.2) There is nothing you can do in advance.

3) Yes you can.

---

### Post by farkinid on 2009-12-07
Thank you for your answers. Wish me luck, I'll be attempting an installation in a couple of hours.

---

### Post by 3rdalbum on 2009-12-07
Honestly, just tell Ubuntu to use what is currently the Windows XP partition. (if you use the "manual partitioning" function in the installer, you need to set this partition with a mount point of "/" and a filesystem type of "ext3" or "ext4".

The Ubuntu installer will install a bootloader into your master boot record, which will be able to boot Windows 7 as well.

For streaming music and videos, you might want to just set up a Samba share, and then forward a port on your router. Security shouldn't be an issue if you have a strong password.

---

### Post by Temposs on 2009-12-07
Regarding partitioning:

When you are running the Ubuntu installer, it will get to the partitioning section of the Install process. In order to do your specialized partitioning process, where you want to delete your XP partition but keep your Win7 partition, you probably will have to choose the third option, the Manual Partition setup. 

This will start the interactive partitioning tool and you'll be able to set your XP partition to be deleted. Nothing will be done until you go to the next step. You're simply telling what will happen. Then you should make a new ext4 partition in the free space, and set the mount point to "/"(without the quotes). Leave a little bit of free space(equal to the amount of RAM in your system). In that last bit of free space make a swap partition. That should do it. You should have 3 partitions: Win7, Ubuntu, and Swap.

Continue on and it will apply all those steps and finish the installation :-)

Good luck!

---

### Post by farkinid on 2009-12-07
Hi and thanks for the replies. It is much appreciated. However, I think I messed up something. I formatted the xp partition and somehow my Windows 7 MBR is gone. So I'm trying to decide if I should repair the Windows 7 partition via reinstallation or I should go ahead with Ubuntu installation 1st.

Its all gone pear shaped on me now.

---

### Post by Temposs on 2009-12-07
Oy. I dunno what you did. You used a Windows-based partitioner, yeah? If you're going to have to reinstall Win7, you should do that first, before installing Ubuntu.

---

### Post by Temposs on 2009-12-07
And since you got rid of XP already, you don't have to do all that manual partition setup stuff. Just choose the Ubuntu Installer partition option that's something like "Install Ubuntu side-by-side with another Operating System"

---

### Post by farkinid on 2009-12-07
Hmm I think you are right. Oh well, most of my important data is on my external drive. Only some save files (of games which I will never get to complete) are there. Guess I'll fix Windows 1st. 

For the record, I'm using Ubuntu (without installation) to type this and honestly, I'm very impressed. Or maybe its just the novelty :p

---

### Post by Temposs on 2009-12-07
Probably you're impressed and it's a novelty ^_^

---

### Post by ST3ALTHPSYCH0 on 2009-12-07
There is a certain novelty factor.... kind of like when I discovered mini XP on the Hiren's util CD. Just the novelty of running windows as a live environment made it fun.... for 2 minutes.

---


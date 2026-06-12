---
title: "Partitioning help"
date: 2009-08-14
forum: New to Ubuntu
---

### Post by Majik_420 on 2009-08-14
I'm trying to setup a dual boot with Vista and Kubuntu, but I'm havin some real problems with this Partitioning stuff. Don't know anything about linux either but I'm tryin.

I had some problems installing Kubuntu and a few times druring the installition my computer shut down for some unknown reason, so now I find that I have 7 primary partitions under the disk manager in windows. From my understanding so far I thought I could only have 4 primary partitions with x extended ....? or is that possibly because of the two failed installs?

I'm also not clear on how to setup the FAT32 partition so that I can access my files from either operating system. I've tried searching some but I can't really find much helpful info on HOW to actually setup the partitions.

---

### Post by starcraft.man on 2009-08-14
Ubuntu has native read and write access to NTFS. Please, don't use FAT32, it's not a good fs anymore by modern standards.

As to partitioning, may I recommend the kind poeple at [gparted]("http://gparted.sourceforge.net/documentation.php") who made an excellent guide for new people. See old documentation, top to bottom in your means and language preferred.

If you've any questions after, feel free to post again.

I don't think you've more than 4 primaries, use a live CD and run gparted from that once ya know what your doing then see how the partitions are set up. If you need further help in that department, I can also help.

Edit: I've been instructed by the supreme kahoona Bodhi.Zazen that some people still like Fat32. Go figure! 

*runs away before bodhi thwaps him one*

---

### Post by bodhi.zazen on 2009-08-15
Here is a basic link :

[HowTo: Partitioning Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=282018&highlight=partitioning") 

what do you mean "set up" a partition ? You simply make a partition, fromat it FAT, and mount it. In windows it will get a letter such as F:\ in Linux use ntfs-config or add an entry in /etc/fstab

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131") 

Other then that we need to see your partitions. Boot the live desktop CD and take a screen shot of gparted or post the output of 

```
sudo fdisk -l
```

---

### Post by swerdna on 2009-08-15
I suggest you carefully recheck in vista's partitioner. It's impossible that there really are are 7 primaries. But, who knows how vista's partitioner thinks.

I recommend you delete the extraneous partitions with Gparted, which can be accessed from the Gparted live CD or from the Ubuntu live CD if you have a copy (I don't know about the Kubuntu CD).

Regarding mounting fat32 drives: [HowTo Mount a Fat32 / Vfat Partition Read Write in Ubuntu & Kubuntu]("http://ubuntu.swerdna.org/ubufat32.html")

---

### Post by Majik_420 on 2009-08-15
Alright so I dont know how to take a screen shot but heres my Partition Breakdown according to GParted:

/dev/sda2   extended   9.8g
  /dev/sda5   ext3   6.8g
  /dev/sda7   ext3   2.3g
  /dev/sda8   linux-swap   172m
  /dev/sda6   linux-swap   470m
unallocated                 7.2m
/dev/sda1   ntfs   220g
unallocated                 1.2m
/dev/sda3   ext3   2.3g
/dev/sda4   linux-swap   172.m


So I think the Vista partition manager just doesn't understand whats going on... anyway... Should I just delete everything except windows and reinstall Kubuntu? Im guessing theres so many of them because my computer would shut down during the installation process if I left the computer... weird. 

but yeah... Should I delete all of them or would it be ok to keep one ext3 and one linux swap? and then how do I consolidate the unallocated space to make a Fat partition if I choose...

And If kubuntu can read ntfs then why do I need fat? so that windows can get files from kubuntu because windows can't read ext3 without some program or something?

---

### Post by swerdna on 2009-08-15
I'd use Gparted to defo delete all but sda1 windows. And yes Kubuntu can read NTFS so you don't need fat32. So there'll be space after sda1 spare after you've deleted all the Linux stuff. Let the Kubuntu installer have its head with that spare space (just so long as it doesn't suggest any alterations to the windows partition).

One thing you might consider is shrinking sda1 before the install to give Kubuntu a bit more room.

---

### Post by Bartender on 2009-08-15
I think the first thing to do is address that part about the PC shutting down "for no reason".  There was a reason, and you need to find it.

There's just no way around it - you cannot have the machine shutting down while it's doing brain surgery on itself.

---

### Post by Majik_420 on 2009-08-15
> **Bartender said:**
> I think the first thing to do is address that part about the PC shutting down "for no reason".  There was a reason, and you need to find it.

There's just no way around it - you cannot have the machine shutting down while it's doing brain surgery on itself.


Well heres what happened with that. I installed ubuntu a few months ago with no problem, could dual boot between vista and ubuntu, but there was no communication between them, files were only on the respective  operating system they were stored on. So I went looking for a solution and find all this talk about partitioning and other distros.

So I read about Kubuntu, think it sounds cool, so I wipe out Ubuntu and try to install kubuntu from the cd I burned, Which yes I did check for integrity and defects and all that jazz, it seems to be fine. 

I have a power connection issue with my laptop anyway, Im pretty hard on my electronics unfortunately, so its kinda loose where the cord plugs in to my computer, so at first I thought it shut down because of that, which still may be the problem. Additionally I find that my computer will shut down if it gets too hot. I have ghetto not-so-great solutions for these small problems that allow me to at least use my computer throughout the day 95 percent problem free besides my computer unex[pectedly shutting down every now and then.

But what I noticed with the install was that I could install from the (bootmenu?) or I could try Kubuntu and actually install from Kubuntu while I was trying it. I tried both ways once, but I would just click install and then walk away for the sake of watching a pot of water boil. I think I just need to babysit it and make sure it stays on when I install Kubuntu again.

Sorry so long winded, just woke up, still puttin things together in my brain lol. So right now here is my plan of attack:
1.delete all partitions except for ntfs using GParted
2. resize ntfs so that there's a l;ittle more room for Kubuntu 
   -What is a good size for this partition? I have about 100G free. This is where I was also wondering about FAT32 partitioning. I've read that you only really need about 50G for windows, but yet I have so many files on the partition that I can't resize it down to 50G... then the whole fat32 thing is supposed to be like a common grounds, but now windows and kubuntu can read each other.... I feel like I'm reading old information and then coming here and I have to re learn a concept I don't completely understand in the first place lol.

Anyway thanks for helping, I'm sure I'll start pickin it up soon.

---

### Post by swerdna on 2009-08-15
Before you resize windows, defrag it, important.
What size for windows: boot to windows and go into My Computer --> C: drive icon, Right-click --> properties. That will tell you how much is being used at the moment. Calculate about 10-20 % more than that and make that the target for resizing.

You don't need a go-between fat32 partition for swapping files between Linux and windows. You have a perfectly good go-between partition in sda1/ntfs already. It's easy to mount sda1/ntfs into Linux.

Then after you defrag windows, boot to the Gparted CD / whatever CD, and size the ntfs down to your target. Then install Linux.

It's always a good idea (and important) to make a copy of important data on a hard drive before partitioning the hard drive -- simple good sense.

---

### Post by Majik_420 on 2009-08-21
Right now I have 9.8G of unallocated space at the front of my drive, 220.58G OS(C:) NTFS in the middle, and 2.5G unallocated at the end.

I defragged windows... Using Gparted would it be safe for me to now move OS to the front? and will the unallocated space condense into one section?

then after I move it, I plan to resize it. its at 220 right now, using about 100 so would 110-120 be ok? then the rest I can use for kubuntu correct?

---

### Post by swerdna on 2009-08-22
> **Majik_420 said:**
> Right now I have 9.8G of unallocated space at the front of my drive, 220.58G OS(C:) NTFS in the middle, and 2.5G unallocated at the end.

I defragged windows... Using Gparted would it be safe for me to now move OS to the front? and will the unallocated space condense into one section?

then after I move it, I plan to resize it. its at 220 right now, using about 100 so would 110-120 be ok? then the rest I can use for kubuntu correct?
120 would be fine
I would move it in one piece. Use your mouse in the Gparted GUI. Right-click and choose resize/move. Use the mouse to drag the whole NTFS partition to the  left. Then use the mouse to drag the right hand end to the left the amount you require.

---

### Post by Majik_420 on 2009-08-22
> **swerdna said:**
> 120 would be fine
I would move it in one piece. Use your mouse in the Gparted GUI. Right-click and choose resize/move. Use the mouse to drag the whole NTFS partition to the  left. Then use the mouse to drag the right hand end to the left the amount you require.


well.... game over. Tried to move it... but about ten minutes into it it said operation failed because there is no operating system.

I'm guessing that means windows was done? I installed a clean copy of Kubuntu using the full disk anyway... oh well. Good to move on and learn new things, just sucks to lose so much.

---

### Post by swerdna on 2009-08-22
> **Majik_420 said:**
> well.... game over. Tried to move it... but about ten minutes into it it said operation failed because there is no operating system.

I'm guessing that means windows was done? I installed a clean copy of Kubuntu using the full disk anyway... oh well. Good to move on and learn new things, just sucks to lose so much.

Never mind -- most likely finger trouble -- happens to me too occasionally -- restore the files you need from the backup.

---


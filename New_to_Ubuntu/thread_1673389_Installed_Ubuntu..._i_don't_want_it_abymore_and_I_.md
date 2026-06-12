---
title: "Installed Ubuntu... i don't want it abymore and I can't install Windows!"
date: 2011-01-22
forum: New to Ubuntu
---

### Post by Therisis on 2011-01-22
Hi, when i was installing Ubuntu, I've created a 200GB partion for ubuntu, I've selected that partion whilst installing. But no, expect install where i want it too install, IT WIPED OUT THE WHOLE DRIIVE. I got over that, but now i only have 1 big partion of 1tb and I'm STUCK. I cant create another partion, I cant even install windows HELP! :(

---

### Post by cgroza on 2011-01-22
If you want to get rid of Ubuntu just boot a live CD, format your big partition to NTFS, reboot, boot the Windows CD and install.

Also, if you just want another partition you do like above except you do not format it, but you resize it.
You may need to format the resulted unallocated space as ext4  or ext3.

People around here can help you making another partition and fix you problems if you are willing to.

---

### Post by candtalan on 2011-01-22
> **Therisis said:**
> Hi, when i was installing Ubuntu, I've created a 200GB partion for ubuntu, I've selected that partion whilst installing. But no, expect install where i want it too install, IT WIPED OUT THE WHOLE DRIIVE. I got over that, but now i only have 1 big partion of 1tb and I'm STUCK. I cant create another partion, I cant even install windows HELP! :(

Sorry to hear that. Which version of Ubuntu were you using?

---

### Post by Therisis on 2011-01-22
Well.... the latest .__.

updated and stuff

---

### Post by candtalan on 2011-01-22
> **Therisis said:**
>  now i only have 1 big partion of 1tb and I'm STUCK. I cant create another partion, I cant even install windows HELP! :(

Using the Ubuntu live CD you can easily resize the single partition. Using the Live session
System>Administration>Gparted partition editor

Try to resize the partition to get it up towards the right hand end (the end) of the display. This would leave a big unused space at the left hand end (the beginning of the hard drive). Then create a new partition to fill the space at the beginning Note what the size of the partition is, for future reference. You should set the new partition to be formatted as NTFS. You will then need to click on the commit (green arrow I think) to get it to do what you have set up.

Now, after this, when you go to install Windows, you can choose the new (NTFS) partition to install Windows into. When installing  then you might still choose to format the partition again if you wish.

After Windows is installed again, you will still have Ubuntu on the drive as before, but you will not see a boot choice for Ubuntu, only windows will boot. Later, when you are ready, you can use the live CD to follow instructions to re install the Ubuntu boot loader (grub2) to give you the choice to boot into either Windows or Ubuntu.

---

### Post by akand074 on 2011-01-22
> **Therisis said:**
> Hi, when i was installing Ubuntu, I've created a 200GB partion for ubuntu, I've selected that partion whilst installing. But no, expect install where i want it too install, IT WIPED OUT THE WHOLE DRIIVE. I got over that, but now i only have 1 big partion of 1tb and I'm STUCK. I cant create another partion, I cant even install windows HELP! :(

I'm sorry you made a mistake while installing Ubuntu. It would be helpful if in the future you explain your problem more thoroughly, i.e. why can't you create another partition (what errors are you getting), why can't you install windows? What is happening when you try?

Though, like someone said previously, Use the Ubuntu disk you have to wipe the entire drive again and format it to NTFS then use your Windows disk to install Windows. Though if I'm not mistaken, if you are using the entire drive, your windows disk/recovery disk should be able to do it itself by just deleting the entire drive. Though I think the worry is that Windows won't be able to read the ext4 partition (the file format Ubuntu uses by default). I know Windows itself can't.. but the partitioner might if I remember correctly. Anyways give it a try and let us know if you need a hand with anything.

---

### Post by candtalan on 2011-01-22
> **akand074 said:**
> I'm sorry you made a mistake while installing Ubuntu

Mistake?

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/659106](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/659106)

---

### Post by Michael Dooley on 2011-01-22
> **candtalan said:**
> Mistake?

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/659106](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/659106)

Thanks for the bug reference candtalan. I have never quite trusted the install process to decide where a new ubuntu install should reside. Generally, I use Gparted or Parted Magic to prepare the HD before an installation. Thanks again.

---

### Post by akand074 on 2011-01-22
> **candtalan said:**
> Mistake?

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/659106](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/659106)

I'll withdraw that statement. 

I've never done any install but a manual install. I just figured chances are much higher that it's a user error than a software error.

---

### Post by candtalan on 2011-01-22
> **akand074 said:**
> I'll withdraw that statement. 
I've never done any install but a manual install. I just figured chances are much higher that it's a user error than a software error.

Understood, no problem. I was bitten hard by this  particular bug and it gave me quite a shock (and a measure of grief). All other installers in the Ubuntu world have been pretty good, and I am hopeful this bug etc will not appear in natty.

---

### Post by akand074 on 2011-01-22
> **candtalan said:**
> Understood, no problem. I was bitten hard by this  particular bug and it gave me quite a shock (and a measure of grief). All other installers in the Ubuntu world have been pretty good, and I am hopeful this bug etc will not appear in natty.

I once tried to install Ubuntu Moblin Remix on my laptop just to see what it's like. I made the image and I booted into it.. I waited as I was expecting an installer dialogue to open to ask me where I want to install the OS. After a few seconds a dialogue shows "formatting ext3 partition". I was like WHAT! No options or warnings.. just started formatting. I immediately unplugged my laptop. I spent days after recreating my partition table and getting my school files that I had neglected to back up in over a month. That was sure a shock for me.

---

### Post by candtalan on 2011-01-22
> **akand074 said:**
>  After a few seconds a dialogue shows "formatting ext3 partition"

Ouch

---


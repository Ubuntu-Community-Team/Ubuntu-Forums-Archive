---
title: "Any risk in deleting ubuntu partiton from windows using minitool??"
date: 2011-06-26
forum: New to Ubuntu
---

### Post by neo1691 on 2011-06-26
[SIZE=2]Hi!! I have an ubuntu 10.10 installed in a separate partition.!! i have downloaded ubuntu 11.04 and burned it in a cd.!! if i delete the partition from minitool to do a fresh installation, are there any risks of not booting again?? 

here is what is shown while booting!!
[IMG]http://dl.dropbox.com/u/25234323/boot.JPG[/IMG]
[/SIZE]

---

### Post by dFlyer on 2011-06-26
Why delete the partition with minitools when you should be able to just install 11.04 over your old ubuntu installation. I would back up all your data on both windows and /home folder in ubuntu to be safe. I believe the install cd gives you the choice to replace your old ubuntu install.

---

### Post by neo1691 on 2011-06-26
> **dFlyer said:**
> Why delete the partition with minitools when you should be able to just install 11.04 over your old ubuntu installation. I would back up all your data on both windows and /home folder in ubuntu to be safe. I believe the install cd gives you the choice to replace your old ubuntu install.

actually i haven't installed ubuntu 10.10 properly!! i was a complete noob yet i wanted to make a separate partition for that!! so i ended up creating a partition of 20 mb and using advance installation i gave 6 gb of swap and less space to /home!! 
so what should i do to remove old completely and add new version of ubuntu??

---

### Post by -kg- on 2011-06-26
A partition of 20 mb?  Or did you mean 20 gb?

If you can, boot to the Live CD and either pull up a terminal and issue the command:

```
sudo fdisk -l
```
(That's a lower case "-L")

Or better, pull up Gparted and take a screen shot of it and post it.  "Fdisk -l" will show us a list of the partitions on your hard drive, but Gparted will show a graphical representation, as well as partition usage statistics.

Also helpful would be your computer resources...i.e., processor, RAM, total HD size (though that will be shown with either of the above commands), etc.  Before we can make realistic suggestions, we need to know what you're dealing with.

---

### Post by nzjethro on 2011-06-26
> **neo1691 said:**
> actually i haven't installed ubuntu 10.10 properly!! i was a complete noob yet i wanted to make a separate partition for that!! so i ended up creating a partition of 20 mb and using advance installation i gave 6 gb of swap and less space to /home!! 
so what should i do to remove old completely and add new version of ubuntu??

Even so, when you get into your install options, you should be able to install 11.04 over your botched 10.10 install. Just give less space to swap (I don't even bother with swap, and I run fine), and more to /home.

The only risk would be that your Ubuntu 10.10 "install" is controlling booting. If you delete 10.10, you will have to update Grub (which may be difficult without an Ubuntu partition). Basically though, if you are trying to delete 10.10, and immediately reinstall 11.04, there shouldn't be any issues.

And as always, there's absolutely no risk in doing anything as long as you've **backed up all important data.**  :D

---

### Post by neo1691 on 2011-06-27
> **-kg- said:**
> A partition of 20 mb?  Or did you mean 20 gb?

If you can, boot to the Live CD and either pull up a terminal and issue the command:

```
sudo fdisk -l
```(That's a lower case "-L")

Or better, pull up Gparted and take a screen shot of it and post it.  "Fdisk -l" will show us a list of the partitions on your hard drive, but Gparted will show a graphical representation, as well as partition usage statistics.

Also helpful would be your computer resources...i.e., processor, RAM, total HD size (though that will be shown with either of the above commands), etc.  Before we can make realistic suggestions, we need to know what you're dealing with.

Here is the gparted screenshot!!
[IMG]http://dl.dropbox.com/u/25234323/gpared%20screenshot[/IMG]

My ram is 3 gb!! More information of my laptops resources are [here]("http://www.gadgetsguru.in/hp-pavilion-dv6-1111au-notebook-vb627pa-price-specification-buy-india-8169.aspx")

> **nzjethro said:**
> Even so, when you get into your install options, you should be able to install 11.04 over your botched 10.10 install. Just give less space to swap (I don't even bother with swap, and I run fine), and more to /home.

The only risk would be that your Ubuntu 10.10 "install" is controlling booting. If you delete 10.10, you will have to update Grub (which may be difficult without an Ubuntu partition). Basically though, if you are trying to delete 10.10, and immediately reinstall 11.04, there shouldn't be any issues.

And as always, there's absolutely no risk in doing anything as long as you've **backed up all important data.**  :D

I want to start all over again only because i messed up with the installation of ubuntu 10.10. Also if i manage to delete all the partition and make a new drive, i am sure i will be again confused with this thing called sda/dev something and bootloader. Like how much space to give them!! so i am pretty afraid about doing that!!

---

### Post by Paqman on 2011-06-27
Here's one way of sorting yourself out:

Boot up into the LiveCD and start the installer. When you get to partitioning select "manual partitioning".

Shrink /dev/sda5 down to 3GB, partition type "swap".
Delete /dev/sda6, you don't need a /boot partition.
Expand /dev/sda7 into the space created, format as EXT4, mount point /
Leave /dev/sda8 as it is (or maybe give it another couple of GB, since it seems fairly full already). Do not format it, this will leave all your data and settings intact. Make sure you set up your username(s) exactly the same as on the previous system.

---

### Post by neo1691 on 2011-06-27
> **Paqman said:**
> Here's one way of sorting yourself out:

Boot up into the LiveCD and start the installer. When you get to partitioning select "manual partitioning".

Shrink /dev/sda5 down to 3GB, partition type "swap".
Delete /dev/sda6, you don't need a /boot partition.
Expand /dev/sda7 into the space created, format as EXT4, mount point /
Leave /dev/sda8 as it is (or maybe give it another couple of GB, since it seems fairly full already). Do not format it, this will leave all your data and settings intact. Make sure you set up your username(s) exactly the same as on the previous system.

Thanks a lot!! exactly what i wanted!! will back up my windows before!!
I will shrink another 10 gb from my c drive so that it will available as unallocated space while manually installing ubuntu!!
Also i wont have to delete the old 20 gb partition and i will be safe whatsoever happens!! 
One question: after making that 10 gb extra partition how to merge it with already created partitions in my previous installation!!
and does that sd7 is home?? also i have very less space for desktop!! How to increase that too using that 10 gb extra partition that i will be creating!!

Sorry if i am asking way too silly question.. :P :D
Thanks a lot everyone for making this communtity so so helpful!!

---


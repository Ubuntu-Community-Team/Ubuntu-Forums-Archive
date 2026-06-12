---
title: "Making the complete change to Ubuntu!"
date: 2009-04-18
forum: New to Ubuntu
---

### Post by sylvainrb on 2009-04-18
I'm currently running Windows XP and Ubuntu 8.10 (dual boot) and I've come to the point where I don't need XP anymore. So now I want to erase the XP partition and have Ubuntu take up all the hard disk's space. What would be the best way to do it? Also will GRUB update itself?

OR

Could I just insert the live CD and do a complete install? But I want to keep all my installed programs/files/desktop configurations... Can I just save all this in an .iso image and load it in the fresh Ubuntu install?

Another concern: My laptop is a Compaq Presario V2000 and has a recovery partition that I can't delete with Windows. Will Ubuntu erase that partition as well?

Sorry its a long one and thanks in advance. I appreciate the help I receive on this forum. It's making the experience a lot easier and enjoyable!

---

### Post by |Mitch| on 2009-04-18
I believe you can use gparted to delete the Windows/Recovery partition.

---

### Post by CatKiller on 2009-04-18
You can remove both those partitions with GParted. Since you also want to modify the partition with / on, you'll need to use a live cd, since you can't change a partition that's mounted.

You may need to change GRUB's settings manually. GRUB's configuration is stored in /boot/grub/menu.lst. If you have an entry for Windows, you'll want to remove that. menu.lst also says where GRUB should look for the next stage in the booting process, in the form of (hd0,1) where (hd0) means the first hard drive, and (hd0,1) means the **second** partition on the first hard drive (it starts counting from 0). You'll probably need to change these entries to reflect the new partitoning layout.

---

### Post by juancarlospaco on 2009-04-18
Wait 5 days and then make a Clean Install of Jaunty.

---

### Post by Bucky Ball on 2009-04-18
Download the gparted live iso, make a CD and boot from that. Kill the XP partition, resize as you want:

[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

Get the &#313;ive´ version. :)

---

### Post by presence1960 on 2009-04-18
> **sylvainrb said:**
> I'm currently running Windows XP and Ubuntu 8.10 (dual boot) and I've come to the point where I don't need XP anymore. So now I want to erase the XP partition and have Ubuntu take up all the hard disk's space. What would be the best way to do it? Also will GRUB update itself?

OR

Could I just insert the live CD and do a complete install? But I want to keep all my installed programs/files/desktop configurations... Can I just save all this in an .iso image and load it in the fresh Ubuntu install?

Another concern: My laptop is a Compaq Presario V2000 and has a recovery partition that I can't delete with Windows. Will Ubuntu erase that partition as well?

Sorry its a long one and thanks in advance. I appreciate the help I receive on this forum. It's making the experience a lot easier and enjoyable!

I would not remove your recovery partition unless you are given an option to burn this to CD/DVD and have already done so. If you remove this partition and want to reinstall windows you will be unable to do so unless you have another Windows CD/DVD or order the restore discs from the manufacturer.

Another option is to use the windows OS partition as a data storage partition. You can use gparted to delete the windows partition then create an ext 3 partition for storage. But be careful to insure you remove the OS not the recovery partition!

There are a few options presented on this thread for you, choose which best suits your needs.

---

### Post by Bucky Ball on 2009-04-18
Oh, yea, Presence1960. Sorry, forgot. Backup before doing anything, but especially that partition! The manufacturer usually gives you someway to make a bootable recovery disk. :)

---

### Post by stalkingwolf on 2009-04-18
You can use remastersys to make an ISO of your ubuntu system burn it, check it, then wipe your drive and install your system back.  You might still need to edit your grub menu.

---

### Post by sylvainrb on 2009-04-18
Ok thank you everyone for the information!

@ presence1960 and Bucky Ball: I have a back up of my Windows system with recovery CDs. I learned the hard way a long time ago about backing up your information! 

@ juancarlospaco: I was thinking of waiting for Jaunty, but I'm not sure how stable it will be with my system? I don't have any trouble regarding stability with Intrepid and since it will be my only OS on this computer I don't want to spend too much time trying to fix bugs. What do you guys think?

---

### Post by juancarlospaco on 2009-04-18
Jaunty is Stable.

---

### Post by sylvainrb on 2009-04-18
> **juancarlospaco said:**
> Jaunty is Stable.

Lol that's not really what I meant. To clarify, is there a list of known issues with the next release of Jaunty that weren't issues with Intrepid?

---

### Post by longtom on 2009-04-18
> **juancarlospaco said:**
> Jaunty is Stable.

With any hardware under any circumstances?  Where do you get your wisdom from?

---

### Post by Ericyzfr1 on 2009-04-18
I have Jaunty beta as my only OS on this machine and I will do complete install next week once the release is out. If you have a back-up of your MS OS, you are safe. Configuring your settings and prefered apps will take you less time as you get use to do it. Make a list of the programs you need and your settings, you can have a complete running system in less than a couple of hours.

---

### Post by sylvainrb on 2009-04-18
> **Ericyzfr1 said:**
> I have Jaunty beta as my only OS on this machine and I will do complete install next week once the release is out. If you have a back-up of your MS OS, you are safe. Configuring your settings and prefered apps will take you less time as you get use to do it. Make a list of the programs you need and your settings, you can have a complete running system in less than a couple of hours.

I want to do the complete install this week end since I have some free time for once. But once I can use Jaunty, can I just upgrade Intrepid to it or do I need to do a fresh install over Intrepid and reconfigure everything?

Also another total different question: Can I use the Windows recovery discs to install XP on the virtual box (without erasing Ubuntu!)?

---

### Post by CatKiller on 2009-04-18
> **sylvainrb said:**
> But once I can use Jaunty, can I just upgrade Intrepid to it or do I need to do a fresh install over Intrepid and reconfigure everything?

Generally you can just upgrade. I've been upgrading this install in place since Hoary (4 years ago). It's probably worth backing up anything you're desperate to keep, just in case, but you're making regular backups anyway, right? :)

---

### Post by tofiluk on 2009-04-18
> **juancarlospaco said:**
> Jaunty is Stable.

i agree. hehehe...

---

### Post by NightwishFan on 2009-04-18
Not sure about Windows, though, if you want to remove it, and have permission to, I advice you make a "data" partition on your disk, and leave space for the "OS" partition.

Example: (In GPARTED or Ubuntu installer)

200gb disk
Partition 1 160gb/ext3 Mount: /mnt/data
Partition 2: SWAP (1.5x your RAM in size)
Partition 3: 35gb/ext3 Mount: /

Copy all of your data to a large Partition 1 (MAKE SURE YOU DO NOT DELETE IT DURING THE RESIZING/CREATING)

Install Ubuntu, and mount partition 1 as /mnt/data (DO NOT FORMAT DURING INSTALL!!!), and format a swap and root partition with the remaining space.

Organize data into proper folders in /mnt/data

When installed, link the folders to your home folder (not copy) So that /mnt/data/Music links to /home/youruser/Music.

That way you have all your data if you choose to reformat, and it is organized like it is all in your home folder. I do not like mounting the data partition as home, because that gets messy.

Please ask for clarification if you do not understand anything.

---

### Post by sylvainrb on 2009-04-18
> **CatKiller said:**
> Generally you can just upgrade. I've been upgrading this install in place since Hoary (4 years ago). It's probably worth backing up anything you're desperate to keep, just in case, but you're making regular backups anyway, right? :)

Yes I am. I will probably go with Intrepid and upgrade to Jaunty when I get a chance.

---

### Post by sylvainrb on 2009-04-18
> **NightwishFan said:**
> Not sure about Windows, though, if you want to remove it, and have permission to, I advice you make a "data" partition on your disk, and leave space for the "OS" partition.

Example: (In GPARTED or Ubuntu installer)

200gb disk
Partition 1 160gb/ext3 Mount: /mnt/data
Partition 2: SWAP (1.5x your RAM in size)
Partition 3: 35gb/ext3 Mount: /

Copy all of your data to a large Partition 1 (MAKE SURE YOU DO NOT DELETE IT DURING THE RESIZING/CREATING)

Install Ubuntu, and mount partition 1 as /mnt/data (DO NOT FORMAT DURING INSTALL!!!), and format a swap and root partition with the remaining space.

Organize data into proper folders in /mnt/data

When installed, link the folders to your home folder (not copy) So that /mnt/data/Music links to /home/youruser/Music.

That way you have all your data if you choose to reformat, and it is organized like it is all in your home folder. I do not like mounting the data partition as home, because that gets messy.

Please ask for clarification if you do not understand anything.

Thank you, but the only reason I want one OS on this machine is that its HD is only 60GB and as I've been using Ubuntu more and more, I'm starting to need more space (since I've been neglecting XP and transferred all music/videos to Ubuntu). But I will look into it and try to understand it better. I'll ask for help if need to haha!

I will upgrade to a larger HD sometimes...

---

### Post by killabee44 on 2009-04-19
I am using remastersys for the first time and am very impressed with it. I made a custom bootable dvd with all my user data and booted from it from another pc. 

Wow. 

That's all this new convert from windows has to say. 

I am VERY impressed. It is as if I had my pc in front of me.

Try it. It might be a good option for you.

---


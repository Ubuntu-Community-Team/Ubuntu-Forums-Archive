---
title: "Time to dump windows but..."
date: 2011-02-04
forum: New to Ubuntu
---

### Post by Sephirotica on 2011-02-04
I have recently downloaded Ubuntu via Wubi and it was kinda love at first sight. As apparent i was running double boot with Windows XP being my "main" OS.

Well, now I'd like to switch to "full-time" Ubuntu since ive gotten accustomed to Wine and other compatibility programs (that i need for some software and random game here and then).

Now, ofc even I can come up with the basic "format HDD and install Ubuntu" but id like to ask if there is a way to remove Windows and install (full) Ubuntu* without loosing all of my HDD data. I'm asking here first since backuping something over 400GB of data (and, thats not including games and other random s@#t i can go without) is not something id do for fun.

If someone can id like to be, in absence of a better word, walked trough it (baby) step by step since 1) Im still not all that "at home" with Ubuntu, and 2) I wouldnt like to do something stupid that will cause me to lose all my data without backuping it first.

*As i understand the one i dloded via Wubi is slightly slower/less powerfull than a full (clean) Ubuntu instalation.

---

### Post by YesWeCan on 2011-02-04
I would recommend you keep your Windows installation and install Ubuntu on a separate HD. You will be able to access your Windows filesystem from Ubuntu. This will keep things simple and protect your Windows install, which you will probably wish to use from time to time.

---

### Post by Rhizoid on 2011-02-04
+1 to the extra HDD - it's what I did when I canned Windows.

Disk space is cheap these days and Ubuntu is very light in terms of space requirements compared with MSWin.

---

### Post by MC_Sketch on 2011-02-04
i agree with YesWeCan
chances are at some point you're going to want to go back to windows. what i would do is buy a new hard drive, download a full version of Ubuntu, burn it to a CD and then install it on the new hard drive, that way you can choose to have both, instead of choosing one or the other =]

---

### Post by jonnny_j22 on 2011-02-04
I second yeswecan,

There are many reasons to keep a windows partition on your machine - mp3 players, phones and digital cameras that have software not supported by wine, bios flashing (so much easier if you have windows) plus a second os is always a backup if something happpens to your ubuntu os (even if windows only reads fat and ntfs grr!)
 
If you don't want to go the second hard drive route, ubuntu's live cd will actually do the hard work for you - when you get to installation, select 'install ubuntu side by side' and ubuntu will shrink your partition to make space for it's self then pop itself in and install grub2 to manage the boot process.
 
Ubuntu comes with gparted on the install cd that will also let you edit your hard drive partitions manually. 

A couple of tips -
 
A typical unix style install such as linux is not actually one partition like windows. Windows uses a primary partition and just starts filling it. A linux install is a little different. You start off with an extended partition (in basic terms a primary partition that can be split up) into that several logical partitions are set up. The minimum you would expect to set up would be 4 - one to be formatted as swap, the others to be formated with a linux flesystem such as ext3/ext4 and then 'filled' by setting mount points - ' /'   '/boot' and '/home'.
 
 the swap partition should be about twice the size of your ram (if you can afford the space) - this is an area of the hard drive that unix systems use as a sort of RAM extension incase they run out of RAM
 
The /boot partition does exactly what it says on the tin - it's where the the booting of your system happens, so it doesn't need to be very big at all - 100mb will be more than enough.

the / partition or 'root' partion is where everything else will go (unless you say otherwise) this should be fairly large to allow for growth - i tend to go for about 8GB (just because I use 2GB swap and 10 seems a nice even number) and I've not run out of space yet.

The /home partition is like mydocuments in windows XP, it's where all your data will go - all the stuff that takes up all the room, so typically this is very large. However ubuntu can read the windows ntfs partitons that your current xp install has created. this means that you can set the /home mountpoint to the windows ntfs partition and all your data will be easily accessibly to both OS's (remember windows cannot read linux filesystems) Just remember if you choose to go this root DO NOT format this partition, just mount it.
 
 
That would be a basic install. you can simply divide the extended partition in two and have just swap and root, though this is considered bad 'linux form' as it means everything is mashed in together (the downsides of this I'm sure you can appreciate from the trouble windows is causing. 

Ideally, you would have a different logical partition for each directory in the linux sytstem, (all the ones that appear in the drop down list for mountpoints.) this is rarely done by those new to linux for simplicity and the fear of creating lots of unused 'dead space, though many would also recomend creating seperate partions for /proc and /tmp to simplify re-installing, changing distros and the like.

The good news is that ubuntu is designed to carve up a windows system to it's needs, I just thought I'd give you an idea of how the system should work - I remember when I first installed linux and had absolutly NO idea what a mountpoint was - the installer was almoast shouting at me for a root partition and i had no idea what it was talking about!

---

### Post by bcbc on 2011-02-05
> **Sephirotica said:**
> I'm asking here first since backuping something over 400GB of data (and, thats not including games and other random s@#t i can go without) is not something id do for fun.

I don't think anyone backs up for fun. You should have a backup if the data is important - buy a 1 TB drive, back it up overnight. It probably won't even take that long - maybe a couple of hours. What would you do if your drive failed?

There're enough sad cases to see on the forums already where all their data is gone without adding another :(

Re. your plan... there's no way to move to a real install of Ubuntu without changing the underlying file system from ntfs. So you cannot convert your drive to ext2/3/4, replace the OS and hope to keep your data in tact. 
What you could do is partition off a large chunk of free space, install Ubuntu on that (or migrate your Wubi to it), and then leave your data on ntfs and access it from there. That'll keep your dual boot going too.

But it seems the easiest way would be to get a cheap, large external drive, copy the data off, format and reinstall and then copy it back on.

Or as the others have said, get a new drive for Ubuntu which works if it's not a laptop.

PS if you have important data on Wubi it's even more important to back it up. If the virtual disk gets corrupted you could lose it all.

---

### Post by Sephirotica on 2011-02-05
> **bcbc said:**
> Or as the others have said, get a new drive for Ubuntu which works if it's not a laptop.

Yeah, thats probably the part i forgot to mention, right? It is a laptop.

So far my HDD is divided into 100GB Windows "system" partition, 700GB "data" partition and 200GB "random" partition.

As for advices to back up my data anyway its not like its something major and important that i dont want to loose. What i dont want to loose i have backed up usually in more than one copy. This is just the sort of stuff that i have, need and use RIGHT NOW. Its not irreplaceable only it would take more time to get it all in one place again than it would to to write Anna Karenina in binary code.

jonnny_j22 thank you for the explanation. 

So would it be possible to "move" my Wubi to the 200GB partition? Or make a fresh Ubuntu install there? And what is the difference between making an install from an actual CD as opposed to Wubi? Is Wubi slower/less reliable or what?

---

### Post by bcbc on 2011-02-05
> **Sephirotica said:**
> So would it be possible to "move" my Wubi to the 200GB partition? Or make a fresh Ubuntu install there? And what is the difference between making an install from an actual CD as opposed to Wubi? Is Wubi slower/less reliable or what?
It's possible to [move your wubi]("http://ubuntuforums.org/showthread.php?t=1519354"). 

The big thing with wubi isn't the speed. It's the fact that everything is stored on a single file (the virtual disk, root.disk). If it gets corrupted or deleted, then you can lose the data on it. I don't think it happens a lot, but it does happen (don't know whether it's random or the users do something to cause it either). There're also the grub problems as described [here]("http://ubuntuforums.org/showthread.php?t=1639198"). If you take precautions like backing up your root.disk you can prevent most of these issues. 

It's supposed to be slower but not that much - it's lot faster than live USB or a virtual machine.

---

### Post by Brian96 on 2011-02-05
> **Sephirotica said:**
> Yeah, thats probably the part i forgot to mention, right? It is a laptop.

So far my HDD is divided into 100GB Windows "system" partition, 700GB "data" partition and 200GB "random" partition.

As for advices to back up my data anyway its not like its something major and important that i dont want to loose. What i dont want to loose i have backed up usually in more than one copy. This is just the sort of stuff that i have, need and use RIGHT NOW. Its not irreplaceable only it would take more time to get it all in one place again than it would to to write Anna Karenina in binary code.

jonnny_j22 thank you for the explanation. 

So would it be possible to "move" my Wubi to the 200GB partition? Or make a fresh Ubuntu install there? And what is the difference between making an install from an actual CD as opposed to Wubi? Is Wubi slower/less reliable or what?

You can easily set up an Ubuntu partition in that 200GB slot.  You won't need more than about 10-15 GB for Ubuntu, and that's assuming you want to install a lot of stuff.  Don't think there's a way to move Wubi install, though.  And if there were, it certainly wouldn't be as stable as a clean install.

---

### Post by bcbc on 2011-02-05
> **Brian96 said:**
> And if there were, it certainly wouldn't be as stable as a clean install.

It works fine. Nothing is as 'stable as a clean install' - except one where you've applied the updates to address bugs that they couldn't fix in time for the release. Or you've spent many hours finding the right drivers and settings to get your hardware working just right. Those are good reasons to migrate the wubi install.

If you've done nothing much and everything worked ootb, then a clean install is easier...

---

### Post by Sephirotica on 2011-02-05
> **bcbc said:**
> If you've done nothing much and everything worked ootb, then a clean install is easier...

Than a clean install it is. 

Thanks guys.

---


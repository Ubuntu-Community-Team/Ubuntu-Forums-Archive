---
title: "Ubuntu Linux on USB"
date: 2011-03-24
forum: New to Ubuntu
---

### Post by Learning Linux 2011 on 2011-03-24
A couple of things:

I don't really understand Ubuntu on a USB device.
Can you install Ubuntu and run it on a USB device?  Or do you just use the USB device like a CD to install Linux on a hard drive?

What size USB device would I need?  4GB? 8GB? 16GB?

I've noticed that Ubuntu seems to need about 256MB of RAM and about 4GB of hard drive space. Is that about right?

---

### Post by lmarmisa on 2011-03-25
> **Learning Linux 2011 said:**
> A couple of things:

I don't really understand Ubuntu on a USB device.
Can you install Ubuntu and run it on a USB device?  Or do you just use the USB device like a CD to install Linux on a hard drive?

What size USB device would I need?  4GB? 8GB? 16GB?

I've noticed that Ubuntu seems to need about 256MB of RAM and about 4GB of hard drive space. Is that about right?

Ubuntu runs just fine on USB devices. I have one USB drive of 1 Gbyte running Ubuntu with no problems.

Ubuntu running on a USB device is better than a Ubuntu Live CD because you can add persistence when you create it. This persistence remembers all the new files you add or any change on the configuration.

You can create a Ubuntu USB install selecting System -> Administration -> Startup Disk Creator.

I recommend [Slax]("http://www.slax.org/") as an alternative to Ubuntu for running on a USB device.

---

### Post by Hedgehog1 on 2011-03-25
There is another way to run Ubuntu from a USB stick.  You can do a real install on it where the USB stick is installed as a hard drive:

[IMG]http://img197.imageshack.us/img197/6631/gparteduaos.png[/IMG]

This is the USB stick (as seen in gparted) I carry to work and back every day.  It has a FAT32 partition so I can copy data from windows, and then the real Ubuntu install.  I keep about a dozen music albums on it.  I can plug it into any PC, boot from the USB, and run my copy of Ubuntu with my music and my documents.

***The Hedge***

:KS

p.s. For a 'real' install, a faster USB stick is better.

---

### Post by hardfire_avk on 2011-03-25
Ubuntu on a USB drive is a very cool concept.
First thing its really easy to install via USB , as u can put in the latest version easily.. not like getting a new CD everytime.
Second, we can also use it as a portable OS, very cool concept .. does take a fair amount of space .. but what's the big deal when we can get the OS we like anywhere anytime ...

---

### Post by Learning Linux 2011 on 2011-03-25
How much space should a USB device have?  I'm still a little uncertain.  

If/when you use Startup Disk Creator, does that just copy an ISO image to the USB device to create a sort of "Live USB" similar to a "Live CD"?
Or do you actually *install* linux to the USB?  

I think I have figured out that my Ubuntu Linux installation uses about 4GB of space.  Would that be about the right size for a USB device, or should I go with like 8GB?  I'm planning on purchasing a new USB device, I saw some in the paper for like $9 for a 4GB and $14 for an 8GB.  Would 8GB be overkill?


Hedge,

How big is that USB stick?  I haven't quite figured out how to read partition info in Ubuntu yet.  It looks to me like there are 3 partitions, part of the device is FAT32, part is swap and the rest is ext4.  Is that right?
The FAT32 is mostly for data, and the ext and swap are for the actual Linux install?
How do you actually "install" Linux on a USB? Is that just using the Startup Disk creator, or is another method used?




> **Hedgehog1 said:**
> There is another way to run Ubuntu from a USB stick.  You can do a real install on it where the USB stick is installed as a hard drive:

[IMG]http://img197.imageshack.us/img197/6631/gparteduaos.png[/IMG]

This is the USB stick (as seen in gparted) I carry to work and back every day.  It has a FAT32 partition so I can copy data from windows, and then the real Ubuntu install.  I keep about a dozen music albums on it.  I can plug it into any PC, boot from the USB, and run my copy of Ubuntu with my music and my documents.

***The Hedge***

:KS

p.s. For a 'real' install, a faster USB stick is better.

---

### Post by I2k4 on 2011-03-25
Ubuntu's official instructions here are almost foolproof:

[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

At Step 2, using the USB "show me how" steps on the recommended installer, be sure to set the installer "Persistence" after the last step - if you are sure you are installing 4GB of packages with Ubuntu, I'd suggest an 8GB USB drive with 2GB set for Persistence, leaving you some breathing room for both the OS and Persistence.

The main other things to know, is that the USB drive does not quickly mount the hard drive when it boots up, so if you are running software that accesses the hard drive, you may have to prevent it from automatically starting up (DropBox is a good example.)  Second, because USB drives are slower, it's best to tweak software that reads/writes to disk (Like GIMP Preferences for swap files or FireFox, using about:config) to do it to the hard drive instead of the USB.

---

### Post by Learning Linux 2011 on 2011-03-25
Do the USB devices use a specific ISO file that was designed for them
or do they just use the regular Live CD ISO?

---

### Post by Learning Linux 2011 on 2011-03-25
Ok, I'm getting it now. 

That was a good idea to link to the Ubuntu download.  I never read the whole thing about USB devices.

I guess you can either essentially install a "Live CD" to the USB device (make the USB device a "live cd")
or you can start from a "Live CD" and then do a full install of Linux onto a USB device instead of a hard drive.

---

### Post by I2k4 on 2011-03-25
Not sure I understand you.  What you do is download the Pendrive installer as recommended by Ubuntu, and then download the ISO file for whatever version you want to use to your hard drive.  Then, plug in a USB drive.  

Running the installer, you just install directly to the USB drive, which will be identified in the installer dialog box. Go step by step according to the "Show me How" directions - they are very good, go slow.

The only extra step not listed in the Ubuntu instructions, is to to define "Persistence".  The "Persistence" option is there on the installer interface - I suggest setting 2GB of Persistence if you have a 4GB USB Drive.  That leaves you enough room for a standard Ubuntu install and some extra packages you might get interested in.

There's no CD involved. Forget about burning CDs.  Have fun with it.

---

### Post by Hedgehog1 on 2011-03-26
> **Learning Linux 2011 said:**
> Ok, I'm getting it now. 

That was a good idea to link to the Ubuntu download.  I never read the whole thing about USB devices.

I guess you can either essentially install a "Live CD" to the USB device (make the USB device a "live cd")
or you can start from a "Live CD" and then do a full install of Linux onto a USB device instead of a hard drive.

You are correct - you have two options.  The 'pendrive installer option', or the 'use the USB as THE hard drive' option.  Both work, both have advantages.

***The Hedge***

p.s. The USB stick in the image is 16 gigs before formatting.

---


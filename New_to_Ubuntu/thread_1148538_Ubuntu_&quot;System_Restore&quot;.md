---
title: "Ubuntu &quot;System Restore&quot;?"
date: 2009-05-04
forum: New to Ubuntu
---

### Post by Vonnick on 2009-05-04
SOLVED

Hello,

I've really been enjoying Ubuntu and have been having a blast screwing with it. However, I've borked it and reinstalled about 12 (the best way to learn Linux is to mess with it until it won't boot. :P) times within the last five days. It's really getting annoying to do full reinstalls, and I wanted to know if there was any built-in application that could back up the entire system on disk, then restore it. I would do one more reinstall and make the image, never doing a wipe + reinstall again. Thanks in advance.

---

### Post by Didius Falco on 2009-05-04
There is nothing built-in, but you can download and burn the System Rescue CD, which contains Partimage.

[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)


Here is a good tutorial on using it:

[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage) 

BTW, I use the same method of learning. I currently have two installs of 8.10 (one for use, one for creating my own Live CD; the Live CD one will soon be moved to 9.04, for EXT4 support because the Live CD I'm making will be my own Ubuntu Rescue Disk. The 8.10 one works well, but EXT4 is the wave of the future so I figured I should update it to support that) an install of 9.04 32 Bit, and install of 9.04 64 Bit on an EXT4 partition and a 9.04 32 Bit install that I'll soon be upgrading to the Karmic pre-alpha.

I have them all backed up, and with so many installs, if I screw one up, I can always get into another one. That's not even counting the various Live and Rescue CDs.... :biggrin:

---

### Post by Vonnick on 2009-05-04
Well, that seems the thing for me. Does it back up the swap partition, too? Or will I need to recreate it?

---

### Post by Didius Falco on 2009-05-04
No it won't back up the Swap partition, but then you won't need to. Ubuntu will just see it and use it. though with 4 Gigs of ram, mine has been a dead-zone from day one - Never been used...

---

### Post by Vonnick on 2009-05-04
Alright, thanks. At least now I'm a master of reinstall. :P

---

### Post by ibuclaw on 2009-05-04
I recommend [Remastersys]("http://www.geekconnection.org/remastersys/remastersystool.html"), it allows you to turn your current installation into a LiveCD/DVD snapshot. So if your installation breaks, you can restore it to that point in time. (**Note: **You need to burn the resultant iso image to disk first)

For keeping your /home files and folders safe after each re-installation, create a [separate /home partition.]("http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/")

Also, the swap partition is "Virtual RAM", so it is volatile, there is no point in even attempting to backup any data (which is erased when you shutdown) which may be kept there.

Regards
Iain

---

### Post by Didius Falco on 2009-05-04
Yes, that's what I'm using to create my Ubuntu Rescue CD's. Quite nice, and fun to mess around with. I have a DVD backup of one of my systems, but my CD/DVD burner is only burning CDs these days...

---

### Post by Vonnick on 2009-05-04
Oh, wait. If I used the highest compression algorithm with Partimage, would a 2GB fresh install fit on a regular CD? My DVD drive doesn't work. :(

---

### Post by Didius Falco on 2009-05-04
> **Vonnick said:**
> Oh, wait. If I used the highest compression algorithm with Partimage, would a 2GB fresh install fit on a regular CD? My DVD drive doesn't work. :(

maybe, but even if it doesn't you can set the maximum image size and span it across several disks.

Here is the documentation from the creators of Partimage.

[]("http://www.partimage.org/Partimage-manual_Usage#What_compression_level_to_use_.3F")[http://www.partimage.org/Partimage-manual_Usage](http://www.partimage.org/Partimage-manual_Usage)

---


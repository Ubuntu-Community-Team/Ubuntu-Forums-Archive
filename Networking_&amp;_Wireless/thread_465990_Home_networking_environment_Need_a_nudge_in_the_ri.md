---
title: "Home networking environment: Need a nudge in the right direction"
date: 2007-06-06
forum: Networking &amp; Wireless
---

### Post by mvsjes2 on 2007-06-06
I have a mythtv set up in my home. I have a backend server in  my utility room that acts as a file server and web site as well. I have a frontend in my living room which also doubles as my personal computer where I do a lot of my daily work.

I was considering making my frontend diskless so that I could remove a fan or two to make it quieter. I'm a bit overwhelmed by all the possibilities for setting this up, and was hoping someone could help get me started.

Should I look at installing a very basic system on a thumb drive for the front end and from there xdmcp onto my fileserver? Should I PXE boot my root filesystem into RAM and network mount my other filesystems like "home"? Should I use freenx for my desktop or use xdmcp? If I share my "home" directory can I login both from my frontend and backend at the same time using the same username?

Once I have a direction I can figure out the technology. I get stuck on the overall design though. A little help would be appreciated?

---

### Post by tgalati4 on 2007-06-06
Spend $300 and get an iTV from Apple.  It's quiet.  Move your noisy desktop machine into a closet and reroute the cables.  With Ubuntu, you can leave it up for months at a time--so you won't need access to the machine often.  This makes closet solutions practical.

The compromises that you will make with your front-end system by thumb-drive booting would probably cost you more than $300 for a dedicated media device.

In other words, since you use the front end system for daily work, you have to account for all of the uses of the machine besides media playback.  

For $150 to $200 you can get a quiet notebook drive (160 GB are the current max available--5400 rpm) and either an IDE or SATA adapter that allows you to install it internally.  This gives  you the space and speed for a complete operating system for your head end.  However, you still have cooling fans in the processor heat sink and power supply to consider.  The longevity of notebook drives is not great--2-3 years max.

Now, if you have a spare machine (i.e. atticware) then you could convert it to a media playback client by adding a decent video card ($150-$200) and RAM (you will need a fair amount--perhaps 1 GB) so you can boot from USB Stick/CD-ROM and run entirely in RAM.  

I've never seen a diskless mythTV setup.  So although it's possible (as most things are in Linux) it may not be practical.  MythTV is fiddly enough to get configured without having to worry about remote booting.

Another possibility.  External USB drives are cheap.  Buy a big one and a long (5 m) USB cable and put the drive in a cabinet.  That moves one noisy component to an isolated space while giving you access to the machine.

I find dedicated devices (like iTV) or a TIVO box make life so much easier than trying to use a PC to perform both.

---

### Post by mvsjes2 on 2007-06-06
Thanks for the suggestion of using an iTV, but I'd rather have a full desktop available in my livingroom. I had the idea that I could somehow retain access to a full desktop and mythfrontend, but run the filesystems off the fileserver, negating the need for hard drives. At this point I'm not sure if what I'm considering even makes sense. I'll keep reading up on this (your other comments included). Thanks again.

---

### Post by tgalati4 on 2007-06-07
Please let the community know what you ended up doing.  We're curious.

---

### Post by mvsjes2 on 2007-06-14
For the curious:

After many hours of reading (I'm fairly new to Linux) I decided to pxe boot my root file system off my fileserver, and share a single common home directory between all my systems, also located on my fileserver. I'm not sure yet what I'll do with my swap partition, but I'm pretty close to being diskless if I can get around a last problem:
[http://ubuntuforums.org/showthread.php?t=473828](http://ubuntuforums.org/showthread.php?t=473828)

This will allow me to use a common /home that I can access from any mythfrontend in the house. I won't need to buy hard drives for each of the front ends since I can simply carve out a new root file system on the fileserver and share the home dir like all the others.

I opted to manually keep the uid's and gid's in sync for anyone that has a home directory, but I may decide to install nis later on.

---


---
title: "Can a single installation of Ubuntu running on multiple computers?"
date: 2010-06-23
forum: New to Ubuntu
---

### Post by Rick 250 on 2010-06-23
I have a extra 2.5" 500GB HDD, and I plan on using it primarily for all my videos/music/pictures.  I would like to put a 20GB partition on it for Ubuntu, while Ubuntu won't be my primary operating system, it would be used for whenever I wanted to transport those files, and so the hard drive would have an operating system to access the files.  So the installation would be on different desktops/laptop of completely different hardware, so my question is:
Will there be big driver issues moving Ubuntu to other computers than the computer it was originally installed on?

And if there would be issues, how would I be able to make it so that when I boot off of this Hard Drive, it would boot up a Ubuntu Live CD instead of an OS?  As I believe that would work if a full installation wouldn't be portable. 

I have plenty of experience with computers, and a bit with Ubuntu and a few other flavors of Linux, I'm just wondering the answers to these questions before I try it out, and what method I should use.

---

### Post by S.R on 2010-06-23
I think so. My situation is kind of like yours. I had an extra 2.5 laying around so I bought an enclosure just planning to back things up. Got to thinking since with my job that keeps me out of country for two weeks at a time it would be nice to have a back up drive that was loaded with an OS. Which is how I stumbled on to Ubuntu and linux in general. I put two partitions on the external. One was NTFS and the other EXT4. Reset the boot order on my laptop bios. With out the external drive hooked up it boots straight to Vista. With the external hooked up it gives me the GRUB menu. No hassles AND redundancy. I can access my music and pics on the NTFS partition while running ubuntu.

I checked to see if the external drive would load on my desktop and it did. Kind of surprised me since 9.4 is on my external drive and I have been running 10.4 on my desktop. When I loaded 10.4 on the desktop I had to do an alternate install because it would not auto configure the dual ASUS 5770's I have in it. So far it has worked out pretty well.

Hope that helps you out some.

---

### Post by Rick 250 on 2010-06-23
Thanks, that's pretty much what I wanted to know, it's good to know the it'll work on different hardware, I wasn't sure if the installation would only install the drivers it needed for the hardware on the installation computer.

---

### Post by marin123 on 2010-06-23
can you make an USB startup disk in ubuntu and make the rest of the disk as storage space... then you could boot live cd everytime you connect the disk to a computer...

---

### Post by C.S.Cameron on 2010-06-23
I do full install to USB flash drives and they work on any computer that can boot USB.
You should be OK as long as you do not install proprietary drivers.

If you go the persistent image install route you might find the installer objecting to HDD. If so you could use the Grub2 boot iso method with a casper-rw / home-rw persistence partition.

Or you could use usb-creator to install to thumb drive and then clone this install to the HDD using dd.

---


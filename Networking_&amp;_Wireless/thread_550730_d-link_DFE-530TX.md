---
title: "d-link DFE-530TX"
date: 2007-09-14
forum: Networking &amp; Wireless
---

### Post by LAdakota on 2007-09-14
Hello All,
This is my absolute first post.  I only installed Ubuntu yesterday!  Here's where I need help.  I am trying to install drivers for the d-link DFE-530TX.  Linux drivers in the form of  a ".tar.gz" file are included on the CD.  The install directions tell me to to a make a temp directory and switch to it, which I did.  Then it tells me to copy the file to the temp directory.  I need to mention that I used my Windows computer to copy the .tar.gz file to a floppy.  So I am trying to copy the file from my floppy drive. This is where I am having difficulty.  First it says use mtools, which apparently I don't have.  Then it says if you don't have mtools to use:
mount -t msdos /dev/fd0 /mnt
When I put that command in the terminal window I get:
only root can do that
So my question is where do I go from here?  I don't know what root is, where to find it, how to get to it, anything.  I looked at the other posts dealing with my particular adapter, but no one seemed to have the same problem I am having.  Thanks.  BTW I have version 7.04 which is feisty fawn (I think)

---

### Post by jirah on 2007-09-14
It is my experience with this card that Ubuntu has always detected and initiated it without the use of any external drivers. I currently use this card on my Ubuntu64 machine running Fiesty. If you are having trouble with the card not being recognized or initiated by Fiesty and you still wish to install the DLink provided drivers, change your mount command from this
mount -t msdos /dev/fd0 /mnt, to this
*sudo mount -t msdos /dev/fd0 /mnt* , you will then be prompted for the password that you set up during install to allow you 'root' access. Any time you wish to attempt any 'administrative' tasks on your Ubuntu install you will be prompted for your 'root' password. Root, put into Windows terms is the Administrator of the machine.

---

### Post by LAdakota on 2007-09-14
Thanks, going to give that a try right now.  I'll let you know how it works and if I still have problems.  Thanks again.

---

### Post by cwayacita on 2008-06-05
hello i have a problem i have tried to install driver for dfe-530 tx on ubuntu 2.6.22-14 and it is not a version that is accepted by the driver so how can i do i have tried to compile the makefile but he doesnt want
Maybe there are some new driver but i dont find them
Thank you for yours responses

---


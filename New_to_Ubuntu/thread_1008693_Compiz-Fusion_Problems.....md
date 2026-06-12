---
title: "Compiz-Fusion Problems...."
date: 2008-12-11
forum: New to Ubuntu
---

### Post by 11010110 on 2008-12-11
Hey guys,

I am an absolute newbie so please pardon if im a lil slow on the uptake lol. Im running ibex (installed 10 min ago lol)

When i typed in cpmiz-manager into the terminal i got this...

Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (2048 ): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

now i assume this means that i lack the necessary drivers or hardware to run it... i doubt its the hardware because I posted a topic a few says ago and someone with the same hardware as me was running it cube and all just fine... 

Im running a toshiba laptop with an intel dual core 1.6 1.7gh processor 2gig of ram and the "intel chipset" for a graphics card. intel should be suppprted so i have no idea where to go from here lol. 

Lovin Ubuntu cant wait to love it more!

Thanks in advance everyone!

if need be i can fall back to vista (im using wubi) if i need to find more info as i have no clue how thru ubuntu yet lol


oh also... since i typed that in i have the whole wiggly window thing going on but no other effects or ways to edit them as the manager wont open.

---

### Post by 11010110 on 2008-12-11
I just installed all of the system updates and its still doing it...


Thanks in advance everyone

---

### Post by tuxxy on 2008-12-11
Have you installed the provided drivers for your video card?

---

### Post by 11010110 on 2008-12-11
how do you do that? I updated the system but i didnt do any special installing

---

### Post by Hospadar on 2008-12-11
Go to System->Advanced->Hardware drivers and see if there is an intel driver for you to enable.  After that, try enabling compiz.

---

### Post by 11010110 on 2008-12-11
no there are no proprietary drivers available it says... any other ideas?

---

### Post by 11010110 on 2008-12-11
good news all is well it decided to kick in for me after a restart. no clue why but i wont complain!

Thanks for your help everyone!

---


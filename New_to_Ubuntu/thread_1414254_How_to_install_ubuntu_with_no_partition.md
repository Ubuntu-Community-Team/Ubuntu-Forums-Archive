---
title: "How to install ubuntu with no partition"
date: 2010-02-23
forum: New to Ubuntu
---

### Post by chiaboy on 2010-02-23
I'm trying to install via the disc on a IBM Thinkpad that occasionally has start up issues in window. I basically get the blue screen of death after it tries to cycle through the start menus.

So install ubuntu, it's mostly loaded, it can connect to internet etc, but on the desktop is the "Install" command that walks you through final set up (e.g. set your date, user name etc.) when it gets to the partition part (Screen 4 of 7) it's blank (probably since it can't identify the Windows install because of whatever problem it has) and I can't proceed past that step.

Is there a terminal command I can use instead or some sort of process I can use to finish installing/configuring Ubuntu?

---

### Post by undecim on 2010-02-23
It sounds like there is a problem with your hard drive. What kind of information do you get from the BSoD when windows fails to start up?

---

### Post by Cabs21 on 2010-02-23
try ubuntu without doing anything to your system. ie running Ubuntu from a Live CD and go to the top left of the screen and open

SYSTEM>ADMINISTRATION>gParted.

Then see if gParted can find your harddrive and if you can format it to ext3 (or ext4 if you know what your doing) and then when you are finished reboot to the first Ubuntu menu and chose install.  This will take you through the same steps as before but hopefully your drive will be reformatted and easily recognized.  Also if your computer is having hardware issues (block errors, hard drive failures, etc.) It will take much longer for step for to finish.  This happened to me I got stuck at step four for quite a while, just walked away and let it take its time until i returned after dinner and it was ready to format and install.

---


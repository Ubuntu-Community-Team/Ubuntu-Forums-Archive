---
title: "Black Screen After Install"
date: 2010-11-28
forum: New to Ubuntu
---

### Post by Genesis213 on 2010-11-28
For a frame of reference for where I'm coming from I am a trying Ubuntu and have very limited experience with Linux in general. I picked Ubuntu specically because it was recomended to me as a good place to start and learn. However I've run into the following problem. 
 
I had trouble installing Ubuntu initially and kept being met by a black/blank screen with no keystrokes resulting in any sort of response and no HDD activity. 
 
Eventually using the alternate install CD I managed to get through the installation. Though it still required some playing around to not get the black/blank screen.
 
Now everything is installed and when I reboot I get to Gnome. However if I pick Ubunto or Ubunto recovery mode I am again met by the mysterious black/blank screen.
 
I have a strong suspicion that this is a result of my graphics driver, but don't know enough about gnome or Ubuntu to get around this issue. My system is:
 
Mobo: Asus P5W DH Deluxe
Proc: Inter Core2 Quad Q8600
RAM: 2 x 1GB
Gfx: ATI Radeon HD3850 256MB
HDD: 2x75GB Raptors in Raid 1 (Windows 7 and Ubuntu installed on these drives)
3x1.5 TB WD Black
 
I think that I need to change the command line in Gnome but I haven't a clue what to change. Tried "vga=771" and "nomodeset=true". Any suggestions for what I should do?

---

### Post by sanderd17 on 2010-11-28
I think you mean GRUB instead of Gnome. It's the screen where you can choose the OS right? Gnome is the (default) desktop manager of ubuntu, so you can only get into gnome when ubuntu is completely loaded.

---

### Post by Genesis213 on 2010-11-28
Hi, yes I meant GRUB. I've been floating around forums for hours trying to figure it out and all the terms are quite foreign to me. 
 
I managed to solve the problem. I edited the command line removing "splash quiet" with "nomodeset" and it worked.

---

### Post by sikander3786 on 2010-11-28
> **Genesis213 said:**
> Hi, yes I meant GRUB. I've been floating around forums for hours trying to figure it out and all the terms are quite foreign to me. 
 
I managed to solve the problem. I edited the command line removing "splash quiet" with "nomodeset" and it worked.
You need to install the proprietary drivers for your graphics card from under System > Administration > Additional Driver in order to get rid of that problem permanently.

---

### Post by sanderd17 on 2010-11-28
Ok, great you solved it.

did you use the post of my signature to solve it? or did you find another post?

---

### Post by Genesis213 on 2010-11-28
sanderd17

Found another post.

sikander3786

Updating drivers now :)

---

### Post by muss02 on 2010-11-29
Could you please post a link to the solution or a writeup of how you fixed it.  I am having the same issue.  Thanks.

---

### Post by sanderd17 on 2010-11-29
look in the link in my signature, about the boot options. There, temporarily set the "nomodeset" option. When your ubuntu starts, install the graphical drivers and you can boot ubuntu without setting nomodeset.

That is if you have the same problem.

---

### Post by muss02 on 2010-11-29
It works now.  Thanks for the link!

---


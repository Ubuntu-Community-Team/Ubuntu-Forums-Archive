---
title: "Nvidia-173 error when installing pkgs"
date: 2010-05-11
forum: New to Ubuntu
---

### Post by tenfortytwo on 2010-05-11
hey guys I've been messing with Ubuntu 9.10 for a few days and have noticed this problem.

Setting up nvidia-173 (173.14.22-0ubuntu11) ... 
dpkg: error processing nvidia-173 (--configure): 
 subprocess installed post-installation script returned error exit status 1 
dpkg: dependency problems prevent configuration of nvidia-glx-173: 
 nvidia-glx-173 depends on nvidia-173; however: 
  Package nvidia-173 is not configured yet. 
dpkg: error processing nvidia-glx-173 (--configure): 
 dependency problems - leaving unconfigured

I get this error everytime i try to install a pkg that uses any sort of graphics.  I have looked through the forums and have not found anything that can help my situation.  If anyone knows of anything that can help it would be great I'm trying to get wine to install so i can play eve since they droped there linux version.  I'm pretty computer literate but new to linux.

---

### Post by -humanaut- on 2010-05-11
Are you sure you need the Nvidia 173 driver vs the Current driver? What type of card do you have?

---

### Post by tenfortytwo on 2010-05-11
8600 gts i thought that was newest driver but like i said i'm new to the whole linux thing so i may have gotten the wrong

---

### Post by -humanaut- on 2010-05-11
Are you installing with GTK-Jockey? It should listen the "Current" Recommend driver I think you should be using the 19* driver not the 173 driver thats a fairly old driver now.

---

### Post by tenfortytwo on 2010-05-12
jockey says i have current and it is activated but not currently being used what does that mean

---

### Post by tenfortytwo on 2010-05-12
i think i might have fixed it.  first i disabled the old driver through jockey then i did a
sudo apt-get install -f
then a 
sudo apt-get autoremove
then
sudo apt-get clean
and i think that cleared out the problem.  I had some how gotten both the current driver and the old one.  Think its fixed now.  but the new driver does still say its activated but not currently being used.  what does that mean

oh yeah i also did 
sudo apt-get remove nvidia-173

---

### Post by -humanaut- on 2010-05-12
It was probably the Nvidia173 Driver causing the problems glad its working now.

---


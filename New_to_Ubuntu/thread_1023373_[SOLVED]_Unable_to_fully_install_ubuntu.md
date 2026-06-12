---
title: "[SOLVED] Unable to fully install ubuntu"
date: 2008-12-27
forum: New to Ubuntu
---

### Post by wenn_die on 2008-12-27
I have been interested in using linux for a while and here I am. I have an XP home, Intel dual core, 2X HDD system
The first HDD is windows only 350GB.
The second HDD which is blank I partitioned into 3 partitions with msoft disk manager, the ran Parted Magic where I made the first partition ext3 10GB, the second partition swap/linux 35GB and wish to keep the remaining extended partition for windows backup. I got confused about where these partitions should be mounted.
I then tried to install ubuntu 8.10 form a live cd which I had checked for errors and was ok.
The first menu loads, I choose english then the first option of demo ubuntu with later install. It starts to install, the slide progress bar gets to about 95%, then the screen goes black and nothing happens. Cant use my mouse, nothing, though the cd spins for a few minutes and the screen occassionally flickers. I tried this several times, each with the same result, and eventually have to reset.
Any help much appreciated.:confused:

---

### Post by nhasian on 2008-12-27
sounds like you need to try to install ubuntu from the alternateCD:

[http://www.ubuntu.com/getubuntu/downloadmirrors#alternate](http://www.ubuntu.com/getubuntu/downloadmirrors#alternate)

did you say you have a 35GB swap partition? unless your doing some massive video editing thats way overkill.  just do 1.5-2.0 times your system ram.

---

### Post by hyper_ch on 2008-12-28
in addition: how did you create those three partitions on the second drive?

---

### Post by wenn_die on 2008-12-28
start->run->compmgmt.msc->disk management
then used parted magic to convert the formats

---

### Post by hyper_ch on 2008-12-28
I rather meant what kind of partitions and how big did you make them...

---

### Post by Michael.Godawski on 2008-12-28
here is a good guide on planning partitions by aysiu:


[LIST]
[*][http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[/LIST]

Also if you want to dual boot have a look at these guides:


[LIST]
[*][http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)
[/LIST]
Just select the windows version you have and the order of the installation.

PS: Welcome to the Ubuntu Experience. :)

---

### Post by wenn_die on 2008-12-29
10Gb ext3 home, 4 GB swap (I have 2GB ram) and 30 GB for any ohter linux stuff. I might add, I now have ubuntu installed, but it wont load. I get to the progress bar which almost finishes, than a black screen. At this point I have to reset.

---


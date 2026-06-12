---
title: "Clean install of Ubuntu 8.10"
date: 2009-01-14
forum: New to Ubuntu
---

### Post by michael.693 on 2009-01-14
Hey, 
i have tried to clean install ubuntu 8.10 on my ubuntu 8.04, 
i installed it, put the hard drive back into its original computer (can clean install on it)but it didnt work. now when i try and install it it wants me to choose a partition from a list, but there isnt anything there :confused: 
How would i install it now???


Thanks

---

### Post by utnubuuser on 2009-01-15
Hi -- your posting is a little confusing.  Waht are you trying to do?  Install 8.10 while the harddrive is in one computer then transfer the harddisk to another computer?

Can you access your partitions with a liveCD?  Gparted is on the liveCD, how about deleting all the old partitions, then a fresh install.

---

### Post by michael.693 on 2009-01-15
> **utnubuuser said:**
> Hi -- your posting is a little confusing.  Waht are you trying to do?  Install 8.10 while the harddrive is in one computer then transfer the harddisk to another computer?

Can you access your partitions with a liveCD?  Gparted is on the liveCD, how about deleting all the old partitions, then a fresh install.


Yeah thats what im trying to do..
when im trying to install it (step 4 of 7) it says i have to select a partition but there is none there...
"Gparted is on the liveCD, how about deleting all the old partitions, then a fresh install" how would i do this??
Thanks!!

---

### Post by Vantrax on 2009-01-15
Boot into the live CD

hit Alt F2 and type gksudo gparted

remove all the linux partitions by right clicking and selecting delete.

You will need to turn the swap file off most likely to be able to edit the extended/swap. 

Good luck, let us know how you go.

---

### Post by michael.693 on 2009-01-15
hey,
When i do the alt F2, there are no partitions there, i tried to install it again but the error message came up - 
it says no root file system is defined pleace correct this from partition menu... 
Thanks, 
Michael.

---

### Post by michael.693 on 2009-01-15
> **Vantrax said:**
> 

You will need to turn the swap file off most likely to be able to edit the extended/swap. 

Good luck, let us know how you go.

How do i do this?
(sorry im a noob when it comes to ubuntu...)

---

### Post by michael.693 on 2009-01-15
I have found  post with the same problem, here it is - 
[http://ubuntuforums.org/showthread.php?t=1039823&highlight=swap+file](http://ubuntuforums.org/showthread.php?t=1039823&highlight=swap+file)

---

### Post by michael.693 on 2009-01-15
Still dont know what to do :confused:

---

### Post by Vantrax on 2009-01-16
Assuming you wanted the whole drive, let the setup partition the disk for you using a guided partition (should be the second radio button).

---


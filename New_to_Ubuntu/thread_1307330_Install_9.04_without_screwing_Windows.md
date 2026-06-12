---
title: "Install 9.04 without screwing Windows?"
date: 2009-10-31
forum: New to Ubuntu
---

### Post by CheshireMac on 2009-10-31
Hey folks. I'm really rusty and I'm also not well versed in harddrive issues. 
I've finally convinced my wife to come to the greener pasture, but she doesn't want to completely remove Windows. I was about to install 9.04 on her Inspiron 1420 when I noticed that her C:\ is the only partition with enough free space to install on. 
What I also discovered is that we don't have a recovery cd for Vista. I could download and burn one, but I'm hoping that I don't have to. Is there any way I can turn over 7 of the 11 gb to Ubuntu until we can back-up the rest of her files? Without harming Vista, that is?
Alternatively, I have a harddrive with Ubuntu already installed. Is it an easy switch to remove her current harddrive for mine and adjust the sources? If not, could someone enlighten me as to what I need to change to make it work?
I appreciate any help you guys can offer. Thanks.

---

### Post by sliketymo on 2009-10-31
> **CheshireMac said:**
> Hey folks. I'm really rusty and I'm also not well versed in harddrive issues. 
I've finally convinced my wife to come to the greener pasture, but she doesn't want to completely remove Windows. I was about to install 9.04 on her Inspiron 1420 when I noticed that her C:\ is the only partition with enough free space to install on. 
What I also discovered is that we don't have a recovery cd for Vista. I could download and burn one, but I'm hoping that I don't have to. Is there any way I can turn over 7 of the 11 gb to Ubuntu until we can back-up the rest of her files? Without harming Vista, that is?
Alternatively, I have a harddrive with Ubuntu already installed. Is it an easy switch to remove her current harddrive for mine and adjust the sources? If not, could someone enlighten me as to what I need to change to make it work?
I appreciate any help you guys can offer. Thanks.


What is the Total size of the C:\ , and how much of it is actually used? Or are you saying you only have 7, or 11 gb free on C:\  ?

---

### Post by PaulInBHC on 2009-10-31
[https://help.ubuntu.com/8.04/switching/installing-partitioning.html](https://help.ubuntu.com/8.04/switching/installing-partitioning.html)

I used the above to dual install 9.04 with XP. I have one HDD with C: 57g and D: at 17g. I did the manual partition, changed the C: to about 30g and used the new space for 2g swap and the rest for /
Worked great.

Edit
The pocket guide has some admin info for vista users.
I did create a /home for 9.04 and later installed 9.10 by creating some space from the above. I used the same swap partition and did not create a /home for 9.10. I like 9.10 better and will remove 9.04 soon. You might be better to start with 9.04 and see how it goes.

---

### Post by Warpnow on 2009-10-31
Just put the CD in while windows is running and it will let you install a dual boot using wubi which uses a virtual partition inside of windows. If she decided to remove ubuntu it can be removed from the add/remove progeams in the control panel.

---

### Post by CheshireMac on 2009-10-31
When I looked at Wubi before, it gave me partition options and all that convenient good stuff. Now, it only requests that I boot from the liveCD or go to the homepage. Either way, I can't install side-by-side through Vista anymore. I don't know why I can't get to the partitioning section in Wubi, and I don't know if I can get this to work without screwing her Vista portion of the partition.

---


---
title: "Help Installing PSC 2710 Scanner..."
date: 2005-08-23
forum: Networking &amp; Wireless
---

### Post by jroskos on 2005-08-23
First of all I am new to Linux..... (Yes, Newbie ALERT!)


Okay, I have a HP PSC 2710 All-In-One, I am running it across the network with wireless. So far I have been able to get the printer to work by setting it up with JetDirect, but I have no clue of how to install a scanner in Linux?

Please Help...


Rosko
Windows Guru - Trying To Convert

---

### Post by s_p_a_r_k_y on 2005-08-24
ummm scanning is done on most linux setups I have seen via sane. I setup my PSC 1315 with sane with no problem, but it was over USB. I didn't know if how the PSC does its scanning over the network. Does it try to FTP the scanned image? Does it try to send it to a windows share? ALl these could be setup easily.

---

### Post by matthew on 2005-08-24
These might help, neither one is the same model as yours, but both threads involve getting the printer and the scanner working on HP PSC's

[http://www.ubuntuforums.org/showthread.php?t=49288](http://www.ubuntuforums.org/showthread.php?t=49288)

[http://www.ubuntuforums.org/showthread.php?t=33424](http://www.ubuntuforums.org/showthread.php?t=33424)

---

### Post by jroskos on 2005-08-24
sweet.... everything is working

I had tried going to that hp printing project site, was to complicated to do, when all i had to do was gointo root type "apt-get install hpoj" and then run the setup for it, but instead of using usb or parallel, it will let you put in a ip address to the PSC.

Thanks again guys....

---


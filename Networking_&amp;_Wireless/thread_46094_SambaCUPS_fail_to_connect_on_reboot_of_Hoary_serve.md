---
title: "Samba/CUPS fail to connect on reboot of Hoary server"
date: 2005-07-03
forum: Networking &amp; Wireless
---

### Post by Imerio on 2005-07-03
After some hours installing Hoary, a RAID system, Samba and some tinkering on some revitalised h/w, I managed to get printing working from remote Windoze clients to my freshly commissioned server. I concluded my session with a reboot of the box and found that the Windoze clients could not see the Samba printer shares. Further investigation revealed the following:

CUPS and Samba processes are up and running:

 cupsys    6089  0.0  0.5   5852  2888 ?        Ss   13:09   0:00 /usr/sbin/cupsd -F
 root      7324  0.0  0.5   7900  2788 ?        Ss   13:09   0:00 /usr/sbin/smbd -D
 root      7345  0.0  0.5   7900  2768 ?        S    13:09   0:00 /usr/sbin/smbd -D
 nobody    8363  0.0  0.5   8164  3028 ?        S    13:25   0:00 /usr/sbin/smbd -D
 root      7322  0.0  0.3   5428  1864 ?        Ss   13:09   0:00 /usr/sbin/nmbd -D

Samba log:

 [2005/07/03 13:09:53, 0] printing/print_cups.c:cups_cache_reload(85)
   Unable to connect to CUPS server localhost - Connection refused

Nothing of note in CUPS error log.

I do not believe I have anything particularly wrong with the config files since:

 /etc/init.d/samba restart

fixes the problem! Could there be some kind of start-up race condition between CUPS and Samba? Samba certainly appears to start after CUPS but before CUPS completes initialising. CUPS is S19 at runlevel 3 and Samba is S20 on same runlevel. I also do not understand why there is a nobody owned smbd service started? I wonder if this might be the problem as on a samba restart I am only left with two smbd services - both root owned.

I would welcome ANY ideas on this as I'm at a total loss...

By the way, thank you all on these forums and howtos etc. - you've all made Ubuntu one great Linux disty.

---

### Post by Peturrr on 2006-02-16
I am having the same problem. I changed Samba to be S99, but this didn't solved the problem.
Did you found a solution? Anybody else an idea?

---

### Post by Imerio on 2006-02-19
Yes, I solved my problem by changing run priority to S50/K50 for samba at ALL runlevels. Clearly the K50 shouldn't matter...

I am suprised so few of us have encountered this.

---

### Post by Imerio on 2006-02-19
Can't think why S99 may not be working for you. 
 - ensure samba at S99 at all appropriate run-levels
 - check /var/log/samba/log.smbd - should be nice and clean

Does "sudo /etc/init.d/samba restart" fix samba based printing for you?

---


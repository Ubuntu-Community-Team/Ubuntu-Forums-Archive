---
title: "Compiz fusion will not start during startup"
date: 2009-05-27
forum: New to Ubuntu
---

### Post by 11010110 on 2009-05-27
Hi everyone,

I just finished getting Jaunty all set up and for some reason compiz fusion will not startup when i start the system up. I tried following some other posts ideas but i guess im doing something wrong. as a consequence AWN wont start until i start up ocmpiz manually and reload the window manager. its a hassle and id love to find a way to fix this. i never had this problem with intrepid. 

Thanks in advance everyone!

---

### Post by 11010110 on 2009-05-27
Hey i managed to get it working after some trial and error. the command for the compiz fusion icon ended with --no-start so i made a startup item without the --no-start and it works just fine.

---

### Post by Didius Falco on 2009-05-27
+1 for solving it yourself **and** for posting how you solved it. You'll make  life a little easier for someone else!!

Regards,

Didius

---

### Post by Flash858 on 2009-06-06
Hey -> This helped me indirectly, as I had already had the fusion-icon in my startup apps with no parameters, but still had to go through the dreaded "reload window manager" hassle to get compiz to start in 9.04.

I simply added "--start" to the end of the command, and VOILA!

I think this is the magic bullet, as it is the 2nd or 3rd time I have had the same issue, and there are MANY threads about this in the forum.

This needs to go in the Wiki...


:D

---

### Post by ken_do_san on 2009-06-06
There is a blacklist of intel video chips for 9.04, it is not your install or your video chip, there is a problem in 9.04 concerning compositing.  It will be eventually fixed and an update made available.  There is a work around for deactivating the blacklist (search google) in 9.04 if you want to have compositing working.

---


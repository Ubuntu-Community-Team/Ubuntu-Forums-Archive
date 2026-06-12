---
title: "Desktop effects no longer working"
date: 2009-05-05
forum: New to Ubuntu
---

### Post by db4sn3r on 2009-05-05
Hi all,

Yesterday, I had all of these neat compiz effects set up and they were working very nicely.  Then I plugged in my external monitor and they no longer worked, thinking it was just the monitor for some reason, I thought nothing of it.   Today, I turned my laptop on, without the external monitor, and the effects no longer work.  I went into appearance and now none of the effects work, it says that it can't find the drivers, even though it was just working yesterday very nicely.  Could someone tell me what happened that caused this and how to fix it?  I don't believe my computer made any updates between now and then, unless they were in the backround and didn't notify me or something.  I am on a samsung nc10 netbook.

Thanks,

db4sn3r

---

### Post by db4sn3r on 2009-05-05
could someone please help!?

---

### Post by Richard9795 on 2009-05-30
can you post your xorg.conf please? the same happened to me, but i fixed it by editing something in there...

---

### Post by adaw on 2009-06-09
> **db4sn3r said:**
> could someone please help!?

db4sn3r, try reconfigure your Xorg server with:
```
sudo dpkg-reconfigure xserver-xorg 
```

I had the exact same problem, and it worked for me.
I hope this will help.

regards

---

### Post by zeroseven0183 on 2009-06-09
Have you tried selecting again either the Normal or Extra options in the Visual Effects?

---

### Post by theozzlives on 2009-06-09
Do you have an Intel chipset?

---


---
title: "I/O errors on reboot"
date: 2009-10-29
forum: New to Ubuntu
---

### Post by Papajerry on 2009-10-29
Please help.  I did a WUBI install of 9.04 a couple of days ago i did the install of the pre release of 9.10.  now I get "Buffer i/o error on device loop0 logical block xxxxxx' at restart, and every thing stops till I turn machine (compac presario f700 amd 64 ect.) off.  what should I do to fix this?

---

### Post by grar05 on 2009-10-31
The same happens to me. Nobody knows anything to solve this, or if this would have any solution without uninstalling?

---

### Post by jjcv on 2009-10-31
> **Papajerry said:**
> Please help.  I did a WUBI install of 9.04 a couple of days ago i did the install of the pre release of 9.10.  now I get "Buffer i/o error on device loop0 logical block xxxxxx' at restart, and every thing stops till I turn machine (compac presario f700 amd 64 ect.) off.  what should I do to fix this?

Doesn't look good.

I suspect there is a problem with your hard drive.   Usually when I see these sort of errors I go anb buy a new hard drive.

---

### Post by grar05 on 2009-10-31
> **jjcv said:**
> Doesn't look good.

I suspect there is a problem with your hard drive.   Usually when I see these sort of errors I go anb buy a new hard drive.

I don't think so. It seems to happen to all of us that are installed Wubi Jaunty and then upgraded to Karmic. Windows work as usual.

---

### Post by poo706 on 2009-11-01
This is getting talked about on all of these other threads:
[http://ubuntuforums.org/showthread.php?t=1306005](http://ubuntuforums.org/showthread.php?t=1306005)
[http://swiss.ubuntuforums.org/showthread.php?p=8206421](http://swiss.ubuntuforums.org/showthread.php?p=8206421)
[http://georgia.ubuntuforums.org/showthread.php?p=8206461](http://georgia.ubuntuforums.org/showthread.php?p=8206461)
[http://ubuntu-ky.ubuntuforums.org/showthread.php?p=8212799](http://ubuntu-ky.ubuntuforums.org/showthread.php?p=8212799)

The most promising thing I've seen is from the last one, and it's just a workaround at best.  The advice from post #6 (from P4man) halfway worked for me.  When I get the buffer errors, I can get it to shutdown without holding the power button, but I couldn't get it to reboot via that method.  In doing searches for this nearly every day for the last few weeks, it looks like it's a problem that's hit Wubi before.  And there's a lot of people talking about it, so I'm sure a fix will be released soon.

[poo]

---

### Post by garvinrick4 on 2009-11-01
The only thing I have had to do was  fsck  before restart.

Wait the 60 seconds on restart.

1/2 the time it restarts fine.

The other I have to I alt/ctrl/delete  says there is an ext3 error.

ctrl/sys rq/b    to restart.

   

until they find WUBI fix.  

Not any sort of fix just works for me for time being.

---

### Post by soma123 on 2009-11-02
Hi,
       I am also having the same problem since I have upgraded from wubi 9.04.
Will this be fixed soon??

---

### Post by soma123 on 2009-11-04
Hi,
        Comment # 19 in
[https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/468589](https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/468589)

seems to fix this problem.

Cheers!!

---

### Post by ukripper on 2009-11-04
Best solution is to dual boot in this situation rather running via Wubi.

---

### Post by ibizatunes on 2009-11-04
I had a similar issue, check that your BOIS thinks it has a floppy that isnt there
My BIOS had the same error, in my BIOS, it thinks it has a floppy attach so i turned it off in the BIOS and and it stopped the problem

Dont know if that will worth but worth a quick look

---


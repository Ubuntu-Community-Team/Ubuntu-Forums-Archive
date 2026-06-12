---
title: "MAJOR hard drive issue"
date: 2011-03-03
forum: New to Ubuntu
---

### Post by kingdraco41 on 2011-03-03
I got ubu 10.04 a few months ago for my laptop, and I have been able to fix any small errors I've encountered since then, but yesterday, when I tried to boot my computer, it got stuck on init ("initramfs") and stated: 
```

mount: mounting /dev on /root/dev failed: no such file or directory
mount: mounting /sys on /root/sys failed: no such file or directory
mount: mounting /proc on /root/proc failed: no such file or directory

```
and that it could not find init in /sbin - or something similar. I tried an older kernel, and I got the same result. 
I tried looking at /etc/fstab in init, but it couldn't find it. I also tried booting a live cd, but that failed as well; the startup would reach a point and then stop. It never would give me an error message, but it would not progress.

I tried mounting the file system with an external hard drive hooked up to my laptop, but (though linux worked and works fine) it stated that it was attempting to mount, but never (after six hours) would do so. It never gave me an error message, but I just gave up on it.

I am just completely at a loss as to what is going on and how to fix it. The only possibly detrimental thing I can think of would be using a cold shutdown because my soft shutdown did not seem to be working (it took forever without giving me an error message - what a shocker!) Any insight and advice would be a godsend!

---

### Post by Terry of Astoria on 2011-03-03
Most likely your hard drive was not unmounted properly. It might be failing (or it might not..) I'm not an expert. I hope someone smarter comes to your aid. Years ago the ratio of geeks to noobs here was a lot better . . .I guess Ubuntu is becoming a lot more popular!
Here is a link to an archived forum thread that might help shed some light on the issue:
[http://ubuntuforums.org/archive/index.php/t-1244466.html](http://ubuntuforums.org/archive/index.php/t-1244466.html)
 
  You should be careful, maybe get some good advice before hosing it further by mistake, though . . 

In general terms, I suggest booting up a Live CD or USB stick, and running fsck on your hard drive to try to repair the filesystem.

If you find that fsck can't help then try testdisk. I have recovered a "hosed" drive before using testdisk.
   Do google your error messages to try to find clues . . .
   By the way, if my machine ever hangs, I can usually hit <ctrl-alt-f4> to switch to another console, log in , and then ```
sudo halt
```
or even ```
sudo killall (name of offending program)
```

---

### Post by kingdraco41 on 2011-03-04
Okay, I was able to solve it. I managed to boot a Knoppix 6.4.4 live cd and run fsck on my /dev/sda1 drive. It's all working uber now.

---

### Post by kroq-gar78 on 2011-03-04
If it's all solved, please mark this thread as "Solved" by selected the "Thread tools" menu near the top of the page, and then "Mark this thread as solved".

---


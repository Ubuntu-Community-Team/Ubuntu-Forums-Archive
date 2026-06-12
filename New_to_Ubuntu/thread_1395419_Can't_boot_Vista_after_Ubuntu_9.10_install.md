---
title: "Can't boot Vista after Ubuntu 9.10 install"
date: 2010-01-31
forum: New to Ubuntu
---

### Post by lesPaul456 on 2010-01-31
Hello,

I just installed Ubuntu 9.10. Everything works fine, except for Vista. When I first tried to boot Vista from the GRUB2 menu, the computer simply restarted. After that I tried again. This time I got a screen asking whether I wanted to run the startup repair, or start normally. I selected startup repair. This had the same result: the computer just restarted.

I saw some older posts about the problem, but they were using a different version of GRUB that used a menu.lst file.

If it helps, I will walk through how I installed Ubuntu...

First, I download the iso and burned it to a CD. I then freed-up some space on my "C:\" drive (about 15 GB). I rebooted, and ran the installer. I used the installer to create a new partition from the free space I just made. Everything installed fine. 

After exploring my new Ubuntu install, I restarted and attempted to boot Vista, and that's when I started having problems.

I'm sure I can repair the Windows MBR. If I do, though, how can I boot Ubuntu? I'm a little worried right now (this is the first time I've done this). Hopefully someone can give me some suggestions.

Thanks!

---

### Post by lesPaul456 on 2010-01-31
Okay. I repaired the Windows MBR and can now boot Vista...but I have no idea how to boot Ubuntu!

Any ideas? Can I do this with EasyBCD?

Thanks!

---

### Post by drs305 on 2010-01-31
Check this link to see if you can restore Grub 2:
[http://ubuntuforums.org/showthread.php?t=1014708]("http://ubuntuforums.org/showthread.php?t=1014708")

---

### Post by lesPaul456 on 2010-01-31
> **drs305 said:**
> Check this link to see if you can restore Grub 2:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Thanks. I actually solved the problem by installing the newest beta release of EasyBCD (which supports Grub 2). I can now boot Ubuntu and Vista with no problems.

Thanks again for the reply drs305!

---


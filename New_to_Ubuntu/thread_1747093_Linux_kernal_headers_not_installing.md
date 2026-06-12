---
title: "Linux kernal headers not installing"
date: 2011-05-02
forum: New to Ubuntu
---

### Post by kapi on 2011-05-02
Hi there am getting an error message when trying to use the update manager for a particular package.


installArchives() failed: (Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 250904 files and directories currently installed.)
Preparing to replace linux-headers-2.6.35-28-generic 2.6.35-28.49 (using .../linux-headers-2.6.35-28-generic_2.6.35-28.50_i386.deb) ...
Unpacking replacement linux-headers-2.6.35-28-generic ...
dpkg: error processing /var/cache/apt/archives/linux-headers-2.6.35-28-generic_2.6.35-28.50_i386.deb (--unpack):
 failed to stat (dereference) existing symlink `/usr/src/linux-headers-2.6.35-28-generic/include/linux/hw_breakpoint.h': Input/output error
Errors were encountered while processing:
 /var/cache/apt/archives/linux-headers-2.6.35-28-generic_2.6.35-28.50_i386.deb

---

### Post by kapi on 2011-05-02
Hello again, I've had this problem for a week now and find it difficult to comprehend that no one seems to be able to offer a solution. If anyone can help, I'd be extremely grateful.

Thanks

---

### Post by CharlesA on 2011-05-02
Run fsck on the root file system and try again.

```
sudo touch /forcefsck
```

Reboot.

---

### Post by kapi on 2011-05-02
Thanks for the help but no effect after re boot, any other ideas?

---

### Post by New Linux Usr on 2011-05-02
I did a bit of searching, and some people were having trouble with packages in general and to correct their problems, opened a terminal and entered:
[INDENT]sudo dpkg --configure -a
[/INDENT]This then corrected their problems with packages - you may want to give it a try?

Kind regards,

New Linux Usr

---

### Post by kapi on 2011-05-02
will try now, many thanks :-)

---

### Post by kapi on 2011-05-02
No even using update dpkg doesn't work but I'll try again

---

### Post by New Linux Usr on 2011-05-02
In the output you provided, it mentions about a symlink already exists - i did a search and found this, that you may make better heads at it than I will.

[http://www.linuxquestions.org/questions/linux-newbie-8/how-can-i-remove-symbolic-links-436542/](http://www.linuxquestions.org/questions/linux-newbie-8/how-can-i-remove-symbolic-links-436542/)

My thought is that by removing the symlink, and attempt to repeat what you did in the first place, may work?

Kind regards,

New Linux Usr

---

### Post by THE CARTER on 2011-05-02
I had this problem once before.  What I ended up being forced to do was a clean install.  However, if you can back up everything in your home folder, then when you clean install, you can still have all your stuff.  Even better, if you back up all the hidden files (.config, etc.) then you can install your old applications with the same configurations that you had earlier.

---

### Post by kapi on 2011-05-02
Thanks for the input, I'm a bit miffed that that may be the only option, if thats the case I may as well upgrade to 11.04 or what ever the latest is.

Thanks again though for all your help and advice, it's what I really like about Linux - everyone helps each other.

---


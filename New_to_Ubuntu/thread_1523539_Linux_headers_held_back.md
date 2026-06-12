---
title: "Linux headers held back"
date: 2010-07-03
forum: New to Ubuntu
---

### Post by mikodo on 2010-07-03
Hi everyone,

Why are 3 Linux headers being held back. I guessing it has to do with a question I answered regarding the kernel selection when installing Lucid. Here is the end result of my ```
sudo apt-get update && sudo apt-get upgrade:
```


The following packages have been kept back:
  linux-generic linux-headers-generic linux-image-generic
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
mikodo@mikodo-desktop:~$ 

How can I change things, so that I receive the newest headers? Or, is this somthing not that important, as everything is running smoothly, in this, the only OS on my computer?

Thanks

EDIT: Would sudo aptitude dist-upgrade sort it out?

---

### Post by wojox on 2010-07-03
Try this:

```
sudo apt-get upgrade && sudo apt-get upgrade && sudo apt-get dist-upgrade
```

---

### Post by mikodo on 2010-07-03
> **wojox said:**
> Try this:

```
sudo apt-get upgrade && sudo apt-get update && sudo apt-get dist-upgrade
```

Yes that did it!

Thanks,

Mike

---

### Post by noneofthem on 2010-07-08
Hey!

I´ve got the same issue on 10.10 alpha 2 but "sudo apt-get upgrade && sudo apt-get upgrade && sudo apt-get dist-upgrade" didn´t do it for me. Any suggestions? I am lost.

Thanks a lot!

none of them

---

### Post by philinux on 2010-07-08
> **noneofthem said:**
> Hey!

I´ve got the same issue on 10.10 alpha 2 but "sudo apt-get upgrade && sudo apt-get upgrade && sudo apt-get dist-upgrade" didn´t do it for me. Any suggestions? I am lost.

Thanks a lot!

none of them

You dont need the double upgrade by the way this will do "sudo apt-get update && sudo apt-get dist-upgrade"

In the development release using dist-upgrade can remove packages so be very careful.
Instead use this. 
```
sudo aptitude update && sudo aptitude safe-upgrade
```
If any packages are still held back it means all the dependencies are still not available.
 
See this forums stickys. [Maverick]("http://ubuntuforums.org/forumdisplay.php?f=385")
And post in there for 10.10 issues.

---

### Post by noneofthem on 2010-07-09
Thanks a lot! That did it for me! :-)

All the best from Germany!

none of them

---

### Post by mikodo on 2010-07-14
Sorry, I had realized that the command should have been
```
sudo apt-get upgrade && sudo apt-get update && sudo apt-get dist-upgrade
```I should have corrected it, for anyone else to read. Done now.

Good thing though, that it wasn't used in a Alpha/developmental release, as Phil pointed out.

Mike

---


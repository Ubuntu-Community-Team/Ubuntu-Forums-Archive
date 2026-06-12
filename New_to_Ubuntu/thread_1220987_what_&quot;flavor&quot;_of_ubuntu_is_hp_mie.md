---
title: "what &quot;flavor&quot; of ubuntu is hp mie ?"
date: 2009-07-23
forum: New to Ubuntu
---

### Post by jimmystyle on 2009-07-23
Hi all-

Just started playing around with my hp mini and am looking forward to learning a bit from these forums as I become a more adept linux/ubuntu user.
  
quick question, which I couldn't find an answer to with a bit of searching.... what type of ubuntu is hp mie?  is it jaunty, hardy, intrepid?  I'm not sure what exactly these versions indicate...but I ask because I'd like to download some software, and the sites have asked for my version, as well as whehter it is a 32 or 64 bit version, of which I'm also unsure of.

any help would be appreciated.

Thank you.

---

### Post by wojox on 2009-07-23
Version:

```
cat /etc/issue
```

Bit width:

```
sudo lshw >lshw.txt
```

```
head lshw.txt
```

---

### Post by ~sHyLoCk~ on 2009-07-23
```
cat /proc/version

dmesg | head -1

cat /etc/issue



```

---

### Post by Keen101 on 2009-08-27
> root@andrew-umpc:/home/andrew# cat /etc/issue
Ubuntu 8.04.2 \n \l


> root@andrew-umpc:/home/andrew# cat /proc/version
Linux version 2.6.24-22-lpia (buildd@midyim) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Thu Apr 2 02:03:56 UTC 2009

It is LPIA architecture. I dont know much about LPIA, but i think it is neither 32bit or 64bit. Someone correct me if im wrong.

---

### Post by Grenage on 2009-08-27
LPIA is quite similar to i386, but targets the Low-Power Intel Architecture with different compile-time optimizations.

---

### Post by 3rdalbum on 2009-08-27
> **Keen101 said:**
> It is LPIA architecture. I dont know much about LPIA, but i think it is neither 32bit or 64bit.

Every processor has a bit width, and Intel Atom processors are (almost all) 32-bit. LPIA is x86 compatible, with extensions for using low-power features of the chip. However, ordinary i386 Debs won't install due to limitations of Dpkg, but you can manually open up the Deb package and copy the contents to your filesystem.

---

### Post by aysiu on 2009-08-27
Ubuntu 8.04 is Hardy Heron.

Most .deb files will come as i386, though, so you'll have to "convert" them to lpia to install them (they're not really converted--you're really just tricking the package installer into *thinking* they're lpia).

This script will help for that:
[http://ubuntuforums.org/showpost.php?p=6358248&postcount=7](http://ubuntuforums.org/showpost.php?p=6358248&postcount=7)

---

### Post by aysiu on 2009-08-27
Ubuntu 8.04 is Hardy Heron.

Most .deb files will come as i386, though, so you'll have to "convert" them to lpia to install them (they're not really converted--you're really just tricking the package installer into *thinking* they're lpia).

This script will help for that:
[http://ubuntuforums.org/showpost.php?p=6358248&postcount=7](http://ubuntuforums.org/showpost.php?p=6358248&postcount=7)

---

### Post by lifeluvr on 2011-12-28
After spending a week playing with HP's MIE, I'm still loving it! Finally, all of my wireless drivers work! HP MIE (Mobile Internet Experience) is a hardware specific OS, made for HP Mini 1000s (although I've heard rumors of it working for other netbooks). MIE is built with a Ubuntu core (32bit,hardy heron) but, the OS is locked up pretty tight (like an iPhone,before jail breaking). Good luck trying to alter, add to, or tweak MIE.  A dual boot w/ Ubuntu is next on my list. That should solve all wireless driver issues when using Ubuntu. With a 100% linux core! No more "windows wireless drivers"!

---

### Post by benpack101 on 2011-12-28
Thats awesome lifeluvr! Its been a lot of work but the payoff rocks! Enjoy!:guitar:

---

### Post by coffeecat on 2011-12-28
Old thread. Closed.

---


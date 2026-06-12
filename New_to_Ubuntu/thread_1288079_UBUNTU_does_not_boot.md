---
title: "UBUNTU does not boot"
date: 2009-10-10
forum: New to Ubuntu
---

### Post by ifhamr on 2009-10-10
Hello everyone,

Im totally a fresher to ubuntu.

I installed Ubuntu 9.04 into my system yesterday, things were going on good till I had some graphics problem which was sorted out via the forum community (thanks BTW).

I did some updates via the update manager (nearly 200MB of updates.)

last night I shut down my PC and Powered it up on this morning to see UBUNTU does not boot, it halts at GRUB:confused:

GRUB:>

can Someone suggest me what I should do? 

Thanks in advance..

Ifham

---

### Post by Saint_ on 2009-10-11
hm, only thing i can think of is that your boot manager was changed during the update. Though unless you're like dual booting operating systems that shouldn't have really been a problem. put this in your console and post the results on here. 
```
sudo gedit /boot/grub/menu.lst
```

---

### Post by louieb on 2009-10-11
Often overlooked but I consider an essential tool for Linux users and those that dual boot is the   [Super Grub Disk]("http://linux.softpedia.com/progDownload/Super-Grub-Disk-Download-8071.html")   If its a Grub problem then it should be able to get it to boot.

---


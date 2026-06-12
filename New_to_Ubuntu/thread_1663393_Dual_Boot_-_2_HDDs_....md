---
title: "Dual Boot - 2 HDDs ..."
date: 2011-01-09
forum: New to Ubuntu
---

### Post by LogiDen on 2011-01-09
Here's hoping somebody can help me out a little :D

Basically I've been using Windows 7 since its release, but I've now taken the decision to install (and use) Ubuntu 10.10 as well - therefore requiring a dual boot setup in the process.

Windows 7 is installed on one HDD, whilst Ubuntu 10.10 is installed on a second HDD. 

I followed the steps from this thread ([http://ubuntuforums.org/showthread.php?t=1242793](http://ubuntuforums.org/showthread.php?t=1242793)), i.e. disconnecting the Windows 7 HDD first, then installing Ubuntu on the other HDD and then updating the GRUB (menu.lst) on the Ubuntu HDD (in the lowest SATA port) - well I tried ...

The problem I have (and hadn't realised before installing Ubuntu 10.10), is that Ubuntu 10.10 utilises GRUB2 - meaning that I can't edit the menu.lst file as was detailed in the link I posted above.

What should I be looking to do now? Any links would be great ...

Thanks.

---

### Post by cipherboy_loc on 2011-01-09
What happens when you boot Ubuntu and run:

```

sudo update-grub2

```

---

### Post by LogiDen on 2011-01-09
> **cipherboy_loc said:**
> What happens when you boot Ubuntu and run:

```

sudo update-grub2

```

Ah that's perfect. Thanks.

Out of interest, is it possible to alter the boot menu? I.e. remove some options, and move the Windows option to the top?

---

### Post by radar2020 on 2011-01-09
> Out of interest, is it possible to alter the boot menu? I.e. remove some options, and move the Windows option to the top? 

The easiest way is install StartUpManager.

For more information:  [https://help.ubuntu.com/community/StartUpManager](https://help.ubuntu.com/community/StartUpManager)

---

### Post by LogiDen on 2011-01-09
> **radar2020 said:**
> The easiest way is install StartUpManager.

For more information:  [https://help.ubuntu.com/community/StartUpManager](https://help.ubuntu.com/community/StartUpManager)

Excellent. Thanks.

---


---
title: "ubuntu 11.04 x64, sudden restarts"
date: 2011-06-25
forum: New to Ubuntu
---

### Post by koko84 on 2011-06-25
I'm a new Ubuntu user since a few days and I have a big problem:(!
 
I'm using Win7,x86 and I wanted a second OS for trying out Ubuntu. Installation was fine and it works. But after GRUB starts, my pc sudden restarts sometimes. Sometimes it happens in GRUB, sometimes after login to ubuntu or later. Hardware works fine because I'm having no problems starting or working with Win7.
 
Hardware is:
Acer Aspire 5680
-Core2Duo T7200 @2,00GHz
-4 GB Memory DDR2
-NVIDIA GeForce Go 7200 256MB
-750 GB Western Digital Harddrive
 
My Partition for Ubuntu has 60GB of space, ext4 and I reserved 3GB for Swap.
 
I do really need help about this problem:(. I thought Linux were a stable OS. But since I'm using it a few days I had more problems as in using Win7 or XP for many years.

---

### Post by josephmills on 2011-06-25
> **koko84 said:**
> I'm a new Ubuntu user since a few days and I have a big problem:(!
 
I'm using Win7,x86 and I wanted a second OS for trying out Ubuntu. Installation was fine and it works. But after GRUB starts, my pc sudden restarts sometimes. Sometimes it happens in GRUB, sometimes after login to ubuntu or later. Hardware works fine because I'm having no problems starting or working with Win7.
 
Hardware is:
Acer Aspire 5680
-Core2Duo T7200 @2,00GHz
-4 GB Memory DDR2
-NVIDIA GeForce Go 7200 256MB
-750 GB Western Digital Harddrive
 
My Partition for Ubuntu has 60GB of space, ext4 and I reserved 3GB for Swap.
 
I do really need help about this problem:(. I thought Linux were a stable OS. But since I'm using it a few days I had more problems as in using Win7 or XP for many years.

did you install the nivda driver what goes ```
dmesg 
``` have to say about this

---

### Post by quequotion on 2012-01-18
> **josephmills said:**
> did you install the nivda driver what goes ```
dmesg 
``` have to say about this

Was there ever a cause found for this?

Does it actually have something to do with nVidia or is it a kernel bug?

I think it's very likely a kernel bug.

I am also experiencing these sudden, random, and extremely frightening reboots.

They tend to happen whenever CPU usage spikes.

In my PC I have a Phenom II x 6.

If a process uses a lot of CPU in one thread, it doesn't seem to be a problem, but some processes that can use multiple cores cause sudden reboot.

---


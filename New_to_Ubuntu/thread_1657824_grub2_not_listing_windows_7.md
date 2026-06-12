---
title: "grub2 not listing windows 7"
date: 2011-01-01
forum: New to Ubuntu
---

### Post by carvish on 2011-01-01
hi, big fan, want to get this working, I am trying to dual boot win 7 and ubuntu 10.10. I have separate hard drives for each os 60g ssd for win 7 and 160g hhd for ubuntu and 2-1 tb storage drives, I installed win 7 first, worked fine, bought a copy of "Linux format" in december, had a copy of ubuntu 10.10 so I installed it . Upon boot grub does not see my windows 7 os, just ubuntu10.10. How do I get grub 2 to see the other os?

---

### Post by coffeecat on 2011-01-01
Try two things.

First, open a terminal, and:

```
sudo update-grub
```

If that doesn't work, I've come across a couple of cases where the app os-prober - which is responsible for detecting other operating systems for grub - was not installed. That is quite inexplicable because os-prober should be  part of a default installation. Nevertheless, open System > Administration > Synaptic. See if os-prober is installed. If it isn't, install it and run 'sudo update-grub' again.

---

### Post by carvish on 2011-01-01
thank you for replying, got it working by typing in the terminal 

sudo apt-get install os-prober
now grub sees it and its working fine, thank you

---

### Post by drs305 on 2011-01-01
> **carvish said:**
> thank you for replying, got it working by typing in the terminal 

sudo apt-get install os-prober
now grub sees it and its working fine, thank you

I'm curious - are you using lubuntu? I know that it wasn't 'shipping' with os-prober but wasn't aware of other Ubuntu distros which didn't include it.

---

### Post by coffeecat on 2011-01-01
> **drs305 said:**
> I'm curious - are you using lubuntu? I know that it wasn't 'shipping' with os-prober but wasn't aware of other Ubuntu distros which didn't include it.

The OP installed from the Linux Format DVD, so I'm wondering if os-prober went awol somewhere in the remastering. One of the cases I came across was on the Linux Format forum. The other was on this forum. I'll see if I can find it.

**EDIT**: yes, here it is. Seemingly confirmed in Ubuntu 10.10. Odd

[http://ubuntuforums.org/showthread.php?t=1647659](http://ubuntuforums.org/showthread.php?t=1647659)

---

### Post by drs305 on 2011-01-01
Thanks *coffeecat*. I do seem to vaguely remember that now that you have dug it up...

---

### Post by carvish on 2011-01-01
> **drs305 said:**
> I'm curious - are you using lubuntu? I know that it wasn't 'shipping' with os-prober but wasn't aware of other Ubuntu distros which didn't include it.

ubuntu 10.10

---


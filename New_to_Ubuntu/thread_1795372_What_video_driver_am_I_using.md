---
title: "What video driver am I using?"
date: 2011-07-02
forum: New to Ubuntu
---

### Post by Luke M on 2011-07-02
How do I find out what video driver I'm using, add/remove etc? I looked in the xorg.conf file, but there's nothing of interest there; the file is almost empty. In general, is there any way to manage drivers from a convenient GUI interface, or does everything have to be done via text files?

---

### Post by Frogs Hair on 2011-07-02
Try the log file viewer > Xorg.O.log if you have not installed a proprietary video driver . If you have check Xserver settings for Nvidia or the ATI counterpart . I am not familiar with Intel drivers.

---

### Post by s1baker on 2011-07-02
Here is some commands I have copied from this forum.


```
lspci  -mm | grep VGA
lspci -v
lsmod
sudo lshw -C display ; dpkg -l grep nvidia

```

---

### Post by wildmanne39 on 2011-07-02
Hi, if you have an intel graphics chip you can run this command and it will show all the intel modules that are loaded including intel graphics driver.
```
sudo lspci -k
```

---

### Post by zekayi on 2011-11-15
> **s1baker said:**
> Here is some commands I have copied from this forum.


```
lspci  -mm | grep VGA
lspci -v
lsmod
sudo lshw -C display ; dpkg -l grep nvidia

```

Hi s1baker,

can it be that "|" is missing in your last command before the grep?

Regs
Zekayi

---


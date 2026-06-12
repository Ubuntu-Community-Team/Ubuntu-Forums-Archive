---
title: "Copy folders to usb drive using terminal"
date: 2009-02-14
forum: New to Ubuntu
---

### Post by Sims12345 on 2009-02-14
Hi,

Ubuntu wont boot anymore so I have decided to just reinstall (see [this]("http://ubuntuforums.org/showthread.php?p=6729421#post6729421") thread for a description of my problem) 

My question is how do I copy folders (i.e my Desktop folder from the seesion I cannot boot into anymore) onto a usb flash drive? I am booted into a live CD session (using a USB drive different from the one I am trying to copy files over to) I have tried drag and drop but it says I dont have permission to do it.

Thanks for your help!

---

### Post by cerealtx on 2009-02-14
> **Sims12345 said:**
> Hi,

Ubuntu wont boot anymore so I have decided to just reinstall (see [this]("http://ubuntuforums.org/showthread.php?p=6729421#post6729421") thread for a description of my problem) 

My question is how do I copy folders (i.e my Desktop folder from the seesion I cannot boot into anymore) onto a usb flash drive? I am booted into a live CD session (using a USB drive different from the one I am trying to copy files over to) I have tried drag and drop but it says I dont have permission to do it.

Thanks for your help!

```
sudo cp /where/ever /media/<media name>
```
could also use mv

---

### Post by Sims12345 on 2009-02-14
> **cerealtx said:**
> ```
sudo cp /where/ever /media/<media name>
```


I had to use ```
sudo cp -R /where/ever /media/<media name>
``` because I was copying folders.

Thanks for your help, I got it done, time for the reinstall :)

---


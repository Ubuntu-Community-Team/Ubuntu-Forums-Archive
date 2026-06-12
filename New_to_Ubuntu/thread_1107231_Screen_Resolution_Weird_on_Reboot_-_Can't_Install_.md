---
title: "Screen Resolution Weird on Reboot - Can't Install NVIDIA Driver"
date: 2009-03-26
forum: New to Ubuntu
---

### Post by UnknownFear on 2009-03-26
I recently shut down my computer and upon reboot, the screen resolution changed from 1024x768 to 604 something. I tried downloading and installing an updated driver for nVIDIA, but it won't run. I tried doing it in the terminal, but got:

```

daniel@daniel-desktop:~$ sudo sh NVIDIA-Linux-x86-173.14.18-pkg1.run
sh: Can't open NVIDIA-Linux-x86-173.14.18-pkg1.run
daniel@daniel-desktop:~$

```

And I tried running it in the terminal, but all I got was

**ERROR: nvidia-installer must be run as root**

Can someone help me out?

---

### Post by sandyd on 2009-03-26
> **UnknownFear said:**
> I recently shut down my computer and upon reboot, the screen resolution changed from 1024x768 to 604 something. I tried downloading and installing an updated driver for nVIDIA, but it won't run. I tried doing it in the terminal, but got:
 
```

daniel@daniel-desktop:~$ sudo sh NVIDIA-Linux-x86-173.14.18-pkg1.run
sh: Can't open NVIDIA-Linux-x86-173.14.18-pkg1.run
daniel@daniel-desktop:~$

```
 
And I tried running it in the terminal, but all I got was
 
**ERROR: nvidia-installer must be run as root**
 
Can someone help me out?
 
just run 
 
```

sudo ./NVIDIA-Linux-x86-173.14.18-pkg1.run

```
 
OR
 
```

sudo ~/Desktop/NVIDIA-Linux-x86-173.14.18-pkg1.run

```

---

### Post by UnknownFear on 2009-03-26
> **carlee said:**
> just run 
 
```

sudo ./NVIDIA-Linux-x86-173.14.18-pkg1.run

```
 
OR
 
```

sudo ~/Desktop/NVIDIA-Linux-x86-173.14.18-pkg1.run

```

I don't know why but, I shut down my computer after making this thread and, when I turned it back on, the resolution is fixed. I'll install the driver just to make sure.

---


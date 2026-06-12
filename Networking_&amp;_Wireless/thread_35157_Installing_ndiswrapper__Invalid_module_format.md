---
title: "Installing ndiswrapper : Invalid module format"
date: 2005-05-17
forum: Networking &amp; Wireless
---

### Post by Jones on 2005-05-17
Hey all, 
I've been attempting to get ndiswrapper installed on my machine. I've gotten through the instalation of ndiswrapper and the installation of the drivers ok. However, when I try to modprobe, I recieve the error: 

```
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.8.1-3-386/misc/ndiswrapper.ko) : Invalid module format
```

when I run dmesg, It spits out

```
ndiswrapper: version magic '2.6.8.1 SMP preempt PENTIUM4 4KSTACKS gcc-3.3' should be '2.6.8.1-3-386 preempt 386 gcc-3.3'
```

Not sure whats going on. I have gotten my wireless to work before, but I reformatted and I didn't document the steps I took to get ndiswrapper working.. ](*,) 

Thanks in advance.

---


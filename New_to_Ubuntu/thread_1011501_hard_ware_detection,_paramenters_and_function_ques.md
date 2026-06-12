---
title: "hard ware detection, paramenters and function questions"
date: 2008-12-14
forum: New to Ubuntu
---

### Post by 2blue on 2008-12-14
Hi

I have installed xubuntu on my old computer and used it fairly reguarly for about a year now. It took some time before figured out some functions but regular applications like office, nettwork, update manager are very easy to understand and something that comes immediatley. 

How ever I have some subject I am wondering about.

This is an old laptop with a 10 GB hard disk, 700 MHz Duron processor, and I am not quite shore what RAM is. I have put in two new memory cards I found very cheaply on ebay each 512 MB, and I suspect that maximum RAM for this laptop realy is 256 MB or 512MB. I cannot find any spesific data, because Packard Bell has several "easy one" models. Is there a way to find out how Xubuntu is running the hard ware; figures, parameters, numbers...? 

In System Monitor I find these numbers:

Hardware: 
Memory 755,6 MiB (Is this RAM ?) 
AMD Duron Processor
System Status: 2,9 GiB Available Disk Space

Under File Systems: dev/sda1 total 5,9 GiB with 2,9 GiB available space. 
Now where have the remaining 4,1 GiB hard disk space gone? 
I am asking about this because I am not shore if I installed Xubuntu correctly on the computer. Of course I wanted Xubuntu as the only OS and for it to take over the entire hard drive.  

I hope someone are able to guide me through these facts and numbers and verify if I'm understanding this correctly.

---

### Post by jbrown96 on 2008-12-14
That memory is your RAM. There are several ways to find info about your hardware. I prefer using a shell (terminal) to find out information, so these are all shell methods. 

To find general info about your hardware
```
lspci
```

To find more info that you want about your ram and cpu
```
cat /proc/cpuinfo
```
```
cat /proc/meminfo
```

You can find out the info about your disks with
```
sudo fdisk -l
```

---


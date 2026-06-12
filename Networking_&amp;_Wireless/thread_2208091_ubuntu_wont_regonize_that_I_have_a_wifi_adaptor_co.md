---
title: "ubuntu wont regonize that I have a wifi adaptor connected via usb"
date: 2014-02-26
forum: Networking &amp; Wireless
---

### Post by twilkins111 on 2014-02-26
So I find this quite strange. I originally had a AE2500 Cisco adapter and attempted to get Ubuntu 13.10 both two different version one 32 and one 64 bit and cant get Ubuntu to recognize it.  I had also bought a Netgear N300 adapter thinking it was a issue with the adapter, which also didn't work.  I know these two adapters work because they work when other versions of Linux are installed. I tried connecting both to all 6 usb ports that I have on my custom built thinking it was an issue with the port. I have also tried running ndiswrapper and applying a firmware upgrade to the bios. I am pretty fluent when it comes to troubleshooting Ubuntu or any other flavor of Linux as I am a system administrator and have to know it. Any tips to help me troubleshoot this would be greatly appreciated as I am kind of stumped on this one.

---

### Post by IvoGuerreiro on 2014-02-26
Hi,
Give a look in the Link:
[http://www.grailbox.com/2012/05/installing-cisco-linksys-ae2500-wireless-adapter-in-linux/](http://www.grailbox.com/2012/05/installing-cisco-linksys-ae2500-wireless-adapter-in-linux/)
[http://ubuntuforums.org/showthread.php?t=1805830&highlight=AE2500](http://ubuntuforums.org/showthread.php?t=1805830&highlight=AE2500)

---

### Post by twilkins111 on 2014-02-26
Tried that but it didn't seem to work for me. Note that this was done in super user mode. Im now focusing on the Netgear N300 but if I can get one or the other to work I will be happy.

---

### Post by chili555 on 2014-02-26
Please be sure the device is inserted and then open a terminal; may we see:```
lsusb
ndiswrapper -l
arch
```Thanks.

---

### Post by IvoGuerreiro on 2014-02-26
Hi, Chili555
What do you think about this procedure?


[http://www.youtube.com/watch?v=ZMYBWMD6cg8](http://www.youtube.com/watch?v=ZMYBWMD6cg8)

---

### Post by twilkins111 on 2014-02-26
> **chili555 said:**
> Please be sure the device is inserted and then open a terminal; may we see:```
lsusb
ndiswrapper -l
```Thanks.

I will post this as soon as I have access to this client machine. ETA 6pm EST

---

### Post by chili555 on 2014-02-26
> **IvoGuerreiro said:**
> Hi, Chili555
What do you think about this procedure?


[http://www.youtube.com/watch?v=ZMYBWMD6cg8](http://www.youtube.com/watch?v=ZMYBWMD6cg8)I think it is certainly a good demonstration of one of many methods to do the job. I think there are a few versions of the device and I'd rather verify the device with *lsusb* before I propose a solution. Also, although you did use the Windows XP files, your video doesn't make that clear. Also, you do not specify what to use for a 64-bit system. 32-bit .inf and .sys files won't work in a 64-bit system.

---

### Post by twilkins111 on 2014-02-26
Here is lsusb. When I try to run ndiswrapper -l as a superuser in the terminal, it just goes to a new line and dosnt report anything. I don't thinks its installing correctly. What am I forgetting to do?

twilkins111@ubuntu:~$ lsusb
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 0846:9020 NetGear, Inc. WNA3100(v1) Wireless-N 300 [Broadcom BCM43231]
Bus 001 Device 004: ID 04f3:01a4 Elan Microelectronics Corp. Wireless Keyboard
Bus 002 Device 003: ID 1058:0740 Western Digital Technologies, Inc. My Passport 1TB

---

### Post by chili555 on 2014-02-26
Is ndiswrapper installed correctly?```
sudo modprobe ndiswrapper
```Errors? Warnings? Screams?? Try to install it:```
sudo apt-get install ndisgtk
```That will install it and the prerequisites in one step. Now can you load it?```
sudo modprobe ndiswrapper
ndiswrapper -l
```Let's also see:```
arch
```If it is x86_64, I will take up an easier hobby like particle acceleration or forging the currency of Iceland.

---

### Post by twilkins111 on 2014-02-27
Ill try those when I get home from work. If all else fails I may just decide to run an extra cat 6 cable over and call it a day.

---


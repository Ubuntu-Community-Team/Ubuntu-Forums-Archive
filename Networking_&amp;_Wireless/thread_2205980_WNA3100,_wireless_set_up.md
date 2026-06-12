---
title: "WNA3100, wireless set up"
date: 2014-02-16
forum: Networking &amp; Wireless
---

### Post by sonnyjbr on 2014-02-16
I am new to Ubuntu and Linux and I am having an issue with getting wireless internet working.  I installed Ubuntu 13.10 a few days ago and have been struggling to get on the internet since then.  This is on my desktop and where it is located I am not able to get a wired connection to it. I am a NetGear WNA3100 USB network adapter  and I have been doing some research on this site and others to try to get it working, but to no avail.  I found the Windows driver for the network adapter (bcmwlhigh6.inf) and was able to use ndiswrapper to install the driver through terminal.  However, when I look under the Network it only lists Wired and Network Proxy, there is no wireless.  When I run lsusb I am able to see the network adapter, but when I run iwconfig I only get eth0 and lo, there is no entry for wlan0.  I am not sure what steps to take next.  My lsusb and iwconfig results are below.

LSUSB

Bus 003 Device 003: ID 0846:9020 NetGear, Inc. WNA3100(v1) Wireless-N 300 [Broadcom BCM43231] 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 009 Device 002: ID 04e8:326c Samsung Electronics Co., Ltd ML-2010P Mono Laser Printer 
Bus 009 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 002 Device 004: ID 090c:1000 Silicon Motion, Inc. - Taiwan (formerly Feiya Technology Corp.) Flash Drive 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 007 Device 002: ID 1d57:32da Xenta 2.4GHz Receiver (Keyboard and Mouse) 
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 001 Device 002: ID 1058:1021 Western Digital Technologies, Inc. Elements 2TB 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 006 Device 002: ID 045e:00db Microsoft Corp. Natural Ergonomic Keyboard 4000 V1.0 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 005 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub 
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 

IWCONFIG
eth0      no wireless extensions. 
lo        no wireless extensions.

---

### Post by wildmanne39 on 2014-02-16
*Thread moved to **Networking & Wireless**.*

---

### Post by sonnyjbr on 2014-02-18
I don't mean to be impatient, I know that you guys volunteer your time to help people like me with their Linux problems, but I am anxious to start exploring Ubuntu and right now it is not a lot of value to me since I can't connect.  I have done more research over the last couple days and I am still stuck. Any help on this would really be appreciated. Thanks.

---

### Post by sonnyjbr on 2014-02-22
I would really appreciate if anyone might be able to help with this.

---

### Post by sonnyjbr on 2014-03-03
If anyone could help with this I would really appreciate it. Thanks.

---

### Post by sonnyjbr on 2014-03-07
Any suggestions would be appreciated.

---

### Post by chili555 on 2014-03-07
I hate this device. I am only answering because you have posted for two weeks and none of the smart and fast guys is self-destructive enough to answer. I guess you are stuck with me. 

Here is the short and sweet. The drivers you need are the XP inf and sys files matching your architecture; either 32- or 64-bit:```
arch
```The files here at post #5 are probably what you need: [http://ubuntuforums.org/showthread.php?t=2174748](http://ubuntuforums.org/showthread.php?t=2174748)

Do you have any interesting clues here?```
sudo modprobe ndiswrapper
dmesg | grep ndis
ndiswrapper -l
```

---

### Post by sonnyjbr on 2014-03-07
Thank you for the response.

If it is any consolation I am hating this device as well, at least as far as Ubuntu goes.  My system is 64 bit and I wasn't able to look at the link for the drivers yet but here are the results from the other commands that you recommended.

sonny@sonny-ubuntu:~$ sudo modprobe ndiswrapper
[sudo] password for sonny: 
FATAL: Module ndiswrapper not found.

Nothing for the second one.

sonny@sonny-ubuntu:~$ ndiswrapper -l
bcmwlhigh6 : driver installed
	device (0846:9020) present

---

### Post by chili555 on 2014-03-08
As has been stated before, one step at a time. First, we'll address this:> FATAL: Module ndiswrapper not found.Here is a recent question that addresses the very same issue. [http://askubuntu.com/questions/403597/problems-re-establishing-wireless-connection-after-messing-with-ndiswrapper-modu](http://askubuntu.com/questions/403597/problems-re-establishing-wireless-connection-after-messing-with-ndiswrapper-modu)

I suggest you try the reinstall part first. If that doesn't work, then compile. I am confident one will work and then we can look for errors in dmesg. I have never seen bcmwlhigh6 working correctly, so I am also quite confident the dmesg will be crazy.

---


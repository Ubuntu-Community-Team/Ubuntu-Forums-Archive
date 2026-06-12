---
title: "Wireless connection dropping"
date: 2015-01-12
forum: Networking &amp; Wireless
---

### Post by rakesh343 on 2015-01-12
I have installed 14.04.1. I'm able to connect to the wireless, but it gets dropped every now and then. There is no problem with the modem as other devices are running fine with it. Is there any malicious command that is causing it? Or, can it be a hardware issue. This is a new machine that I've bought. It Is Lenovo G50-70 series model.

---

### Post by ajgreeny on 2015-01-12
Let's see the output of command **lspci** in terminal which will show us the wifi chip in use on that machine, though it looks as if its a Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter according to the info at [http://ubuntuforums.org/showthread.php?t=2240673](http://ubuntuforums.org/showthread.php?t=2240673) and other posts.

Maybe, as in that thread, a more recent kernel will sort out the problem.  GIve 3.16.0-28 a try as it's in the repos.

---

### Post by rakesh343 on 2015-01-13
Thanks ajgreeny, I'm trying to do something on the basis of the other thread you suggested. Let me see, will be back with the result, hopefully positive. :-)

---

### Post by rakesh343 on 2015-01-13
Results for code:   lspci

yayavar@yayavar:~$ lspci 
00:00.0 Host bridge: Intel Corporation Haswell-ULT DRAM Controller (rev 0b) 
00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 0b) 
00:03.0 Audio device: Intel Corporation Haswell-ULT HD Audio Controller (rev 0b) 
00:14.0 USB controller: Intel Corporation Lynx Point-LP USB xHCI HC (rev 04) 
00:16.0 Communication controller: Intel Corporation Lynx Point-LP HECI #0 (rev 04) 
00:1b.0 Audio device: Intel Corporation Lynx Point-LP HD Audio Controller (rev 04) 
00:1c.0 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 3 (rev e4) 
00:1c.3 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 4 (rev e4) 
00:1d.0 USB controller: Intel Corporation Lynx Point-LP USB EHCI #1 (rev 04) 
00:1f.0 ISA bridge: Intel Corporation Lynx Point-LP LPC Controller (rev 04) 
00:1f.2 SATA controller: Intel Corporation Lynx Point-LP SATA Controller 1 [AHCI mode] (rev 04) 
00:1f.3 SMBus: Intel Corporation Lynx Point-LP SMBus Controller (rev 04) 
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 10) 
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter


I guess this is for information regarding network adapter, etc.

---

### Post by rakesh343 on 2015-01-13
The output of other commands suggested in the [http://ubuntuforums.org/showthread.php?t=2240673]("http://ubuntuforums.org/showthread.php?t=2240673") are the following:

```
pkexec kill -9 'pidoff NetworkManager' 
```

Result:
yayavar@yayavar:~$ pkexec kill -9 'pidoff NetworkManager' 
kill: failed to parse argument: 'pidoff NetworkManager'

```
sudo service network-manager restart
```

Result:
yayavar@yayavar:~$ sudo service network-manager restart 
[sudo] password for yayavar: 
network-manager stop/waiting 
network-manager start/running, process 4008

```
sudo rmmod rtl8723be && modprobe rtl8723be
```

Result:
yayavar@yayavar:~$ sudo rmmod rtl8723be && modprobe rtl8723be 
modprobe: ERROR: could not insert 'rtl8723be': Operation not permitted

```
sudo modprobe-r rtl8723be && modprobe rtl8723be
```

Result:
yayavar@yayavar:~$ sudo modprobe-r rtl8723be && modprobe rtl8723be 
sudo: modprobe-r: command not found


Now, after doing all this, my wireless connectin is dropping just a few minutes after I restart my computer. What has changed?

---

### Post by rakesh343 on 2015-01-13
Please reply. I need to fix it urgently, or else I have to return this laptop if it is a hardware issue. Please help.:confused:

---

### Post by rakesh343 on 2015-01-14
Has this thread been discarded? Please help...

---


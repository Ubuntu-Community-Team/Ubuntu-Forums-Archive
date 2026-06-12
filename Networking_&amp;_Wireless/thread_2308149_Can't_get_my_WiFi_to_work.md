---
title: "Can't get my WiFi to work"
date: 2015-12-31
forum: Networking &amp; Wireless
---

### Post by UniqueActive on 2015-12-31
Hey guys, I am new to Ubuntu and just installed it but I am having trouble getting it to recognize my wireless card. I will post some outputs to commands that could give you a starting point to my problem:

**ifconfig -a**
Output:
enp0s25   Link encap:Ethernet  HWaddr 00:1a:a0:9e:60:21  
          inet addr:192.168.0.108  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:a0ff:fe9e:6021/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14485 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8574 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:16435441 (16.4 MB)  TX bytes:1059171 (1.0 MB)
          Interrupt:20 Memory:fdfc0000-fdfe0000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1694 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1694 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:171499 (171.4 KB)  TX bytes:171499 (171.4 KB)

**lspci**
Output:
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82562V-2 10/100 Network Connection (rev 02)
00:1a.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1d.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA Controller [IDE mode] (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA Controller [IDE mode] (rev 02)
01:00.0 VGA compatible controller: NVIDIA Corporation G84 [GeForce 8600 GT] (rev a1)
02:01.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

I am guessing by the name that the last entry is the wireless card and it's PCI-E aswell.
All help would be greatly appreciated!

UniqueActive

---

### Post by howefield on 2015-12-31
Thread moved to the "*Networking & Wireless*" forum.

You might read this [sticky thread]("http://ubuntuforums.org/showthread.php?t=370108"), run the wireless script and paste the info back here.

---

### Post by chili555 on 2015-12-31
Please check here: [http://ubuntuforums.org/showthread.php?t=2214110](http://ubuntuforums.org/showthread.php?t=2214110)

---

### Post by UniqueActive on 2015-12-31
wireless-info.txt attatched to this answer for additional info :)

---

### Post by Hadaka on 2015-12-31
Hi,from a working wired connection open a terminal ctrl/alt/t
then COPY and paste one line at a time.
```
sudo apt-get update
sudo sed -i '/^wl/ d' /etc/modules
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install firmware-b43-installer
sudo modprobe b43

```
then do..
```
sudo iw reg set DE
sudo sed -i 's/^REG.*=$/&DE/' /etc/default/crda
```
remove wired connection,boot and test wireless

---

### Post by UniqueActive on 2015-12-31
Thanks a lot, it works perfectly fine now!

---

### Post by Hadaka on 2015-12-31
Great !, glad that worked for you.

---


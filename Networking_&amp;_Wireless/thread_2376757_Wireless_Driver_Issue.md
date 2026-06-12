---
title: "Wireless Driver Issue"
date: 2017-11-05
forum: Networking &amp; Wireless
---

### Post by kevkel on 2017-11-05
I'm completely new to Ubuntu and can't get my wireless card working. I tried several things I found here, but nothing has worked so far and my mind is starting to go numb. Ubuntu does recognize my card. lspci shows it's a BCM4311, but doesn't give me a chipset, so I may have installed the wrong driver. Here's a couple things that might help you figure things out for me. Any help would be much appreciated, apologies for being a noobuntard.

iwconfig
lo        no wireless extensions.

enp9s0    no wireless extensions.

ifconfig
enp9s0    Link encap:Ethernet  HWaddr 00:1c:23:0e:4d:11  
          inet addr:192.168.137.47  Bcast:192.168.137.255  Mask:255.255.255.0
          inet6 addr: fe80::2165:1f50:9b24:9fac/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:91588 errors:0 dropped:0 overruns:0 frame:0
          TX packets:56818 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:122609481 (122.6 MB)  TX bytes:5413698 (5.4 MB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:3674 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3674 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:348218 (348.2 KB)  TX bytes:348218 (348.2 KB)

---

### Post by westie457 on 2017-11-06
Hi, welcome to UF.

With the ethernet cable connected open a terminal copy and paste, one at a time, the following commands.```
sudo apt update
sudo apt purge bcmwl-kernel-source
sudo apt install firmware-b43-installer
sudo modprobe -rfv wl
sudo modprobe b43
```
Ignore all errors and warnings of items not found, just move on to the next command.

After the last command check the Network Manager icon for any found networks. If none show reboot the system.

See you on the other side.

---

### Post by kevkel on 2017-11-06
Awesome, that worked. Thank you so much! Marking as solved.

---

### Post by westie457 on 2017-11-07
Glad it worked and thank you for marking as 'solved', it will help someone with the same situation as yours.

---


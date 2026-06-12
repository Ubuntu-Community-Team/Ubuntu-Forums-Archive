---
title: "Ubuntu 16.04 LTS Asus Vivobook S S510U Wifi not working"
date: 2018-03-22
forum: Networking &amp; Wireless
---

### Post by nahir on 2018-03-22
Hi, I've just installed Ubuntu 16.04 lts in my new Asus s510u, which has a NVIDIA GEFORCE 940mx 348.111 driver. The problem is that the option to connect the wifi (Enable Wifi) does not appear. I've tried the solutions from [https://ubuntuforums.org/showthread.php?t=2385373](https://ubuntuforums.org/showthread.php?t=2385373) and  [https://www.reddit.com/r/linuxquestions/comments/4je63z/no_wireless_on_ubuntu_1604/](https://www.reddit.com/r/linuxquestions/comments/4je63z/no_wireless_on_ubuntu_1604/) , but nothing works. I have this outputs:

lspci
00:00.0 Host bridge: Intel Corporation Device 5904 (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Device 5916 (rev 02)
00:04.0 Signal processing controller: Intel Corporation Skylake Processor Thermal Subsystem (rev 02)
00:14.0 USB controller: Intel Corporation Sunrise Point-LP USB 3.0 xHCI Controller (rev 21)
00:14.2 Signal processing controller: Intel Corporation Sunrise Point-LP Thermal subsystem (rev 21)
00:15.0 Signal processing controller: Intel Corporation Sunrise Point-LP Serial IO I2C Controller (rev 21)
00:15.1 Signal processing controller: Intel Corporation Sunrise Point-LP Serial IO I2C Controller (rev 21)
00:16.0 Communication controller: Intel Corporation Sunrise Point-LP CSME HECI (rev 21)
00:17.0 SATA controller: Intel Corporation Sunrise Point-LP SATA Controller [AHCI mode] (rev 21)
00:1c.0 PCI bridge: Intel Corporation Device 9d10 (rev f1)
00:1c.5 PCI bridge: Intel Corporation Sunrise Point-LP PCI Express Root Port (rev f1)
00:1e.0 Signal processing controller: Intel Corporation Sunrise Point-LP Serial IO UART Controller (rev 21)
00:1e.2 Signal processing controller: Intel Corporation Sunrise Point-LP Serial IO SPI Controller (rev 21)
00:1f.0 ISA bridge: Intel Corporation Device 9d4e (rev 21)
00:1f.2 Memory controller: Intel Corporation Sunrise Point-LP PMC (rev 21)
00:1f.3 Audio device: Intel Corporation Device 9d71 (rev 21)
00:1f.4 SMBus: Intel Corporation Sunrise Point-LP SMBus (rev 21)
01:00.0 3D controller: NVIDIA Corporation GM108M [GeForce 940MX] (rev a2)
02:00.0 Network controller: Intel Corporation Device 24fd (rev 78)

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ifconfig
eth0      Link encap:Ethernet  HWaddr 00:10:13:af:aa:2f  
          inet addr:10.3.120.26  Bcast:10.3.120.255  Mask:255.255.255.0
          inet6 addr: fe80::8224:62d2:6f1c:30e6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:31361 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28211 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:23839631 (23.8 MB)  TX bytes:3761323 (3.7 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:3791 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3791 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:395268 (395.2 KB)  TX bytes:395268 (395.2 KB)


I have also tried 
 sudo apt-get purge bcmwl-kernel-source

  sudo apt-get install linux-generic bcmwl-kernel-source

Reboot

and restarting the network manager and nothing works.

Also, on Additional Drivers there is no option to select a Wifi driver, only the one to select my Nvidia driver (which I selected).

Please help, I don't know what else to try!

---


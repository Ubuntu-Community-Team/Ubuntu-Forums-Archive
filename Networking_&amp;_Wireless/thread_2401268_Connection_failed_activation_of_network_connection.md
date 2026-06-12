---
title: "Connection failed activation of network connection failed"
date: 2018-09-15
forum: Networking &amp; Wireless
---

### Post by th3gentleman on 2018-09-15
Background: I'm dual booting Ubuntu 18.04 alongside windows10.  Everything was fine and dandy up to the wifi issue. The wifi takes 30-45  seconds to eventually end up giving me the error "Connection failed\n  Activation of network connection failed"

  Here's the following information if it may be helpful:  [URL="http://paste.ubuntu.com/p/Sgy7CM4y7v/"]http://paste.ubuntu.com/p/Sgy7CM4y7v/

[/URL]

  00:00.0 Host bridge: Intel Corporation Device 3ec4 (rev 07) 00:01.0 PCI bridge: Intel Corporation Skylake PCIe Controller (x16) (rev 07) 00:02.0 VGA compatible controller: Intel Corporation Device 3e9b 00:12.0 Signal processing controller: Intel Corporation Device a379 (rev 10) 00:14.0 USB controller: Intel Corporation Device a36d (rev 10) 00:14.2 RAM memory: Intel Corporation Device a36f (rev 10) 00:14.3 Network controller: Intel Corporation Device a370 (rev 10) 00:16.0 Communication controller: Intel Corporation Device a360 (rev 10) 00:1b.0 PCI bridge: Intel Corporation Device a340 (rev f0) 00:1d.0 PCI bridge: Intel Corporation Device a330 (rev f0) 00:1d.4 PCI bridge: Intel Corporation Device a334 (rev f0) 00:1f.0 ISA bridge: Intel Corporation Device a30d (rev 10) 00:1f.3 Audio device: Intel Corporation Device a348 (rev 10) 00:1f.4 SMBus: Intel Corporation Device a323 (rev 10) 00:1f.5 Serial bus controller [0c80]: Intel Corporation Device a324 (rev 10) 01:00.0 VGA compatible controller: NVIDIA Corporation GP106M [GeForce GTX 1060 M obile] (rev a1) 3b:00.0 Non-Volatile memory controller: Samsung Electronics Co Ltd Device a808 3c:00.0 Ethernet controller: Qualcomm Atheros Killer E2500 Gigabit Ethernet Cont roller (rev 10)


  **ifconfig** 
enp60s0: flags=4163  mtu 1500         inet 192.168.1.8  netmask 255.255.255.0  broadcast 192.168.1.255         inet6 fe80::73be:f01e:5eab:2848  prefixlen 64  scopeid 0x20         ether 30:9c:23:93:2f:bf  txqueuelen 1000  (Ethernet)         RX packets 2165  bytes 1807601 (1.8 MB)         RX errors 0  dropped 0  overruns 0  frame 0         TX packets 2051  bytes 256729 (256.7 KB)         TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0         device interrupt 16  

  lo: flags=73  mtu 65536         inet 127.0.0.1  netmask 255.0.0.0         inet6 ::1  prefixlen 128  scopeid 0x10         loop  txqueuelen 1000  (Local Loopback)         RX packets 488  bytes 46548 (46.5 KB)         RX errors 0  dropped 0  overruns 0  frame 0         TX packets 488  bytes 46548 (46.5 KB)         TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


  [B]iwconfig
[/B] wlo1      IEEE 802.11  ESSID:off/any
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off
          Retry short limit:7   RTS thr:off   Fragment thr:off           Power Management:on



  It seems that when I close my lid on the laptop and reopen it >  airplane mode is on and it says on a greyed icon of the wifi that the  "Wi-Fi hardware disabled" 
  I tried a whole bunch of other solutions and decided to make a ubuntu forum account to get the real experts help.


  currently using a ethernet cord to connect. Sorry for any noob traits I displayed while posting :P appreciate any help...

---

### Post by th3gentleman on 2018-09-16
Bumping:P

---

### Post by th3gentleman on 2018-09-17
Solved it. Thank you

---

### Post by ihendley on 2018-11-23
How did you solve it?

---


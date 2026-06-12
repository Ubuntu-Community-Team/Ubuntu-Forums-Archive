---
title: "Auto-generation of network interfaces"
date: 2016-01-26
forum: Networking &amp; Wireless
---

### Post by andrei90 on 2016-01-26
Hello,

I'm running on **Lubuntu 15.10** (codename wily) connected with a Fast Ethernet cable to the Internet, and my network interfaces keep piling up.
To be honest I don't know why, probably because it auto-switched from cable to wifi from time-to-time, but I don't think this is the main reason.

Here's the output of **ifconfig** and **lshw**
```
dminca@dev:~$ ifconfig -s                                                    
Iface   MTU Met   RX-OK RX-ERR RX-DRP RX-OVR    TX-OK TX-ERR TX-DRP TX-OVR Flg       
docker0    1500 0     76263      0      0 0         76227      0      0      0 BMRU  
enp3s0     1500 0    773898      0      0 0        550258      0      0      0 BMRU  
lo        65536 0     58850      0      0 0         58850      0      0      0 LRU   
tun0       1500 0      2625      0      0 0          2215      0      0      0 MOPRU 
veth04bb350  1500 0     46263      0      0 0         49362      0      0      0 BMRU
veth328720b  1500 0     20935      0      0 0         29381      0      0      0 BMRU
veth488be88  1500 0     47035      0      0 0         45148      0      0      0 BMRU
veth4e8426b  1500 0     50982      0      0 0         43391      0      0      0 BMRU
veth52d1d8d  1500 0   7639547      0      0 0       3991177      0      0      0 BMRU
veth88d3c58  1500 0    485278      0      0 0        479864      0      0      0 BMRU
veth8bd06f3  1500 0    384665      0      0 0        387519      0      0      0 BMRU
vetha27650c  1500 0   1840482      0      0 0       1597198      0      0      0 BMRU
vethb2c2a7d  1500 0   7171879      0      0 0      11411847      0      0      0 BMRU
vethc0e3923  1500 0      1556      0      0 0          1461      0      0      0 BMRU
vethfec966f  1500 0   1116738      0      0 0        772101      0      0      0 BMRU
```

```
dminca@dev:~$ lshw -C network -short
WARNING: you should run this program as super-user.
H/W path       Device       Class          Description
======================================================
/0/100/1c.2/0  wlp2s0       network        QCA9565 / AR9565 Wireless Network Adapter
/0/100/1c.3/0  enp3s0       network        QCA8172 Fast Ethernet
/2             vetha27650c  network        Ethernet interface
/3             vethc0e3923  network        Ethernet interface
/4             veth4e8426b  network        Ethernet interface
/5             veth8bd06f3  network        Ethernet interface
/6             veth52d1d8d  network        Ethernet interface
/7             veth88d3c58  network        Ethernet interface
/8             veth04bb350  network        Ethernet interface
/9             vethb2c2a7d  network        Ethernet interface
/a             veth488be88  network        Ethernet interface
/b             veth328720b  network        Ethernet interface
/c             vethfec966f  network        Ethernet interface
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
```

How can I make it stop auto-generating new interfaces beside the default ones (eht0, wlan0...) ????

---

### Post by annkapul on 2016-01-26
It seems you have installed VirtualBox with several virtual machines. VETH is virtual ethernet interface and created by openVZ, so re-switching between wlan and eth doesn't matter.

---

### Post by andrei90 on 2016-01-28
I've checked in my packages and I have no VirtualBox installed whatsoever. Could this be from the Docker containers ?

---


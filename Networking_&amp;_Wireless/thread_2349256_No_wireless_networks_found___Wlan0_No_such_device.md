---
title: "No wireless networks found \  Wlan0 No such device"
date: 2017-01-12
forum: Networking &amp; Wireless
---

### Post by theend66 on 2017-01-12
Hello all, I  have been googling and trying out so many methods now that i no longer know what im doing so here i am. I am running Ubuntu 14.04.5 LTS on a Dell Inspiron 14 5000 series. I am using Wicd as my network manager. I am able to connect to the internet through my ethernet cable but not through my wireless. It says "No wireless networks found." 


Network controller: Qualcomm Atheros Device

My wireless works on Kali so im assuming from that , that there is nothing wrong with the wireless card itself.  Please advise further.

```

dmesg|grep ath10k
[  330.445016] ath10k_pci 0000:02:00.0: pci irq msi-x interrupts 8 irq_mode 0 reset_mode 0
[  330.780392] ath10k_pci 0000:02:00.0: Direct firmware load for ath10k/cal-pci-0000:02:00.0.bin failed with error -2
[  331.061915] ath10k_pci 0000:02:00.0: failed to fetch board data for ath10k/QCA9377/hw1.0 from bus=pci,vendor=168c,device=0042,subsystem-vendor=1028,subsystem-device=1810/board-2.bin
[  332.887649] ath10k_pci 0000:02:00.0: qca9377 hw1.1 (0x05020001, 0x003821ff sub 1028:1810) fw WLAN.TF.1.0-00267-1 fwapi 5 bdapi 1 htt-ver 3.1 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features ignore-otp
[  332.887652] ath10k_pci 0000:02:00.0: debug 0 debugfs 1 tracing 1 dfs 0 testmode 0

```

```
sudo ifconfig -a
eth0      Link encap:Ethernet  HWaddr 18:db:f2:06:16:9f  
          inet addr:192.168.1.135  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::1adb:f2ff:fe06:169f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:46881 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36865 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:50952073 (50.9 MB)  TX bytes:3687496 (3.6 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:230 errors:0 dropped:0 overruns:0 frame:0
          TX packets:230 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:74609 (74.6 KB)  TX bytes:74609 (74.6 KB)

```

```
lspci
00:00.0 Host bridge: Intel Corporation Device 5904 (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Device 5916 (rev 02)
00:14.0 USB controller: Intel Corporation Device 9d2f (rev 21)
00:14.2 Signal processing controller: Intel Corporation Device 9d31 (rev 21)
00:15.0 Signal processing controller: Intel Corporation Device 9d60 (rev 21)
00:15.1 Signal processing controller: Intel Corporation Device 9d61 (rev 21)
00:16.0 Communication controller: Intel Corporation Device 9d3a (rev 21)
00:17.0 SATA controller: Intel Corporation Device 9d03 (rev 21)
00:1c.0 PCI bridge: Intel Corporation Device 9d10 (rev f1)
00:1c.4 PCI bridge: Intel Corporation Device 9d14 (rev f1)
00:1c.5 PCI bridge: Intel Corporation Device 9d15 (rev f1)
00:1f.0 ISA bridge: Intel Corporation Device 9d58 (rev 21)
00:1f.2 Memory controller: Intel Corporation Device 9d21 (rev 21)
00:1f.3 Audio device: Intel Corporation Device 9d71 (rev 21)
00:1f.4 SMBus: Intel Corporation Device 9d23 (rev 21)
01:00.0 Display controller: Advanced Micro Devices, Inc. [AMD/ATI] Topaz XT [Radeon R7 M260/M265] (rev ff)
**02:00.0 Network controller: Qualcomm Atheros Device 0042 (rev 31)**
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller (rev 07)
```

```
$ sudo ifup wlan0
Internet Systems Consortium DHCP Client 4.2.4
Copyright 2004-2012 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Cannot find device "wlan0"
Error getting hardware address for "wlan0": No such device
Failed to bring up wlan0.
```


```
 iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

```

```
ls -1 /etc/modprobe.d/
alsa-base.conf
ath10k_core.conf
blacklist-ath_pci.conf
blacklist.conf
blacklist-firewire.conf
blacklist-framebuffer.conf
blacklist-modem.conf
blacklist-oss.conf
blacklist-rare-network.conf
blacklist-watchdog.conf
dkms.conf
fbdev-blacklist.conf
iwlwifi.conf
mlx4.conf
vmwgfx-fbdev.conf


```

```
lspci  | grep Network
02:00.0 Network controller: Qualcomm Atheros Device 0042 (rev 31)

```

```
sudo ifconfig wlan0
wlan0: error fetching interface information: Device not found
```

Your advise would be greatly appreciated. Thank you for your time!!!

---

### Post by praseodym on 2017-01-12
Install the firmware from 16.10 and reboot:

[http://de.archive.ubuntu.com/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.161_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.161_all.deb)

---

### Post by theend66 on 2017-01-12
Hi there, Thank you for your response but it does not work. 

 sudo dpkg -i linux-firmware_1.161_all.deb
[sudo] password for theend: 
(Reading database ... 219690 files and directories currently installed.)
Preparing to unpack linux-firmware_1.161_all.deb ...
Unpacking linux-firmware (1.161) over (1.127.23) ...
Setting up linux-firmware (1.161) ...

rebooted

---

### Post by theend66 on 2017-01-12
Solved with Ndiswrapper.

---


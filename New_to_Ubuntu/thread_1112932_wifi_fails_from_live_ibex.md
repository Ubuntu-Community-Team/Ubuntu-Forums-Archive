---
title: "wifi fails from live ibex"
date: 2009-04-01
forum: New to Ubuntu
---

### Post by nnjond on 2009-04-01
Hi, Can anyone help me?
Network Connections/Wireless displays nothing while I'm using the live CD and i have no connection.

---

### Post by skymera on 2009-04-01
Can you post the output of

```
 iwconfig 
```

Is it USB or PCI wireless?

---

### Post by ibuclaw on 2009-04-01
And the output from
```
lspci | grep -i net
```
and
```
lsusb
```
Would help us identify just what card you are using to connect.

If possible, for the moment, you may have to connect via Ethernet cable while we help you get setup.

Regards
Iain

---

### Post by nnjond on 2009-04-01
Thanks for your interest. My wifi is internal.

ubuntu@ubuntu:~$ iwconfig 
lo        no wireless extensions. 

eth0      no wireless extensions. 

pan0      no wireless extensions. 

ubuntu@ubuntu:~$ lspci 
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07) 
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07) 
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07) 
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03) 
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03) 
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03) 
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03) 
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03) 
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03) 
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03) 
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03) 
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03) 
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03) 
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03) 
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93) 
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03) 
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03) 
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03) 
00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03) 
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02) 
ubuntu@ubuntu:~$


                                                                    
To run a command as administrator (user "root"), use "sudo <command>". 
See "man sudo_root" for details. 

ubuntu@ubuntu:~$ lsusb 
Bus 008 Device 003: ID 058f:6387 Alcor Micro Corp. Transcend JetFlash Flash Drive 
Bus 008 Device 002: ID 0bda:8198 Realtek Semiconductor Corp. 
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ lspci | grep -i net 
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02) 
ubuntu@ubuntu:~$

---

### Post by ibuclaw on 2009-04-01
> **nnjond said:**
> ubuntu@ubuntu:~$ lspci | grep -i net 
**02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02) **


lspci doesn't report that a wireless card has been detected on your machine. !

Try a more deep-rooted approach
```
sudo lshw -C network
```
Also, most laptops these days have a wifi switch which allows you to enable/disable the device. Ensure that it is turned on, if available, before we overlook the obvious.

Regards
Iain

---

### Post by nnjond on 2009-04-01
The pc wifi works fine from installed ibex.


ubuntu@ubuntu:~$ sudo lshw -C network 
  *-network               
       description: Ethernet interface 
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller 
       vendor: Realtek Semiconductor Co., Ltd. 
       physical id: 0 
       bus info: pci@0000:02:00.0 
       logical name: eth0 
       version: 02 
       serial: 00:1e:33:6b:c2:9d 
       capacity: 1GB/s 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no module=r8169 multicast=yes port=twisted pair 
  *-network DISABLED 
       description: Ethernet interface 
       physical id: 1 
       logical name: pan0 
       serial: 9a:c6:f1:08:fe:0f 
       capabilities: ethernet physical 
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes 
ubuntu@ubuntu:~$ iwconfig

---


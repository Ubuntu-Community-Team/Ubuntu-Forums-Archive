---
title: "lg express p1 laptop - unable to turn on wireless (fn + 6)"
date: 2007-11-10
forum: Networking &amp; Wireless
---

### Post by cyberb on 2007-11-10
I have LG P1 Express Dual laptop and I cannot turn on wireless. I know that there is a fn + f6 combination that turn it on, but it works only under windows.

Under linux fn+f6 does not send any code, I tried all 3 methods from this post , but no signal from fn+f6. Other but not all fn keys send signals, for example fn+f9 sends mute code, fn+up/fn+down send brightness +/-.

Here is my dmesg:
------------------------ 
[   14.372000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.2.2mp.ubuntu1
[   14.372000] ipw3945: Copyright(c) 2003-2006 Intel Corporation
[   14.372000] ipw3945: Detected Intel PRO/Wireless 3945BG Network Connection
[   16.264000] ipw3945: Radio Frequency Kill Switch is On:
[   16.264000] Kill switch must be turned off for wireless networking to work.
------------------------


sudo lshw -C network
------------------------
  *-network
       description: Ethernet interface
       product: ET-131x PCI-E Ethernet Controller
       vendor: Agere Systems
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 02
       serial: 00:e0:91:15:02:08
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=et131x ip=66.171.122.43 latency=0 module=et131x multicast=yes
  *-network
       description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=ipw3945 latency=0 module=ipw3945
--------------------------

cat /sys/bus/pci/drivers/ipw3945/0000\:05\:00.0/rf_kill
2
echo 0 /sys/bus/pci/drivers/ipw3945/0000\:05\:00.0/rf_kill
cat /sys/bus/pci/drivers/ipw3945/0000\:05\:00.0/rf_kill
2
echo 1 /sys/bus/pci/drivers/ipw3945/0000\:05\:00.0/rf_kill
cat /sys/bus/pci/drivers/ipw3945/0000\:05\:00.0/rf_kill
3

# sudo dmidecode -s system-manufacturer
LG Electronics
# sudo dmidecode -s system-product-name
P1-KP55R1

# uname -a
Linux bob-desktop 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux

I hope anyone can help me.

---

### Post by Lambert on 2007-11-10
Try this.

```

sudo modprobe -r ipw3945

sudo modprobe ipw3945 disable=0

```

---


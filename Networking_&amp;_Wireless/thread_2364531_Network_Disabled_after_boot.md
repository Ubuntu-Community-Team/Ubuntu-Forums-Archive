---
title: "Network Disabled after boot"
date: 2017-06-24
forum: Networking &amp; Wireless
---

### Post by arindam1997007 on 2017-06-24
I'm a new Ubuntu user and have been using it just for the past 2 days. I saw that my wifi strength is much superior in windows than in Ubuntu. So, I thought of installing the wireless driver in Ubuntu.
I am having a problem that my network is disabled after boot. I'm currently running dual boot with Windows 8.1.
Here's the output of ```
sudo lshw -C network
``` :
```
  *-network
       description: Ethernet interface
       product: RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: enp8s0
       version: 07
       serial: 38:63:bb:72:97:97
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8106e-1_0.0.1 06/29/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:41 ioport:4000(size=256) memory:b5600000-b5600fff memory:b5400000-b5403fff
  *-network DISABLED
       description: Wireless interface
       product: RT3290 Wireless 802.11n 1T/1R PCIe
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:0a:00.0
       logical name: eno1
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=RALINK WLAN latency=0 multicast=yes wireless=Ralink STA
       resources: irq:16 memory:b5510000-b551ffff
```[HR][/HR]
 After I boot, I need to run these 2 commands: 
```
sudo ifconfig eno1 up
```
```
sudo service network-manager restart 
```
It's really frustrating, that I need to run these 2 commands, everytime I boot my laptop. It started happening after I installed the rt3290 drivers as mentioned here [https://askubuntu.com/a/593018/692756](https://askubuntu.com/a/593018/692756)

[HR][/HR]After the commands, here's the output of ```
sudo lshw -C network
``` :
```
  *-network
       description: Ethernet interface
       product: RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: enp8s0
       version: 07
       serial: 38:63:bb:72:97:97
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8106e-1_0.0.1 06/29/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:41 ioport:4000(size=256) memory:b5600000-b5600fff memory:b5400000-b5403fff
  *-network
       description: Wireless interface
       product: RT3290 Wireless 802.11n 1T/1R PCIe
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:0a:00.0
       logical name: eno1
       version: 00
       serial: c0:38:96:6e:ae:d7
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=RALINK WLAN ip=192.168.225.110 latency=0 multicast=yes wireless=Ralink STA
       resources: irq:16 memory:b5510000-b551ffff
```

---

### Post by praseodym on 2017-06-24
Try this driver:
```

sudo apt-get install linux-headers-$(uname -r) linux-headers-generic build-essential dkms
wget https://media-cdn.ubuntu-de.org/forum/attachments/06/23/5641297-RT3290_u16_v3.tar.gz
tar xvf RT3290_u16_v3.tar.gz
cd RT3290_u16
tar xvf src.tar.gz
./compile.sh
sudo ./install.sh
sudo cp /firmware/rt3290.bin /lib/firmware 
echo "blacklist rt2800pci" | sudo tee -a /etc/modprobe.d/blacklist-rt2800pci.conf  
```
Reboot

---

### Post by arindam1997007 on 2017-06-24
I did all of that and rebooted, but the problem still persists. I had to do the same process to get my wifi started.

---


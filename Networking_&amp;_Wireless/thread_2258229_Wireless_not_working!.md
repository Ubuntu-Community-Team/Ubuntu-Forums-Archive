---
title: "Wireless not working!"
date: 2014-12-25
forum: Networking &amp; Wireless
---

### Post by bhaskar6 on 2014-12-25
Hi, I am new to linux and ubuntu. I installed ubuntu but some reason wireless not working. My laptop is dell inspiron and i get blow output for sudo lshw -C network. I am not sure whether my wireless card working or not.

Inspiron-1545:~$ sudo lshw -C network
  *-network               
       description: Network controller
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:f69fc000-f69fffff
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 13
       serial: 00:23:ae:1a:61:97
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.30 duplex=full ip=192.168.2.8 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:44 memory:f68fc000-f68fffff ioport:de00(size=256)
swetha@swetha-Inspiron-1545:~$ sudo iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

---

### Post by bhaskar6 on 2014-12-25
attached the wireless-info.txt from below command output.
 wget -N -t 5 -T 10 [http://dl.dropbox.com/u/57264241/wireless_script](http://dl.dropbox.com/u/57264241/wireless_script) && chmod +x wireless_script && ./wireless_script

---

### Post by binchunsu on 2014-12-25
I am also using Dell Inspiron and when I first installed Ubuntu, the wireless was also not working. I fixed it by pluging in the ethernet cable, running this command in the terminal and rebooting: "sudo apt-get install firmware-b43-installer". I hope this helps.

---

### Post by bhaskar6 on 2014-12-27
Thank you for your reply. I did install and how do i check wireless is on ?

---

### Post by praseodym on 2014-12-27
Hi,

you need the firmware for the low-power chipset (LP-PHY):
```

wget http://media.cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz 
sudo tar xvf 2480236-Broadcom_Firmware.tar.gz -C /lib/firmware/ 
```

---


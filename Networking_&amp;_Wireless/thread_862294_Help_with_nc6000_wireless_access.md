---
title: "Help with nc6000 wireless access"
date: 2008-07-17
forum: Networking &amp; Wireless
---

### Post by noobasks on 2008-07-17
Hi, I am a noob Ubuntu user. I recently installed Ubuntu 8.04 on HP/Compaq nc6000 laptop. This laptop does not contain the mini-PCI & am using a Cisco aironet 350 wireless lan adapter for wireless access.

I have difficulty with getting the Network settings to show a wireless icon. I re-installed Ubuntu with the Cisco adapter hoping that the wireless icon would show up - it did not. I tried googling up to see if anyone else faced a similar problem and following steps on page [http://ubuntuforums.org/printthread.php?t=334419&pp=75](http://ubuntuforums.org/printthread.php?t=334419&pp=75)
for guidance. 

Here is thecode from the command prompts entered. I would appreciate if you could help me out.

Thank you.


ubuntu@ubuntu-laptop:~$ sudo lshw -C network
  *-network               
       description: Cisco Systems
       physical id: 0
       version: 350 Series Wireless LAN Adapter
       slot: Socket 0
       resources: irq:3
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5705M_2 Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: e
       bus info: pci@0000:02:0e.0
       logical name: eth0
       version: 03
       serial: 00:12:79:c1:88:a8
       capacity: 1GB/s
       width: 64 bits
       clock: 66MHz
       capabilities: pm vpd msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.86 firmware=5705-v3.14 latency=64 link=no mingnt=64 module=tg3 multicast=yes port=twisted pair


ubuntu@ubuntu-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.


ubuntu@ubuntu-laptop:~$ sudo lsmod |grep airo
airo_cs                 7168  2 
airo                   73884  1 airo_cs
pcmcia                 40876  1 airo_cs
pcmcia_core            40596  4 airo_cs,pcmcia,yenta_socket,rsrc_nonstatic


ubuntu@ubuntu-laptop:~$ sudo iwlist eth1 scan
eth1      Interface doesn't support scanning.


ubuntu@ubuntu-laptop:~$ sudo dhclient eth1
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device

---

### Post by noobasks on 2008-07-17
Can anyone help me :(

---


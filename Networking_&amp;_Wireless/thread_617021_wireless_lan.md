---
title: "wireless lan"
date: 2007-11-18
forum: Networking &amp; Wireless
---

### Post by jvillan555 on 2007-11-18
I am connected through a wire connection but my ultimate goal is to  connect thru a wireless  connection, I have  tried to use methods that have been posted here but to no avail. i still am connected thru a wire connection. 
jaime@jaime-desktop:~$ sudo aptitude install wpasupplicant
[sudo] password for jaime:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
jaime@jaime-desktop:~$ sudo ifconfig <interface> down
bash: interface: No such file or directory
jaime@jaime-desktop:~$ sudo dhclient -r <interface>
bash: syntax error near unexpected token `newline'
jaime@jaime-desktop:~$ sudo wpa_supplicant -w -D<****see footer below***> -i<interface> -c/etc/wpa_supplicant.conf -dd 
bash: ****see: No such file or directory
jaime@jaime-desktop:~$ sudo ifconfig <interface> up
bash: interface: No such file or directory
jaime@jaime-desktop:~$ sudo iwconfig <interface> mode Managed
bash: interface: No such file or directory
jaime@jaime-desktop:~$ sudo dhclient <interface>

---

### Post by jvillan555 on 2007-11-18
jaime@jaime-desktop:~$ lspci -nn | grep Network
01:04.0 Network controller [0280]: Intersil Corporation Prism 2.5 Wavelan chipset [1260:3873] (rev 01)
jaime@jaime-desktop:~$ lshw -C network | grep driver | sed 's/ /\n/g' | grep driver=
WARNING: you should run this program as super-user.
driver=hostap             
driver=b44
jaime@jaime-desktop:~$

---

### Post by jvillan555 on 2007-11-18
i have also tried these commands but still to no avail....please help///////



jaime@jaime-desktop:~$ lspci -nn | grep Network
01:04.0 Network controller [0280]: Intersil Corporation Prism 2.5 Wavelan chipset [1260:3873] (rev 01)
jaime@jaime-desktop:~$ lshw -C network | grep driver | sed 's/ /\n/g' | grep driver=
WARNING: you should run this program as super-user.
driver=hostap             
driver=b44
jaime@jaime-desktop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0 DISABLED    
       description: Wireless interface
       product: Prism 2.5 Wavelan chipset
       vendor: Intersil Corporation
       physical id: 4
       bus info: pci@0000:01:04.0
       logical name: wifi0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical wireless ethernet physical
       configuration: broadcast=yes driver=hostap driverversion=0.4.4-kernel firmware=0.0.0 latency=64 module=hostap_pci multicast=yes wireless=IEEE 802.11-DS
  *-network:1
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 9
       bus info: pci@0000:01:09.0
       logical name: eth0
       version: 01
       serial: 00:0f:1f:47:51:b4
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=1.01 ip=192.168.0.150 latency=64 module=b44 multicast=yes
jaime@jaime-desktop:~$

---


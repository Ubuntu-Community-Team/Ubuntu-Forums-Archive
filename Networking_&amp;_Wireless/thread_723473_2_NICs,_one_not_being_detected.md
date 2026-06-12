---
title: "2 NICs, one not being detected"
date: 2008-03-13
forum: Networking &amp; Wireless
---

### Post by ubf4abhinav on 2008-03-13
Hi,
    I have a small network of 3 computers, one of them having 2 NICs. With Windows XP running on the comp with two NICs everything runs fine and we can connect to our ISP and share internet connection with remaining comps. The configuration for server machine with Windows XP is:

   NIC for ISP-> IP addr = 10.23.24.65, subnet mask = 255.255.255.0, gateway addr = 10.23.24.1
   NIC for local network: IP addr = 192.168.0.1 subnet = 255.255.255.0
         Both are Realtek 8139 NICs

    However, when I switch to Ubuntu on the server machine(2 NICs), Ubuntu does not show the second NIC in Administration->Network, it shows only one NIC in ifconfig output. However, in Preferences->Hardware Information it shows both NICs.

    Moreover, when I let the NIC that is being detected and displayed, have its IP address assigned through DHCP, it takes an address of 192.168.0.238 and its connected to Internet while other 2 comps don't have valid IP addresses (and no Internet).

     Kindly let me know how to get Ubuntu to detect and activate the 2nd NIC and what could be the problem. Thanks in advance.

---

### Post by Iowan on 2008-03-13
Please post results of **ifconfig** and contents of **/etc/network/interfaces** file.[Here]("http://ubuntuforums.org/showthread.php?t=713874"  ) is a thread about what you want to do.

---

### Post by ubf4abhinav on 2008-03-22
Hi Iowan,
               Thanks for your reply. We lost Internet connectivity for some time so couldn't reply to your query. Here are the outputs of ifconfig and interfaces file .

_**ifconfig**_

eth0      Link encap:Ethernet  HWaddr 00:16:76:66:CD:BD  
          inet addr:192.168.0.238  Bcast:192.168.0.255  Mask:255.255.255.0 
          inet6 addr: fe80::216:76ff:fe66:cdbd/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:1769 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:30 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:110665 (108.0 KiB)  TX bytes:5117 (4.9 KiB) 
          Interrupt:21 Base address:0xa100 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b) 

_**/etc/network/interfaces**_

auto lo 
iface lo inet loopback 

auto eth0 
iface eth0 inet dhcp 
address 192.168.0.1 
netmask 255.255.255.0 

auto eth1 
iface eth1 inet dhcp 

auto eth2 
iface eth2 inet dhcp 

auto ath0 
iface ath0 inet dhcp 

auto wlan0 
iface wlan0 inet dhcp

The link you gave didn't work though. Waiting eagerly for your reply. Thanks.

---


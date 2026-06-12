---
title: "Breezy Static IP and Ubuntu-Windows PC-to-PC connection"
date: 2006-08-07
forum: Networking &amp; Wireless
---

### Post by prakash_prabhu on 2006-08-07
Hi,

I recently installed the Breezy version of Ubuntu  ( that was wonderfully shipped on CD by request ) on my PC at home. I have configured my PC for dual boot with the other OS being Win XP. 

I also have a DELL laptop which has (only) Windows 2000 installed on it. Since I can only use my laptop at work ( where i can access the net ), i would download most of the stuff on laptop and later would want to move it to the PC.

I tried to setup a data ( network ) cable sort of connection between the Win 2000 on the laptop and Ubuntu Breezy on the PC. I set the IP addresses of both the machines to Static IP as follows :

1. PC : ( Ubuntu -- using the Networking option in the Administration Menu on the Task Bar)
  
        Interface : eth0
	IP Address : 192.168.1.5
        Subnet Mask : 255.255.255.0
      Remaining Gateway and DNS server entries were left blank.

2. Laptop : ( Win 2000 -- using the TCP/IP properties of My Network Places' Properties )

	IP Address : 192.168.1.6
        Subnet Mask : 255.255.255.0
      Again Gateway and DNS server entries were left blank.


However when i try to ping the Win 2000 box from the Ubuntu machine, i get a destination Host unreachable error. The irony is that I have tried the same pinging of the Win 2000 machine from Win XP (on the PC), then i get a response and also am able to share folders and files. so i dont think there is any problem with the cable/NIC. How do i get to do the same from Ubuntu ? Also I would like to know how to connect to the internet from Ubuntu ( Broadban - rite now to connect from Win XP, i just set the option in the Control Panel to 'Obtain IP address automatically' and 'Obtain DNS server automatically and it works ).

Any pointers would be highly appreciated !

Thanks :-) !

---

### Post by bensexson on 2006-08-07
Please post the output of route -n from the Ubuntu box.

---

### Post by prakash_prabhu on 2006-08-07
Thanks for the reply. Here are the outputs of ifconfig and route -n from the Ubuntu machine :

root@blade:/boot/grub# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:2F:35:0A:D7
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:2fff:fe35:ad7/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:22 Base address:0xc000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:963 errors:0 dropped:0 overruns:0 frame:0
          TX packets:963 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:86085 (84.0 KiB)  TX bytes:86085 (84.0 KiB)

root@blade:/boot/grub# route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0

---


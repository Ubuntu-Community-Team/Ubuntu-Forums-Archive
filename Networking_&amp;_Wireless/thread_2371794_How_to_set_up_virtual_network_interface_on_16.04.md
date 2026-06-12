---
title: "How to set up virtual network interface on 16.04"
date: 2017-09-18
forum: Networking &amp; Wireless
---

### Post by Alex_Filonov on 2017-09-18
Can't set up virtual interface on my 16.04 server. Previously I just set up interface like eth0:1 in /etc/network/interfaces. Now, with "predictable" udev interface names, it doesn't work:

Content of /etc/network/interfaces:

 auto enp0s25#iface enp0s25 inet dhcp
iface enp0s25 inet static
address 192.168.111.3
netmask 255.255.255.0


auto enp0s25:1
iface enp0s25:1 inet static
address 192.168.111.3
netmast 255.255.255.0

========================================
ifup enp0s25
ifconfig enp0s25
enp0s25   Link encap:Ethernet  HWaddr 00:1a:a0:93:50:71  
          inet addr:192.168.111.3  Bcast:192.168.111.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Memory:fdfc0000-fdfe0000 

ifup enp0s25:1
ifup: interface enp0s25:1 already configured
ifconfig enp0s25:1
enp0s25:1 Link encap:Ethernet  HWaddr 00:1a:a0:93:50:71  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:20 Memory:fdfc0000-fdfe0000

---

### Post by SeijiSensei on 2017-09-19
> auto enp0s25#iface enp0s25 inet dhcp
iface enp0s25 inet static
address 192.168.111.3
netmask 255.255.255.0


auto enp0s25:1
iface enp0s25:1 inet static
address 192.168.111.3
netmast 255.255.255.0

What happens if you give them different addresses (within the 192.168.111.0/24 subnet)?  I don't understand the point of assigning the same address to the virtual interface.  Usually such interfaces are used to let the computer have a number of different IPs assigned to the same adapter.  I use virtual interfaces for that purpose, but it don't create them in /etc/network/interfaces.  Instead I add lines to /etc/rc.local like this
```
ifconfig enp0s25:2 192.168.111.33 netmask 255.255.255.0
```

I notice that the stanza for the virtual adapter has the line "**netmast** 255.255.255.0" rather than "netmask 255.255.255.0".  Is that error actually in the interfaces file?

---

### Post by Alex_Filonov on 2017-09-19
Actually, you don't need format <iface>:n anymore. Found answer here:
[https://ubuntuforums.org/showthread.php?t=2368932&highlight=virtual+network+interface](https://ubuntuforums.org/showthread.php?t=2368932&highlight=virtual+network+interface)

Second entry should be:

iface enp0s25 inet static
address 192.168.111.1
netmask 255.255.255.0

---


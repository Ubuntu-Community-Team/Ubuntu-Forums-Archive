---
title: "Possible bridge network interface problem -- with Samba troubles"
date: 2015-12-09
forum: Networking &amp; Wireless
---

### Post by cjsmall on 2015-12-09
Xubuntu 15.10 with all latest updates.

I was setting up a KVM/QEMU virtual machine to run Windows 8.1 Pro and the VM is now running properly with the hosted OS.  I'm running a LAN behind a gateway router, using static IP addresses and the LAN consists of Ubuntu 15.10, Solaris 10, Win-XP, Win7 and Win8.1 Pro systems along with various devices.

Prior to setting up the VM, I created a bridge network interface in accordance with the KVM documentation.  My system has two Ethernet interfaces which were configured as eth0 (204.107.91.3) and eth1 (204.107.91.4).  I decided to leave eth0 as the primary Ubuntu system interface use the eth1 interface for the bridge.  I edited the **/etc/network/interfaces** file as follows:

```
auto eth1
    iface eth1 inet manual

auto br0
    iface br0 inet static
    address      204.107.91.100
    network      204.107.91.0
    netmask      255.255.255.0
    broadcast    204.107.91.255
    bridge_ports eth1
    bridge_stp   off
```

And here is the current output from **ifconfig**:

```
br0       Link encap:Ethernet  HWaddr e0:3f:49:e8:1a:32  
          inet addr:204.107.91.100  Bcast:204.107.91.255  Mask:255.255.255.0
          inet6 addr: fe80::e23f:49ff:fee8:1a32/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3339 errors:0 dropped:0 overruns:0 frame:0
          TX packets:297 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:319152 (319.1 KB)  TX bytes:28977 (28.9 KB)

eth0      Link encap:Ethernet  HWaddr e0:3f:49:e8:1a:31  
          inet addr:204.107.91.3  Bcast:204.107.91.255  Mask:255.255.255.0
          inet6 addr: fe80::e23f:49ff:fee8:1a31/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:89957 errors:0 dropped:0 overruns:0 frame:0
          TX packets:61639 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:84983929 (84.9 MB)  TX bytes:18427776 (18.4 MB)
          Interrupt:16 Memory:b3f00000-b3f20000 

eth1      Link encap:Ethernet  HWaddr e0:3f:49:e8:1a:32  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:30517 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17942 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:27351082 (27.3 MB)  TX bytes:2550884 (2.5 MB)
          Interrupt:17 Memory:b3e00000-b3e20000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:248611 errors:0 dropped:0 overruns:0 frame:0
          TX packets:248611 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:96507274 (96.5 MB)  TX bytes:96507274 (96.5 MB)

virbr0    Link encap:Ethernet  HWaddr 52:54:00:51:05:9f  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vnet0     Link encap:Ethernet  HWaddr fe:54:00:02:49:76  
          inet6 addr: fe80::fc54:ff:fe02:4976/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:17645 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28546 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:2450127 (2.4 MB)  TX bytes:26917908 (26.9 MB)
```

The problem:

All machines on the network can ping each other and themselves except for the Windows 8.1 Pro VM system which can ping everything except the Ubuntu eth0 (204.107.91.3) or the br0 (204.107.91.100).  In both cases, the ping times out.  All I can think is that there is something wrong with the bridge interface configuration that is causing this problem.  Just to be clear, all other machines, including the Ubuntu system can ping these two interfaces.  It's only the Win8 system that exhibits this problem.

Despite this, the Win8 VM system connects to the SMB network shares on itself as well as the Solaris, Win-XP and Win7 systems, but it is **not** able to connect to the SMB shares on its Ubuntu host machine.  Neither can the other machines on the network access the SMB shares on the Ubuntu system.   However, the Ubuntu system connects to the Solaris Samba and Win-XP systems, but **not** to the Win7 or Win8 shares nor to its own shares.  So clearly there is a Samba misconfiguration here on the Ubuntu system, but I don't think it can be successfully diagnosed until the ping problem is corrected.

Finally, **testparm** reports no problems on the Ubuntu smb.conf file, but, like the other systems, **smbclient** cannot connect to the Ubuntu shares.

Any suggestions?  Thanks.

---

### Post by cjsmall on 2015-12-14
I got no responses to my query.  However I did solve the network ping problem which turned out to have two factors, neither of which was related to the bridge network interface implementation.

1: There was a typo in the /etc/hosts file caused the IP address to be misidentified for one of the systems.

2: After trial and error work, it looks like there is either a line length limit or a token count limit on entries in the C:\\Windows\System32\drivers\etc\host file on Windows systems.  Once I deleted some of the hostname aliases for the Linux system, the network connections between the two machines worked properly.

The samba problem remain and can now be tackled -- but that's another issue.

---


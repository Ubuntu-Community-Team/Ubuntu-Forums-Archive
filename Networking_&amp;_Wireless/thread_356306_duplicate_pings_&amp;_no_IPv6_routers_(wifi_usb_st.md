---
title: "duplicate pings &amp; no IPv6 routers (wifi usb stick ZD1211B)"
date: 2007-02-08
forum: Networking &amp; Wireless
---

### Post by HilliBilly on 2007-02-08
hi,

i do not understand why i have duplicated pings when using rate of 11M instead of 54M as rate for my pheenet wifi usb stick?

could you help me please? i have edgy, gnome, 2.6.17-10-386 kernel on a sharp notebook.

second question: what do i have to do to avoid this "eth1: no IPv6 routers present" error message?

xyz@xyz-ubuntu-laptop:~$ **sudo iwconfig eth1 rate 11M**
xyz@xyz-ubuntu-laptop:~$ **ping [www.ubuntu.com](www.ubuntu.com)**
PING [www.ubuntu.com](www.ubuntu.com) (82.211.81.166) 56(84) bytes of data.
64 bytes from signey.ubuntu.com (82.211.81.166): icmp_seq=**1** ttl=46 time=58.9 ms
64 bytes from signey.ubuntu.com (82.211.81.166): icmp_seq=**1** ttl=46 time=60.8 ms **(DUP!)**
64 bytes from signey.ubuntu.com (82.211.81.166): icmp_seq=**1** ttl=46 time=63.8 ms **(DUP!)**
64 bytes from signey.ubuntu.com (82.211.81.166): icmp_seq=2 ttl=46 time=63.4 ms
64 bytes from signey.ubuntu.com (82.211.81.166): icmp_seq=2 ttl=46 time=73.4 ms (DUP!)
64 bytes from signey.ubuntu.com (82.211.81.166): icmp_seq=2 ttl=46 time=78.4 ms (DUP!)
64 bytes from signey.ubuntu.com (82.211.81.166): icmp_seq=3 ttl=46 time=58.2 ms
64 bytes from signey.ubuntu.com (82.211.81.166): icmp_seq=3 ttl=46 time=62.2 ms (DUP!)
64 bytes from signey.ubuntu.com (82.211.81.166): icmp_seq=3 ttl=46 time=67.1 ms (DUP!)
64 bytes from signey.ubuntu.com (82.211.81.166): icmp_seq=4 ttl=46 time=57.9 ms
64 bytes from signey.ubuntu.com (82.211.81.166): icmp_seq=4 ttl=46 time=59.9 ms (DUP!)
64 bytes from signey.ubuntu.com (82.211.81.166): icmp_seq=4 ttl=46 time=62.9 ms (DUP!)
64 bytes from signey.ubuntu.com (82.211.81.166): icmp_seq=5 ttl=46 time=58.7 ms
64 bytes from signey.ubuntu.com (82.211.81.166): icmp_seq=5 ttl=46 time=61.7 ms (DUP!)
64 bytes from signey.ubuntu.com (82.211.81.166): icmp_seq=5 ttl=46 time=65.7 ms (DUP!)

--- [www.ubuntu.com](www.ubuntu.com) ping statistics ---
5 packets transmitted, 5 received, +10 duplicates, 0% packet loss, time 4000ms
rtt min/avg/max/mdev = 57.974/63.575/78.411/5.576 ms

xyz@xyz-ubuntu-laptop:~$ sudo iwconfig eth1 rate **54M**
xyz@xyz-ubuntu-laptop:~$ **ping [www.ubuntu.com](www.ubuntu.com)**
PING [www.ubuntu.com](www.ubuntu.com) (82.211.81.166) 56(84) bytes of data.
64 bytes from signey.ubuntu.com (82.211.81.166): icmp_seq=1 ttl=46 time=58.6 ms
64 bytes from signey.ubuntu.com (82.211.81.166): icmp_seq=2 ttl=46 time=58.7 ms
64 bytes from signey.ubuntu.com (82.211.81.166): icmp_seq=3 ttl=46 time=57.5 ms
64 bytes from signey.ubuntu.com (82.211.81.166): icmp_seq=4 ttl=46 time=58.2 ms
64 bytes from signey.ubuntu.com (82.211.81.166): icmp_seq=5 ttl=46 time=59.0 ms
64 bytes from signey.ubuntu.com (82.211.81.166): icmp_seq=6 ttl=46 time=57.8 ms
64 bytes from signey.ubuntu.com (82.211.81.166): icmp_seq=7 ttl=46 time=63.6 ms

--- [www.ubuntu.com](www.ubuntu.com) ping statistics ---
7 packets transmitted, 7 received, 0% packet loss, time 6000ms
rtt min/avg/max/mdev = 57.507/59.102/63.619/1.930 ms
xyz@xyz-ubuntu-laptop:~$ 

xyz@xyz-ubuntu-laptop:~$ **route -n**
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth1

xyz@xyz-ubuntu-laptop:~$ **iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

eth1      802.11g zd1211  ESSID:"USR9106"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:C0:49:D3:DA:6B   
          Bit Rate=54 Mb/s   
          Link Quality=64/100  Signal level=84/100  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

xyz@xyz-ubuntu-laptop:~$ 


xyz@xyz-ubuntu-laptop:~$ **ifconfig**
eth1      Link encap:Ethernet  HWaddr 00:1A:50:00:04:87  
          inet addr:192.168.1.16  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:50ff:fe00:487/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:17 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1656 (1.6 KiB)  TX bytes:1656 (1.6 KiB)


xyz@xyz-ubuntu-laptop:~$ [B]dmesg
[/B]
[17185367.480000] SoftMAC: Open Authentication completed with 00:c0:49:d3:da:6b
[17185367.504000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[17185378.240000] eth1: no IPv6 routers present
[17185441.564000] usb 1-1: USB disconnect, address 7
[17185441.564000] zd1211rw 1-1:1.0: error ioread32(CR_REG1): -22
[17185474.240000] usb 1-1: new full speed USB device using uhci_hcd and address 8
[17185474.408000] usb 1-1: configuration #1 chosen from 1 choice
[17185475.244000] zd1211rw 1-1:1.0: firmware version 4725
[17185475.308000] zd1211rw 1-1:1.0: zd1211b chip 0ace:1215 v4810 full 00-1a-50 AL2230_RF pa0 ---
[17185475.312000] zd1211rw 1-1:1.0: eth1
[17185477.116000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[17185517.716000] SoftMAC: Open Authentication completed with 00:c0:49:d3:da:6b
[17185517.740000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[17185528.144000] **eth1: no IPv6 routers present**


xyz@xyz-ubuntu-laptop:~$ **tail -f /var/log/messages**
11:53 xyz-ubuntu-laptop kernel: [17185441.564000] usb 1-1: USB disconnect, address 7
Feb  8 12:12:25 xyz-ubuntu-laptop kernel: [17185474.240000] usb 1-1: new full speed USB device using uhci_hcd and address 8
Feb  8 12:12:25 xyz-ubuntu-laptop kernel: [17185474.408000] usb 1-1: configuration #1 chosen from 1 choice
Feb  8 12:12:26 xyz-ubuntu-laptop kernel: [17185475.244000] zd1211rw 1-1:1.0: firmware version 4725
Feb  8 12:12:26 xyz-ubuntu-laptop kernel: [17185475.308000] zd1211rw 1-1:1.0: zd1211b chip 0ace:1215 v4810 full 00-1a-50 AL2230_RF pa0 ---
Feb  8 12:12:27 xyz-ubuntu-laptop kernel: [17185475.312000] zd1211rw 1-1:1.0: eth1
Feb  8 12:12:28 xyz-ubuntu-laptop kernel: [17185477.116000] ADDRCONF(NETDEV_UP): eth1: link is not ready
Feb  8 12:13:09 xyz-ubuntu-laptop kernel: [17185517.716000] SoftMAC: Open Authentication completed with 00:c0:49:d3:da:6b
Feb  8 12:13:09 xyz-ubuntu-laptop kernel: [17185517.740000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready

---


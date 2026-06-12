---
title: "MTU problems on Edgy"
date: 2007-01-19
forum: Networking &amp; Wireless
---

### Post by Uriel2006 on 2007-01-19
Hello all,

i'm facing one IP fragmentation problem on Edgy Edge.

I've an interface eth1 , that is one wireless one. (there is no problem with this, since it works both with ndiswrapper and with the native driver, i get DHCP address and i may use ssh)

Problem is when i try to do an scp or a ftp: any service using sized IP packet is givin problems.

So i tried to ping my router with different size of packets, and i get the following:

ping 10.101.13.1 -s 1389
PING 10.101.13.1 (10.101.13.1) 1389(1417) bytes of data.
--- 10.101.13.1 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2001ms

ping 10.101.13.1 -s 1388
PING 10.101.13.1 (10.101.13.1) 1388(1416) bytes of data.
1396 bytes from 10.101.13.1: icmp_seq=1 ttl=255 time=10.3 ms
1396 bytes from 10.101.13.1: icmp_seq=2 ttl=255 time=11.4 ms


As you see, the network interface is working: when packets are tiny, (less than 1416) i'm able to send and receive packets. So, my ssh is working, and so on. Problem is i get stalled whith other services.

Network adapter is broadcom 4318 , and the problem is the same both using ndiswrapper or the native driver for the edgy edge. I have all firmware already in place, using fwcutter, last version. 

I tried to change the mtu in the eth1 interface, and the problem was the same , i mean the size limit is 1416, even the eth1  mtu is 500. Perhaps i tried too using iwconfig to change the fragment size, and it was the same.

iwlist eth1 scan :
 Cell 02 - Address: XX:XX:XX:XX:XX:XX
                    ESSID:"XXXXXXX"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.472 GHz (Channel 13)
                    Quality:53/100  Signal level:-62 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0


ifconfig eth1:

eth1    Link encap:Ethernet  HWaddr 00:14:A5:29:EF:FE  
          inet addr:xx.xx.xx.xx  Bcast:xx.xx.xx.255  Mask:255.255.255.0
          inet6 addr: fe80::214:xxxx:xxxx:xxxx/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:962 errors:0 dropped:0 overruns:0 frame:0
          TX packets:352 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:129053 (126.0 KiB)  TX bytes:30242 (29.5 KiB)
          Interrupt:177 Memory:b0204000-b0206000 


anyone had the same problem or have any suggestion?

thanks in advance,

Uriel

---


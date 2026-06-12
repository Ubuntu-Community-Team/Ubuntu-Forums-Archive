---
title: "Wireless interface exists, can't connect"
date: 2006-10-02
forum: Networking &amp; Wireless
---

### Post by kernco on 2006-10-02
Here is my situation.  iwconfig outputs this:
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  IEEE 802.11g  Frequency:2.412 GHz  
          RTS thr:off   Fragment thr=2346 B   
          
wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          RTS thr:off   Fragment thr=2346 B   
          
sit0      no wireless extensions.

ifconfig is this:
eth0      Link encap:Ethernet  HWaddr 00:40:45:2A:B4:41  
          inet addr:192.168.0.142  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::240:45ff:fe2a:b441/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:551 errors:0 dropped:0 overruns:0 frame:0
          TX packets:365 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:420394 (410.5 KiB)  TX bytes:40417 (39.4 KiB)
          Interrupt:66 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:800 (800.0 b)  TX bytes:800 (800.0 b)

sit0      Link encap:IPv6-in-IPv4  
          inet6 addr: ::192.168.0.142/96 Scope:Compat
          inet6 addr: ::127.0.0.1/96 Scope:Unknown
          UP RUNNING NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:5 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:13:D3:76:CC:73  
          UP RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:216 (216.0 b)
          Base address:0xa000 

wmaster0  Link encap:UNSPEC  HWaddr 00-13-D3-76-CC-73-00-A0-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Base address:0xa000 

When I go to System->Administration->Networking, I see wlan0 and wmaster0, but they are "not configured".  I can click on either one and select "properties", and there is a check box for "enable this connection".  I click it and then click "ok", but it still says it is not configured.  If I go back to properties, I find the box unchecked again.  The ESSID dropdown menu is empty.  If I type something in there, the connection says that it is enabled, but I still can't access the internet.  I can't even select it in the network monitor panel applet.  I have installed the network-manager package, but that isn't able to use the wireless device either.

When Windows XP was installed, it could find the wireless network, and there is another computer in the room right now that is connected to it, so it is not a problem with not getting the wireless signal.

My wireless device is Ralink.  It is built in to my laptop, but some people on forums have said that they have the same laptop as me and it is a USB interface not a PCI interface.  Will that change anything?

Does anyone know how to get this working?

---

### Post by NoWhereMan on 2006-10-28
same here

---


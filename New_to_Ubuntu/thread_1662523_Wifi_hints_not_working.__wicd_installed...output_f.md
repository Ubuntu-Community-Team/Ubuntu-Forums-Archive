---
title: "Wifi hints not working.  wicd installed...output from terminal here."
date: 2011-01-08
forum: New to Ubuntu
---

### Post by philodice on 2011-01-08
wingbolt@wingbolt-Inspiron-910:~$ sudo ishw -C network; rfkill list; sudo iwlist scan | head -n 25
[sudo] password for wingbolt: 
sudo: ishw: command not found
0: compal-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: compal-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

dell mini 910  10.10
02:00.3 System peripheral: JMicron Technology Corp. MS Host Controller
03:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

I am posting to this forum using wired connection from the computer I am fixing.  :)

ifconfig
eth0      Link encap:Ethernet  HWaddr 00:21:70:d2:2d:e8  
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::221:70ff:fed2:2de8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2296 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1613 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1748660 (1.7 MB)  TX bytes:293665 (293.6 KB)
          Interrupt:43 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:28 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2096 (2.0 KB)  TX bytes:2096 (2.0 KB)

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0

---

### Post by philodice on 2011-01-08
ping -c 3 208.67.219.101
PING 208.67.219.101 (208.67.219.101) 56(84) bytes of data.

 ping -c 3 [www.opendns.com](www.opendns.com)
PING [www.opendns.com](www.opendns.com) (208.69.38.150) 56(84) bytes of data.
64 bytes from 208.69.38.150: icmp_req=1 ttl=58 time=36.2 ms
64 bytes from 208.69.38.150: icmp_req=2 ttl=58 time=57.2 ms
64 bytes from 208.69.38.150: icmp_req=3 ttl=58 time=33.9 ms

--- [www.opendns.com](www.opendns.com) ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 10174ms
rtt min/avg/max/mdev = 33.975/42.469/57.211/10.465 ms

I've gone through several online threads and I'm not getting it.  Sorry, I'm not doing well at the self taught Ubuntu kungfu.

---

### Post by nothingspecial on 2011-01-08
First try getting a wired connection and looking in System > Administration > Additional Drivers.

If that doesn`t help, try installing the b43-fwcutter package.

---


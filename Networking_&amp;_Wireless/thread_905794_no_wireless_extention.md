---
title: "no wireless extention"
date: 2008-08-30
forum: Networking &amp; Wireless
---

### Post by dsr4866 on 2008-08-30
I have been fighting with this usb wireless for days trying to get either linux driver or ndis to work. I have no wireless extention for lshw -C command, can anybody help me get this going???? here is the  if,iw,-c print   also the kwifi shows no access point and unavailable ip and freq. at 2.412 (1)  i assume thats cahnnel one and my router is on #6, scan for networks show my net but can't connect. I tried switching to wicd from net manager but that didn't help

dsr@dsr-desktop:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan1     IEEE 802.11g  ESSID:off/any  
          Mode:Auto  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

dsr@dsr-desktop:~$ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:01:29:74:7c:e1  
          inet addr:192.168.1.106  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::201:29ff:fe74:7ce1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:39 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2506 (2.4 KB)  TX bytes:5205 (5.0 KB)
          Interrupt:20 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2764 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2764 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:138200 (134.9 KB)  TX bytes:138200 (134.9 KB)

wlan1     Link encap:Ethernet  HWaddr 00:1d:6a:0c:82:8b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

dsr@dsr-desktop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:01:01.0
       logical name: eth0
       version: 10

---


---
title: "Can't bring up wlan0 : SIOCSIFFLAGS: Operation not permitted"
date: 2016-02-15
forum: Networking &amp; Wireless
---

### Post by mohamed26 on 2016-02-15
hi to you all
my wlan0 is down and when i run "ifconfig wlan0 up" i get "SIOCSIFFLAGS: Operation not permitted"

these are some reports you might need

adminn@ubuntu:~$ dmesg | tail 
[  541.460169] ssb: Core 3 found: PCI-E (cc 0x820, rev 0x05, vendor 0x4243)
[  541.524254] b43-phy3: Broadcom 4311 WLAN found (core revision 13)
[  541.568109] b43-phy3: Found PHY: Analog 4, Type 2 (G), Revision 9
[  541.592291] ssb: Sonics Silicon Backplane found on PCI device 0000:30:00.0
[  541.593202] ieee80211 phy3: Selected rate control algorithm 'minstrel_ht'
[  542.092067] usb 2-2: new full-speed USB device number 4 using ohci-pci
[  542.273822] usb 2-2: New USB device found, idVendor=03f0, idProduct=171d
[  542.273832] usb 2-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[  542.273839] usb 2-2: Product: HP Integrated Module
[  542.273846] usb 2-2: Manufacturer: Broadcom Corp
adminn@ubuntu:~$ Welcome to Ubuntu 14.04.3 LTS (GNU/Linux 3.13.0-77-generic x86_64)

 * Documentation:  [https://help.ubuntu.com/](https://help.ubuntu.com/)
Last login: Mon Feb 15 19:24:46 2016

------------------------------------------------

adminn@ubuntu:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1a:4b:70:34:00  
          inet addr:192.168.0.105  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:4bff:fe70:3400/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2510 errors:0 dropped:0 overruns:0 frame:0
          TX packets:653 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:390570 (390.5 KB)  TX bytes:109483 (109.4 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1a:73:9e:a5:dc  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

-----------------------------------

adminn@ubuntu:~$ iwlist scan 
eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Failed to read scan data : Network is down

---------------------

adminn@ubuntu:~$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on

thank you in advance

---

### Post by mohamed26 on 2016-02-15
never mind guys,i solved it,i have to put _**sudo **_in-front of _**ifconfig wlan0 up **_ to get the permission

---


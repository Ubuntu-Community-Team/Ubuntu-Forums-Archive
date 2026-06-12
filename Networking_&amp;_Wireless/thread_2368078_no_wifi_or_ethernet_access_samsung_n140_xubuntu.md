---
title: "no wifi or ethernet access samsung n140 xubuntu"
date: 2017-08-06
forum: Networking &amp; Wireless
---

### Post by gandhi2 on 2017-08-06
hi all! :)

ive recently installed xubuntu 16.04 to my samsung N140...... installation went fine.....

but after entering my internet password.... it will not connect.... also ethernet detected my network but will not connect either.... which is making this even more frustrating :( 

so I think i found some drivers for realtek "rtl8192e" (this is the correct hardware)  but i've no idea how to install them... or if this is even the right solution

any help would be appreciated

thank you

Gandhi 

this might help
```
gandhi@gandhi-mini-two:~$ rfkill list all
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: samsung-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
gandhi@gandhi-mini-two:~$ lspci -knn | grep Net -A2
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8192E/RTL8192SE Wireless LAN Controller [10ec:8192] (rev 01)
    Subsystem: Askey Computer Corp. RTL8192E/RTL8192SE Wireless LAN Controller [144f:7160]
    Kernel driver in use: rtl819xE
gandhi@gandhi-mini-two:~$ ifconfig && iwconfig && route -n 
enp2s0    Link encap:Ethernet  HWaddr 00:26:b6:79:1f:51  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:32 errors:0 dropped:0 overruns:0 frame:0
          TX packets:63 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3735 (3.7 KB)  TX bytes:10832 (10.8 KB)
          Interrupt:16 Memory:f89f8000-f89f8100 


enp3s0    Link encap:Ethernet  HWaddr 00:24:54:3b:6f:7e  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:5517 errors:0 dropped:2 overruns:0 frame:0
          TX packets:805 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:794207 (794.2 KB)  TX bytes:124998 (124.9 KB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:19286 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19286 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:1440789 (1.4 MB)  TX bytes:1440789 (1.4 MB)


lo        no wireless extensions.


enp2s0    802.11bgn  Nickname:"rtl8192E"
          Mode:Managed  Frequency=2.427 GHz  Access Point: Not-Associated   
          Bit Rate:135 Mb/s   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=10/100  Signal level=0 dBm  Noise level=-100 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


enp3s0    no wireless extensions.


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
gandhi@gandhi-mini-two:~$ ping -c 1 google.com
ping: unknown host google.com
gandhi@gandhi-mini-two:~$ 



```

---

### Post by johndough2 on 2017-08-08
Hi

I dont want to teach granny how to suck eggs, so please be tolerant.

Normally I would try and install 

and see if anything is offered, you can say no and read the list and try to be more specific.

sudo apt install wireless*
Reading package lists... Done
Building dependency tree
Reading state information... Done
Note, selecting 'wireless-tools' for glob 'wireless*'
Note, selecting 'wireless-crda' for glob 'wireless*'
Note, selecting 'wireless-regdb' for glob 'wireless*'
wireless-tools is already the newest version (30~pre9-8ubuntu1).
The following additional packages will be installed:
  crda iw libnl-3-200 libnl-genl-3-200
The following NEW packages will be installed
  crda iw libnl-3-200 libnl-genl-3-200 wireless-crda wireless-regdb
0 to upgrade, 6 to newly install, 0 to remove and 108 not to upgrade.
Need to get 199 kB of archives.
After this operation, 808 kB of additional disk space will be used.
Do you want to continue? [Y/n] n

AND then choose wireless-tools

---


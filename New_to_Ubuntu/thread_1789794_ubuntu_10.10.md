---
title: "ubuntu 10.10"
date: 2011-06-24
forum: New to Ubuntu
---

### Post by deepakpathak on 2011-06-24
i have installed ubuntu 10.10 in my vaio laptop, but the problem is ethernet is not being detected in this.Its working perfectly in windows7 but not here.
I have done ipv4 settings.
when i do ifconfig -a in terminal it displays l0 and wlan0 but not displays eth0 connection details.
but when i do 'lspci' in terminal it displays ethernet controller...
please help me out..
many thanks in advance:)

---

### Post by jtarin on 2011-06-24
Post your **ifconfig** so we can see....a picture is worth a thousand words. What kind of connection? Cable,DSL etc?

---

### Post by deepakpathak on 2011-06-24
the connection is using cable(lan cord).
here with ifconfig -a it displays:

> lo        Link encap:Local Loopback  
          
    inet addr:127.0.0.1  Mask:255.0.0.0
          
    inet6 addr: ::1/128 Scope:Host
          
    UP LOOPBACK RUNNING  MTU:16436  Metric:1
          
    RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          
    TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          
    collisions:0 txqueuelen:0 
          
    RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)


wlan0     Link encap:Ethernet  HWaddr 90:00:4e:ae:59:33  
          
    BROADCAST MULTICAST  MTU:1500  Metric:1
              
    RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          
    TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          
    collisions:0 txqueuelen:1000 
          
    RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)




* with lspic it shows:

> 
.

.

.

..

05:00.0 Ethernet controller [0200]: Atheros Communications Device [1969:1083] (rev c0)



* moreover the ethernet is not displayed in /etc/network/interfaces



* with
following command result is:
> 
deepak@deepak-VPCCB15FG:~$ sudo modprobe e1000

deepak@deepak-VPCCB15FG:~$ dmesg | grep e1000

[  353.005705] e1000: Intel(R) PRO/1000 Network Driver - version 7.3.21-k6-NAPI

[  353.005716] e1000: Copyright (c) 1999-2006 Intel Corporation.


---


---
title: "Network Access"
date: 2010-03-23
forum: New to Ubuntu
---

### Post by mikehem on 2010-03-23
Hi i am new to linux... i have 9.10 installed on vmware on a desktop in the company where i'm working... it shows the presence of eth0 and ifcofig:
 Link encap:Ethernet  HWaddr 00:0c:29:5f:20:29  
          inet6 addr: fe80::20c:29ff:fe5f:2029/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:22 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2831 (2.8 KB)  TX bytes:1494 (1.4 KB)
          Interrupt:19 Base address:0x2024
but im not able to connect to the internet can someone help pls..

Thanks

---

### Post by dineshs on 2010-03-23
Try the  notes under networking in this link
[http://ubuntuguide.org/wiki/Ubuntu:Karmic#Networking](http://ubuntuguide.org/wiki/Ubuntu:Karmic#Networking)

---

### Post by readycarpenter on 2010-03-23
virtual box creates a bridge from your physical Ethernet to the virtual eth0 that ubuntu sees inside virtual box, you need to configure this bridge in the virtual box settings

---

### Post by mikewhatever on 2010-03-23
> **readycarpenter said:**
> virtual box creates a bridge from your physical Ethernet to the virtual eth0 that ubuntu sees inside virtual box, you need to configure this bridge in the virtual box settings

As you may have noticed, the OP is not running Virtual Box.;)

---

### Post by errrata on 2010-03-23
Is it dangerous to publish your MAC Address?

---

### Post by readycarpenter on 2010-03-23
> Hi i am new to linux... i have 9.10 installed on vmware on a desktop in the company where i'm working... it shows the presence of eth0 and ifcofig:

vmware, virtual box they both have the same virtual bridge options in the settings

---


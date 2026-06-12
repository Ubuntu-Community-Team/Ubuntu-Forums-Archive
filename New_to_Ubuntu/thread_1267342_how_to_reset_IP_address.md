---
title: "how to reset IP address"
date: 2009-09-15
forum: New to Ubuntu
---

### Post by Prince Valiant on 2009-09-15
Hello,

Quick question:  how can I reset my laptop's IP address in Ubuntu 9.04?  My printer isn't working, and I think that will solve the problem (error 5012) based on other threads I've read.  Thanks in advance!

-Val

---

### Post by k33bz on 2009-09-15
Go here and read
[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch03_:_Linux_Networking]("http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch03_:_Linux_Networking")

---

### Post by halitech on 2009-09-15
what printer and how is it connected?

as far as resetting the IP, run
```
sudo dhclient (device)
```
change (device) to your network device

---

### Post by abdusamed on 2009-09-20
> **halitech said:**
> what printer and how is it connected?

as far as resetting the IP, run
```
sudo dhclient (device)
```change (device) to your network device


how do i figure out my device? :confused:

---

### Post by hambone79 on 2009-09-20
Just type this in a terminal window:
```
ifconfig
```

This will spit out a list of all the active network devices. The one you are looking for will most likely be something like "eth0".

---

### Post by abdusamed on 2009-09-21
> **hambone79 said:**
> Just type this in a terminal window:
```
ifconfig
```This will spit out a list of all the active network devices. The one you are looking for will most likely be something like "eth0".


:confused::confused: i get this

```
eth0      Link encap:Ethernet  HWaddr 00:1e:ec:3f:6f:e8  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:ecff:fe3f:6fe8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:137666 errors:0 dropped:0 overruns:0 frame:0
          TX packets:111926 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:176962415 (176.9 MB)  TX bytes:16466991 (16.4 MB)
          Interrupt:249 Base address:0x8000 

```device?? :icon_frown:

---

### Post by nandemonai on 2009-09-21
> **abdusamed said:**
> :confused::confused: i get this

```
eth0      Link encap:Ethernet  HWaddr 00:1e:ec:3f:6f:e8  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:ecff:fe3f:6fe8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:137666 errors:0 dropped:0 overruns:0 frame:0
          TX packets:111926 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:176962415 (176.9 MB)  TX bytes:16466991 (16.4 MB)
          Interrupt:249 Base address:0x8000 

```device?? :icon_frown:

```
sudo dhclient eth0
```

---

### Post by abdusamed on 2009-10-01
> **nandemonai said:**
> ```
sudo dhclient eth0
```

ooh yea..it was eth0.. like in windows ](*,)](*,)

:thankyou:

---


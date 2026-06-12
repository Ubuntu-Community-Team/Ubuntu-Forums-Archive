---
title: "Which network device to add"
date: 2009-03-11
forum: New to Ubuntu
---

### Post by RichardCL on 2009-03-11
Hi Forum,

I'm trying to install my Windows mobile 6 PDA to sync with Evolution.

Tutorial is here [http://ubuntuforums.org/showpost.php?p=6258719&postcount=6/]("http://ubuntuforums.org/showpost.php?p=6258719&postcount=6/")

Only problem is that I can't find how to remove exclude the synce device from the network manager.

```
/sbin/ifconfig -a | grep 80:00:60:0f:e8:00 | cut -d " " -f 1 
```returns nothing at all.

```
ifconfig -a
```

returns

> eth0      Link encap:Ethernet  HWaddr 00:22:68:3a:90:99  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:249 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:408 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:408 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:31360 (31.3 KB)  TX bytes:31360 (31.3 KB) 

pan0      Link encap:Ethernet  HWaddr b2:55:08:d2:42:94  
          BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 

ra0       Link encap:Ethernet  HWaddr 00:22:b0:57:cd:84  
          BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:17368 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:5647 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:8709223 (8.7 MB)  TX bytes:918441 (918.4 KB) 


```
synce-pls
```

returns

> synce-pls: Could not find configuration at path '(Default)'

The taskbar plugin shows > unable to contact VDCCM check that it is installed

---

### Post by Dedoimedo on 2009-03-11
Hello,

The grep you're doing is for a MAC address that is not listed under your devices. That MAC was what the guy who wrote the tutorial had.

Dedoimedo

---

### Post by RichardCL on 2009-03-12
> **Dedoimedo said:**
> Hello,

The grep you're doing is for a MAC address that is not listed under your devices. That MAC was what the guy who wrote the tutorial had.

Dedoimedo

Seems that the Windows mobile device always uses that address. I've just done a reinstall following the tutorial. My XDA is listed at eth1 using that. When I do the grep, the return is just eth1.

Not sure what I didn't do right last time. Seems that I followed the tutorial twice and got a different result. Works now though.

---


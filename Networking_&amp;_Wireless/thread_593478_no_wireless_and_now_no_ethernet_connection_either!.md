---
title: "no wireless and now no ethernet connection either!!!"
date: 2007-10-27
forum: Networking &amp; Wireless
---

### Post by enchance on 2007-10-27
I was trying to fix my wireless connection in gutsy since my Intel Pro/Wireless 2200BG won't work but [SIZE="4"]after several tries now even my ethernet connection doesn't work!![/SIZE] I can't even see the network icon anymore! It totally messed up my gutsy...is there a way to reinstall just the networking part of gutsy?

I don't want to have to reinstall...

---

### Post by lH)4~mK0e on 2007-10-27
OK, since you have a 2200bg I would venture to say you have a laptop.  I need to know what your cards are configured at, and if the wireless is encrypted.  Please post the results of these commands.

```


$ lspci | grep Intel Pro
$ ifconfig
$ iwlist eth1 scan


```

This will help to determine if the hardware is ok and being detected properly.

---

### Post by enchance on 2007-10-29
I've reinstalled Gutsy with frustration from tampering with the wireless but I still want to get it to work. Do you know a way I can install Pro/Wireless 2200BG? I tried going to the ndiswrapper site but the [list of supported cards]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_g-l/") has a broken link which won't let me download the files needed for the 2200BG. How do I get around this? I really want my wireless to work. :confused:

---

### Post by enchance on 2007-10-29
Here is the info you wanted. This is after a reinstall of Gutsy. I hope it helps:

"$ lspci | grep Intel Pro"
```
grep: Pro: No such file or directory
```

"ifconfig"
```
eth0      Link encap:Ethernet  HWaddr 00:15:F2:D8:10:51  
          inet addr:124.104.122.129  Bcast:124.104.127.255  Mask:255.255.240.0
          inet6 addr: fe80::215:f2ff:fed8:1051/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:38934 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25131 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:54681473 (52.1 MB)  TX bytes:2349571 (2.2 MB)
          Interrupt:19 Base address:0x2c00 

eth1      Link encap:Ethernet  HWaddr 00:15:00:51:0B:A2  
          inet6 addr: fe80::215:ff:fe51:ba2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5871 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:22 Base address:0xa000 Memory:feafe000-feafefff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
```

"iwlist eth1 scan"
```
eth1      No scan results
```

Card is an Intel PRO/Wireless 2200BG running on an Asus A6R laptop.

---


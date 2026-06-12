---
title: "when My T400 goes to sleep it does not come to live and when it comes it has problems"
date: 2009-11-19
forum: New to Ubuntu
---

### Post by legolas_w on 2009-11-19
Hi
I have a Lenovo thinkpad T400 and when it goes to sleep (the moon led indicate it) I can not bring it out of sleep simply by pressing any button.

After pressing many combination of buttons it comes out of sleep but the wireless network is completely down. Even If I turn the wireless off and then on it can not detect the wireless adapter and again.

If you know a solution to this problem, please let me know,

Thanks

---

### Post by Jon Monreal on 2009-11-19
> **legolas_w said:**
> Hi
I have a Lenovo thinkpad T400 and when it goes to sleep (the moon led indicate it) I can not bring it out of sleep simply by pressing any button.

After pressing many combination of buttons it comes out of sleep but the wireless network is completely down. Even If I turn the wireless off and then on it can not detect the wireless adapter and again.

If you know a solution to this problem, please let me know,

Thanks

Are you using the latest release of Ubuntu (9.10 Karmic)? Also, did you upgrade or do a clean install? [This page]("http://www.thinkwiki.org/wiki/Install_Ubuntu_9.10_%28Karmic_Koala%29_on_a_ThinkPad_T400") contains a number of things you can do to get your T400 running best as possible under Karmic, and includes a section on sleep problems.

---

### Post by jbrown96 on 2009-11-19
When the wireless is working, open a terminal (apps-->accessories-->terminal) and run ```
ifconfig
``` you should get something like > eth0      Link encap:Ethernet  HWaddr 00:1c:25:18:97:7d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Memory:fe200000-fe220000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:54 errors:0 dropped:0 overruns:0 frame:0
          TX packets:54 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3300 (3.3 KB)  TX bytes:3300 (3.3 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1c:bf:25:c1:47  
          inet addr:172.22.112.188  Bcast:172.22.119.255  Mask:255.255.248.0
          inet6 addr: fe80::21c:bfff:fe25:c147/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:115785 errors:0 dropped:0 overruns:0 frame:0
          TX packets:75460 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:140680477 (140.6 MB)  TX bytes:10664453 (10.6 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1C-BF-25-C1-47-00-00-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



There should be an entry for "wlan0". Now suspend your computer, then re-run that command. If wlan0 doesn't show up, try running this ```
sudo ifconfig wlan0 up
```

---


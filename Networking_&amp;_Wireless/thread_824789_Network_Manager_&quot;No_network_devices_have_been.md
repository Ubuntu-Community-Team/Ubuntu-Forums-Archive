---
title: "Network Manager &quot;No network devices have been found.&quot;"
date: 2008-06-10
forum: Networking &amp; Wireless
---

### Post by kasio on 2008-06-10
Network Manager 0.7 says "No network devices have been found." It always shows the offline icon, when a connection IS present! It is setup as a static IP.

Also, Firefox keeps going into offline mode!!!!

Output of ifconfig:

```
eth0      Link encap:Ethernet  HWaddr 00:20:ed:b4:ff:05  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::220:edff:feb4:ff05/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15431 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10981 errors:0 dropped:0 overruns:0 carrier:0
          collisions:86 txqueuelen:1000 
          RX bytes:18592864 (17.7 MB)  TX bytes:1366398 (1.3 MB)
          Interrupt:21 Base address:0xdc00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2996 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2996 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:151748 (148.1 KB)  TX bytes:151748 (148.1 KB)
```

---

### Post by kasio on 2008-06-10
Has anyone had this problem?

---

### Post by kasio on 2008-06-11
Can no one save me?

---

### Post by kasio on 2008-06-11
***bump***

---

### Post by Milardo on 2008-06-11
I would try this-using hardy,open synaptic manager and make sure you check the cd option so it can install stuff from cd, search for ndis and install all those ndis that come up in the search. After installing them in adminstration go to windows wireless drivers. Have your 3 or 2 files from the linksys cd or the one from linksys website. The .cat, .sys, and .inf files. Install new driver the .inf file and next go to the top right icon that looks like a computer monitor. Right click the iconand make sure network and wireless are checked. Next left click it and click the option that is search or find new wireless network not the create or manual option. Now you can enter your wireless security settings and you can easily choose wpa/wpa 2 as well. It should connect pretty fast. I got high speeds as well. To disconnect and unplug adapter (if that is what you have) just uncheck wireless from the icon and then pull out the adapter. To connect to the same wireless network you just have to plug it back in and check wireless if not already checked. You should be connected in about 50 seconds or so. This worked for my linksys wusb54gc.

---

### Post by lswb on 2008-06-11
This is bug 191889. The problem is that Network Manager can actually only manage a subset of typical network connections; the version of NM in 8.04 doesn't recognize a connected ppp session, which is what I have an issue with, and the problem with the static ip address is troublesome to many others judging by forum and bug posts. 

If your system is always connected to the same network and has the same ip address (e.g. a desktop system that is never moved) the most expeditious solution is probably to just uninstall NM and use the tried and true /etc/network/interfaces method. If you have a laptop or other system that connects to different networks at different times, you can either adapt to NM quirks or use a different solution. Many people have reported good results with a program named "wicd". On my older laptop with dapper installed, I used ifplugd and the interfaces file for wired nets, and wifi-radar for wireless.

I have heard that the next version of Network Manager addresses these problems, I hope that is true and that it will be released in a hardy update soon.

---

### Post by kasio on 2008-06-11
I have an ethernet connection on a desktop, and will try the /etc/network/interfaces method.

---


---
title: "Wireless network connected, but no connection to the internet."
date: 2014-05-20
forum: Networking &amp; Wireless
---

### Post by keenen on 2014-05-20
I've read around these forums for solutions and none have worked for me. I'm a total newbie to Linux, so I could just be doing something wrong. 

The computer we were using as a sign-in machine, only displaying a google doc spreadsheet stopped loading web pages. I noticed that the WiFi toggle (ThinkPad X60) was turned off and that's why it wasn't connecting to the internet. Once sliding it back on, the computer would connect to the internet, but no traffic would reach the web. Wired internet works fine, but wireless internet does not at all, even when I try to ping in terminal. 

I found a few responses on here, but being a total beginner I have no idea how to install gedit, or anything else to completely step through some of the solutions I've found. 

I do know that my wireless adapter has the name iwl3945.

Thanks for all the help in advance.

---

### Post by Terry of Astoria on 2014-05-20
Is your wireless router connected to the Internet properly? If not, then the computer could connect to it, and indicate "connected" even if there's no real Internet connection.
to install gedit you go:
```
sudo apt-get install gedit
```
However, it could already be installed. It's called "Text Editor" in some distros.
However, to solve your problem, a simple reboot might do the trick. The wifi card will be re-initialized with a restart of the computer.

---

### Post by keenen on 2014-05-20
Terry of Astoria,

All other computers on the network are connected to the network with an internet connection. 
I have rebooted the machine and no cigar.
Trying to install gedit right now to see if I can get through any of the other solutions. 

Thanks for your response.

---

### Post by keenen on 2014-05-20
I was able to install gedit, but the other solution I found (below) didn't solve my problem.


[COLOR=#000000][FONT=verdana]sudo gedit /etc/modprobe.d/iwlwifi.conf[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]Add a single line:[/FONT][/COLOR]


[COLOR=#000000][FONT=verdana]options iwlwifi 11n_disable=1[/FONT][/COLOR]

---

### Post by drink1297 on 2014-05-20
what does ifconfig -a report?

Can you see other network devices?

---

### Post by keenen on 2014-05-21
I am able to see and access the other servers on the network. Just not able to access the internet. ifconfig returns

```
eth0      Link encap:Ethernet  HWaddr 00:16:d3:3d:5d:4b  
          inet addr:192.168.0.112  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::216:d3ff:fe3d:5d4b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2507 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1426 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2925802 (2.9 MB)  TX bytes:173118 (173.1 KB)
          Interrupt:16 Memory:ee000000-ee020000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:148 errors:0 dropped:0 overruns:0 frame:0
          TX packets:148 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:26721 (26.7 KB)  TX bytes:26721 (26.7 KB)

wlan0     Link encap:Ethernet  HWaddr 00:19:d2:85:42:5a  
          inet addr:10.0.0.91  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::219:d2ff:fe85:425a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:693 errors:0 dropped:0 overruns:0 frame:0
          TX packets:162 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:134766 (134.7 KB)  TX bytes:22113 (22.1 KB)

oem@oem-MX3560:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:16:d3:3d:5d:4b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:60579 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6378 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11384771 (11.3 MB)  TX bytes:879017 (879.0 KB)
          Interrupt:16 Memory:ee000000-ee020000 

irda0     Link encap:IrLAP  HWaddr 00:00:00:00  
          NOARP  MTU:2048  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:8 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:228 errors:0 dropped:0 overruns:0 frame:0
          TX packets:228 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:38548 (38.5 KB)  TX bytes:38548 (38.5 KB)

wlan0     Link encap:Ethernet  HWaddr 00:19:d2:85:42:5a  
          inet addr:10.0.0.91  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::219:d2ff:fe85:425a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:56003 errors:0 dropped:0 overruns:0 frame:0
          TX packets:309 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13576618 (13.5 MB)  TX bytes:45077 (45.0 KB)
```

---

### Post by wildmanne39 on 2014-05-21
Moved to networking.

---

### Post by varunendra on 2014-05-22
> **keenen said:**
> ```
wlan0     Link encap:Ethernet  HWaddr 00:19:d2:85:42:5a  
         ** inet addr:[COLOR="#FF0000"]10.0.0.91[/COLOR]**  Bcast:10.0.0.255  Mask:255.255.255.0
```

That looks like an ad-hoc address. Have you (intentionally or accidentally) configured the wireless interface as a wifi HotSpot in network settings somewhere?

Please disconnect the Ethernet cable, reboot and try wireless with the cable connection unplugged.

If you still can't connect to internet, please follow the instructions in this post to download and run 'wireless_script' (experimental version), and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

---


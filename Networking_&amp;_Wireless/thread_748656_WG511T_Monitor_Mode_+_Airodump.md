---
title: "WG511T Monitor Mode + Airodump"
date: 2008-04-07
forum: Networking &amp; Wireless
---

### Post by ataxicwolf on 2008-04-07
Hey everyone,

Let me first say that I'm aware that you can get a WG511T into monitor mode with a work around, I've searched forums and google and found out about this, but no solution to my problem.

My problem is that after using the workaround with the following commands:
```
ifconfig ath0 down
wlanconfig ath0 destroy
wlanconfig ath0 create wlandev wifi0 wlanmode monitor
```
Although I will have a new athX (x being number higher than last virtual device created), when I use the command
```
sudo airodump-ng athX
```
Airodump successfully starts up, however no packets are captured.

*Note: After going through these commands and executing them, airodump-ng successfully started up and began capturing packets. When I tried again (after rebooting), it did not work, and airodump did not capture any packets.

Here's my ifconfig and iwconfig before running commands above:
```
ataxicwolf@laptop-ubuntu:~$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:1E:2A:67:2F:7E  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:2aff:fe67:2f7e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:68663 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36104 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:99240802 (94.6 MB)  TX bytes:3032581 (2.8 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wifi0     Link encap:UNSPEC  HWaddr 00-1E-2A-67-2F-7E-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:154398 errors:0 dropped:0 overruns:0 frame:154487
          TX packets:37763 errors:253 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:115482801 (110.1 MB)  TX bytes:3907385 (3.7 MB)
          Interrupt:11 

ataxicwolf@laptop-ubuntu:~$ iwconfig
lo        no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"NETGEAR"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1E:2A:08:E7:70   
          Bit Rate:36 Mb/s   Tx-Power:18 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=4/70  Signal level=-87 dBm  Noise level=-91 dBm
          Rx invalid nwid:74  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

Here's that same information repeated after the above commmands:
```

ataxicwolf@laptop-ubuntu:~$ iwconfig
lo        no wireless extensions.

wifi0     no wireless extensions.

ath28     IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Monitor  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:19 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-94 dBm  Noise level=-94 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ataxicwolf@laptop-ubuntu:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)



```

Thanks for any help you guys can give me. I really hope this problem can be fixed :)

---

### Post by pseudo-random on 2008-04-07
```
sudo airodump-ng ath28
```
At a guess. You're doing it right so far...

---

### Post by ataxicwolf on 2008-04-07
Yeah, I've been trying it for awhile now, I'm not really sure why it worked perfectly 3 times in the middle of a bunch of not working. I don't have to update madwifi drivers or anything do i? This is a fresh install of gutsy...

Does anyone else out there use the WG511T? If so, are you able to get it into monitor mode and use airodump?

---

### Post by ataxicwolf on 2008-04-08
Found a solution :)

For anyone else Googling by with the same problem, the solution was to use airmon-ng to create the new virtual device, rather than do it manually. Here are the steps to follow:

1) Unplug card, plug back in (not really necessary, but I did it since I had been trying with other monitor mode attempts)
2) Use command ```
sudo airmon-ng start wifi0
``` It should come up with the output of something like:
```
 
Interface       Chipset         Driver

wifi0           Atheros         madwifi-ng
ath0            Atheros         madwifi-ng VAP (parent: wifi0)
ath1            Atheros         madwifi-ng VAP (parent: wifi0) (monitor mode enabled)
```
*Note: Once or twice, this came up with something not working, solution was to retry by unplugging and plugging card back in, then redoing commaand
3) Use ifconfig to confirm that you have on ath1, and one wifi0
4)Use iwconfig to confirm that you have both ath0 and ath1, ath1 should be in monitor mode
5)use ```
sudo airodump-ng wifi0
``` to start airodump.

Hope this is of some use to someone, thanks for the help.

---


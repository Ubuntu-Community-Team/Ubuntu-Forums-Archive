---
title: "ADSL connection drops out needs reboot to reconnect"
date: 2009-01-17
forum: New to Ubuntu
---

### Post by patpilot on 2009-01-17
My internet connection drops out after a while and then i can only reconnect by rebooting my modem/router and PC.
 I have tried a number of sugestions including a manual connection but the problem persists  
 I am using a wired network connection on ethO and a speedstream 4200 router connected to my service provider (Bigpond)

Where do I find the log of the internet connection
and any other details to help me locate the problem:
  
Thanks in advance

---

### Post by HermanAB on 2009-01-17
$ sudo service network restart

---

### Post by patpilot on 2009-01-19
I tried to use the above command the computer does not recognise it
 To add to the above I am having the same problem trying to connect with
OpenSUSE ,Mandriva also my printer behaves in a similar way in that it works at first but sometimes drops out.

For what it is worth here is the output of ifconfig when connection is OK and when it fails


Output of ifconfig after [COLOR="Red"]**connection lost**[/COLOR]

eth0      Link encap:Ethernet  HWaddr 00:30:18:c1:35:54  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:190 errors:0 dropped:0 overruns:0 frame:0
          TX packets:210 errors:11 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:191378 (186.8 KB)  TX bytes:31577 (30.8 KB)
          Interrupt:19 

eth0:avahi Link encap:Ethernet  HWaddr 00:30:18:c1:35:54  
          inet addr:169.254.5.28  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:19 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1285 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1285 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:65872 (64.3 KB)  TX bytes:65872 (64.3 KB)

Output of ifconfig when connection[COLOR="SeaGreen"] **good**[/COLOR]

eth0      Link encap:Ethernet  HWaddr 00:30:18:c1:35:54  
          inet addr:10.0.0.1  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::230:18ff:fec1:3554/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:223 errors:0 dropped:0 overruns:0 frame:0
          TX packets:228 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:246502 (240.7 KB)  TX bytes:26493 (25.8 KB)
          Interrupt:19 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1262 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1262 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:63100 (61.6 KB)  TX bytes:63100 (61.6 KB)

---

### Post by mikewhatever on 2009-01-19
I think you should try changing the MTU value for eth0 from 1500 to 1492. You can do it temporarily with <sudo ifconfig eth0 MTU 1492>. If it works, making the change permanent depends on the version of Ubuntu you use.
As for rebooting, I think <sudo ifconfig eth0 down && sudo ifconfig eth0 up> should do the job.

---

### Post by patpilot on 2009-01-19
Thanks I will try that

---

### Post by patpilot on 2009-01-21
I tried the sugestion as above

The result of changing **MTU** made no diference

using ifconfig down or up came back with **device not found**

So far I have made no progress with this problem.

anybody got any ideas how to proceed ?

---

### Post by mikewhatever on 2009-01-22
> **patpilot said:**
> I tried the sugestion as above

The result of changing **MTU** made no diference

using ifconfig down or up came back with **device not found**

So far I have made no progress with this problem.

anybody got any ideas how to proceed ?

Did you check that the MTU really changed? As for 'device not found', I don't think there is an **ethO** one. You may want to post the output of <dmesg | grep eth0> too.

> **patpilot said:**
> 
 I am using a wired network connection on **ethO** and a speedstream 4200...

---

### Post by patpilot on 2009-01-22
Here is the result of the < dmesg | grep eth0 >

After the connection **[COLOR="Red"]fails[/COLOR]** 


 [   57.862093] eth0: VIA Rhine II at 0xfa003000, 00:30:18:c1:35:54, IRQ 19.
[   57.862807] eth0: MII PHY found at address 1, status 0x786d advertising 05e1 Link 41e1.
[   67.813349] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[  156.860376] eth0: no IPv6 routers present
[  542.914979] NETDEV WATCHDOG: eth0: transmit timed out
[  542.915132] eth0: Transmit timed out, status 0003, PHY status 786d, resetting...
[  542.915793] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[  558.056966] NETDEV WATCHDOG: eth0: transmit timed out
[  558.057139] eth0: Transmit timed out, status 0003, PHY status 786d, resetting...
[  558.057802] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[  290.201555] NETDEV WATCHDOG: eth0: transmit timed out
[  290.201764] eth0: Transmit timed out, status 0003, PHY status 786d, resetting...
[  290.202392] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[  597.533639] NETDEV WATCHDOG: eth0: transmit timed out
[  597.533792] eth0: Transmit timed out, status 0003, PHY status 786d, resetting...
[  597.534456] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[  616.892742] NETDEV WATCHDOG: eth0: transmit timed out
[  616.892895] eth0: Transmit timed out, status 0003, PHY status 786d, resetting...
[  616.893555] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[  634.781292] NETDEV WATCHDOG: eth0: transmit timed out
[  634.781445] eth0: Transmit timed out, status 0003, PHY status 786d, resetting...
[  634.782106] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[  650.682241] NETDEV WATCHDOG: eth0: transmit timed out
[  650.682394] eth0: Transmit timed out, status 0003, PHY status 786d, resetting...
[  650.683054] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[  666.583235] NETDEV WATCHDOG: eth0: transmit timed out
[  666.583388] eth0: Transmit timed out, status 0003, PHY status 786d, resetting...
[  666.584052] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[  685.705336] NETDEV WATCHDOG: eth0: transmit timed out
[  685.705491] eth0: Transmit timed out, status 0003, PHY status 786d, resetting...
[  685.706154] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[  701.606256] NETDEV WATCHDOG: eth0: transmit timed out
[  701.606408] eth0: Transmit timed out, status 0003, PHY status 786d, resetting...
[  701.607087] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1

Here is the result when connection is **[COLOR="SeaGreen"]good[/COLOR]**

[   31.671873] eth0: VIA Rhine II at 0xfa003000, 00:30:18:c1:35:54, IRQ 19.
[   31.672588] eth0: MII PHY found at address 1, status 0x7849 advertising 05e1 Link 0000.
[   40.471535] eth0: link down
[  117.653274] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  149.396717] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[  149.398489] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  159.649753] eth0: no IPv6 routers present

Further to the above the Lan is inbuilt part of the mother board on my computer. I understand this can cause problems but is it worthwhile buying an add on Lan card ?

---


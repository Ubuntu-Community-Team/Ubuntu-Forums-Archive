---
title: "WIFI - Router works with Windows, not Unbutu"
date: 2007-08-25
forum: Networking &amp; Wireless
---

### Post by csnowman00 on 2007-08-25
Hi Community,
I have been a real hardcore MS user since the  MSDos 5.0, For the longest time I wanted to try Linux because of all the hype around it.  This is my second time trying it (the first time was with Damn small linux and Fedora Core) with about 2 days of playing around with it under my belt, so I am kinda new.    I am writing an article "30 Days with Ubuntu" and I was really hoping you people could help me with my problem.

Here's the Problem:
-My laptop will connect okay to my neighbors wireless router (Linksys ???)
-My laptop will connect okay to my router wired (US Robotics 8054)
-My laptop will NOT connect to my router wireless (US Robotics 8054)
-Using Windows, the laptop will connect to all 3 without any configuration
-Neither routers currently have encryption.

My Laptop is a Toshiba Satellite L25, the internal wireless card is an Atheros® 802.11b/g wireless-LAN card.

If I am posting too much information, Im sorry but I want to give you all the information I need.  Please disregard my Background!

[IMG]http://carlschiel.com/documents/screenshot1.png[/IMG]
When I click on the wireless manager, this is what appears.

[IMG]http://carlschiel.com/documents/screenshot2.png[/IMG]
If I click on USR8054, it just stays like this.

[IMG]http://carlschiel.com/documents/screenshot4.png[/IMG]
 The icon swirls then eventually stops then turns into this error icon.

[IMG]http://carlschiel.com/documents/screenshot3.png[/IMG]
This is what my manual network setting look like.  I disabled wired networking in my BIOS to lessen my confusion.

[IMG]http://carlschiel.com/documents/screenshot5.png[/IMG]
When I click on the 'Linksys' router, the icon swirls a little bit then says this.

[IMG]http://carlschiel.com/documents/screenshot6.png[/IMG]
These are my router settings.  
Note:  the 'Kevin' computer is not the one I am using.

Here is the IFCONFIG when connected to the Linksys Router:
```

ath0      Link encap:Ethernet  HWaddr 00:11:F5:DD:6B:55  
          inet addr:192.168.0.12  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::211:f5ff:fedd:6b55/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:66790 errors:0 dropped:0 overruns:0 frame:0
          TX packets:46850 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:99526551 (94.9 MiB)  TX bytes:3417731 (3.2 MiB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

wifi0     Link encap:UNSPEC  HWaddr 00-11-F5-DD-6B-55-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:84796 errors:0 dropped:0 overruns:0 frame:116794
          TX packets:47610 errors:2291 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:104348274 (99.5 MiB)  TX bytes:4483345 (4.2 MiB)
          Interrupt:20 

```

Here is the IWCONFIG when connected to the Linksys Router:
```

lo        no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"linksys"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:13:10:54:0C:7C   
          Bit Rate:11 Mb/s   Tx-Power:16 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=10/94  Signal level=-83 dBm  Noise level=-93 dBm
          Rx invalid nwid:109  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

Here is the IFCONFIG when trying to connect to the US Robotics 8054 router:
```

ath0      Link encap:Ethernet  HWaddr 00:11:F5:DD:6B:55  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:67002 errors:0 dropped:0 overruns:0 frame:0
          TX packets:46988 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:99830970 (95.2 MiB)  TX bytes:3428171 (3.2 MiB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

wifi0     Link encap:UNSPEC  HWaddr 00-11-F5-DD-6B-55-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:86621 errors:0 dropped:0 overruns:0 frame:117562
          TX packets:47806 errors:2292 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:104800875 (99.9 MiB)  TX bytes:4499491 (4.2 MiB)
          Interrupt:20 

```

Here is the IWCONFIG when trying to connect to the US Robotics 8054 router:
```

lo        no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"USR8054"  Nickname:""
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Tx-Power:16 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=42/94  Signal level=-51 dBm  Noise level=-93 dBm
          Rx invalid nwid:109  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```


And then Finally, here is what is under /var/log/messages
```

Aug 24 23:56:42 Apollo kernel: [ 2490.088000] ADDRCONF(NETDEV_UP): ath0: link is not ready
Aug 24 23:57:43 Apollo kernel: [ 2550.276000] ADDRCONF(NETDEV_UP): ath0: link is not ready
Aug 24 23:57:45 Apollo kernel: [ 2552.572000] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready
Aug 24 23:57:50 Apollo dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/ath0 for sub-path ath0.dbus.get.host_name
Aug 24 23:57:50 Apollo dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/ath0 for sub-path ath0.dbus.get.domain_name
Aug 24 23:57:50 Apollo dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/ath0 for sub-path ath0.dbus.get.nis_domain
Aug 24 23:57:50 Apollo dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/ath0 for sub-path ath0.dbus.get.nis_servers

```

Can someone please tell me what I can possibly do?

---

### Post by leohart on 2007-08-25
Hi,

Not a solution however just to let you know that I am having the same problem.

A brand new Dlink router. 

If I boot up Windows first and get a DHCP release then only Windows can get DHCP not Ubuntu.
If I boot up Ubuntu first and get a DHCP release then only Ubuntu can get DHCP and not Windows.

I think this might have something to do with the wireless protocol or DHCP to prevent MAC address spoofing. The system while trying to get DHCP offer might also send some extra information regarding what OS it is running thus making the router refusing the second OS that is trying to the IP.

Just speculation. If I find a solution, I would definitely post.

Btw, next time, don't post anything too long. People don't answer to long posts.

---

### Post by Dimitriid on 2007-08-25
I noticed the exact same problem on a hotspot yesterday, vista worked fine with it, Ubuntu couldn't connect. Came back home and used the neighbors wireless just fine ( neighbor's router is a linksys, the hotspot restaurant was using a 2wire ). One suggestion I was reading was switching network manager for wicd though dont know if that would do any good ( thats usually recommended to handle encryption better but we're talking no encryption here )

---

### Post by leohart on 2007-08-25
I found a solution for my problem which is swithing encryption from WPA2 to WPA.

---

### Post by csnowman00 on 2007-08-29
Okay, so I finally gave up on ubunu. I refuse to be stuck using wired networking when I have a laptop.  I installed Vista tonight and I went to use it....but one problem.  Vista will not connect to my router either!  WTF?   But Vista was able to tell me the problem was the frmware with my router.  I updated it and was able to use Ubuntu with it.


**If you have a USR8054 Router, you need to upgrade your firmware to get it to work with Ubuntu and Vista, or it will hang when it tries to get an IP address.**

---


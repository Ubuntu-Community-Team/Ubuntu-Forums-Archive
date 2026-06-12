---
title: "Help with WiFi and Feisty"
date: 2007-04-24
forum: Networking &amp; Wireless
---

### Post by NobleSavage on 2007-04-24
Ok - I did this from the live CD - didn't install yet, but I can if that will help.

I have an IPW2200  and my WiFi network used WPA2.   Network Manager detected my access point and detected it was WPA2-PSK and asked for my key.  I entered the key,  The it connected i.e. I got the little blue bars.  However, I'm not able to reach any websites on the net. 

I manually added the DNS to make sure that was correct.  Any idea why it's not working? What should I try?

---

### Post by bnuytten on 2007-04-24
Check if you have an IP address, that at least there is a default route, etc. And you may post the output of the following commands here. It will help pinpoint the cause.
```
iwconfig
ifconfig
route -n
```

---

### Post by NobleSavage on 2007-04-24
Here is the output: 


ubuntu@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

eth1      IEEE 802.11g  ESSID:":)"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:15:E9:66:E0:52   
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=99/100  Signal level=-21 dBm  Noise level=-90 dBm
          Rx invalid nwid:0  Rx invalid crypt:159  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ubuntu@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:15:58:0B:03:B1  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:16 

eth1      Link encap:Ethernet  HWaddr 00:16:6F:3E:33:F9  
          inet addr:192.168.2.144  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::216:6fff:fe3e:33f9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:334 errors:185 dropped:185 overruns:0 frame:0
          TX packets:110 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2096 (2.0 KiB)  TX bytes:11775 (11.4 KiB)
          Interrupt:23 Base address:0xc000 Memory:a8401000-a8401fff 

eth0:avah Link encap:Ethernet  HWaddr 00:15:58:0B:03:B1  
          inet addr:169.254.4.104  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:36 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2664 (2.6 KiB)  TX bytes:2664 (2.6 KiB)

ubuntu@ubuntu:~$ rout -n
bash: rout: command not found
ubuntu@ubuntu:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 eth1
0.0.0.0         0.0.0.0         0.0.0.0         U     1000   0        0 eth0
ubuntu@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

eth1      IEEE 802.11g  ESSID:":)"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:15:E9:66:E0:52   
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=99/100  Signal level=-21 dBm  Noise level=-90 dBm
          Rx invalid nwid:0  Rx invalid crypt:224  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ubuntu@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:15:58:0B:03:B1  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:16 

eth1      Link encap:Ethernet  HWaddr 00:16:6F:3E:33:F9  
          inet addr:192.168.2.144  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::216:6fff:fe3e:33f9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:401 errors:237 dropped:237 overruns:0 frame:0
          TX packets:112 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2096 (2.0 KiB)  TX bytes:11775 (11.4 KiB)
          Interrupt:23 Base address:0xc000 Memory:a8401000-a8401fff 

eth0:avah Link encap:Ethernet  HWaddr 00:15:58:0B:03:B1  
          inet addr:169.254.4.104  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:36 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2664 (2.6 KiB)  TX bytes:2664 (2.6 KiB)

ubuntu@ubuntu:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 eth1
0.0.0.0         0.0.0.0         0.0.0.0         U     1000   0        0 eth0
ubuntu@ubuntu:~$

---

### Post by bnuytten on 2007-04-24
Yup it's routing. You default route forces you to use eth0 and not eth1. If you do not use eth0, disable it and Ubuntu should adjust the network configu and use the eth1 in stead.

If it doesn't or you want a temporary fix, remove the default route and add the correct one.
```
ip r d default dev eth0
ip r a default via 192.168.2.1 dev eth1
```
Just guessing the 192.168.2.1. It is the IP address of your wireless router.

Other solutions possible too. :D

---

### Post by NobleSavage on 2007-04-24
Ok - I'm assuming eth0 is the wired eathernet port (this is an IBM Thinkpad) and eth1 is the built in IPW2200?

I unchecked the "wired" network in network manager.  


ip r d default dev eth0 give me:

No such process (perhaps because I unchecked it in networkmanager?)


ip r a default via 192.168.2.1 dev eth1:

Error: either "to" is duplicate, or "eth1" is a garbage.  


Yes, 192.168.2.1  is the IP of the Wirless AP.    

Still I'm not able to get a website on the net.

---

### Post by bnuytten on 2007-04-24
> **NobleSavage said:**
> Ok - I'm assuming eth0 is the wired eathernet port (this is an IBM Thinkpad) and eth1 is the built in IPW2200?

I unchecked the "wired" network in network manager.  


ip r d default dev eth0 give me:

No such process (perhaps because I unchecked it in networkmanager?)


ip r a default via 192.168.2.1 dev eth1:

Error: either "to" is duplicate, or "eth1" is a garbage.  


Yes, 192.168.2.1  is the IP of the Wirless AP.    

Still I'm not able to get a website on the net.
Hmmm can you ping 192.168.2.1 from your linux box?

---

### Post by NobleSavage on 2007-04-24
Nope - it says network unreachable.

---

### Post by NobleSavage on 2007-04-24
never mind - I'm able to ping 192.168.2.1 now.   But I can't ping any IP's outside of the network i.e.  209.131.36.158 (Yahoo)

---

### Post by NobleSavage on 2007-04-24
Ok - anyone have any ideas on what else I should try?  I actually installed Feisty.  Everything works fine but my WiFI ( The most importing thing :mad:  )   The wired connection works just fine.  WiFi just won't work.

---

### Post by bnuytten on 2007-04-26
> **NobleSavage said:**
> Ok - anyone have any ideas on what else I should try?  I actually installed Feisty.  Everything works fine but my WiFI ( The most importing thing :mad:  )   The wired connection works just fine.  WiFi just won't work.

Try to discover where the problem is at. The link between your Ubuntu box and router is ok since you can ping it. I see two possibilities: routing issue (default route) or our router blocks Internet access for wifi connected machines. The first lines of the following command are important:
```
tracepath 209.131.36.158
```

---

### Post by H.E. Pennypacker on 2007-04-26
> **NobleSavage said:**
> Ok - I did this from the live CD - didn't install yet, but I can if that will help.

I have an IPW2200  and my WiFi network used WPA2.   Network Manager detected my access point and detected it was WPA2-PSK and asked for my key.  I entered the key,  The it connected i.e. I got the little blue bars.  However, I'm not able to reach any websites on the net. 

I manually added the DNS to make sure that was correct.  Any idea why it's not working? What should I try?

I have this very same problem.  Network Manager tells me that I am connected to my WPA2 network, but I am obviously not, because I can't access websites.

iwconfig agrees with Network Manager, and gives me the name of my wireless network, but I am clearly not, as I said before.  

Let me know if you find anything.  I am now connected to a non-secured network.

I have a BCM4318 card.

---

### Post by bnuytten on 2007-04-27
> **H.E. Pennypacker said:**
> I have this very same problem.  Network Manager tells me that I am connected to my WPA2 network, but I am obviously not, because I can't access websites.

iwconfig agrees with Network Manager, and gives me the name of my wireless network, but I am clearly not, as I said before.  

Let me know if you find anything.  I am now connected to a non-secured network.

I have a BCM4318 card.

If you cannot access the Internet it does not necessarely mean you are not connected to your access point/router. In most cases you are connected but you do not have a valid IP address or some routes are missing. Sometimes it is also due to an invalid wifi key... There are many factors involved. Feel free to PM me if you can't find the solution.

---


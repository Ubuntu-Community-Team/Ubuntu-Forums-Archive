---
title: "Desperately do not want to roll back to Vista! Please help!"
date: 2008-09-28
forum: Networking &amp; Wireless
---

### Post by raquel goldstein on 2008-09-28
After buying my 1525 Dell Inspiron and having vista for 2 months I finally had it and loaded ubuntu 8.04. Everything seems ok but of course the wireless internet. I followed all kinds of forums and step by step how to's. At this time I have loaded the drivers for the broadcom wifi card i have. I have gotten the system to recognize the connections but it just wont connect. I have downloaded wifi radar and set it up. I think i have everything entered correctly. It pretends to let me connect and shows the ip address but still says connected to none(ip address here). I just dont get it. I really dont want to go back to vista but i must have a wireless connection for work. please help...

---

### Post by olejorgen on 2008-09-29
What kind of wireless network is it? Does it use wpa, wep, etc.?
Post the output of:
```

sudo iwlist scan
sudo iwconfig
sudo ifconfig

```

---

### Post by raquel goldstein on 2008-09-29
I hope this helps, here are the results of the code entered.

sudo iwlist scan:
lo        Interface doesn't support scanning. 

eth0      Interface doesn't support scanning. 

eth1      Scan completed : 
          Cell 01 - Address: 00:0F:66:DD:3A:41 
                    ESSID:"Thomas Fred" 
                    Mode:Managed 
                    Frequency:2.437 GHz (Channel 6) 
                    Quality:5/5  Signal level:-41 dBm            Noise           level 27 dBm 
                    Encryption key:on 
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s 
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s 
                              12 Mb/s; 48 Mb/s 
          Cell 02 - Address: 00:0F:66:F0:C2:6E 
                    ESSID:"Thomas Fred" 
                    Mode:Managed 
                    Frequency:2.437 GHz (Channel 6) 
                    Quality:4/5  Signal level:-67 dBm  Noise level:-27 dBm 
                    Encryption key:on 
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s 
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s 
                              12 Mb/s; 48 Mb/s 
          Cell 03 - Address: 00:1C:10:95:F8:82 
                    ESSID:"West-Tech" 
                    Mode:Managed 
                    Frequency:2.437 GHz (Channel 6) 
                    Quality:1/5  Signal level:-86 dBm  Noise level:-27 dBm 
                    Encryption key:on 
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s 
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s 
                              12 Mb/s; 48 Mb/s 



sudo iwconfig:

raquel@raquel-laptop:~$ sudo iwconfig 
[sudo] password for raquel: 
lo        no wireless extensions. 

eth0      no wireless extensions. 

eth1      IEEE 802.11bg  ESSID:""  Nickname:"Thomas Fre" 
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:32 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr:off 
          Power Management:off 
          Link Quality=5/5  Signal level=-57 dBm  Noise level=0 dBm 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 




sudo ifconfig:
raquel@raquel-laptop:~$ sudo ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:1d:09:50:fe:42  
          inet addr:192.168.5.111  Bcast:192.168.5.255  Mask:255.255.255.0 
          inet6 addr: fe80::21d:9ff:fe50:fe42/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:184 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:166 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:31657 (30.9 KB)  TX bytes:16627 (16.2 KB) 
          Interrupt:16 

eth1      Link encap:Ethernet  HWaddr 00:1f:e1:d0:4c:cf  
          inet addr:192.168.5.110  Bcast:192.168.5.255  Mask:255.255.255.0 
          inet6 addr: fe80::21f:e1ff:fed0:4ccf/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:291 
          TX packets:1 errors:68 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:350 (350.0 B) 
          Interrupt:17 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:1542 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:1542 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:81060 (79.1 KB)  TX bytes:81060 (79.1 KB) 

I don't know how to show you other than copy and paste. Sorry if it looks a little jumbled. The network called Thomas Fred is the one im trying to connect to.

---

### Post by superprash2003 on 2008-09-29
are you able to ping your router?? in your terminal type ping google.com and post output

---

### Post by olejorgen on 2008-09-29
Ok, next time, put the output in [HTML]```
 output here 
```[/HTML] code blocks

1. Your network does use a key. 
```
...
Encryption key:on
...
```
2. I've never heard og this nickname thing...
3. Have you tried NetworkManager?

Unless wifi-rader or NetworkManager can figure out what kind of key scheme the network is using, you need to figure it out yourself. Access your router from a wired computer and look for wireless security.

---


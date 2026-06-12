---
title: "My WiFi. It works great...or really doesn't."
date: 2007-11-07
forum: Networking &amp; Wireless
---

### Post by horrorpunk138 on 2007-11-07
Having my own problems with wireless here on a Compaq Presario V6000 with a Broadcom card, running 7.10 Gibbon.

At home I use a LinksysWRT54G, and it uses WEP security. (I know, I know, don't ask, it just does...)

At home I connect just fine and everything hauls along just fine with no problems at all.
If I go to the Internet Cafe I work at, they use the same router, with no security, and although it does work per se, it goes very slowly. We are talking 2 to 3 minutes to load a single web page at a time, and that's with no other applications running.

This is what I have with the following at home, (fast, works, and the router name is Linksys_SES_27695)

ifconfig

```
rob@alkaline:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:16:36:92:78:D2  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b) 
          Interrupt:10 Base address:0x4000 

eth1      Link encap:Ethernet  HWaddr 00:14:A5:F1:CA:D2  
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0 
          inet6 addr: fe80::214:a5ff:fef1:cad2/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:7090 errors:0 dropped:521 overruns:0 frame:0 
          TX packets:6398 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:7763848 (7.4 MB)  TX bytes:1217181 (1.1 MB) 
          Interrupt:255 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
```


iwlistscan

```
rob@alkaline:~$ iwlist scan 
lo        Interface doesn't support scanning. 

eth0      Interface doesn't support scanning. 

eth1      Scan completed : 
          Cell 01 - Address: 00:18:39:5A:D4:E2 
                    ESSID:"SlipShot_Records" 
                    Protocol:IEEE 802.11bg 
                    Mode:Master 
                    Channel:6 
                    Frequency:2.437 GHz (Channel 6) 
                    Encryption key:on 
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s 
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s 
                              48 Mb/s; 54 Mb/s 
                    Quality=81/100  Signal level=-81 dBm  Noise level=-70 dBm 
                    IE: WPA Version 1 
                        Group Cipher : WEP-40 
                        Pairwise Ciphers (1) : WEP-40 
                        Authentication Suites (1) : PSK 
                    Extra: Last beacon: 64ms ago 
          Cell 02 - Address: 00:16:B6:35:15:46 
                    ESSID:"linksys_SES_27695" 
                    Protocol:IEEE 802.11bg 
                    Mode:Master 
                    Channel:6 
                    Frequency:2.437 GHz (Channel 6) 
                    Encryption key:on 
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s 
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s 
                              48 Mb/s; 54 Mb/s 
                    Quality=99/100  Signal level=-38 dBm  Noise level=-70 dBm 
                    Extra: Last beacon: 24ms ago 
```


route -n

```
rob@alkaline:~$ route -n 
Kernel IP routing table 
Destination     Gateway         Genmask         Flags      Metric          Ref    Use Iface 
192.168.1.0      0.0.0.0         255.255.255.0   U             0                    0        0 eth1 
169.254.0.0     0.0.0.0         255.255.0.0       U             1000              0        0 eth1 
0.0.0.0             192.168.1.1     0.0.0.0            UG           0                   0        0 eth1 

```



Now, same stuff, but at work, (slow and sucks).

ifconfig

```
rob@alkaline:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:36:92:78:D2  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:10 Base address:0x2000 

eth1      Link encap:Ethernet  HWaddr 00:14:A5:F1:CA:D2  
          inet addr:192.168.1.104  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::214:a5ff:fef1:cad2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:28038 errors:0 dropped:1955 overruns:0 frame:0
          TX packets:17605 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:32805098 (31.2 MB)  TX bytes:1976657 (1.8 MB)
          Interrupt:255 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

iwlistscan

```
rob@alkaline:~$ iwlistscan
bash: iwlistscan: command not found

```

route -n

```
rob@alkaline:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 eth1

```



Anyone have a clue what's going on?

---

### Post by ByteJuggler on 2007-11-07
Just to note, you mistyped the "iwlist scan" command at work as one word instead of 2, hence the "command not found."  You should perhaps re-do that one.

That said, I know that the broadcom native driver is not completely done in all respects yet, for example some of the features dealing with low signal strength and interference isn't implemented yet, so in such situations you will have problems with the native broadcom driver.  I have an HP laptop also with the broadcom chipset, and the laptop is basically unusable in our lounge with the native driver, where it works just fine with the Windows one.  I put this down to these unimplemented features.  I suggest, if you're affected by the lack of these features, that you try using the Windows driver with NDisWrapper.

---

### Post by horrorpunk138 on 2007-11-07
Heh...my fault. It's still pretty early here ;)

(still at work)

iwlist scan

```
rob@alkaline:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:0F:CC:77:57:EC
                    ESSID:"solstice"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 22 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Quality=98/100  Signal level=-42 dBm  Noise level=-71 dBm
                    Extra: Last beacon: 172ms ago
          Cell 02 - Address: 00:0D:72:BC:8E:09
                    ESSID:"2WIRE084"
                    Protocol:IEEE 802.11b
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                    Quality=81/100  Signal level=-81 dBm  Noise level=-71 dBm
                    Extra: Last beacon: 4ms ago

```


Unfortuatly, with my first drive of Ubuntu a few months ago, I realized that Ndiswrapper may work just fine for other people, but apparently is racist against me. Yup. Pretty much hates me.

---

### Post by ByteJuggler on 2007-11-07
OK well maybe it'll work better now?  I really didn't have much trouble installing it and making it work.  Was your previous trial of ndiswrapper on Gutsy?

---

### Post by horrorpunk138 on 2007-11-08
I'm at work right now, but the first time I tried to use it it was with 7.04. I haven't tried it with 7.10

I go home in about 3 hours, and I'll give it a go then and keep touch.

---


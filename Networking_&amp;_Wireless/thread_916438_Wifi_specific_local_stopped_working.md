---
title: "Wifi specific local stopped working"
date: 2008-09-10
forum: Networking &amp; Wireless
---

### Post by jackBnimble on 2008-09-10
Okay, I admit I need help online!  I don't know anyone else around who know a darn thing about Ubuntu 8.04.  
So the story is; I've somehow messed up my wifi at my favorite cafe.  It works everywhere else, so my wifi works.  The cafe was working just fine, then just went out.  I'm sure I did it unknowingly, but I can't freaking figure out how to undo it.  I've tried everything from re-installing to exorcism! Yes, I'm a newbie to all this. Any help would be great. Please make it step by step.  

Thanks a billion!

---

### Post by p_quarles on 2008-09-10
Moved to Networking & Wireless.

Please run the following command within range of the cafe's wireless router, and post the results:
```
sudo iwlist eth1 scan
```
Replace "eth1" with the wireless device's name if it is something else. Run:
```
/sbin/ifconfig -a
```
to get a a list of devices and their names.

---

### Post by jackBnimble on 2008-09-10
Okay I will give a shot, but I first need to resolve another issue with my updates.  Thanks I will get back to you tomorrow with the results about the same time of day.  

:popcorn:

---

### Post by jackBnimble on 2008-09-11
I should have written your instructions down p-quarles, I got to the cafe and duh I can't connect to read your instructions #-o  I will post later I guess.  Not too many late night wifi cafes in Austin.

---

### Post by jackBnimble on 2008-09-13
Ok p-quarles, I ran the commands down at the cafe: sudo iwlist ethl scan, results- Interface doesn't support scanning. 
So I tried the other command you suggested.  results of running: /sbin/ifconfig -a


eth0      Link encap:Ethernet  HWaddr 00:e0:b8:91:ae:a9  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 

eth1      Link encap:Ethernet  HWaddr 00:12:f0:96:9d:38  
          inet addr:192.168.200.30  Bcast:192.168.200.255  Mask:255.255.255.0
          inet6 addr: fe80::212:f0ff:fe96:9d38/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:263 errors:0 dropped:8 overruns:0 frame:0
          TX packets:85 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:16408 (16.0 KB)  TX bytes:10426 (10.1 KB)
          Interrupt:11 Base address:0xa000 Memory:e0208000-e0208fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1610 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1610 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:80500 (78.6 KB)  TX bytes:80500 (78.6 KB)

You suggested that I replace eth1 with the wireless device's name.  Okay but I don't know what the wireless name is and I not sure what to do with the above jive. Also where exactly would I replace the eth1 with the wirelesses name?  Thanks for you time.

---

### Post by p_quarles on 2008-09-13
Well, it looks like you ran the command with the device name "ethl" instead of "eth1" (note, that's a lower case L in the first, the numeral one in the second). Try again with that command.

Also, post the results of:
```
/sbin/iwconfig
```
That will tell us which of the onboard devices is actually wireless.

---

### Post by jackBnimble on 2008-09-20
sorry I ran off on you I will try your suggestions and post back ASAP, thanks for you support.  I really miss my favorite cafe and after considering something drastic like aircrack-ng, which wouldn't work with my chipset anyway, geez!  I've turned into a forum junkie.  Okay, I'm headed out to Epoch to sniff the wifi. out

---

### Post by Crowchild on 2008-09-20
I am having the same problem.

```
ubuntu:~$ /sbin/iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.


@ubuntu:~$ /sbin/ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1d:09:37:64:fb  
          inet addr:192.168.0.114  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:9ff:fe37:64fb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:83008 errors:0 dropped:0 overruns:0 frame:0
          TX packets:76491 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:100295734 (95.6 MB)  TX bytes:8488280 (8.0 MB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2382 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2382 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:119100 (116.3 KB)  TX bytes:119100 (116.3 KB)


```

I seem to be able to get only one wifi connection, the home network that I am on. Elsewhere, I can't even see any other networks in my wifi radar...

Any help would be appreciated.

---

### Post by jackBnimble on 2008-09-20
I don't know how but I'm here at my favorite cafe"Epoch" and lo and behold the wifi is working! I am clueless as to how the connection ceased and resumed.  I will post the info anyway, because you never know it my go away again.  eth1      Scan completed :
          Cell 01 - Address: 00:02:6F:4B:34:97
                    ESSID:"epoch"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:off
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Quality=84/100  Signal level=-46 dBm  
                    Extra: Last beacon: 1096ms ago
          Cell 02 - Address: 00:1C:DF:A9:0C:43
                    ESSID:"Imp"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 11 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=77/100  Signal level=-52 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 204ms ago

/sbin/ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:e0:b8:91:ae:a9  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 

eth1      Link encap:Ethernet  HWaddr 00:12:f0:96:9d:38  
          inet addr:192.168.200.227  Bcast:192.168.200.255  Mask:255.255.255.0
          inet6 addr: fe80::212:f0ff:fe96:9d38/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:582 errors:0 dropped:2 overruns:0 frame:0
          TX packets:244 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:138784 (135.5 KB)  TX bytes:55661 (54.3 KB)
          Interrupt:11 Memory:e0208000-e0208fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1822 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1822 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:91100 (88.9 KB)  TX bytes:91100 (88.9 KB)

Don't know much what this tells me.  Thanks again!

---

### Post by jackBnimble on 2008-10-01
I think I found the problem with my cafe.  Firewall limits the amount of data downloaded and then cuts you off for the rest of the week.  opps my bad:)

---


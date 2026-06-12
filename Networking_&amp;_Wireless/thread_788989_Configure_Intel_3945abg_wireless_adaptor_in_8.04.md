---
title: "Configure Intel 3945abg wireless adaptor in 8.04"
date: 2008-05-10
forum: Networking &amp; Wireless
---

### Post by evilpaddy on 2008-05-10
Hi guys,

I'm new(ish) to linux but wish to explore the possibility of replacing my bloated vista install. I have installed the latest Ubuntu Studio 64bit kernal onto my [HP laptop](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00777686&cc=pl&lc=en&dlc=en&product=3280036&dlc=en&lang=en).

i am having problems configuring the wireless adaptor and it's starting to drive me crazy! 

I can connect via the ethernet port with a static IP as i don't use DHCP. 
Here is an output from ifconfig: ```
bushe@Flappy:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:36:b0:65:03  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:36ff:feb0:6503/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1106 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1235 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:986250 (963.1 KB)  TX bytes:172061 (168.0 KB)
          Base address:0x4000 Memory:da000000-da020000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2090 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2090 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:104500 (102.0 KB)  TX bytes:104500 (102.0 KB)

wlan0     Link encap:Ethernet  HWaddr 00:18:de:8c:a9:ec  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0:avahi Link encap:Ethernet  HWaddr 00:18:de:8c:a9:ec  
          inet addr:169.254.10.185  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

wmaster0  Link encap:UNSPEC  HWaddr 00-18-DE-8C-A9-EC-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

i am not sure why i have both wlan0:avahi and wlan0?

If i do iwconfig:
```
bushe@Flappy:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

This is despite 'network settings' showing the wireless adaptor enabled.
I then realised that ubuntu wont enable the wlan0 if eth0 has a connection. So if i pull the ethernet cable and repeat iwconfig:
```

wlan0     IEEE 802.11g  ESSID:"The Lobster Pot - WiFi"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:12:17:2D:6B:5B   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality=66/100  Signal level=-65 dBm  Noise level=-81 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```


If i insert the correct network settings i get this from ifconfig
```
wlan0     Link encap:Ethernet  HWaddr 00:18:de:8c:a9:ec  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::218:deff:fe8c:a9ec/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:132 errors:0 dropped:0 overruns:0 frame:0
          TX packets:190 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:14916 (14.5 KB)  TX bytes:29442 (28.7 KB)

```

this is as far as i can get. As long as i specify the essid and WPA I get the above results. If i insert the wrong passkey i get the same results. It appears to me as if the wireless card and router are talking, but not authenticating... I am using vanilla drivers out of the box.  Any suggestions?

---

### Post by evilpaddy on 2008-05-10
A bit more progress...
```
wlan0     Scan completed :
          Cell 01 - Address: 00:12:17:2D:6B:5B
                    ESSID:"The Lobster Pot - WiFi"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=55/100  Signal level=-75 dBm  Noise level=-127 dBm
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=0000009e80bb098a
          Cell 02 - Address: 00:1A:C4:E2:B6:53
                    ESSID:"BT Fusion-6271"
                    Mode:Master
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=58/100  Signal level=-73 dBm  Noise level=-127 dBm
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=0000000061e81348
          Cell 03 - Address: 00:1A:C4:E2:B6:51
                    ESSID:"BTBusinessHub-271"
                    Mode:Master
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=66/100  Signal level=-67 dBm  Noise level=-127 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=0000000061e9a181

```

---

### Post by chili555 on 2008-05-10
Network Manager, which is installed by default, will not allow a wireless connection if you have a good, working IP address with an ethernet connection, which you do:> eth0      Link encap:Ethernet  HWaddr 00:16:36:b0:65:03  
          inet addr:192.168.1.100So, please detach the wire and reboot. Can you now configure wireless?

---

### Post by evilpaddy on 2008-05-10
Yes, even if i disable eth0 I still cant get any further.

---

### Post by eggert on 2008-05-11
You could try installing linux-backports-modules

sudo apt-get install linux-backports-modules-`uname -r`

This installs a newer version of iwl3945 driver.

hth
Eggert

---


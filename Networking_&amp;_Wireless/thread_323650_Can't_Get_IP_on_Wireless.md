---
title: "Can't Get IP on Wireless"
date: 2006-12-22
forum: Networking &amp; Wireless
---

### Post by river-1 on 2006-12-22
Struggled for a while to get drivers installed (Dell Inspiron 8600, Broadcom 4306). Now it seems to be working -driver/hardware=OK, enabled in Network Manager, etc.

Using Wifi Radar I can see a signal from my AP, it is good. Does this confirm correct Driver/Hardware function?

Now the trouble: I have opened the Network and Disabled all security including MAC FIltering. I select connect in WiFi Radar and  the "Acquiring IP Address" dialog comes up for a while and then get "Could Not Get IP Address" and I am right back to where I started....

thanks for the help...

---

### Post by n00b@linux on 2006-12-22
I seldom use GUIs for configuration but I may be able to help you identify (and fix) your problem through the command line.

What output do you get from running the 'iwconfig' command?

---

### Post by stupidkid on 2006-12-22
What is the interface?

sudo ifconfig -a

and you should see something like 

# ifconfig -a
ath0      Link encap:Ethernet  HWaddr 00:0F:3D:EA:16:EE  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:3dff:feea:16ee/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:37079 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21941 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:45347116 (43.2 MiB)  TX bytes:1938418 (1.8 MiB)

eth0      Link encap:Ethernet  HWaddr 00:11:43:AF:C5:EC  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:169 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wifi0     Link encap:UNSPEC  HWaddr 00-0F-3D-EA-16-EE-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:113275 errors:0 dropped:0 overruns:0 frame:4360
          TX packets:22250 errors:70 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:54425156 (51.9 MiB)  TX bytes:2611642 (2.4 MiB)
          Interrupt:169 Memory:f8ae0000-f8af0000 

Here ath0 is the wireless interface so you'd run 

sudo dhclient ath0

This will pick up the IP.

---

### Post by river-1 on 2006-12-22
Now I am lost... good news is that I am connected, bad news is I have no idea why... Set the router back to previous settings (Shared and MAC Filters) Rebooted both router and laptop, made changes to laptop through WiFi Radar and now I am connected. 

**iwconfig gives**

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"RiverHouse"  Nickname:"RiverHouse"
          Mode:Auto  Frequency:2.412 GHz  Access Point: 00:13:A3:0F:B9:47   
          Bit Rate=54 Mb/s   Tx-Power:25 dBm   
          RTS thr=2347 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:100/100  Signal level:-41 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

thanks for the help - hope that it stays this way!

---

### Post by river-1 on 2006-12-22
and...

** sudo ifconfig -a** gives

eth0      Link encap:Ethernet  HWaddr 00:0D:56:EA:46:69  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:57 errors:0 dropped:0 overruns:0 frame:0
          TX packets:45 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7821 (7.6 KiB)  TX bytes:4873 (4.7 KiB)
          Interrupt:11 

eth1      Link encap:Ethernet  HWaddr 00:90:4B:6B:0B:B6  
          inet addr:192.168.2.55  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::290:4bff:fe6b:bb6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1549 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1494 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1350646 (1.2 MiB)  TX bytes:216277 (211.2 KiB)
          Interrupt:5 Memory:faff6000-faff8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

---

### Post by stupidkid on 2006-12-22
run

sudo dhclient eth1

if you ever lose your IP again.

---

### Post by lemoniceblock on 2006-12-28
Hello!
I have the same problem here.  I am using a Linksys WPC54G ver.4 Wireless-G Notebook Adaptor.  I'm a newbie with Linux but this laptop and this same card worked when it was running on Windows XP Home.

I *think* I got ndiswrapper to fix the drivers etc because when I type **ndiswrapper -l**, I get:
```

Installed drivers:
wlipnds         driver installed, hardware present 

```

But then it seemed like my card couldn't detect access points because iwlist scan only came up with something like no wireless points or something to that effect until I downloaded Wifi radar, and now **iwlist scan** has the following output:
```

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

sit0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:13:46:F7:3E:10
                    ESSID:"Kwong"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:0/100  Signal level:-61 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: 00:12:17:01:C8:B5
                    ESSID:""
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:0/100  Signal level:-78 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 03 - Address: 00:14:BF:F4:05:46
                    ESSID:"sophia"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:0/100  Signal level:-75 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK  
          Cell 04 - Address: 00:09:5B:ED:1D:C4
                    ESSID:"Seyffert Network"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:0/100  Signal level:-73 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 05 - Address: 00:14:BF:0C:F3:32
                    ESSID:"linksys"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:0/100  Signal level:-73 dBm  Noise level:-256 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 06 - Address: 00:0F:66:8A:A4:47
                    ESSID:"blacksheep"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:0/100  Signal level:-10 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
  

```
But when I try to connect to any one of them, even the unsecured ones won't let me connect (Wifi-radar is saying 'IP could not be resolved' or something along those lines).

**iwconfig** gives:
```

lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
 

```

and** sudo ifconfig -a** gives:
```

eth0      Link encap:Ethernet  HWaddr 00:02:3F:B0:E5:8F  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::202:3fff:feb0:e58f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16912 errors:28 dropped:118 overruns:28 frame:0
          TX packets:16432 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:17578666 (16.7 MiB)  TX bytes:2082625 (1.9 MiB)
          Interrupt:10 Base address:0xe800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:69 errors:0 dropped:0 overruns:0 frame:0
          TX packets:69 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6844 (6.6 KiB)  TX bytes:6844 (6.6 KiB)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:0F:66:90:32:5E  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:10 Memory:16000000-16000800 

```


Thank you in advance, I've been ] @__________@ for 3 days now

---

### Post by Floppyjoe on 2006-12-28
Try going into your routers configuration and changing to a channel other than 1, 6, or 11.

---

### Post by lemoniceblock on 2006-12-28
Hi, Floppyjoe, thanks, I just tried that and it's still not working =x

---

### Post by alexmoon on 2007-06-27
I'm having the same problem, again with a Broadcom 4306 card on a laptop.

I've got ndiswrapper running, as far as I can tell (after many, many HOWTOs), but when I put in 'sudo dhclient eth1' I get some attempts to connect and then:
No working leases in persistent database - sleeping, which I'm guessing is linked to the 'Can't get IP address error'.

Any ideas where to go from here?

---

### Post by lemoniceblock on 2007-06-28
I got it to work eventually by using the newest version of ndiswrapper.

---


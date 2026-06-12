---
title: "Weird Wireless Connections Pt. 2"
date: 2007-03-13
forum: Networking &amp; Wireless
---

### Post by drefined on 2007-03-13
Let me just start out by saying I have tried almost everything including installing the wpasupplicant... so here it goes part 2, to see if anyone is able to help me get my wireless connection going. wired connection = no problem.

ifconfig
```

eth0      Link encap:Ethernet  HWaddr 00:A0:D1:4D:64:2B  
          inet6 addr: fe80::2a0:d1ff:fe4d:642b/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1492  Metric:1
          RX packets:80 errors:0 dropped:0 overruns:0 frame:0
          TX packets:67 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:22149 (21.6 KiB)  TX bytes:6879 (6.7 KiB)

eth1      Link encap:Ethernet  HWaddr 00:13:02:CF:19:4B  
          inet6 addr: fe80::213:2ff:fecf:194b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2875 errors:0 dropped:303 overruns:0 frame:0
          TX packets:29 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:54 (54.0 b)  TX bytes:8185 (7.9 KiB)
          Interrupt:185 Memory:da000000-da000fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:14 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1116 (1.0 KiB)  TX bytes:1116 (1.0 KiB)

```

iwconfig
```

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:"dp_epic"  
          Mode:Managed  Frequency:2.417 GHz  Access Point: 00:09:5B:72:59:E6   
          Bit Rate:11 Mb/s   Tx-Power:15 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=98/100  Signal level=-29 dBm  Noise level=-30 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:289   Missed beacon:0

sit0      no wireless extensions.

```

iwlist scan
```

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:09:5B:72:59:E6
                    ESSID:"dp_epic"
                    Protocol:IEEE 802.11b
                    Mode:Master
                    Channel:2
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Quality=98/100  Signal level=-25 dBm  Noise level=-25 dBm
                    Extra: Last beacon: 72ms ago

sit0      Interface doesn't support scanning.

```

Ok heres the thing... my router is able to see the wireless card because it was able to identify its MAC address, and from iwlist scan, the wireless card was able to see the router - the only thing is when i try sudo dhclient eth, it will not connect. The signal is great because im standing right infront of the router. 

I am stuck at this point. ive visited the ipw3945 sourceforge site but was clueless; I dont know what i should do first to upgrade the ipw3945 drivers. I am a super newb and need step by step instructions :lolflag: 

Im running 6.10 and have updated everything through the synaptic package manager. if someone could help me out - I will forever call you the greatest!

:popcorn: 

btw: my laptop is a toshiba satellite a105-s4094 with a builtin Intel Pro\Wireless 3945ABG

---

### Post by drefined on 2007-03-13
I would also like to add

uname -r
```

2.6.17-11-generic

```

lsmod | grep ipw3945
```

ipw3945               124576  1 
ieee80211              35272  1 ipw3945

```

lsmod | grep ieee80211
```

ieee80211              35272  1 ipw3945
ieee80211_crypt         7552  1 ieee80211

```

If anyone needs me to do anything else, please let me know.

---

### Post by drefined on 2007-03-13
bump! :)

---

### Post by drefined on 2007-03-13
fixed... posting on my wireless connection!

if anyone is having trouble with their toshiba satellite a105-s4094, pm me!

---

### Post by hasinasi on 2007-03-16
hey drefined!
I have the same problem and have seen many people having it in other forums. 
So please let me know: what was your solution?

---


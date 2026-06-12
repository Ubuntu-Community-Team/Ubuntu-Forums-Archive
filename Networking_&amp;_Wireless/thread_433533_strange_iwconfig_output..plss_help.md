---
title: "strange iwconfig output..plss help"
date: 2007-05-05
forum: Networking &amp; Wireless
---

### Post by tomiu on 2007-05-05
hi..what does this output means:

```

iwconfig:

wlan0     Auto  Access Point: Not-Associated
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

does this mean that my card is ok but i can't connect to the network or smthg else?:confused:

---

### Post by MrHorus on 2007-05-05
> **tomiu said:**
> 
does this mean that my card is ok but i can't connect to the network or smthg else?:confused:

Yes.

it looks like you will need to tell it the SSID and encryption key (if used).

---

### Post by sdide on 2007-05-05
Hey,

I am not really sure how much that output means.
Usually. - you get more lines of output from iwconfig.

example 1: (when associated)

```
~# iwconfig eth1
eth1      IEEE 802.11g  ESSID:"W_SDKFN"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:14:BF:16:0A:74   
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Encryption key: <long_key> Security mode:open
          Power Management:off
          Link Quality=68/100  Signal level=-59 dBm  Noise level=-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:1  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

example 2 : (when NOT associated)

```

~# iwconfig eth1
eth1      unassociated  ESSID:"W_SDKFN"  
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:1  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

You are definately not associated, 

Is your card ok? I dunno, does it work under windows or any other OS? 
if yes - then it is ok.

What version is your iwconfig? Check with: (as root or with sudo)

~# iwconfig --version

and what is your NIC?  Check with (as root or with sudo)

~# lshw -C network

---

### Post by tomiu on 2007-05-05
hi..this are the outputs:


iwconfig --version:
```

iwconfig  Wireless-Tools version 28
          Compatible with Wireless Extension v11 to v19.

Kernel    Currently compiled with Wireless Extension v19.

wlan0     Recommend Wireless Extension v18 or later,
          Currently compiled with Wireless Extension v19.

```

lshw -C network:
```

  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:c1:32:f5:ed
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=Auto

```

---

### Post by sdide on 2007-05-05
is the AP associated via WEP or WPA, or is there no security?

---

### Post by tomiu on 2007-05-06
> **sdide said:**
> is the AP associated via WEP or WPA, or is there no security?

the AP is associated with WEP..i have added key and essid, but it doesn't find any network..any Suggestion how to solve this problem?

thx for trying to help me

---

### Post by tomiu on 2007-05-13
hi..i see nobody can help me..maybe u need more infos..this is output from ifconfig:

ifconfig:
```

wlan0     Protokoll:Ethernet  Hardware Adresse 00:14:C1:32:F5:ED
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 SendewarteschlangenlÃ¤nge:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

---

### Post by tomiu on 2007-05-16
ok tried smthg yesterday and now i have this **ifconfig** output:

```

lo        Protokoll:Lokale Schleife
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6 Adresse: ::1/128 Gültigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:224 errors:0 dropped:0 overruns:0 frame:0
          TX packets:224 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0
          RX bytes:18816 (18.3 KiB)  TX bytes:18816 (18.3 KiB)

wlan0     Protokoll:Ethernet  Hardware Adresse 00:14:C1:32:F5:ED
          inet6 Adresse: fe80::214:c1ff:fe32:f5ed/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

---


---
title: "wireless problem: USRobotics 805423"
date: 2007-03-19
forum: Networking &amp; Wireless
---

### Post by tomiu on 2007-03-19
Hi, i installed windows drivers with ndiswrapper..this is output for ifconfig and iwconfig:

```


**ifconfig**

lo        Protokoll:Lokale Schleife
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 SendewarteschlangenlÃ¤nge:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Protokoll:Ethernet  Hardware Adresse 00:14:C1:32:F5:ED
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 SendewarteschlangenlÃ¤nge:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


**iwconfig**

lo        no wireless extensions.

wlan0     Auto  Access Point: Not-Associated
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```


My usb card can't find any network..any idea how can i solve this problem?

thx in advance
tomiu

---

### Post by tomiu on 2007-03-20
this is output when i type: iwconfig wlan0 essid E2

```

Error for wireless request "Set ESSID" (8B1A) :
SET failed on device wlan0 ; Invalid argument.

```

??

---

### Post by tomiu on 2007-03-26
Am i the only one that uses USR5423?  Plss help meee [-o<

---

### Post by tomiu on 2007-05-18
bump

---


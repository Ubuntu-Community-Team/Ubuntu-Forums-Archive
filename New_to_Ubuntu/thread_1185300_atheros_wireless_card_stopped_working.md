---
title: "atheros wireless card stopped working"
date: 2009-06-12
forum: New to Ubuntu
---

### Post by duruttye on 2009-06-12
Hey guys!

Due to some update I just lost my huawei vodafone mobile connection. I have a wireless network at home, but I had to buy some cables to be able to use the ethernet card, because the wireless is gone, too . I'm using a dell vostro a680, and ubuntu 9.04.

outputs:
lspci

```
09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
0c:00.0 Network controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

```

```
sudo ./madwifi.sh --info
Found at least one Atheros device.
Linux ubuntuboxdell 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux
Distro: Debian
0c:00.0 Network controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
	Subsystem: Device 1a32:0112
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at f6cf0000 (64-bit, non-prefetchable) [size=64K]
	Kernel driver in use: ath5k
	Kernel modules: ath_pci, ath5k

ath_pci               208440  0 
wlan                  234352  1 ath_pci
ath_hal               371488  1 ath_pci
wifi0: 0 ath0: 0

```

```


$ iwlist wlan0 scan
wlan0     No scan results
```

```

$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:21:70:8e:ad:42  
          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::221:70ff:fe8e:ad42/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:6987 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5905 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7853459 (7.8 MB)  TX bytes:473336 (473.3 KB)
          Interrupt:252 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:17:c4:4e:cd:69  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-17-C4-4E-CD-69-00-00-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

```

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.
```

The hardware driver says that a different version of the madwifi driver is in the use. There is no change when I deactivate it.

In case somebody needs some additional information, just ask!

I don't know what could I do without this forum... I am sure I won't be Ubuntu user for long...

thanx guys!

---

### Post by superprash2003 on 2009-06-12
ensure that your wireless switch is set to ON , thats probably why you are getting NO SCAN RESULTS

For reference : [http://www.prash-babu.com/2009/05/how-to-fix-wireless-no-scan-results-in.html](http://www.prash-babu.com/2009/05/how-to-fix-wireless-no-scan-results-in.html)

---

### Post by duruttye on 2009-06-12
OMG you are right!!

It turns out that the update didn't break my wireless, it actually fixed it! Until now, the Fn+wireless button didn't work at all, the led was always off, but the wireless was always on. Now, I can switch it on and off, the led isn't on, but that is not a problem. Ohh, and I was mad at ubuntu for a few weeks now!!! 

Thank you very much, my dear superprash2003!!

---


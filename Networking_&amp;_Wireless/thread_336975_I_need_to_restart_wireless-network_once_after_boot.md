---
title: "I need to restart wireless-network once after boot"
date: 2007-01-12
forum: Networking &amp; Wireless
---

### Post by Gustav Nilsson on 2007-01-12
Hi!

After I have booted my computer, I need to run **/etc/init.d/networking restart** once for getting my network working. The start-argument isn't enough. Here's my /etc/network/interfaces:
```

auto lo
iface lo inet loopback

auto ath0
iface ath0 inet static
address 192.168.1.10
netmask 255.255.255.0
network 192.168.1.0
gateway 192.168.1.1
dns-nameservers 195.67.199.33
wpa-driver madwifi
wpa-conf managed
wpa-ssid <my essid>
wpa-ap-scan 1
wpa-proto WPA
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
wpa-psk <my generated key>

```

Anyone who knows how to solve it?

Thanks in advice!

---

### Post by joneberger on 2007-01-12
reboot and before you restart your networking post the results of sudo ifconfig and sudo iwconfig.

---

### Post by Gustav Nilsson on 2007-01-12
**sudo iwconfig**
```

lo        no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:18 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

```

**sudo ifconfig**
```

ath0      Link encap:Ethernet  HWaddr 00:03:2F:3B:EC:7D  
          inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::203:2fff:fe3b:ec7d/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:17 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1420 (1.3 KiB)  TX bytes:1420 (1.3 KiB)

wifi0     Link encap:UNSPEC  HWaddr 00-03-2F-3B-EC-7D-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:293 errors:0 dropped:0 overruns:0 frame:7559
          TX packets:393 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:34917 (34.0 KiB)  TX bytes:18078 (17.6 KiB)
          Interrupt:193 Memory:e0ae0000-e0af0000 

```

---

### Post by fotzlapen on 2007-11-25
I'm having the same issue.  Anyone know a fix for this?

---


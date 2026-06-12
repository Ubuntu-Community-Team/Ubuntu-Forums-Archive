---
title: "No WLAN after boot of 6.10, works with manual ifup/ifdown"
date: 2006-10-31
forum: Networking &amp; Wireless
---

### Post by einarmr on 2006-10-31
Just installed Ubuntu Server 6.10 (Edgy) on a Pentium 4 computer here, with a Atheros AR5212 PCI NIC.

I set up /etc/network/interfaces as per the instructions in /usr/share/doc/wpasupplicant/README.modes.

After a fresh boot, I get no network.

ifconfig:
```
ath0      Link encap:Ethernet  HWaddr 00:13:F7:40:25:D5
          inet addr:10.0.0.3  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::213:f7ff:fe40:25d5/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:9 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:816 (816.0 b)  TX bytes:816 (816.0 b)

wifi0     Link encap:UNSPEC  HWaddr 00-13-F7-40-25-D5-00-00-00-00-00-00-00-00-00-00
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:150 errors:0 dropped:0 overruns:0 frame:15
          TX packets:19 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199
          RX bytes:13754 (13.4 KiB)  TX bytes:838 (838.0 b)
          Interrupt:177 Memory:f8b80000-f8b90000
```


route -n:
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.0.0.0        0.0.0.0         255.255.255.0   U     0      0        0 ath0
0.0.0.0         10.0.0.1        0.0.0.0         UG    0      0        0 ath0
```

I.e. everything seems OK, but I cannot ping my router (10.0.0.1).

If I manually restart networking, i.e.
```
    /etc/init.d/networking restart
```

Everything seems to work just fine.

I have added VERBOSITY=1 to the beginning of /etc/wpa_supplicant/ifupdown.sh. Restarting networking then tells me that everything works well with wpa_supplicant. However, redirecting the output to a file doesn't work (not even when grabbing both stdout and stderr), so I can't post the output here.

/etc/network/interfaces:
```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto ath0
iface ath0 inet static
        wpa-driver wext
        wpa-ssid mynetwork
        wpa-passphrase verysecret
        wpa-key-mgmt WPA-PSK
        wpa-pairwise TKIP CCMP
        wpa-group TKIP CCMP
        wpa-proto WPA RSN
        address 10.0.0.3
        netmask 255.255.255.0
        gateway 10.0.0.1
        dns-nameservers 10.0.0.1
```

I'm stuck here... How do I debug and diagnose wpa_supplicant problems during boot??

Any suggestions? Or should I just file a bug report for this?

---

### Post by einarmr on 2006-10-31
BTW, I forgot iwconfig output:

iwconfig after fresh boot:
```
ath0      IEEE 802.11g  ESSID:""
          Mode:Managed  Channel:0  Access Point: Not-Associated
          Bit Rate:0 kb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:21  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

iwconfig after /etc/init.d/networking restart:
```
ath0      IEEE 802.11g  ESSID:"mynetwork"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:18:39:C0:20:35
          Bit Rate:48 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:SECRET-SOMETHING-HERE   Security mode:restricted
          Power Management:off
          Link Quality=57/94  Signal level=-38 dBm  Noise level=-95 dBm
          Rx invalid nwid:62  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

BTW, access point is a Linksys WRT54GL running OpenWRT RC5, which works perfectly with other computers (Linux and Windows).

I just need this to work after a fresh boot, so any hack is acceptable to me. Any suggestions are very welcome!

---


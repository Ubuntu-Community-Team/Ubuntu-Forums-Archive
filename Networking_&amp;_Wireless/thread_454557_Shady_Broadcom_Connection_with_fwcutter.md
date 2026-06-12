---
title: "Shady Broadcom Connection with fwcutter"
date: 2007-05-25
forum: Networking &amp; Wireless
---

### Post by leetcharmer on 2007-05-25
Hello, I just installed Feisty on my laptop; I've got a broadcom 4306 wireless chipset.  I installed it with fwcutter and it's giving me mixed feelings.  I've got two wireless access points at my location, and all three have the same WEP HEX code.  The laptop seems to connect to only one of them though.  Under windows, it can connect to all three, but in Ubuntu, just one.  This laptop dual boots.

1) How do I troubleshoot to connect to all of them?

2) How do I save the encryption key under all users on the laptop?

Thanks

Here's additional info for you hackers out there:

```
simbala@gerbert:~$ iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"LocationFreeTV"  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.437 GHz  Access Point: XX:XX:XX:XX:XX:XX   
          Bit Rate=11 Mb/s   Tx-Power=15 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=93/100  Signal level=-45 dBm  Noise level=-70 dBm
          Rx invalid nwid:0  Rx invalid crypt:570  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

--

```
simbala@gerbert:~$ iwlist eth1 scan
eth1      Scan completed :
          Cell 01 - Address: XX:XX:XX:XX:XX:XX
                    ESSID:"WLAN"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=100/100  Signal level=-30 dBm  Noise level=-70 dBm
                    Extra: Last beacon: 28ms ago
          Cell 02 - Address: XX:XX:XX:XX:XX:XX
                    ESSID:"LocationFreeTV"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=100/100  Signal level=-33 dBm  Noise level=-70 dBm
                    Extra: Last beacon: 92ms ago
```

---


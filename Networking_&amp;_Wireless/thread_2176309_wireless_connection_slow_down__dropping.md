---
title: "wireless connection slow down / dropping"
date: 2013-09-23
forum: Networking &amp; Wireless
---

### Post by cshaw2 on 2013-09-23
Greetings,

Somewhat new to Linux, mucked around with Mint on an old lappy for a while, recently installed Ubuntu on desktop.  Bought a usb wireless adapter out of necessity, and of course am now experience some issues (what else is new, right?)

The problem:  Wireless connection is flaky at times, either slowing down to be unusable or dropping completely.  Happens every 10 minutes or so.  Sometimes "sudo modprobe rt2800usb" will give me another 10 minutes, sometimes a reboot is in order.

Intel i7 920, ASUS p6t motherboard, Tenda W311m usb wireless adapter

lsusb:
```

$ lsusb
Bus 002 Device 003: ID 148f:5370 Ralink Technology, Corp. RT5370 Wireless Adapter

```

iwconfig:
```

$ iwconfig
wlan2     IEEE 802.11bgn  ESSID:"GiantButtMonkey"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: C0:3F:0E:D0:8D:F0   
          Bit Rate=30 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=35/70  Signal level=-75 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:43  Invalid misc:42   Missed beacon:0

```

lsmod:
```

$ lsmod | grep rt2
rt2800usb              26854  0 
rt2x00usb              20635  1 rt2800usb
rt2800lib              66507  1 rt2800usb
rt2x00lib              54869  3 rt2x00usb,rt2800lib,rt2800usb
mac80211              606457  3 rt2x00lib,rt2x00usb,rt2800lib
cfg80211              510937  2 mac80211,rt2x00lib
crc_ccitt              12707  1 rt2800lib

```

iwlist scan:
```

$ iwlist scan
wlan2     Scan completed :
          Cell 01 - Address: C0:3F:0E:D0:8D:F0
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"GiantButtMonkey"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000030f775ee1c0
                    Extra: Last beacon: 1104ms ago
                    IE: Unknown: 000F4769616E74427574744D6F6E6B6579
                    IE: Unknown: 010882840B162430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0106
                    IE: Unknown: 2F0106
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7E181BFFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D1606071300000000000000000000000000000000000000
                    IE: Unknown: DD800050F204104A00011010440001021041000100103B0001031047001005E06856E645F66107BC9472CF39509D1021000D4E4554474541522C20496E632E10230008574E52333530304C10240008574E52333530304C10420004333530301054000800060050F204000110110008574E52333530304C100800020084103C000101
                    IE: Unknown: DD090010180204F0050000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C337E181BFFFF000001000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406071300000000000000000000000000000000000000

```

uname:
```

$ uname -mr
3.8.0-30-generic x86_64

```

Enabled rt2800usb driver using instructions found here: [https://help.ubuntu.com/community/WifiDocs/Device/Tenda_W311M](https://help.ubuntu.com/community/WifiDocs/Device/Tenda_W311M)

Anyone got any tips to resolve this?

---

### Post by varunendra on 2013-09-24
Welcome to the forums cshaw2! :)

Let's mess with the native driver a bit first. As per your outputs above, your encryption mode in the router is WPA/WPA2 mixed mode which is not good for Linux. Please change it to anything but the mixed mode. Pure WPA2-PSK (AES) is strongly recommended. No TKIP either.

After changing that in the router, don't forget to save and reboot the router. Rebooting it is not always necessary, but is recommended to be sure the new settings have effectively taken place. Accordingly change the security settings in Ubuntu's Network Manager as well (better delete the existing connection, and create a fresh one).

Apart from above, please turn the power management off on the interface -
```
sudo iwconfig wlan2 power off
```
Check with "iwconfig" again to make sure power management is off.

Once these are effective, please do -
```
sudo modprobe -rv rt2800usb
sudo modprobe -v rt2800usb nohwcrypt=Y
```
Retry to connect and see if the connection gets any better. If not, you can additionally try changing the channel to 1 or 11 in the router (change > save > reboot again).

Post back how it goes.

---


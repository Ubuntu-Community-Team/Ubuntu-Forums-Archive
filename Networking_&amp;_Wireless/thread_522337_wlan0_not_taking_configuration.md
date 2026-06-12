---
title: "wlan0 not taking configuration ?"
date: 2007-08-10
forum: Networking &amp; Wireless
---

### Post by Metheos on 2007-08-10
/etc/network/interfaces
```
iface wlan0 inet dhcp
wireless-essid Nelson227
wireless-key 2fa580545ae8e52db4a4f797c8
auto wlan0
```

iwconfig
```
wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate=54 Mb/s   Tx-Power:32 dBm   
          RTS thr=2347 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

iwlist wlan0 scan
```
wlan0     Scan completed :
          Cell 01 - Address: 00:0C:41:66:F2:6C
                    ESSID:"Nelson227"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.442 GHz (Channel 7)
                    Quality:75/100  Signal level:-48 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

```

Ok.... so the card is working, but it looks like it's not taking my configuration. What to do?

---

### Post by noob12 on 2007-08-10
Have you connected before successfully at all with or without encryption?  If not, I'd back up and make sure that you can connect without encryption enabled.  Is the router broadcasting its ESSID?  If not, I'd enable that as well.

If you've connected before successfully without encryption, I'd try these things.

Did you bounce the interface, reboot, or restart networking after you added that config?  If not, try this:
```

sudo /sbin/ifdown wlan0
sudo /sbin/ifup wlan0

```

If you did already bounce the interface and it isn't connecting, see if you are successful connecting with these commands manually
```

sudo iwconfig wlan0 essid Nelson227
sudo iwconfig wlan0 key 2fa580545ae8e52db4a4f797c8

```

Finally, try manually switching to the right frequency and rate as well
```

sudo iwconfig wlan0 freq 2.442G
sudo iwconfig wlan0 channel 7
sudo iwconfig wlan0 rate 11M

```

These last ones might report that you can't set them if the driver doesn't support these operations.

---


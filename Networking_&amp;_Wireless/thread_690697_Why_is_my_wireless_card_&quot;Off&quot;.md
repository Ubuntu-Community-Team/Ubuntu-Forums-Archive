---
title: "Why is my wireless card &quot;Off&quot;??"
date: 2008-02-07
forum: Networking &amp; Wireless
---

### Post by smooveg on 2008-02-07
My wireless card just seemed to turn "off." Has anyone run into this before? (yes -- the wireless switch is still On!!)

iwconfig shows:
ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:15 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

I've done all of the usual checks -- all madwifi modules are running, lshw -C network shows the driver loaded.

By the way, I've just loaded Wicd and uninstalled NetworkManager, and I was able to scan before I changed my router security to WEP from WPA. Why would that have anything to do with this though????

---

### Post by pytheas22 on 2008-02-07
you need to put your device "up" before it's accessible:
```

sudo ifconfig ath0 up
```

If that doesn't work, what is the output of ```
ifconfig -a
```

Also, reinserting the madwifi modules might help, as would pulling your card out and plugging it back in, if it's detachable.

Changing router security should have nothing to do with it.

EDIT: I remembered that sometimes madwifi does things its own way.  If the ifconfig command doesn't work, try

```
wlanconfig ath0 create wlandev wifi0 wlanmode managed
```

---


---
title: "wmp54g pci card not connecting to WPA network, but recognizes it"
date: 2013-09-05
forum: Networking &amp; Wireless
---

### Post by smithc2005 on 2013-09-05
I am having problems connecting to my WPA network on 13.04 , I know there is a fix because I had it working before on 12.04 , I formated and installed 13.04 and it no longer works, it recognizes the network (N router) it shows three different SSID's name , name1, and name2.  But it will not finish the connection. I am on the 3.8.0-19-generic kernel  

my intefaces.conf 
```
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
iface wlan0 inet dhcp
        pre-up ip link set wlan0 up
        pre-up ip link set wlan0 down
        pre-up ip link set wlan0 up
        pre-up ip link set wlan0 down
        pre-up iwconfig wlan0 essid Stephen
        pre-up iwconfig wlan0 mode Managed
        pre-up iwpriv wlan0 set AuthMode=WPAPSK
        pre-up iwpriv wlan0 set EncrypType=TKIP
        pre-up iwpriv wlan0 set WPAPSK=61 62 63 64 65 31 32 33 34 35
        pre-up ip link set wlan0 up
```



dmesg output:
```
[ 3995.394614] wlan0: authenticate with 00:22:3f:93:67:dc
[ 3995.395054] wlan0: send auth to 00:22:3f:93:67:dc (try 1/3)
[ 3995.397517] wlan0: authenticated
[ 3995.398173] rt2500pci 0000:00:09.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 3995.400056] wlan0: associate with 00:22:3f:93:67:dc (try 1/3)
[ 3995.408285] wlan0: RX AssocResp from 00:22:3f:93:67:dc (capab=0x431 status=0 aid=1)
[ 3995.408667] wlan0: associated
[ 3995.408769] cfg80211: Calling CRDA for country: US
[ 3995.433289] wlan0: Limiting TX power to 27 (27 - 0) dBm as advertised by 00:22:3f:93:67:dc
[ 4000.965129] cfg80211: Regulatory domain changed to country: US
[ 4000.965140] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 4000.965143] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 4000.965146] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[ 4000.965148] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 4000.965151] cfg80211:   (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 4000.965153] cfg80211:   (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 4000.965156] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[ 4042.072613] wlan0: deauthenticating from 00:22:3f:93:67:dc by local choice (reason=3)
[ 4042.101952] cfg80211: Calling CRDA to update world regulatory domain
[ 4042.690162] cfg80211: World regulatory domain updated:
[ 4042.690174] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 4042.690177] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 4042.690180] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 4042.690183] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 4042.690185] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 4042.690188] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
```

---

### Post by chili555 on 2013-09-05
I don't understand why you are using /etc/network/interfaces when the usually reliable Network Manager comes with 13.04 by default. Even if you wanted to use manual methods, that's probably the busiest interfaces file I've ever seen. Ever. It is also missing the most important line: auto wlan0.

What about NM isn't working for you?

---

### Post by smithc2005 on 2013-09-05
It would not connect to my WPA network.  Do I just just set interfaces.conf to what it was before? I was following 3.2 on this guide . [https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500)

---

### Post by chili555 on 2013-09-05
That guide is old; almost as old as me. We no longer use wooden wheels on our sleek black BMWs.

Just for giggles, set it to this:```
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
        wpa-ssid Stephen
        wpa-psk your_key
```'your_key' is your actual WPA key in plain text; no spaces. Then restart Network Manager and look for errors or warnings:```
sudo service network-manager restart
dmesg | grep -e wlan -e rt2
```I actually think the driver is the fault, not NM or the interfaces file, but let's see.

---

### Post by smithc2005 on 2013-09-05
DIdn't work, just went back to the Network Manager and reset the interfaces file.  Here is the dmesg 
```

[ 3509.256120] wlan0: authenticate with 00:22:3f:93:67:dc
[ 3509.256571] wlan0: send auth to 00:22:3f:93:67:dc (try 1/3)
[ 3509.258581] wlan0: authenticated
[ 3509.259430] rt2500pci 0000:00:09.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 3509.260049] wlan0: associate with 00:22:3f:93:67:dc (try 1/3)
[ 3509.263627] wlan0: RX AssocResp from 00:22:3f:93:67:dc (capab=0x431 status=0 aid=2)
[ 3509.263990] wlan0: associated
[ 3509.264044] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 3509.329738] wlan0: Limiting TX power to 27 (27 - 0) dBm as advertised by 00:22:3f:93:67:dc
[ 3555.013969] wlan0: deauthenticating from 00:22:3f:93:67:dc by local choice (reason=3)

```

---

### Post by chili555 on 2013-09-05
It looks like it connected just fine for a few moments and then dropped. Is that what you saw? I am trying to decide between adjusting probe response and going straight to compling a newer driver suite.

We might also see if the country code is handled correctly:```
sudo iw reg get
```What should your country code be? US? GB? IN? Or...?

---

### Post by smithc2005 on 2013-09-06
Us
```

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 20), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


```

---

### Post by smithc2005 on 2013-09-06
So it turns out I have no Internet access, but it does connect

---

### Post by chili555 on 2013-09-06
> **smithc2005 said:**
> I set it to US and all was fixed!!! Thank You!  Enlighten me on why this matters so much?I am not sure why; I just know that sometimes it helps. To make it persistent:```
gksudo gedit /etc/rc.local
```Add a single line above exit 0:```
iw reg set US
```Proofread, save, close and enjoy.

---

### Post by smithc2005 on 2013-09-06
I thought it was working since it connected but i have no internet access with it

---

### Post by chili555 on 2013-09-06
Let's have a look at:```
nm-tool
iwconfig
```Thanks.

---


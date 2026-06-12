---
title: "Wireless interface connects to wrong AP on boot"
date: 2008-08-01
forum: Networking &amp; Wireless
---

### Post by Pawel Stolowski on 2008-08-01
Hello,

I've a strange issue with wireless connection. Some setup information first:
- I've atheros-based NIC that works well with madwifi
- I've removed NetworkManager as I need a fixed (static) connection
- my ath0 interface is configured via /etc/network/interfaces with "auto" flag
- I use WPA2 and it's properly configured in the "interfaces" file

Now onto the problem... For some reason ath0 attempts to connect to wrong access point on startup (e.g. when Ubuntu boots up), but I can bring it up manually with no problems (sudo ifup ath0 - connects to correct AP and works fine).

Any idea on what may be wrong?

PS. BTW, I tried wicd (just out of curiosity) and it also would not connect to my AP automatically on boot - I had to manually select my AP to connect to it (and yes, "Automatically connect" option was set). I noticed that I had to click "Refresh" in wicd for my AP to appear on the list - is it possible the my AP gets unnoticed due to some delays in response? I haven't had any problems with any distro with this so far -- just with Hardy.

---

### Post by chili555 on 2008-08-01
> my ath0 interface is configured via /etc/network/interfacesI suggest specifying the MAC address of the access point you want to connect to in *interfaces.* Determine it with:```
sudo iwlist ath0 scan
```You will get a result like this:```
Cell 01 - Address: **99:13:19:62:8D:F7**
                    ESSID:"mylilrouter"
                    Mode:Master
                    Channel:11
=== snip ===
```Then specify it in *interfaces*:```
auto lo
iface lo inet loopback

auto ath0
iface ath0 inet dhcp
wireless-essid mylilrouter
wireless-key 096c7fblahfoo
wireless-ap 99:13:19:62:8D:F7
```

---

### Post by Pawel Stolowski on 2008-08-02
> **chili555 said:**
> I suggest specifying the MAC address of the access point you want to connect to in *interfaces.*
(...)


Hello,

That didn't help. My current interfaces entry for ath0 is:
```

auto ath0
iface ath0 inet static
	wpa-ssid foobar
	wpa-bssid 00:08:B1:C1:D1:01
	wpa-ap-scan 0
	wpa-scan-ssid 0
	wpa-driver wext
	wpa-proto WPA2
	wpa-key-mgmt WPA-PSK
	wpa-psk "********"
	address 192.168.0.5
	netmask 255.255.255.0
	gateway 192.168.0.254

```

The only workaround I've found so far is to remove "auto ath0" and add "/sbin/ifup ath0" line to /etc/rc.local, but I don't like it... Any other ideas on what maybe wrong?

Thanks,

Pawel

---

### Post by Pawel Stolowski on 2008-08-04
Ok, It looks like I've finally found a workaround for my problem. The solution is to configure wireless interface with dedicated wpa_supplicant config file. My entry for ath0 in /etc/network/interfaces:

```

auto ath0
iface ath0 inet static
	address 192.168.0.5
	netmask 255.255.255.0
	gateway 192.168.0.254
	wpa-driver madwifi
	wpa-conf /etc/wpa_supplicant/wpa_supplicant.conf

```

And in /etc/wpa_supplicant/wpa_supplicant.conf I have:

```

ap_scan=1
network={
	key_mgmt=NONE
	priority=-9999999
}
network={
	ssid="foobar"
	proto=RSN
	key_mgmt=WPA-PSK
	pairwise=TKIP
	group=TKIP
	psk="************"
	priority=1
}

```

Some conclusions:
- if I entered the above settings in "interfaces" file directly (no separate wpa config file) - it didn't work
- adding pairwise and group parameters seem to be crucial too

It tooks me several hours and a lot of frustration to figure this out... Maybe this helps someone.

---


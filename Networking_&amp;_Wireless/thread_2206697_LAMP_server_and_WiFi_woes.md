---
title: "LAMP server and WiFi woes"
date: 2014-02-20
forum: Networking &amp; Wireless
---

### Post by sdenham on 2014-02-20
Hi all,

So I'm trying to make sure I'm configuring WiFi properly.  For some reason it claims it cannot connect at boot up.  Can I get a sanity check?

Here's my /etc/wpa_supplicant/wpa_supplicant.conf:
```

network={
ssid="MySSIDgoesHere"
#psk="MyPSK"
psk=reallylonggeneratedkeyhere
}

```

Here is my /etc/network/interfaces:
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wpa-driver wext
wpa-conf /etc/wpa_supplicant/wpa_supplicant.conf

```

Bootup:
```

* Starting configure network device
Waiting for network configuration...
Waiting up to 60 more seconds for network configuration...
Booting system without full network configuration...

```

Once I log in:
```

steve@LAMP-server:~$ ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr XX:XX:XX:XX:XX:XX
          inet addr:10.XXX.XXX.16  Bcast:10.XXX.XXX.XXX  Mask:255.255.255.XXX
          inet6 addr: XXXX:XXXX/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:119 errors:0 dropped:0 overruns:0 frame:0
          TX packets:82 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:13874 (13.8 KB)  TX bytes:14449 (14.4 KB)

```

Why can it not connect during boot up but once I log in, it is able to pull an IP?  Does wpa_supplicant not function during boot up?  I don't mind it taking so long to boot, just would like it to go a little faster :)  I tried using 'rc.local' instead, but that doesn't fix the issue either.

Thanx,
Steve

---

### Post by sdenham on 2014-02-20
I solved my problem.  It appears that eth0 was trying to pull an IP even thought it had no cable plugged in.  I changed /etc/network/interfaces to:

```

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
#auto eth0
#iface eth0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
        wpa-driver wext
        wpa-conf /etc/wpa_supplicant/wpa_supplicant.conf

```

Now it boots properly.  I wonder if this is going to be a problem when I finish configuring my webserver and switch to a wired connection....

Hope someone else finds this useful.

Regards,
Steve

---


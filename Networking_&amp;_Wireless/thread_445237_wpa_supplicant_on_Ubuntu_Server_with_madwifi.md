---
title: "wpa_supplicant on Ubuntu Server with madwifi"
date: 2007-05-15
forum: Networking &amp; Wireless
---

### Post by JoeyJoeJoe on 2007-05-15
First of all madwifi appears to be working becuase I can see available wireless networks in my neighborhood when I run

```
wlanconfig ath0 list scan

```

ran
```
cp defconfig .config
```

updated .config file to include the following. /usr/erc/madwifi-0.9.3 is the location where I extracted my madwifi .tar file. I assume that's the "source"

```
CONFIG_DRIVER_MADWIFI=y
CFLAGS += -I/usr/src/madwifi-0.9.3
CONFIG_CTRL_IFACE=y

```
ran:
```
make clean
make
make install
```

used wpa_passphrase to update /etc/wpa_supplicant.conf which now reads

```
NETWORK={ 
     SSID="the ssid of my router"
     #psk="the wpa passphrase in plain english"
     psk="the hexidecimal result..."
key_mgmt=wpa-psk
proto=wpa
proto=rsn
}

```

I ran:

```
wpa_supplicant -Dmadwifi -iath0 -c/etc/wpa_supplicant.conf

```

and got the following errors:

```
Line 5: invalid key_mgmt 'wpa-psk'
Line 5: no key_mgmt values configured
Line 5: failed to parse key_mgmt 'wpa-psk'
Line 6: invalid proto 'wpa'
Line 6: no proto values configured.
Line 6: failed to parse proto 'wpa'
Line 7: invalid proto 'rsn'
Line 7: no proto values configured
Line 7: failed to parse proto 'rsn'
Line 8: failed to parse network block.
Failed to read or parse configuration '/etc/wpa_supplicant.conf'
```

Help me out here. This is probably an "duh" fix, but I'm stumped.

Thanks,
JJJ

---

### Post by spd106 on 2007-05-17
wpa_suppliacnt is clever enough to detect the encryption type most of the time, so you may not need those entries in your wpa_supplicant.conf.

Also try using capitals instead, like so
```

proto=WPA
key_mgnt=WPA-PSK

```

On Dapper I've only managed to get the madwifi driver to work, however since edgy I've found that the wext driver is just as good if not better. I'm not sure if that is an issue with madwifi or wpa_supplicant though.

---

### Post by tankmcp on 2007-05-19
you used:

wpa_supplicant -Dmadwifi -iath0 -c/etc/wpa_supplicant.conf

shouldn't it be 

wpa_supplicant -Dmadwifi -iath0 -c/etc/wpa_supplicant/wpa_supplicant.conf

?

Working on the same type of thing here. no luck yet

---


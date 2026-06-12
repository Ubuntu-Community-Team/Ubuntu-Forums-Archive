---
title: "Wireless Network stopped connecting Fujitsu Lifebook E8420"
date: 2014-05-08
forum: Networking &amp; Wireless
---

### Post by gebeer on 2014-05-08
I just installed 14.04 64Bit on A Fujitsu Lifebook E8420 from a USB stick.

When booting from USB and during installation, wireless network was working fine and the latest packages got downloaded during installation.

After first boot, the wifi connection didn't work anymore.

Here is what I get in sys.log when trying to connect:
```

May  8 20:25:18 gbr-LIFEBOOK-E8420 NetworkManager[779]: <info> Activation (wlan0) starting connection 'Funkfeuer-Norderney'
May  8 20:25:18 gbr-LIFEBOOK-E8420 NetworkManager[779]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
May  8 20:25:18 gbr-LIFEBOOK-E8420 NetworkManager[779]: <info> NetworkManager state is now CONNECTING
May  8 20:25:18 gbr-LIFEBOOK-E8420 NetworkManager[779]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
May  8 20:25:18 gbr-LIFEBOOK-E8420 NetworkManager[779]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
May  8 20:25:18 gbr-LIFEBOOK-E8420 NetworkManager[779]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
May  8 20:25:18 gbr-LIFEBOOK-E8420 NetworkManager[779]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
May  8 20:25:18 gbr-LIFEBOOK-E8420 NetworkManager[779]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
May  8 20:25:18 gbr-LIFEBOOK-E8420 NetworkManager[779]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
May  8 20:25:18 gbr-LIFEBOOK-E8420 NetworkManager[779]: <info> Activation (wlan0/wireless): access point 'Funkfeuer-Norderney' has security, but secrets are required.
May  8 20:25:18 gbr-LIFEBOOK-E8420 NetworkManager[779]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
May  8 20:25:18 gbr-LIFEBOOK-E8420 NetworkManager[779]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
May  8 20:25:18 gbr-LIFEBOOK-E8420 NetworkManager[779]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
May  8 20:25:18 gbr-LIFEBOOK-E8420 NetworkManager[779]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
May  8 20:25:18 gbr-LIFEBOOK-E8420 NetworkManager[779]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
May  8 20:25:18 gbr-LIFEBOOK-E8420 NetworkManager[779]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
May  8 20:25:18 gbr-LIFEBOOK-E8420 NetworkManager[779]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
May  8 20:25:18 gbr-LIFEBOOK-E8420 NetworkManager[779]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
May  8 20:25:18 gbr-LIFEBOOK-E8420 NetworkManager[779]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
May  8 20:25:18 gbr-LIFEBOOK-E8420 NetworkManager[779]: <info> Activation (wlan0/wireless): connection 'Funkfeuer-Norderney' has security, and secrets exist.  No new secrets needed.
May  8 20:25:18 gbr-LIFEBOOK-E8420 NetworkManager[779]: <info> Config: added 'ssid' value 'Funkfeuer Norderney'
May  8 20:25:18 gbr-LIFEBOOK-E8420 NetworkManager[779]: <info> Config: added 'scan_ssid' value '1'
May  8 20:25:18 gbr-LIFEBOOK-E8420 NetworkManager[779]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
May  8 20:25:18 gbr-LIFEBOOK-E8420 NetworkManager[779]: <info> Config: added 'psk' value '<omitted>'
May  8 20:25:18 gbr-LIFEBOOK-E8420 NetworkManager[779]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
May  8 20:25:18 gbr-LIFEBOOK-E8420 NetworkManager[779]: <info> Config: set interface ap_scan to 1
May  8 20:22:29 gbr-LIFEBOOK-E8420 wpa_supplicant[959]: wlan0: Reject scan trigger since one is already pending
May  8 20:25:18 gbr-LIFEBOOK-E8420 wpa_supplicant[959]: wlan0: SME: Trying to authenticate with 00:12:17:b2:ff:5a (SSID='Funkfeuer Norderney' freq=2462 MHz)
May  8 20:25:18 gbr-LIFEBOOK-E8420 kernel: [ 1822.658617] wlan0: authenticate with 00:12:17:b2:ff:5a
May  8 20:25:18 gbr-LIFEBOOK-E8420 NetworkManager[779]: <info> (wlan0): supplicant interface state: disconnected -> authenticating
May  8 20:25:18 gbr-LIFEBOOK-E8420 kernel: [ 1822.713341] wlan0: direct probe to 00:12:17:b2:ff:5a (try 1/3)
May  8 20:25:18 gbr-LIFEBOOK-E8420 kernel: [ 1822.916059] wlan0: send auth to 00:12:17:b2:ff:5a (try 2/3)
May  8 20:25:19 gbr-LIFEBOOK-E8420 kernel: [ 1823.040092] wlan0: send auth to 00:12:17:b2:ff:5a (try 3/3)
May  8 20:25:19 gbr-LIFEBOOK-E8420 kernel: [ 1823.168067] wlan0: authentication with 00:12:17:b2:ff:5a timed out
May  8 20:25:23 gbr-LIFEBOOK-E8420 kernel: [ 1827.718289] wlan0: deauthenticating from 00:12:17:b2:ff:5a by local choice (reason=3)
May  8 20:25:23 gbr-LIFEBOOK-E8420 NetworkManager[779]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
May  8 20:25:23 gbr-LIFEBOOK-E8420 NetworkManager[779]: <info> (wlan0): supplicant interface state: disconnected -> scanning
May  8 20:25:33 gbr-LIFEBOOK-E8420 kernel: [ 1837.824488] wlan0: authenticate with 00:12:17:b2:ff:5a
May  8 20:25:33 gbr-LIFEBOOK-E8420 kernel: [ 1837.883915] wlan0: direct probe to 00:12:17:b2:ff:5a (try 1/3)
May  8 20:25:33 gbr-LIFEBOOK-E8420 NetworkManager[779]: <info> (wlan0): supplicant interface state: scanning -> authenticating
May  8 20:25:34 gbr-LIFEBOOK-E8420 kernel: [ 1838.084052] wlan0: direct probe to 00:12:17:b2:ff:5a (try 2/3)
May  8 20:25:34 gbr-LIFEBOOK-E8420 kernel: [ 1838.288061] wlan0: direct probe to 00:12:17:b2:ff:5a (try 3/3)
May  8 20:25:34 gbr-LIFEBOOK-E8420 kernel: [ 1838.492046] wlan0: authentication with 00:12:17:b2:ff:5a timed out
May  8 20:25:38 gbr-LIFEBOOK-E8420 kernel: [ 1842.884139] wlan0: deauthenticating from 00:12:17:b2:ff:5a by local choice (reason=3)
May  8 20:25:38 gbr-LIFEBOOK-E8420 NetworkManager[779]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
May  8 20:25:39 gbr-LIFEBOOK-E8420 NetworkManager[779]: <info> (wlan0): supplicant interface state: disconnected -> scanning
May  8 20:25:44 gbr-LIFEBOOK-E8420 NetworkManager[779]: <warn> Activation (wlan0/wireless): association took too long, failing activation.
May  8 20:25:44 gbr-LIFEBOOK-E8420 NetworkManager[779]: <info> (wlan0): device state change: config -> failed (reason 'SSID not found') [50 120 53]
May  8 20:25:44 gbr-LIFEBOOK-E8420 NetworkManager[779]: <info> NetworkManager state is now DISCONNECTED
May  8 20:25:44 gbr-LIFEBOOK-E8420 NetworkManager[779]: <warn> Activation (wlan0) failed for connection 'Funkfeuer-Norderney'
May  8 20:25:44 gbr-LIFEBOOK-E8420 NetworkManager[779]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
May  8 20:25:44 gbr-LIFEBOOK-E8420 NetworkManager[779]: <info> (wlan0): deactivating device (reason 'none') [0]
May  8 20:25:33 gbr-LIFEBOOK-E8420 wpa_supplicant[959]: wlan0: SME: Trying to authenticate with 00:12:17:b2:ff:5a (SSID='Funkfeuer Norderney' freq=2462 MHz)
May  8 20:25:44 gbr-LIFEBOOK-E8420 wpa_supplicant[959]: wlan0: Reject scan trigger since one is already pending
May  8 20:25:44 gbr-LIFEBOOK-E8420 NetworkManager[779]: <info> (wlan0): supplicant interface state: scanning -> disconnected
May  8 20:25:44 gbr-LIFEBOOK-E8420 NetworkManager[779]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
```

lshw -C Network:
```

lshw -C Network
  *-network               
       description: Ethernet interface
       product: 82567LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:23:26:5e:da:72
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=2.3.2-k duplex=full firmware=1.8-3 ip=192.168.2.33 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:44 memory:f2400000-f241ffff memory:f2425000-f2425fff ioport:1840(size=32)
  *-network
       description: Wireless interface
       product: Ultimate N WiFi Link 5300
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:20:00.0
       logical name: wlan0
       version: 00
       serial: 00:21:6a:5f:3b:f4
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.13.0-24-generic firmware=8.83.5.1 build 33692 latency=0 link=no multicast=yes wireless=IEEE 802.11abg
       resources: irq:47 memory:f2000000-f2001fff

```

I searched the forum and found these [two]("http://ubuntuforums.org/showthread.php?t=2220377") [posts]("http://ubuntuforums.org/showthread.php?t=2219917") that might be related.

My /etc/modprobe.d/iwlwifi.conf now:
> options iwlwifi 11n_disable=1

This doesn't help.

Here's the output of varunendra's Wireless Script:
[ATTACH]252996[/ATTACH]
Please help. Thank you.

---


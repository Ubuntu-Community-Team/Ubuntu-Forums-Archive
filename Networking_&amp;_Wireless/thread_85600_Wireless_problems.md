---
title: "Wireless problems"
date: 2005-11-03
forum: Networking &amp; Wireless
---

### Post by finni on 2005-11-03
Hello, 

I've got wireless problems after updating from hoary to breezy. It worked ok for a week or so, then all of the sudden I did not have wireless at all. I managed to get wireless working - well sort-of - with updating wpa supplicant to 0.4.6. It did work yesterday pretty nicely but today after booting the laptop my wireless connection keeps disconnecting and connecting all the time (about 20 s interval).
I did have a working wlan on hoary.. :confused:  

I've got a HP nc6000 laptop with atheron chipset wireless mini-pci card and D-link DWL-2000AP+ wireless AP. The AP is set up to use WPA/PSK encryption method.

ifconfig:
```

ath0      Link encap:Ethernet  HWaddr ##:##:##:##:##:##
          inet addr:###.###.###.###  Bcast:###.###.###.###  Mask:###.###.###.###
          inet6 addr: ####::###:####:####:###/## Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12400 errors:26369 dropped:0 overruns:0 frame:26369
          TX packets:13823 errors:6 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:200
          RX bytes:8840502 (8.4 MiB)  TX bytes:1600770 (1.5 MiB)
          Interrupt:11 Memory:f8cc0000-f8cd0000

```

iwconfig:
```

ath0      IEEE 802.11g  ESSID:"####"  Nickname:"####"
          Mode:Managed  Frequency:2.### GHz  Access Point: ##:##:##:##:##:##
          Bit Rate:54 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:####-####-####-####-####-####-####-####   Security mode:restricted
          Power Management:off
          Link Quality=69/94  Signal level=-26 dBm  Noise level=-95 dBm
          Rx invalid nwid:5  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:6  Invalid misc:6  Missed beacon:0

```

/etc/network/interfaces:
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
#auto eth0
#iface eth0 inet dhcp

# Wlan
auto ath0
iface ath0 inet dhcp

```

/etc/default/wpasupplicant:
```

# /etc/default/wpasupplicant
# WARNING! Make sure you have a configuration file!

ENABLED=1

# Useful flags:
#  -D <driver>          Wireless drive, typically optional.
#  -i <ifname>          Interface
#  -c <config file>     Configuration file
#  -d                   Debugging (-dd for more)
#  -w                   Wait for interface to come up

# See the manual page wpa_supplicant(1) for more options and information.

OPTIONS="-w -i ath0 -D madwifi -c /etc/wpa_supplicant.conf -d"

```

/etc/wpa_supplicant.conf:
```

network={
       ssid="####"
       scan_ssid=1
       proto=WPA
       key_mgmt=WPA-PSK
       pairwise=TKIP
       group=TKIP CCMP
#       psk="plain"
       psk=#################################################################
}

```

lspci:
```

0000:02:04.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)

```

lsmod:
```

ath_pci                69148  0
ath_rate_sample        14344  1 ath_pci
ath_hal               148432  3 ath_pci,ath_rate_sample
wlan                  120988  4 wlan_tkip,ath_pci,ath_rate_sample
wlan_tkip              10752  2

```

dmesg:
```

[4294700.617000] ACPI: PCI Interrupt 0000:00:1f.6[B] -> Link [C0C3] -> GSI 11 (level,
low) -> IRQ 11
[4294700.617000] PCI: Setting latency timer of device 0000:00:1f.6 to 64
[4294700.915000] ath_hal: 0.9.14.9 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413)
[4294700.927000] wlan: 0.8.6.0 (EXPERIMENTAL)
[4294700.938000] ath_rate_sample: 1.2
[4294700.952000] ath_pci: 0.9.6.0 (EXPERIMENTAL)
[4294700.963000] ACPI: PCI Interrupt Link [C0C7] enabled at IRQ 11
[4294700.963000] ACPI: PCI Interrupt 0000:02:04.0[A] -> Link [C0C7] -> GSI 11 (level,
low) -> IRQ 11
[4294701.242000] Build date: Oct 11 2005
[4294701.242000] Debugging version (IEEE80211)
[4294701.242000] ath0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[4294701.242000] ath0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[4294701.242000] ath0: H/W encryption support: WEP AES AES_CCM TKIP
[4294701.242000] ath0: mac 5.6 phy 4.1 radio 1.7
[4294701.242000] ath0: Use hw queue 1 for WME_AC_BE traffic
[4294701.242000] ath0: Use hw queue 0 for WME_AC_BK traffic
[4294701.242000] ath0: Use hw queue 2 for WME_AC_VI traffic
[4294701.242000] ath0: Use hw queue 3 for WME_AC_VO traffic
[4294701.242000] ath0: Use hw queue 8 for CAB traffic
[4294701.242000] ath0: Use hw queue 9 for beacons
[4294701.242000] Debugging version (ATH)
[4294701.242000] ath0: Atheros 5212: mem=0x90080000, irq=11

```

---

### Post by finni on 2005-11-10
No problem anymore. Wifi-radar should do it for others with this problem.

I chose to write my own /etc/init.d/wlan -startup script and removed all the entries of wpasupplicant and wifi-radar from /etc/rc* and added my wlan -script symlinks on their place.

---

### Post by finni on 2005-12-01
Clean install with Ubuntu breezy and again no networking. 

EDIT:
I managed to install wpa supplicant 0.4.7 with libssl 0.9.8 and now dhcp works again. :cool: 

You can get wpa supplicant 0.4.7 or newer from here: [http://archive.ubuntu.com/ubuntu/pool/universe/w/wpasupplicant/](http://archive.ubuntu.com/ubuntu/pool/universe/w/wpasupplicant/)

but before installing wpa supplicant you need to install libssl 0.9.8:
[http://archive.ubuntu.com/ubuntu/pool/main/o/openssl/](http://archive.ubuntu.com/ubuntu/pool/main/o/openssl/)

---


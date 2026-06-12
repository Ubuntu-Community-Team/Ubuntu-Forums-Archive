---
title: "wireless setup- interface eth1 is active but not connection"
date: 2006-11-11
forum: Networking &amp; Wireless
---

### Post by jns4x on 2006-11-11
im having trouble setting up my wireless internet connection on my laptop. Network settings indicate that interface eth1 is active.  heres the output to iwconfig (have to retype output, sorry)

lo         no wireless extensions.
eth0       no wireless extensions.
eth1       IEEE 802.11b  ESSID: "knxxxx" Nickname:"HEXXXX"
           Mode: Managed Frequency: 2.412 GHz  Access Point: None
           Bit Rate: 2 Mb/s    Sensitivity: 1/3
           Retry limit: 4  RTS thr: off     Fragment thr: off
      Power management: off
      Link quality= 0/92  Signal level=134/153  Noise level:134/153
      Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
      Tx excessive retries: 0 Invalid misc:0    Missed beacon: 0

sit0     no wireless extensions.

Any suggestions.

---

### Post by FrodoB on 2006-11-11
It just looks good, it may not be working actually. Please post the outputs from:

dmesg (just the part around where eth1 is found)

iwconfig

ifconfig

and post the contents of /etc/network/interfaces.

Then some folks can probably see where you need to go.

---

### Post by jns4x on 2006-11-12
output to dmesq.....(eth1 section)

eth1: Hardware identity 0001:0001:0004:0000
eth1: Station identity 001f:0001:0006:0004
eth1: Firmware detected as Lucent/Agere 6.04
eth1: Ad-hoc demo mode supported
eth1: WEP supported, 104-bit key
eth1: MAC address 00:01:F4:EC:43:F8
eth1: Station name "HERMES I"
eth1: ready
eth1: index 0x01: Vcc 5.0, irq 3, io 0x0100-0x013f

iwconfig output (see earlier post)

ifconfig output...

eth1  Link encap:Ethernet  HWaddr 00:01:F4:EC:43:F8
      UP BROADCAST MULTICAST MTU:1500  Metric:1
      RX packets:0 errors:0 dropped:0 overruns:0 frame:0
      TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
      collisions:0 txqueuelen:1000
      RX bytes:0 (0.0b)  TX bytes: 0 (0.0 b)
      Interrupt:3 Base address:0x100

/etc/network/interfaces output...
bash: /etc/network/interfaces: Permission denied

---

### Post by FrodoB on 2006-11-12
Sorry just type:

$ more /etc/network/interfaces

publish the output

---


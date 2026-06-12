---
title: "'device not ready' after connecting to hotspot in ASUS computer"
date: 2017-01-14
forum: Networking &amp; Wireless
---

### Post by gvso on 2017-01-14
I'm able to connect to a wifi network with no issues. However, when I try to connect my hotspot, wifi stops working and the message 'device not ready' appears.

```

lspci -nnk | grep -A2 0280

02:00.0 Network controller [0280]: Ralink corp. RT3290 Wireless 802.11n 1T/1R PCIe [1814:3290]
    Subsystem: Foxconn International, Inc. RT3290 Wireless 802.11n 1T/1R PCIe [105b:e055]
    Kernel driver in use: rt2800pci

```

```

lsmod | grep -e rt2800pci -e asus

asus_nb_wmi            24576  0
asus_wmi               28672  1 asus_nb_wmi
sparse_keymap          16384  1 asus_wmi
rt2800pci              16384  0
rt2800mmio             20480  1 rt2800pci
rt2800lib              94208  2 rt2800pci,rt2800mmio
rt2x00pci              16384  1 rt2800pci
rt2x00mmio             16384  2 rt2800pci,rt2800mmio
rt2x00lib              57344  5 rt2x00pci,rt2800lib,rt2800pci,rt2800mmio,rt2x00mmio
eeprom_93cx6           16384  1 rt2800pci
wmi                    20480  1 asus_wmi
video                  40960  2 i915,asus_wmi

```

```

rfkill list all

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: asus-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no

```

Although rfkill says it's not hard blocked neither soft blocked, fn + f2 doesn't work. I have an ASUS X200CA.

Thanks in advance

---

### Post by wildmanne39 on 2017-01-14
Hi, please click on the wireless script in my signature, follow the directions for running it and posting the results back here using code tags with the hotspot that you can not connect too.

---


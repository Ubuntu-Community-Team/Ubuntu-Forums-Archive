---
title: "Questions around RTL8812AE 802.11ac PCIe Wireless Network Adapter"
date: 2018-07-24
forum: Networking &amp; Wireless
---

### Post by doktorOblivion on 2018-07-24
I recently purchased a new PCIe wireless NIC hoping to get a/c tri-band connectivity out of it.  However, I am only able to get the traditional g across 2.4Ghz.  I did the following to get my current support.

- git cloned the rtlwifi-next project ([https://github.com/rtlwifi-linux/rtlwifi-next](https://github.com/rtlwifi-linux/rtlwifi-next))
- HACKED base.c and wifi.h to add the following:   #define IEEE80211_NUM_BANDS NUM_NL80211_BANDS
- ran sudo make install
- rebooted

That seemed to get the card working, albeit limping along in g mode.  Problem is, when I try to connect to a/c using 5Ghz it fails with a rather odd authentication time out issue, even though I know I am passing in the correct password.  Here is what I see in dmesg:

```
[  750.926951] wlp12s0: authenticate with d0:17:c2:eb:41:18
[  750.927592] wlp12s0: send auth to d0:17:c2:eb:41:18 (try 1/3)
[  751.030320] wlp12s0: send auth to d0:17:c2:eb:41:18 (try 2/3)
[  751.134323] wlp12s0: send auth to d0:17:c2:eb:41:18 (try 3/3)
[  751.238325] wlp12s0: authentication with d0:17:c2:eb:41:18 timed out
```

Here is the device, using (lshw -C network):

```
       Beschreibung: Kabellose Verbindung
       Produkt: RTL8812AE 802.11ac PCIe Wireless Network Adapter
       Hersteller: Realtek Semiconductor Co., Ltd.
       Physische ID: 0
       Bus-Informationen: pci@0000:0c:00.0
       Logischer Name: wlp12s0
       Version: 01
       Seriennummer: e8:4e:06:61:83:17
       Breite: 64 bits
       Takt: 33MHz
       Fähigkeiten: pm msi pciexpress bus_master cap_list ethernet physical wireless
       Konfiguration: broadcast=yes driver=rtl8821ae driverversion=4.4.0-130-generic firmware=N/A ip=192.168.1.138 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       Ressourcen: irq:62 ioport:a000(Größe=256) memory:fe100000-fe103fff
  *-network DEAKTIVIERT

```

Thoughts on getting the 5Ghz connections working?  I am currently happy just getting the 2.4Ghz working again, but if I could enjoy the other channel (which I do on Windows 10, OOTB), it would be a bonus.
Please let me know if there are additional data needed.

I have the following system:

```
DISTRIB_RELEASE=16.04
DISTRIB_CODENAME=xenial
DISTRIB_DESCRIPTION="Ubuntu 16.04.5 LTS"
NAME="Ubuntu"
VERSION="16.04.5 LTS (Xenial Xerus)"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu 16.04.5 LTS"
VERSION_ID="16.04"

Linux oblivion 4.4.0-130-generic #156-Ubuntu SMP Thu Jun 14 08:53:28 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

```

---


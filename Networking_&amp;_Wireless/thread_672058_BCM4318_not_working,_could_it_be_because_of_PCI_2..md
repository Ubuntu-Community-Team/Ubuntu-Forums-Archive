---
title: "BCM4318 not working, could it be because of PCI 2.1?"
date: 2008-01-19
forum: Networking &amp; Wireless
---

### Post by kaimi&#326;iece on 2008-01-19
I'm trying to get BCM4318 working on 2.6.22-14-server. I followed the instructions at WifiDocs, and this log should explain my current progress better than I could:

```
# modprobe -r bcm43xx
# modprobe bcm43xx
# dmesg | tail
[  262.450000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[  262.490000] bcm43xx driver
[  262.490000] ACPI: PCI Interrupt 0000:00:11.0[A] -> Link [LNKA] -> GSI 12 (level, low) -> IRQ 12
[  283.040000] ACPI: PCI interrupt for device 0000:00:11.0 disabled
[  283.040000] ieee80211_crypt: unregistered algorithm 'NULL'
[  286.270000] ieee80211_crypt: registered algorithm 'NULL'
[  286.290000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[  286.290000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[  286.320000] bcm43xx driver
[  286.330000] ACPI: PCI Interrupt 0000:00:11.0[A] -> Link [LNKA] -> GSI 12 (level, low) -> IRQ 12
# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4318"
          Mode:Managed  Access Point: Invalid
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

# ifup eth1
Ignoring unknown interface eth1=eth1.
```

I was wondering if the cause could be my motherboard only supporting PCI 2.1 and not 2.2. This was the reason a different WLAN adapter from RaLink didn't work on this box.

---

### Post by kaimi&#326;iece on 2008-01-19
This is what dmesg shows if I try to use the ndiswrapper driver:

```
[ 3003.440000] ndiswrapper version 1.51 loaded (smp=yes, preempt=no)
[ 3003.490000] ndiswrapper: driver bcmwl5 (Broadcom,02/11/2005, 3.100.64.0) loaded
[ 3003.490000] ACPI: PCI Interrupt 0000:00:11.0[A] -> Link [LNKA] -> GSI 12 (level, low) -> IRQ 12
[ 3003.500000] ndiswrapper (NdisWriteErrorLogEntry:191): log: C000138D, count: 1, return_address: ccb14d7b
[ 3003.500000] ndiswrapper (NdisWriteErrorLogEntry:194): code: 0x10b
[ 3003.500000] ndiswrapper (mp_init:216): couldn't initialize device: C0000001
[ 3003.500000] ndiswrapper (pnp_start_device:439): Windows driver couldn't initialize the device (C0000001)
[ 3003.500000] ndiswrapper (mp_halt:259): device cbe88500 is not initialized - not halting
[ 3003.500000] ndiswrapper: device eth%d removed
[ 3003.500000] ACPI: PCI interrupt for device 0000:00:11.0 disabled
[ 3003.500000] ndiswrapper: probe of 0000:00:11.0 failed with error -22
[ 3003.520000] usbcore: registered new interface driver ndiswrapper
```

---

### Post by tgalati4 on 2008-01-19
Assuming this is a pci wireless card, you could try changing pci slots.  Some motherboards have fixed interrupts for each slot and you could have an interference problem.  Air Force one cards can be troublesome to set up, but once working they generally work pretty well.

---

### Post by kaimi&#326;iece on 2008-01-19
Changing the PCI slot worked, in the sense that the card now installs and shows up in iwconfig with ndiswrapper, but I still get the same error if I try to use ifup.

```
# ndiswrapper -l
bcmwl5 : driver installed
        device (14E4:4318) present (alternate driver: bcm43xx)
# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated
          Bit Rate:54 Mb/s   Tx-Power:25 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

# ifup eth1
Ignoring unknown interface eth1=eth1.
```

---

### Post by kaimi&#326;iece on 2008-01-20
Bump.

---

### Post by gobuntu on 2008-01-20
I use the ndiswrapper for even when I got BCM working without it, the power (reach)  of the wifi was limitted (rather inadequate).

I look forward to that not being so in the nearest possible future.

---


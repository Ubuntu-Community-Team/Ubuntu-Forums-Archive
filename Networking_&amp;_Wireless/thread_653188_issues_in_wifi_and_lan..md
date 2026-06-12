---
title: "issues in wifi and lan."
date: 2007-12-29
forum: Networking &amp; Wireless
---

### Post by afk on 2007-12-29
i've got an odd issue let me make this easy first off i have 2 wifi lappys both on ubuntu the vaio works fine this acer tho use's a diffent kinda card and its been giving me an issue i can't seem to fix 


ok so i can access this website? and anything outside the router but nothing inside the lan. i can from any other pc but this one and Wired it works fine. so its gotta be something wifi related

wlan0     Link encap:Ethernet  HWaddr 00:00:00:00:00:00
          inet addr:123.123.1.101  Bcast:123.123.1.255  Mask:255.255.255.0
          inet6 addr: fe80::200:ff:fe00:0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:219575 errors:0 dropped:0 overruns:0 frame:0
          TX packets:152927 errors:0 dropped:4 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:260490679 (248.4 MB)  TX bytes:28217839 (26.9 MB)
          Interrupt:19 Memory:f2200000-f2210000


my gateway ofcorse is 123.123.1.1


wlan0     IEEE 802.11g  ESSID:"eh-ef-kay"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:14:BF:BE:E7:2F
          Bit Rate=54 Mb/s
          Encryption key:******************   Security mode:restricted
          Power Management:off
          Link Quality:100/100  Signal level:-26 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:20010  Invalid misc:39457   Missed beacon:0



so here i am asking :D i'm not a newbie i just haven't been able to figure this one out
Thanks in advance.

btw card in the vaio is a intel pro wireless ABG 

this one is an atheros here is the output from lspci
also would be good to prolly note its running under ndiswrapper


05:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)

---

### Post by afk on 2007-12-31
so i've come to the conclusion its something to do with ndiswrapper

Dec 31 19:45:06 ddosin kernel: [151423.648127] ndiswrapper (NdisMIndicateStatus:2053): Unrecognized PMKID_CANDIDATE_LIST ignored
Dec 31 19:45:19 ddosin NetworkManager: <info>  Updating allowed wireless network lists.
Dec 31 19:46:03 ddosin kernel: [151480.440047] ndiswrapper (NdisMIndicateStatus:2053): Unrecognized PMKID_CANDIDATE_LIST ignored
Dec 31 19:46:30 ddosin kernel: [151507.736935] ndiswrapper (NdisMIndicateStatus:2053): Unrecognized PMKID_CANDIDATE_LIST ignored
Dec 31 19:47:00 ddosin kernel: [151537.736735] ndiswrapper (NdisMIndicateStatus:2053): Unrecognized PMKID_CANDIDATE_LIST ignored
Dec 31 19:47:30 ddosin kernel: [151567.744355] ndiswrapper (NdisMIndicateStatus:2053): Unrecognized PMKID_CANDIDATE_LIST ignored
Dec 31 19:48:35 ddosin kernel: [151632.627368] ndiswrapper (NdisMIndicateStatus:2053): Unrecognized PMKID_CANDIDATE_LIST ignored
Dec 31 19:49:40 ddosin kernel: [151697.443569] ndiswrapper (NdisMIndicateStatus:2053): Unrecognized PMKID_CANDIDATE_LIST ignored
Dec 31 19:50:44 ddosin kernel: [151761.804852] ndiswrapper (NdisMIndicateStatus:2053): Unrecognized PMKID_CANDIDATE_LIST ignored
Dec 31 19:51:56 ddosin kernel: [151833.521144] ndiswrapper (NdisMIndicateStatus:2053): Unrecognized PMKID_CANDIDATE_LIST ignored
Dec 31 19:53:07 ddosin kernel: [151903.809543] ndiswrapper (NdisMIndicateStatus:2053): Unrecognized PMKID_CANDIDATE_LIST ignored
Dec 31 19:54:01 ddosin kernel: [151958.293648] ndiswrapper (NdisMIndicateStatus:2053): Unrecognized PMKID_CANDIDATE_LIST ignored
Dec 31 19:54:37 ddosin kernel: [151993.579532] ndiswrapper (NdisMIndicateStatus:2053): Unrecognized PMKID_CANDIDATE_LIST ignored
Dec 31 19:55:08 ddosin kernel: [152024.580276] ndiswrapper (NdisMIndicateStatus:2053): Unrecognized PMKID_CANDIDATE_LIST ignored


thats debug

heres syslog

Dec 31 19:42:01 ddosin NetworkManager: <debug> [1199148121.728319] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_0')$
Dec 31 19:42:01 ddosin NetworkManager: <debug> [1199148121.752269] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port$
Dec 31 19:42:02 ddosin kernel: [151240.093593] input: PS/2 Mouse as /class/input/input9

heres dmesg 

[   36.364246] ACPI: PCI Interrupt Link [LK4E] enabled at IRQ 19
[   36.364256] ACPI: PCI Interrupt 0000:05:00.0[A] -> Link [LK4E] -> GSI 19 (level, low) -> IRQ 19
[   36.364299] ndiswrapper (ZwClose:2247): closing handle 0x0 not implemented
[   36.364430] PCI: Setting latency timer of device 0000:05:00.0 to 64
[   36.776655] ndiswrapper: using IRQ 19
[   36.977269] wlan0: ethernet device 00:00:00:00:00:00 using serialized NDIS driver: net5211, version: 0x50003, NDIS version: 0x501, vendor: '', 168C:001C.5.conf
[   36.981371] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK

kern.log pops this out over and over and over.


Dec 31 19:42:44 ddosin kernel: [151282.463179] ndiswrapper (NdisMIndicateStatus:2053): Unrecognized PMKID_CANDIDATE_LIST ignored
Dec 31 19:44:01 ddosin kernel: [151358.939203] ndiswrapper (NdisMIndicateStatus:2053): Unrecognized PMKID_CANDIDATE_LIST ignored
Dec 31 19:45:06 ddosin kernel: [151423.648127] ndiswrapper (NdisMIndicateStatus:2053): Unrecognized PMKID_CANDIDATE_LIST ignored
Dec 31 19:46:03 ddosin kernel: [151480.440047] ndiswrapper (NdisMIndicateStatus:2053): Unrecognized PMKID_CANDIDATE_LIST ignored
Dec 31 19:46:30 ddosin kernel: [151507.736935] ndiswrapper (NdisMIndicateStatus:2053): Unrecognized PMKID_CANDIDATE_LIST ignored
Dec 31 19:47:00 ddosin kernel: [151537.736735] ndiswrapper (NdisMIndicateStatus:2053): Unrecognized PMKID_CANDIDATE_LIST ignored
Dec 31 19:47:30 ddosin kernel: [151567.744355] ndiswrapper (NdisMIndicateStatus:2053): Unrecognized PMKID_CANDIDATE_LIST ignored
Dec 31 19:48:35 ddosin kernel: [151632.627368] ndiswrapper (NdisMIndicateStatus:2053): Unrecognized PMKID_CANDIDATE_LIST ignored
Dec 31 19:49:40 ddosin kernel: [151697.443569] ndiswrapper (NdisMIndicateStatus:2053): Unrecognized PMKID_CANDIDATE_LIST ignored
Dec 31 19:50:44 ddosin kernel: [151761.804852] ndiswrapper (NdisMIndicateStatus:2053): Unrecognized PMKID_CANDIDATE_LIST ignored
Dec 31 19:51:56 ddosin kernel: [151833.521144] ndiswrapper (NdisMIndicateStatus:2053): Unrecognized PMKID_CANDIDATE_LIST ignored
Dec 31 19:53:07 ddosin kernel: [151903.809543] ndiswrapper (NdisMIndicateStatus:2053): Unrecognized PMKID_CANDIDATE_LIST ignored

any input?

---

### Post by kegobeer on 2007-12-31
Did you get any errors when you installed the drivers under ndiswrapper?  Can you post the steps you took when you installed the drivers?

---


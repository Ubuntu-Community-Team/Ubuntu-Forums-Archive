---
title: "Networking problems with dell 640m and the 1390 wireless card"
date: 2007-02-17
forum: Networking &amp; Wireless
---

### Post by ubuntalicious on 2007-02-17
Hi guys, I'm new to ubuntu and figured I'd give it a shot on my new dell 640m laptop.

I am having several problems, including my wireless card.  I'm realizing that getting the dell 1390 card was a mistake.

So as I said, I have the dell 1390 card and I've tried all of the tutorials and posts on this forum for getting it to work, but still no success.

I installed the latest version of ndiswrapper, installed the most recent bcmwl5.inf driver that I downloaded from dell, and configured everything.

The network tool now recognizes my card as eth1, but it doesn't connect to my network when I type in my SSID and WEP key.  The only thing that I did different from the tutorial at [waningsun]("http://wiki.waningsun.net/index.php?title=Dell_E1405_and_Broadcom_4311_wireless_HOWTO")  is that he must have used an older version of the dell driver because it has been updated since he wrote that tutorial.

One thing that I've noticed is that when I run iwconfig, it displays ESSID as "off/any" even though in the network tool it displays the SSID that I entered.

Any help is much appreciated.


Thanks,
Ben

---

### Post by ubuntalicious on 2007-02-17
One other thing that might help, here is the relevant output from when I run dmesg:


[17179585.092000] ndiswrapper version 1.27 loaded (preempt=no,smp=yes)
[17179585.172000] ndiswrapper: driver bcmwl5 (Broadcom,10/12/2006, 4.100.15.5) loaded
[17179585.172000] ACPI: PCI Interrupt 0000:0c:00.0[A] -> GSI 17 (level, low) -> IRQ 177
[17179585.172000] PCI: Setting latency timer of device 0000:0c:00.0 to 64
[17179585.176000] ndiswrapper: using IRQ 177
[17179585.848000] wlan0: vendor: ''
[17179585.848000] wlan0: ethernet device 00:1a:92:46:51:45 using NDIS driver bcmwl5, 14E4:4311.5.conf
[17179585.848000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[17179585.848000] ndiswrapper: changing interface name from 'wlan0' to 'eth1'
[17179585.848000] ndiswrapper (wrap_procfs_add_ndis_device:364): eth1 already registered?
[17179585.852000] usbcore: registered new driver ndiswrapper




Is it supposed to say "eth1 already registered?"


Thanks,
Ben

---


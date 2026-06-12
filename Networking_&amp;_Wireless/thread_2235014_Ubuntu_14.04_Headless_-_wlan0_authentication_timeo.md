---
title: "Ubuntu 14.04 Headless - wlan0 authentication timeout (iwlwifi)"
date: 2014-07-18
forum: Networking &amp; Wireless
---

### Post by edvar on 2014-07-18
i'm running a headless ubuntu 14.04 server on an Intel NUC and wifi is not working.

I'm using an Intel 7260 wifi card:

> 02:00.0 Network controller: Intel Corporation Wireless 7260 (rev 73)
	Subsystem: Intel Corporation Dual Band Wireless-AC 7260
	Flags: bus master, fast devsel, latency 0, IRQ 62
	Memory at f7c00000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: [c8] Power Management version 3
	Capabilities: [d0] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [40] Express Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting
	Capabilities: [140] Device Serial Number 80-86-f2-ff-ff-26-d7-11
	Capabilities: [14c] Latency Tolerance Reporting
	Capabilities: [154] Vendor Specific Information: ID=cafe Rev=1 Len=014 <?>
	Kernel driver in use: iwlwifi

But I cannot get it to connect:

> Jul 18 21:26:32 stack1 kernel: [  324.003440] wlan0: authenticate with XX:XX:XX:XX:XX:XX
Jul 18 21:26:32 stack1 kernel: [  324.004657] wlan0: direct probe to XX:XX:XX:XX:XX:XX (try 1/3)
Jul 18 21:26:33 stack1 kernel: [  324.206155] wlan0: direct probe to XX:XX:XX:XX:XX:XX (try 2/3)
Jul 18 21:26:33 stack1 kernel: [  324.410081] wlan0: direct probe to XX:XX:XX:XX:XX:XX (try 3/3)
Jul 18 21:26:33 stack1 kernel: [  324.613285] wlan0: authentication with XX:XX:XX:XX:XX:XX timed out

This is what I get on iwconfig:

> wlan0     IEEE 802.11abgn  ESSID:"XXXXX"  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr: off   Fragment thr: off
          Power Management: on

I had the same problem with a laptop but as soon as I installed a xubuntu desktop environment with NetworkManager everything started working fine automagically.

I want to use the NUC as a KVM Host and don't want to install any GUI on it. Any ideas on how to get it working?

---

### Post by steeldriver on 2014-07-18
How are you configuring the interface?

Is your access point running in N mode or G mode? some of the Intel devices seem to have problems with N and need to be forced to G (i.e. 11n_disable) to get a stable connection

---

### Post by edvar on 2014-07-18
The access point is running Wireless N and this is an AC wifi adapter. The same adapter on another computer works fine with wireless N if I'm running a GUI with Network Manager. 

Here's the config:

> auto wlan0
iface wlan0 inet static
        address 192.x.x.x
        netmask 255.x.x.x
	gateway 192.x.x.x
        wireless-essid XXXX
        pre-up wpa_supplicant -B -Dwext -iwlan0 -c/etc/wpa_supplicant/wpa_supplicant.conf
        post-down killall -q wpa_supplicant


I don't see the point of running wireless on G, it too damn slow. If it's capable of AC, I'll take all the extra bandwidth I need to run multiple VMs wirelessly.

---


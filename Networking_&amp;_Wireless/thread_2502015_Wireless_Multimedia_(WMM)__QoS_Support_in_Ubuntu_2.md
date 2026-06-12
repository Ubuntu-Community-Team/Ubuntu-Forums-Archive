---
title: "Wireless Multimedia (WMM)  QoS Support in Ubuntu 24.04 For Traffic Prioritization"
date: 2024-10-29
forum: Networking &amp; Wireless
---

### Post by anspectrum on 2024-10-29
I am using Ubuntu 24.04 with intel WiFi. Below is output of ```
lshw
```
```

-network
       description: Wireless interface
       product: Dual Band Wireless-AC 3165 Plus Bluetooth
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wlp5s0
       version: 99
       serial: xxxxxxxxxxx
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=6.8.0-47-generic firmware=29.4063824552.0 7265D-29.ucode ip=192.168.100.10 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:148 memory:f2100000-f2101fff
```

Below are relevant WMM parameters from AP using command```
 iw dev wlp5s0 scan
```

Output truncated```

----------------------
WMM:     * Parameter version 1
         * u-APSD
         * BE: CW 15-1023, AIFSN 3
         * BK: CW 15-1023, AIFSN 7
         * VI: CW 7-15, AIFSN 2, TXOP 3008 usec
         * VO: CW 3-7, AIFSN 2, TXOP 1504 usec
----------------------
```

I have come to know that WiFi has 802.11e which are QoS enhancements for WiFi. One of the feature is that it defines four classes to prioritize traffic. I understand that but Ive not found any information on Internet about how to do that on our PC/laptop. I know we can set that option in WiFi modems but how to do it in Ubuntu. Also in Ethernet there is only one way to mark a frame for certain treatment and that is via 802.1p (COS in VLAN Tagging). So does it mean that  PC/Laptop should mark WiFi frames with certain QoS value so that it is  treated as per defined criteria in AP? Does it mean creating VLAN interfaces on Ubuntu? Moreover, if end user tags the frames then AP should also be configured for VLAN tagging.

Has anyone ever done it on Ubuntu (or for that matter even on Windows) ?

Thanks for any thoughts.

---

### Post by anspectrum on 2024-10-30
Ive done some more searching, reading and experimenting and wanted to share here so that someone else can get benefited.

 So basically, WMM is negotiated between AP and End Client (Station). Depending upon your OS and configuration (if there is any), different applications will mark packets differently. It is likely that any VOIP/Video/Game application will mark packets as priviledged (either of the DSCP values like EF, AF, CS etc). Once DSCP is marked, wifi frame 802.11 will take that DSCP and map it onto its own QoS field (3 bits in size). And this is done automatically without any intervention from user.  If we capture wifi interface using Wireshark while connected to AP, we can not see those 802.11 QoS marking however, we can see DSCP markings. To see 802.11 marking, we need to use two WiFi adapters, one for Tx/Rx of user traffic while other adapter (in monitor mode) to capture traffic over the air. There is a field in 802.11 frame called QoS Data and in there we can see any bit marking.

But how about making sure that your application is marking the DSCP values. To ensure that we can use iptables to mark the traffic as below:
```
 sudo iptables -t mangle -A OUTPUT -m owner --pid-owner <PID> -j DSCP --set-dscp 46
```

Another way could be to mark all traffic from a specific user as below:
```
sudo iptables -A OUTPUT -t mangle -m owner --uid-owner <UID> -j DSCP --set-dscp 46
```

We can also use traffic control tc, for advanced traffic manipulation techniques.

---


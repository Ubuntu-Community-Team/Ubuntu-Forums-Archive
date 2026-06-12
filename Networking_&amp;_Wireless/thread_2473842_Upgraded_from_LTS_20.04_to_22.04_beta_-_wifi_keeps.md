---
title: "Upgraded from LTS 20.04 to 22.04 beta - wifi keeps dropping"
date: 2022-04-15
forum: Networking &amp; Wireless
---

### Post by gmc1 on 2022-04-15
I've got a Asus laptop and have been running 20.04 LTS for a for years without any issues. 

Yesterday I upgraded to 22.04 beta and since then it's been unusable.  Random freezes for a 10-20 seconds, internet slow and intermittent timeouts on web sites

Upgrade went through without any issues but I've pin pointed the issue down to the wifi. It randomly looses connection for 10-20 seconds and then comes back.

In the dmesg's file I'm seeing lots of errors related to wifi:

```


[  287.165996] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00006100
[  288.226206] wlp2s0: authenticate with xx:xx:xx:xx:xx:xx
[  288.241299] wlp2s0: send auth to xx:xx:xx:xx:xx:xx (try 1/3)
[  288.248805] wlp2s0: authenticated
[  288.249239] wlp2s0: associating with AP with corrupt probe response
[  288.254120] wlp2s0: associate with xx:xx:xx:xx:xx:xx (try 1/3)
[  288.259725] wlp2s0: RX AssocResp from xx:xx:xx:xx:xx:xx (capab=0x411 status=0 aid=6)
[  288.259886] wlp2s0: associated
[  334.189047] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00006100
[  335.196527] wlp2s0: authenticate with xx:xx:xx:xx:xx:xx
[  335.211555] wlp2s0: send auth to xx:xx:xx:xx:xx:xx (try 1/3)
[  335.219539] wlp2s0: authenticated
[  335.219924] wlp2s0: associating with AP with corrupt probe response
[  335.221957] wlp2s0: associate with xx:xx:xx:xx:xx:xx (try 1/3)
[  335.232169] wlp2s0: RX AssocResp from xx:xx:xx:xx:xx:xx (capab=0x411 status=0 aid=6)
[  335.232320] wlp2s0: associated
[  388.154411] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00006100
[  389.180473] wlp2s0: authenticate with xx:xx:xx:xx:xx:xx
[  389.195360] wlp2s0: send auth to xx:xx:xx:xx:xx:xx (try 1/3)
[  389.203206] wlp2s0: authenticated
[  389.203578] wlp2s0: associating with AP with corrupt probe response
[  389.214286] wlp2s0: associate with xx:xx:xx:xx:xx:xx (try 1/3)
[  389.220097] wlp2s0: RX AssocResp from xx:xx:xx:xx:xx:xx (capab=0x411 status=0 aid=6)
[  389.220344] wlp2s0: associated


```


```

  *-network                 
       description: Wireless interface
       product: AR9485 Wireless Network Adapter
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlp2s0
       version: 01
       serial: xx:xx:xx:xx:xx:xx:xx
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=5.15.0-25-generic firmware=N/A ip=x.x.x.x latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:17 memory:d0700000-d077ffff memory:d0780000-d078ffff


```



I've disabled IPv6 which hasn't made any difference. 

I have another laptop with 20.04 LTS (Same hardware) and not seeing any issues there. Have also rebooted my wifi AP just in case, but this looks like some issue on 22.04.

Any ideas as to what I can try to resolve this?

---

### Post by TheFu on 2022-04-15
This post belongs in the Development Release subforum until 22.04 is actually released. That's where any pre-release threads belong.

---

### Post by gmc1 on 2022-04-16
Found the cause for this. It's a regression bug in the kernel.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1968631](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1968631)

---


---
title: "wireless card N on laptop only connecting to G mode router"
date: 2017-04-17
forum: Networking &amp; Wireless
---

### Post by alain.roger on 2017-04-17
Hi,

my router asus is a dual band 2.4Ghz and 5Ghz. My samsung Neo 5 is connected to this router using the 5G band without any problem.
My issue is with may laptop asus which has a b/g/n wireless card integrated and for an unknown reason only connect to router using g band, so max to 1 Mb speed transfer :(
I would like to make my laptop adapter uses N and therefore increase wifi speed.

my laptop is an ASUS G73Sw. Therefore i would like to know what should i check and change to be sure to use N mode, because in the liste of scanned wifi network, it displays only the G (2,4Ghz) networks it detects around... and nothing about my 5Ghz network.

driver installed is: [FONT=monospace][COLOR=#000000]AR9285 Wireless Network Adapter

sudo lspci -v returns:

[/COLOR][/FONT]```
[FONT=monospace][COLOR=#000000]03:00.0 Network controller: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) (rev 01) [/COLOR]
       Subsystem: AzureWave AW-NE785 / AW-NE785H 802.11bgn Wireless Full or Half-size Mini PCIe Card 
       Flags: bus master, fast devsel, latency 0, IRQ 17 
       Memory at f5600000 (64-bit, non-prefetchable) [size=64K] 
       Capabilities: [40] Power Management version 3 
       Capabilities: [50] MSI: Enable- Count=1/1 Maskable- 64bit- 
       Capabilities: [60] Express Legacy Endpoint, MSI 00 
       Capabilities: [100] Advanced Error Reporting 
       Capabilities: [140] Virtual Channel 
       Capabilities: [160] Device Serial Number 00-15-17-ff-ff-24-14-12 
       Capabilities: [170] Power Budgeting <?> 
       Kernel driver in use: ath9k 
       Kernel modules: ath9k

[/FONT]
```

[FONT=monospace][COLOR=#000000]cat /etc/modprobe.d/iwlwifi.conf  returns:
[/COLOR]
```
# /etc/modprobe.d/iwlwifi.conf
# iwlwifi will dyamically load either iwldvm or iwlmvm depending on the
# microcode file installed on the system.  When removing iwlwifi, first
# remove the iwl?vm module and then iwlwifi.
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211
[/FONT]
```

thanks a lot for your help.

Alain

---


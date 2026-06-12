---
title: "Wifi randomly stops working"
date: 2008-10-15
forum: Networking &amp; Wireless
---

### Post by ph1 on 2008-10-15
Though my wifi has been working for something like 6 weeks, last night it randomly stopped.  The only thing that I can think that I did was to install updates, per the update manager's insistence.  The things is, my ethernet connection still works if I plug in, but the output displayed labels it as wlan0.  

Output of iwconfig (when ethernet is plugged in and I have an internet connection):
```
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

output of sudo lshw -C network:
```
  *-network               
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wmaster0
       version: 61
       serial: 00:13:e8:48:3f:75
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl4965 latency=0 module=iwl4965 multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5752 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:18:8b:db:5a:63
       size: 1GB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.86 duplex=full firmware=5752-v3.19 ip=18.247.5.20 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=1GB/s

```

output of lsmod | grep 'iw':
```
iwl4965               105844  0 
iwlwifi_mac80211      219108  1 iwl4965
cfg80211               15112  1 iwlwifi_mac80211

```

From lspci:
```
0c:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)

```

I've tried modprobe to reinsert the module, but it seems to do nothing.  I have no clue what could possibly be wrong.  

Can anyone give me a suggestion as to what I can try to fix this?  My only idea right now is to try upgrading my kernel in order to take advantage of the newer drivers for Intel wireless cards, but I have a feeling that this will break more than it will fix.

Thanks in advance for your help!

---

### Post by ph1 on 2008-10-15
Never mind, I installed wicd and everything seems to be golden now.

---


---
title: "Ubuntu 12.04 Wireless reconnects Compaq Presario"
date: 2013-10-29
forum: Networking &amp; Wireless
---

### Post by ankush-chadda on 2013-10-29
Hi,

I am facing random wireless connection on Compaq Presario CQ43.
Here are the specs - 

uname -mr
3.5.0-42-generic i686

sudo lshw -C network
 *-network
       description: Wireless interface
       product: AR9485 Wireless Network Adapter
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 74:de:2b:8a:5b:18
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.5.0-42-generic firmware=N/A ip=192.168.1.23 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:18 memory:c2500000-c257ffff memory:afb00000-afb0ffff


lsmod | grep "ath9"
ath9k                 117932  0 
mac80211              475546  1 ath9k
ath9k_common           13782  1 ath9k
ath9k_hw              384090  2 ath9k,ath9k_common
ath                    19436  3 ath9k,ath9k_common,ath9k_hw
cfg80211              181041  3 ath9k,mac80211,ath




lspci - 
Network controller: Qualcomm Atheros AR9485 Wireless Network Adapter (rev 01)


dmesg (After the wireless disconnected)

[149975.744675] ath: phy0: Unable to reset channel, reset status -22
[149975.744682] ath: phy0: Unable to set channel
[149975.755747] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[149975.755755] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[149975.817746] ath: phy0: Failed to stop TX DMA, queues=0x10f!
[149975.928110] ath: phy0: Chip reset failed
[149975.928113] ath: phy0: Unable to reset channel, reset status -22
[149975.928122] ath: phy0: Unable to set channel
[150001.909559] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[150001.909570] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[150001.971660] ath: phy0: Failed to stop TX DMA, queues=0x10f!
[150002.082011] ath: phy0: Chip reset failed
[150002.234431] ath9k: ath9k: Driver unloaded  ===>> Here I tried to remove the drivers
[150016.381837] cfg80211: Calling CRDA to update world regulatory domain ===> Here I tried to load them again using the commands given below
[150016.388282] cfg80211: World regulatory domain updated:
[150016.388286] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[150016.388288] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[150016.388290] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[150016.388292] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[150016.388293] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[150016.388295] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[150016.642314] ath9k 0000:02:00.0: Refused to change power state, currently in D3
[150016.754299] ath: phy0: Couldn't reset chip
[150016.754308] ath: phy0: Unable to initialize hardware; initialization status: -5
[150016.754320] ath9k 0000:02:00.0: Failed to initialize device
[150016.754430] ath9k: probe of 0000:02:00.0 failed with error -5
[150032.966012] ath9k: ath9k: Driver unloaded
[150085.122275] cfg80211: Calling CRDA to update world regulatory domain
[150085.133220] cfg80211: World regulatory domain updated:
[150085.133224] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[150085.133226] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[150085.133228] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[150085.133230] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[150085.133231] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[150085.133233] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[150085.147032] ath9k 0000:02:00.0: Refused to change power state, currently in D3
[150085.259139] ath: phy0: Couldn't reset chip
[150085.259149] ath: phy0: Unable to initialize hardware; initialization status: -5
[150085.259161] ath9k 0000:02:00.0: Failed to initialize device
[150085.259312] ath9k: probe of 0000:02:00.0 failed with error -5

Command tried to remove module 
sudo modprobe -rfv ath9k


Command tried to load module
sudo modprobe -v ath9k nohwcrypt=1 . ( Saw these commands in some other post )

After trying to load the module, the wireless doesnt show in network menu, 

Only a restart works . After a restart it is back to normal. Often trying to connect with the "Connect to hidden wireless network" option works, but most of the times , I have to restart.

---

### Post by sicco1 on 2014-01-28
I'm having the same problem on an Asus N53SV-S1827V, Ubuntu 13.10 (3.11.0-15-generic x86_64). The only way to fix it seems to be to restart the laptop. Even modprobing the module doesn't work (see the error below in the syslog output).

sudo lshw -C network:
```
  *-network               
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 74:2f:68:c7:79:39
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.11.0-15-generic firmware=N/A ip=192.168.1.101 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:ddc00000-ddc0ffff

```

sudo lshw -C network:
```
  *-network               
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 74:2f:68:c7:79:39
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k  driverversion=3.11.0-15-generic firmware=N/A ip=192.168.1.101 latency=0  link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:ddc00000-ddc0ffff

```

lspci:
```

03:00.0 Network controller: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) (rev 01)

```

lsmod | grep "ath9":
```
ath9k                 155779  0 
ath9k_common           13859  1 ath9k
ath9k_hw              444732  2 ath9k_common,ath9k
ath                    23827  3 ath9k_common,ath9k,ath9k_hw
mac80211              597268  1 ath9k
cfg80211              480503  3 ath,ath9k,mac80211
```

Output of /var/log/syslog showing the continuous error messages followed by me given the command 'sudo modprobe -r ath9k' (at the end of 23:25:29), followed by 'sudo modprobe ath9k'
```
Jan 28 23:25:24 kernel: [47889.265788] ath: phy0: Failed to wakeup in 500us
Jan 28 23:25:24 kernel: [47889.382997] ath: phy0: RX failed to go idle in 10 ms RXSM=0xffffffff
Jan 28 23:25:24 kernel: [47889.396385] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Jan 28 23:25:29 kernel: [47894.278937] ath: phy0: Failed to wakeup in 500us
Jan 28 23:25:29 kernel: [47894.396175] ath: phy0: RX failed to go idle in 10 ms RXSM=0xffffffff
Jan 28 23:25:29 kernel: [47894.409565] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Jan 28 23:25:29 kernel: [47894.467202] ath: phy0: Failed to wakeup in 500us
Jan 28 23:25:29 kernel: [47894.584645] ath: phy0: RX failed to go idle in 10 ms RXSM=0xffffffff
Jan 28 23:25:29 kernel: [47894.598066] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Jan 28 23:25:29 avahi-daemon[936]: Withdrawing workstation service for wlan0.
Jan 28 23:25:30 kernel: [47895.009824] ath9k: ath9k: Driver unloaded
Jan 28 23:26:09 kernel: [47934.353840] cfg80211: Calling CRDA to update world regulatory domain
Jan 28 23:26:09 kernel: [47934.368284] cfg80211: World regulatory domain updated:
Jan 28 23:26:09 kernel: [47934.368290] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Jan 28 23:26:09 kernel: [47934.368293] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jan 28 23:26:09 kernel: [47934.368296] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jan 28 23:26:09 kernel: [47934.368300] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jan 28 23:26:09 kernel: [47934.368303] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jan 28 23:26:09 kernel: [47934.368306] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jan 28 23:26:09 kernel: [47934.477879] ath9k 0000:03:00.0: enabling device (0000 -> 0002)
Jan 28 23:26:09 kernel: [47934.601697] ath: phy0: Couldn't reset chip
Jan 28 23:26:09 kernel: [47934.601706] ath: phy0: Unable to initialize hardware; initialization status: -5
Jan 28 23:26:09 kernel: [47934.601715] ath9k 0000:03:00.0: Failed to initialize device
Jan 28 23:26:09 kernel: [47934.601858] ath9k: probe of 0000:03:00.0 failed with error -5

```

The problem also occurs on Windows (7). Everything is fine and after a while the wifi connection is gone. Though, using Windows' network troubleshooting it can be fixed as it reloads the module. I'm wondering if it is a hardware issue. What interested me though is that you mentioned using a hidden network. I use this as well; maybe the chip/driver doesn't work well with hidden networks? I am going to use a normal non-hidden wifi network again and will report back if it works.

---

### Post by sicco1 on 2014-02-04
Ok, I changed the settings of my wireless network. It is not hidden anymore (i.e., it is now actively broadcasting its SSID). Since this change I did not once lost my connection! It thus really seems to be a problem with this chip's/driver's compatibility with hidden wireless networks.

---

### Post by wulong710 on 2014-08-07
I met the same problem with wireless connection. Can you share your solution method?

---


---
title: "Unable to recover from pm-suspend"
date: 2018-02-24
forum: Networking &amp; Wireless
---

### Post by poltr1 on 2018-02-24
I have a custom-built home theater PC running Mythbuntu 16.04.3.  (It's not a laptop.)  Due to the placement of this computer and my router, a wired connection was not practical, so I'm using a wireless connection instead of a wired connection.  The wireless card I have installed in the computer is a TP-Link TL-WDN3800 PCIe-1x, which appears to use the same chipset as the Qualcomm Atheros AR93xx, and the ath9k driver.

Output from lspci:
```
jim@goldchannel:/var/log$ lspci | grep -i wireless
02:00.0 Network controller: Qualcomm Atheros AR93xx Wireless Network Adapter (rev 01)
jim@goldchannel:/var/log$ lspci -vv -s 02:00.0
02:00.0 Network controller: Qualcomm Atheros AR93xx Wireless Network Adapter (rev 01)
	Subsystem: Qualcomm Atheros AR93xx Wireless Network Adapter
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 18
	Region 0: Memory at fe8e0000 (64-bit, non-prefetchable) [size=128K]
	Expansion ROM at fe8d0000 [disabled] [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: ath9k
	Kernel modules: ath9k
jim@goldchannel:/var/log$ 

```

Output from lshw:
```
jim@goldchannel:/var/log$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: AR93xx Wireless Network Adapter
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 14:cc:20:17:32:a3
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=4.4.0-112201802110420-generic firmware=N/A ip=192.168.0.25 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:18 memory:fe8e0000-fe8fffff memory:fe8d0000-fe8dffff
  *-network DISABLED
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 06
       serial: ac:9e:17:f0:96:ca
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168e-3_0.0.4 03/27/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:42 ioport:d800(size=256) memory:fdfff000-fdffffff memory:fdff8000-fdffbfff
jim@goldchannel:/var/log$

``` 

Output from iwconfig:
```
jim@goldchannel:/var/log$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"Club_425-5G"  
          Mode:Managed  Frequency:5.18 GHz  Access Point: 28:56:5A:AE:99:A3   
          Bit Rate=240 Mb/s   Tx-Power=16 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=57/70  Signal level=-53 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:2  Invalid misc:3588   Missed beacon:0

eth0      no wireless extensions.

```

If I try to suspend the system manually, or if it automatically suspends due to a lack of activity, it suspends normally, but I cannot recover the system from a suspended state.  The system appears to still be on, but the display does not "wake up" or turn back on.  My monitor then displays a "no signal" message.  I have to reset/reboot the computer in order to recover from this event.

I've traced this problem to the wireless card. I'm unable to enable or disable the power management setting on the wireless card.

From /var/log/pm-powersave.log:
```
Running hook /usr/lib/pm-utils/power.d/wireless false:
Turning powersave for wlan0 off...Error for wireless request "Set Power Manageme
nt" (8B2C) :
    SET failed on device wlan0 ; Operation not supported.
Failed.
/usr/lib/pm-utils/power.d/wireless false: success.

```

If I try to enable or disable the power management manually, I get an error.

```
root@goldchannel:/var/log# iwconfig wlan0 power on
Error for wireless request "Set Power Management" (8B2C) :
    SET failed on device wlan0 ; Operation not supported.
root@goldchannel:/var/log# iwconfig wlan0 power off
Error for wireless request "Set Power Management" (8B2C) :
    SET failed on device wlan0 ; Operation not supported.
root@goldchannel:/var/log# 

```

As a test, I removed the wireless card and was able to get the computer to suspend and recover.  

As a workaround to this issue, I've installed xfce4-power-manager and set it to "presentation mode".  I also set the inactivity settings to never turn off.  But it would be nice to be able to suspend the computer for extended periods of time, and not have to shutdown and restart.  

Before I report this as a bug, I ask: is this a limitation of the wireless card, or of the ath9k driver?

---


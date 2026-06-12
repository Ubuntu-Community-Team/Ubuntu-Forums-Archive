---
title: "[SOLVED] Intel 4965 AG or AGN not available / found"
date: 2008-07-12
forum: Networking &amp; Wireless
---

### Post by Creap on 2008-07-12
Hi.

I just bought a new [Titan A15]("http://www.zepto.com/Shop/Notebook.aspx?notebookid=990") laptop from Zepto Computers and I'm having some problems. I chose a wireless NIC that I thought would be well supported "out of the box" (see [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsIntel](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsIntel)), but it doesn't work for me. 

Under network-admin it doesn't show up at all, and this is what ifconfig and iwconfig gives:

> $ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1b:38:e2:b6:ed  
          inet addr:85.228.118.166  Bcast:85.228.127.255  Mask:255.255.240.0
          inet6 addr: fe80::21b:38ff:fee2:b6ed/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3857 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2858 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5173506 (4.9 MB)  TX bytes:329470 (321.7 KB)
          Interrupt:22 Base address:0xdead 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1770 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1770 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:88500 (86.4 KB)  TX bytes:88500 (86.4 KB)

$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.


This is what lspci -v gives: > 02:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)
	Subsystem: Intel Corporation Unknown device 1101
	Flags: bus master, fast devsel, latency 0, IRQ 221
	Memory at d4100000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>


> $ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 191 Gigabit Ethernet Adapter
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 02
       serial: 00:1b:38:e2:b6:ed
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sis190 driverversion=1.2 duplex=full ip=85.228.118.166 latency=0 link=yes module=sis190 multicast=yes port=MII speed=100MB/s
  *-network
       description: Network controller
       product: PRO/Wireless 4965 AG or AGN Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 61
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=iwl4965 latency=0 module=iwl4965


> $ locate iwl
/lib/firmware/2.6.24-19-generic/iwlwifi-3945-1.ucode
/lib/firmware/2.6.24-19-generic/iwlwifi-3945.ucode
/lib/firmware/2.6.24-19-generic/iwlwifi-4965-1.ucode
/lib/firmware/2.6.24-19-generic/iwlwifi-4965.ucode
/lib/modules/2.6.24-19-generic/ubuntu/wireless/iwlwifi
/lib/modules/2.6.24-19-generic/ubuntu/wireless/iwlwifi/iwlwifi
/lib/modules/2.6.24-19-generic/ubuntu/wireless/iwlwifi/mac80211
/lib/modules/2.6.24-19-generic/ubuntu/wireless/iwlwifi/iwlwifi/compatible
/lib/modules/2.6.24-19-generic/ubuntu/wireless/iwlwifi/iwlwifi/compatible/iwl3945.ko
/lib/modules/2.6.24-19-generic/ubuntu/wireless/iwlwifi/iwlwifi/compatible/iwl4965.ko
/lib/modules/2.6.24-19-generic/ubuntu/wireless/iwlwifi/mac80211/compatible
/lib/modules/2.6.24-19-generic/ubuntu/wireless/iwlwifi/mac80211/compatible/net
/lib/modules/2.6.24-19-generic/ubuntu/wireless/iwlwifi/mac80211/compatible/net/mac80211
/lib/modules/2.6.24-19-generic/ubuntu/wireless/iwlwifi/mac80211/compatible/net/mac80211/iwlwifi_mac80211.ko
/lib/modules/2.6.24-19-generic/ubuntu/wireless/iwlwifi/mac80211/compatible/net/mac80211/iwlwifi_rc80211_simple.ko
/sbin/iwlist
/usr/share/man/cs/man8/iwlist.8.gz
/usr/share/man/fr/man8/iwlist.8.gz
/usr/share/man/man8/iwlist.8.gz
/usr/src/linux-headers-2.6.24-19/drivers/net/wireless/iwlwifi
/usr/src/linux-headers-2.6.24-19/drivers/net/wireless/iwlwifi/Kconfig
/usr/src/linux-headers-2.6.24-19/drivers/net/wireless/iwlwifi/Makefile


uname -a if that's any help:
> Linux munin 2.6.24-19-generic #1 SMP Wed Jun 18 14:43:41 UTC 2008 i686 GNU/Linux


Everything seems fine with the drivers, right? Is there just some stupid thing I forgot to enable? :-(

---

### Post by lyzium on 2008-07-12
ifconfig

wlan0     Link encap:Ethernet  HWaddr 00:1d:e0:b4:ca:9b  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:e0ff:feb4:ca9b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2417483 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1939103 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2398033553 (2.2 GB)  TX bytes:383780512 (366.0 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1D-E0-B4-CA-9B-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"DefaultAP"  Nickname:""
          Mode:Managed  Frequency:2.452 GHz  Access Point: 00:1B:2F:4D:24:BC   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality=100/100  Signal level=-20 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


lspci -v

0c:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)
	Subsystem: Intel Corporation Unknown device 1101
	Flags: bus master, fast devsel, latency 0, IRQ 216
	Memory at f8200000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>

$ sudo lshw -C network
*-network
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wmaster0
       version: 61
       serial: 00:1d:e0:b4:ca:9b
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl4965 ip=192.168.1.3 latency=0 module=iwl4965 multicast=yes wireless=IEEE 802.11g



~$ locate iwl
/lib/firmware/2.6.24-16-generic/iwlwifi-3945-1.ucode
/lib/firmware/2.6.24-16-generic/iwlwifi-3945.ucode
/lib/firmware/2.6.24-16-generic/iwlwifi-4965-1.ucode
/lib/firmware/2.6.24-16-generic/iwlwifi-4965.ucode
/lib/firmware/2.6.24-17-generic/iwlwifi-3945-1.ucode
/lib/firmware/2.6.24-17-generic/iwlwifi-3945.ucode
/lib/firmware/2.6.24-17-generic/iwlwifi-4965-1.ucode
/lib/firmware/2.6.24-17-generic/iwlwifi-4965.ucode
/lib/firmware/2.6.24-18-generic/iwlwifi-3945-1.ucode
/lib/firmware/2.6.24-18-generic/iwlwifi-3945.ucode
/lib/firmware/2.6.24-18-generic/iwlwifi-4965-1.ucode
/lib/firmware/2.6.24-18-generic/iwlwifi-4965.ucode
/lib/firmware/2.6.24-19-generic/iwlwifi-3945-1.ucode
/lib/firmware/2.6.24-19-generic/iwlwifi-3945.ucode
/lib/firmware/2.6.24-19-generic/iwlwifi-4965-1.ucode
/lib/firmware/2.6.24-19-generic/iwlwifi-4965.ucode
/lib/modules/2.6.24-16-generic/ubuntu/wireless/iwlwifi
/lib/modules/2.6.24-16-generic/ubuntu/wireless/iwlwifi/iwlwifi
/lib/modules/2.6.24-16-generic/ubuntu/wireless/iwlwifi/mac80211
/lib/modules/2.6.24-16-generic/ubuntu/wireless/iwlwifi/iwlwifi/compatible
/lib/modules/2.6.24-16-generic/ubuntu/wireless/iwlwifi/iwlwifi/compatible/iwl3945.ko
/lib/modules/2.6.24-16-generic/ubuntu/wireless/iwlwifi/iwlwifi/compatible/iwl4965.ko
/lib/modules/2.6.24-16-generic/ubuntu/wireless/iwlwifi/mac80211/compatible
/lib/modules/2.6.24-16-generic/ubuntu/wireless/iwlwifi/mac80211/compatible/net
/lib/modules/2.6.24-16-generic/ubuntu/wireless/iwlwifi/mac80211/compatible/net/mac80211
/lib/modules/2.6.24-16-generic/ubuntu/wireless/iwlwifi/mac80211/compatible/net/mac80211/iwlwifi_mac80211.ko
/lib/modules/2.6.24-16-generic/ubuntu/wireless/iwlwifi/mac80211/compatible/net/mac80211/iwlwifi_rc80211_simple.ko
/lib/modules/2.6.24-17-generic/ubuntu/wireless/iwlwifi
/lib/modules/2.6.24-17-generic/ubuntu/wireless/iwlwifi/iwlwifi
/lib/modules/2.6.24-17-generic/ubuntu/wireless/iwlwifi/mac80211
/lib/modules/2.6.24-17-generic/ubuntu/wireless/iwlwifi/iwlwifi/compatible
/lib/modules/2.6.24-17-generic/ubuntu/wireless/iwlwifi/iwlwifi/compatible/iwl3945.ko
/lib/modules/2.6.24-17-generic/ubuntu/wireless/iwlwifi/iwlwifi/compatible/iwl4965.ko
/lib/modules/2.6.24-17-generic/ubuntu/wireless/iwlwifi/mac80211/compatible
/lib/modules/2.6.24-17-generic/ubuntu/wireless/iwlwifi/mac80211/compatible/net
/lib/modules/2.6.24-17-generic/ubuntu/wireless/iwlwifi/mac80211/compatible/net/mac80211
/lib/modules/2.6.24-17-generic/ubuntu/wireless/iwlwifi/mac80211/compatible/net/mac80211/iwlwifi_mac80211.ko
/lib/modules/2.6.24-17-generic/ubuntu/wireless/iwlwifi/mac80211/compatible/net/mac80211/iwlwifi_rc80211_simple.ko
/lib/modules/2.6.24-18-generic/ubuntu/wireless/iwlwifi
/lib/modules/2.6.24-18-generic/ubuntu/wireless/iwlwifi/iwlwifi
/lib/modules/2.6.24-18-generic/ubuntu/wireless/iwlwifi/mac80211
/lib/modules/2.6.24-18-generic/ubuntu/wireless/iwlwifi/iwlwifi/compatible
/lib/modules/2.6.24-18-generic/ubuntu/wireless/iwlwifi/iwlwifi/compatible/iwl3945.ko
/lib/modules/2.6.24-18-generic/ubuntu/wireless/iwlwifi/iwlwifi/compatible/iwl4965.ko
/lib/modules/2.6.24-18-generic/ubuntu/wireless/iwlwifi/mac80211/compatible
/lib/modules/2.6.24-18-generic/ubuntu/wireless/iwlwifi/mac80211/compatible/net
/lib/modules/2.6.24-18-generic/ubuntu/wireless/iwlwifi/mac80211/compatible/net/mac80211
/lib/modules/2.6.24-18-generic/ubuntu/wireless/iwlwifi/mac80211/compatible/net/mac80211/iwlwifi_mac80211.ko
/lib/modules/2.6.24-18-generic/ubuntu/wireless/iwlwifi/mac80211/compatible/net/mac80211/iwlwifi_rc80211_simple.ko
/lib/modules/2.6.24-19-generic/ubuntu/wireless/iwlwifi
/lib/modules/2.6.24-19-generic/ubuntu/wireless/iwlwifi/iwlwifi
/lib/modules/2.6.24-19-generic/ubuntu/wireless/iwlwifi/mac80211
/lib/modules/2.6.24-19-generic/ubuntu/wireless/iwlwifi/iwlwifi/compatible
/lib/modules/2.6.24-19-generic/ubuntu/wireless/iwlwifi/iwlwifi/compatible/iwl3945.ko
/lib/modules/2.6.24-19-generic/ubuntu/wireless/iwlwifi/iwlwifi/compatible/iwl4965.ko
/lib/modules/2.6.24-19-generic/ubuntu/wireless/iwlwifi/mac80211/compatible
/lib/modules/2.6.24-19-generic/ubuntu/wireless/iwlwifi/mac80211/compatible/net
/lib/modules/2.6.24-19-generic/ubuntu/wireless/iwlwifi/mac80211/compatible/net/mac80211
/lib/modules/2.6.24-19-generic/ubuntu/wireless/iwlwifi/mac80211/compatible/net/mac80211/iwlwifi_mac80211.ko
/lib/modules/2.6.24-19-generic/ubuntu/wireless/iwlwifi/mac80211/compatible/net/mac80211/iwlwifi_rc80211_simple.ko
/sbin/iwlist
/usr/share/man/cs/man8/iwlist.8.gz
/usr/share/man/fr/man8/iwlist.8.gz
/usr/share/man/man8/iwlist.8.gz
/usr/src/linux-headers-2.6.24-16/drivers/net/wireless/iwlwifi
/usr/src/linux-headers-2.6.24-16/drivers/net/wireless/iwlwifi/Kconfig
/usr/src/linux-headers-2.6.24-16/drivers/net/wireless/iwlwifi/Makefile
/usr/src/linux-headers-2.6.24-18/drivers/net/wireless/iwlwifi
/usr/src/linux-headers-2.6.24-18/drivers/net/wireless/iwlwifi/Kconfig
/usr/src/linux-headers-2.6.24-18/drivers/net/wireless/iwlwifi/Makefile
/usr/src/linux-headers-2.6.24-19/drivers/net/wireless/iwlwifi
/usr/src/linux-headers-2.6.24-19/drivers/net/wireless/iwlwifi/Kconfig
/usr/src/linux-headers-2.6.24-19/drivers/net/wireless/iwlwifi/Makefile


$ uname -a
Linux laptop 2.6.24-19-generic #1 SMP Wed Jun 18 14:43:41 UTC 2008 i686 GNU/Linux


i hope i helped

---

### Post by Creap on 2008-07-12
> **lyzium said:**
> 
$ sudo lshw -C network
*-network
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
**       logical name: wmaster0**
       version: 61
       serial: 00:1d:e0:b4:ca:9b
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list **logical ethernet physical wireless**
       configuration: **broadcast=yes** driver=iwl4965 **ip=192.168.1.3** latency=0 module=iwl4965 **multicast=yes wireless=IEEE 802.11g**
Seems like it's the stuff I bolded that's missing in mine. Will search more, thanks.

---

### Post by Creap on 2008-07-12
I followed some more commands found at [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide) and did:
> $ lsmod |grep iwl
iwl4965 105844 0
iwlwifi_mac80211 219108 1 iwl4965
cfg80211 15112 1 iwlwifi_mac80211

So, the drivers are up and running, right? Other than that, nothing there helped.

---

### Post by Creap on 2008-07-12
> **Creap said:**
> So, the drivers are up and running, right?
Obviously not! I installed linux-backports-modules-hardy which contained some other driver, and it worked, I now have a wlan0 in my iwconfig! Now it's just the question on getting it to communicate with my router... cya.

---


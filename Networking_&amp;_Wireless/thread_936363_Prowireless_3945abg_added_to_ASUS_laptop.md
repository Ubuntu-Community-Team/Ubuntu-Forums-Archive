---
title: "Pro/wireless 3945abg added to ASUS laptop"
date: 2008-10-02
forum: Networking &amp; Wireless
---

### Post by RodBoudreaux on 2008-10-02
I installed a pro/wireless 3945abg in my ASUS and it was reconized and says it is"roaming mode inabled"(network prog). the only thing that stands out is the wmaster0 entry in wconfig says "no wireless extensions", but wlan0 shows info.The hardware address (ifconfig) and the iwl3945 driver( hw) show up. Ihave attached excerpts for these files below. 

When i make a new connection it searches for a while than says no connections available. I have a wireless router in the basement an my mac connected to it out of the box (no security).
any body willing to help this is my first post. Not sure its in the write place. 

rod

rod@rod-laptop:~$ iwconfig
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

from lspci


05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
	Subsystem: Intel Corporation PRO/Wireless 3945ABG Network Connection
	Flags: bus master, fast devsel, latency 0, IRQ 504
	Memory at f7fff000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>



from ifconfig

wlan0     Link encap:Ethernet  HWaddr 00:1f:3c:be:4f:4c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-1F-3C-BE-4F-4C-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

from ls hw


        *-pci:2
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Wireless interface
                product: PRO/Wireless 3945ABG Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:05:00.0
                logical name: wmaster0
                version: 02
                serial: 00:1f:3c:be:4f:4c
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g

---


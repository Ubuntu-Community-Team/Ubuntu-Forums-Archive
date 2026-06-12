---
title: "Getting a Netgear MA311 wirless pci card working"
date: 2007-02-10
forum: Networking &amp; Wireless
---

### Post by h4ck3r on 2007-02-10
Hello,

I am using ubuntu Edgy Eft, and am trying to get a Netgear MA311 wirless pci card working. I have used both ndiswrapper and just messing around with some modules. To be exact I have played with these modules: orinoco_pci, hostap_pci, prism2_pci, and orinoco_pci. I get most of this from this site: [https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/63989](https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/63989)
Basically I have worked a long time on this but with no result. I can detect the card, and everything else, but I just can't seem to get it to see the network. Here are some things that often are asked when posting about networking:

```
lspci:
 00:00.0 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:09.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)
00:0a.0 Network controller: Intersil Corporation Prism 2.5 Wavelan chipset (rev 01)
00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6200] (rev a2)
```
Obviously as you can see, there is the network card on 00:0a.0.
```
dmesg:
[17179614.924000] Bluetooth: HCI device and connection manager initialized
[17179614.924000] Bluetooth: HCI socket layer initialized
[17179614.968000] Bluetooth: L2CAP ver 2.8
[17179614.968000] Bluetooth: L2CAP socket layer initialized
[17179614.968000] Bluetooth: HIDP (Human Interface Emulation) ver 1.1-mh1
[17179614.984000] Bluetooth: RFCOMM socket layer initialized
[17179614.984000] Bluetooth: RFCOMM TTY layer initialized
[17179614.984000] Bluetooth: RFCOMM ver 1.7
[17179700.492000] ISO 9660 Extensions: Microsoft Joliet Level 1
[17179700.728000] ISOFS: changing to secondary root
[17179753.356000] ndiswrapper version 1.22 loaded (preempt=no,smp=no)
[17179753.412000] ndiswrapper (wrapper_init:129): loadndiswrapper failed (1536); check system log for messages from 'loadndisdriver'
[17179753.412000] ndiswrapper (wrapper_init:136): ndiswrapper: initialization failed
[17179872.952000] hostap_pci: Driver unloaded
[17179872.952000] ieee80211_crypt: unregistered algorithm 'NULL'
[17179882.912000] ACPI: PCI interrupt for device 0000:00:0a.0 disabled
[17179894.748000] orinoco 0.15rc3 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
[17179894.748000] orinoco_pci 0.15rc3 (Pavel Roskin <proski@gnu.org>, David Gibson <hermes@gibson.dropbear.id.au> & Jean Tourrilhes <jt@hpl.hp.com>)
[17179894.748000] ACPI: PCI Interrupt 0000:00:0a.0[A] -> GSI 18 (level, low) -> IRQ 193
[17179894.748000] orinoco_pci: Detected device 0000:00:0a.0, mem:0xcbdff000-0xcbdfffff, irq 193
[17179895.696000] eth1: Hardware identity 8013:0000:0001:0000
[17179895.696000] eth1: Station identity  001f:0006:0001:0003
[17179895.696000] eth1: Firmware determined as Intersil 1.3.6
[17179895.696000] eth1: Ad-hoc demo mode supported
[17179895.696000] eth1: IEEE standard IBSS ad-hoc mode supported
[17179895.696000] eth1: WEP supported, 104-bit key
[17179895.696000] eth1: MAC address 00:09:5B:91:59:53
[17179895.696000] eth1: Station name "Prism  I"
[17179895.696000] eth1: ready
[17179895.776000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[17179896.108000] eth1: New link status: Association Failed (0006)
[17179902.240000] ACPI: PCI interrupt for device 0000:00:0a.0 disabled
[17179918.328000] orinoco 0.15rc3 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
[17179918.328000] orinoco_pci 0.15rc3 (Pavel Roskin <proski@gnu.org>, David Gibson <hermes@gibson.dropbear.id.au> & Jean Tourrilhes <jt@hpl.hp.com>)
[17179918.328000] ACPI: PCI Interrupt 0000:00:0a.0[A] -> GSI 18 (level, low) -> IRQ 193
[17179918.328000] orinoco_pci: Detected device 0000:00:0a.0, mem:0xcbdff000-0xcbdfffff, irq 193
[17179919.276000] eth1: Hardware identity 8013:0000:0001:0000
[17179919.276000] eth1: Station identity  001f:0006:0001:0003
[17179919.276000] eth1: Firmware determined as Intersil 1.3.6
[17179919.276000] eth1: Ad-hoc demo mode supported
[17179919.276000] eth1: IEEE standard IBSS ad-hoc mode supported
[17179919.276000] eth1: WEP supported, 104-bit key
[17179919.276000] eth1: MAC address 00:09:5B:91:59:53
[17179919.276000] eth1: Station name "Prism  I"
[17179919.276000] eth1: ready
[17179919.356000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[17179919.688000] eth1: New link status: Association Failed (0006)
[17180023.284000] via-rhine: Reset not complete yet. Trying harder.
[17180023.284000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[17180033.388000] eth0: no IPv6 routers present
[17180056.204000] ndiswrapper version 1.22 loaded (preempt=no,smp=no)
[17180056.204000] ndiswrapper (wrapper_init:129): loadndiswrapper failed (1536); check system log for messages from 'loadndisdriver'
[17180056.204000] ndiswrapper (wrapper_init:136): ndiswrapper: initialization failed
[17180280.088000] ndiswrapper version 1.22 loaded (preempt=no,smp=no)
[17180280.088000] ndiswrapper (wrapper_init:129): loadndiswrapper failed (1536); check system log for messages from 'loadndisdriver'
[17180280.088000] ndiswrapper (wrapper_init:136): ndiswrapper: initialization failed
[17180427.836000] ndiswrapper version 1.22 loaded (preempt=no,smp=no)
[17180427.836000] ndiswrapper (wrapper_init:129): loadndiswrapper failed (1536); check system log for messages from 'loadndisdriver'
[17180427.836000] ndiswrapper (wrapper_init:136): ndiswrapper: initialization failed
[17180456.604000] ndiswrapper version 1.37 loaded (preempt=no,smp=no)
[17180456.616000] usbcore: registered new driver ndiswrapper
[17180560.972000] prism2pci_init: prism2_pci.o: 0.2.5 Loaded
[17180586.728000] usbcore: deregistering driver ndiswrapper
[17180588.360000] ndiswrapper version 1.37 loaded (preempt=no,smp=no)
[17180588.372000] usbcore: registered new driver ndiswrapper
ben@elf:~$ 

```
This is only the more relevant part of dmesg, not the whole thing.

```
iwconfig:
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:"temple"  Nickname:"Prism  I"
          Mode:Managed  Frequency:2.427 GHz  Access Point: None   
          Bit Rate:2 Mb/s   Sensitivity:1/3  
          Retry min limit:8   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/92  Signal level=-68 dBm  Noise level=-122 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

```
ifconfig:
eth0      Link encap:Ethernet  HWaddr 00:11:09:D6:F6:F6  
          inet addr:192.168.10.18  Bcast:192.168.10.255  Mask:255.255.255.0
          inet6 addr: fe80::211:9ff:fed6:f6f6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3818 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3700 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3103201 (2.9 MiB)  TX bytes:415868 (406.1 KiB)
          Interrupt:185 Base address:0xc000 

eth1      Link encap:Ethernet  HWaddr 00:09:5B:91:59:53  
          inet addr:192.168.10.18  Bcast:192.168.10.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:193 Memory:cbdff000-cbdfffff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:77 errors:0 dropped:0 overruns:0 frame:0
          TX packets:77 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8159 (7.9 KiB)  TX bytes:8159 (7.9 KiB)
```
Thats basically it, thanks a lot for any help... I know that I have spent at least 2-4 hours on it so any help would be Greatly appreciated.

Thanks a lot,
Ben

---

### Post by h4ck3r on 2007-02-10
Anyone???

---


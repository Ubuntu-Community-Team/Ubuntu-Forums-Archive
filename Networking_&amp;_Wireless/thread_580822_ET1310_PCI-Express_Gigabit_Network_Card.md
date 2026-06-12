---
title: "ET1310 PCI-Express Gigabit Network Card"
date: 2007-10-19
forum: Networking &amp; Wireless
---

### Post by gareth279 on 2007-10-19
I just installed Gusty desktop AMD64 version.

The ET1310 network card is detected and restricted driver automatically loaded (v1.2.3 by Agere Systems), however the card will not get an IP address from the DHCP server.  If I assign a static address I cannot ping or send any traffic via the card.  It is connected to switch ok, link is active and works fine, here is print out from 'ifconfig -a'.


eth1      Link encap:Ethernet  HWaddr 00:0A:CD:13:6D:66  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:380 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:29873 (29.1 KB)  TX bytes:3600 (3.5 KB)
          Interrupt:18 

eth1:avah Link encap:Ethernet  HWaddr 00:0A:CD:13:6D:66  
          inet addr:169.254.5.144  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:18 


Any ideas on how to detect the fault?  The driver seems to be the most current one available... it works with windows driver ok...

---

### Post by gareth279 on 2007-10-19
Additional info:

lshw -C network
  *-network               
       description: Ethernet interface
       product: ET-131x PCI-E Ethernet Controller
       vendor: Agere Systems
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 02
       serial: 00:0a:cd:13:6d:66
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=et131x latency=0 module=et131x multicast=yes

---

### Post by gareth279 on 2007-10-19
There are some errors in dmesg...

lspci -nn:
03:00.0 Ethernet controller [0200]: Agere Systems ET-131x PCI-E Ethernet Controller [11c1:ed00] (rev 02)

dmesg:
[   38.419598] et131x: module license 'BSD' taints kernel.
[   38.420574] 10/100/1000 Base-T Ethernet Driver for the ET1310, v1.2.3 01/31/2006 15:40:00 by Agere Systems, [http://www.agere.com](http://www.agere.com)
[   38.422468] ACPI: PCI Interrupt Link [LNEB] enabled at IRQ 18
[   38.422478] ACPI: PCI Interrupt 0000:03:00.0[A] -> Link [LNEB] -> GSI 18 (level, low) -> IRQ 18
[   38.422487] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   38.767048] ACPI: PCI Interrupt Link [LNED] enabled at IRQ 17
[   38.767058] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNED] -> GSI 17 (level, low) -> IRQ 17
[   38.767066] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   38.767206] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  100.14.19  Wed Sep 12 14:08:38 PDT 2007
[   38.996105] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 16
[   38.996116] ACPI: PCI Interrupt 0000:01:08.0[A] -> Link [LNKA] -> GSI 16 (level, low) -> IRQ 16
[   38.999164] Installing spdif_bug patch: Audigy 2 ZS [SB0350]
[   39.462577] lp: driver loaded but no devices found
[   39.558818] Adding 7960168k swap on /dev/sdb5.  Priority:-1 extents:1 across:7960168k
[   39.894112] EXT3 FS on sdb1, internal journal
[   40.859766] No dock devices found.
[   40.959594] input: Power Button (FF) as /class/input/input4
[   40.963073] ACPI: Power Button (FF) [PWRF]
[   40.986627] input: Power Button (CM) as /class/input/input5
[   40.990080] ACPI: Power Button (CM) [PWRB]
[   41.158587] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3200+ processors (version 2.00.00)
[   41.161972] powernow-k8: BIOS error - no PSB or ACPI _PSS objects
[   42.273214] et131x.ko:WARNING:et131x_ioctl Unhandled IOCTL Code: 0x8946
[   42.275676] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   42.278334] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[   42.305988] ppdev: user-space parallel port driver
[   42.442535] audit(1192815063.120:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4836 profile="/usr/sbin/cupsd"
[   42.707620] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   42.707624] vboxdrv: Successfully done.
[   43.053549] Failure registering capabilities with primary security module.
[   43.266530] Bluetooth: Core ver 2.11
[   43.266613] NET: Registered protocol family 31
[   43.266616] Bluetooth: HCI device and connection manager initialized
[   43.266619] Bluetooth: HCI socket layer initialized
[   43.289037] Bluetooth: L2CAP ver 2.8
[   43.289042] Bluetooth: L2CAP socket layer initialized
[   43.297049] Bluetooth: RFCOMM socket layer initialized
[   43.297113] Bluetooth: RFCOMM TTY layer initialized
[   43.297115] Bluetooth: RFCOMM ver 1.8
[   47.094922] eth0: no IPv6 routers present
[   47.649105] NET: Registered protocol family 17
[  621.740473] et131x.ko:WARNING:et131x_ioctl Unhandled IOCTL Code: 0x8946
[ 1622.133082] et131x.ko:WARNING:et131x_ioctl Unhandled IOCTL Code: 0x8b01
[ 1622.133152] et131x.ko:WARNING:et131x_ioctl Unhandled IOCTL Code: 0x8946
[ 1622.133210] et131x.ko:WARNING:et131x_ioctl Unhandled IOCTL Code: 0x8946
[ 1622.133268] et131x.ko:WARNING:et131x_ioctl Unhandled IOCTL Code: 0x8946
[ 1630.691815] et131x.ko:WARNING:et131x_ioctl Unhandled IOCTL Code: 0x8946
[ 1630.691893] et131x.ko:WARNING:et131x_ioctl Unhandled IOCTL Code: 0x8946
[ 1630.691958] et131x.ko:WARNING:et131x_ioctl Unhandled IOCTL Code: 0x8946
[ 1630.692022] et131x.ko:WARNING:et131x_ioctl Unhandled IOCTL Code: 0x8946

---

### Post by haggan on 2008-05-08
Hej.

I have an LG R200 with the same Network card. I usint Hardy amd64 and the card is detected and so on but I cant get an ip via dhcp if I set the ip static i still cant get any connection. I tryid the hardy alpha. When testing the nic i managed to get an ip adress once and could do a ping to an internet server. But the connection was really slow and stop to work. Any news about this or any one else got problems with et131x on hardy?

---

### Post by rla3rd on 2008-05-12
download new source at [http://www.sourceforge.net/projects/et131x]("http://www.sourceforge.net/projects/et131x")

---

### Post by haggan on 2008-05-14
Hi I have downloaded and installed still I cant get et131x to work on my LGR200. aldo updated to the proposed 2.6.24-17-generic #1 SMP Thu May 1 13:57:17 UTC 2008 x86_64 GNU/Linux kernel.


I have put on verbose output (et131x_debug_level=7) and I can see


lots of msg like this
et131x.ko:VERBOSE:et131x_isr NOT OUR INTERRUPT

sometimes when i plug in the network cable into a HP switch I almost shutting down all trafic on all other ports. 

some more from dmesg

et131x.ko:>:et131x_stats
[  919.303898] et131x.ko:<:et131x_stats
[  919.304153] et131x.ko:VERBOSE:et131x_isr NOT OUR INTERRUPT
[  919.320844] et131x.ko:VERBOSE:et131x_isr NOT OUR INTERRUPT
[  919.337560] et131x.ko:VERBOSE:et131x_isr NOT OUR INTERRUPT
[  919.354225] et131x.ko:VERBOSE:et131x_isr NOT OUR INTERRUPT
[  919.370907] et131x.ko:VERBOSE:et131x_isr NOT OUR INTERRUPT
[  919.387598] et131x.ko:VERBOSE:et131x_isr NOT OUR INTERRUPT
[  919.404279] et131x.ko:VERBOSE:et131x_isr NOT OUR INTERRUPT
[  919.420981] et131x.ko:VERBOSE:et131x_isr NOT OUR INTERRUPT
[  919.436139] RXDMA_XFR_DONE interrupt
[  919.436142] et131x.ko:>:et131x_handle_recv_interrupt
[  919.436144] et131x.ko:>>:nic_rx_pkts
[  919.436145] RX PACKET STATUS
[  919.436146] 	length      : 94
[  919.436147] 	ringIndex   : 0
[  919.436148] 	bufferIndex : 42
[  919.436149] 	word0       : 0x03800000
[  919.436151] VLAN: No RX packet tag
[  919.436155] et131x.ko:>>>:nic_return_rfd
[  919.436156] et131x.ko:<<<:nic_return_rfd
[  919.436157] (1)
[  919.436158] et131x.ko:<<:nic_rx_pkts
[  919.436159] et131x.ko:>>:nic_rx_pkts
[  919.436160] (0)
[  919.436161] et131x.ko:<<:nic_rx_pkts
[  919.436162] et131x.ko:<:et131x_handle_recv_interrupt
[  919.437661] et131x.ko:VERBOSE:et131x_isr NOT OUR INTERRUPT
[  919.454351] et131x.ko:VERBOSE:et131x_isr NOT OUR INTERRUPT
[  919.471024] et131x.ko:VERBOSE:et131x_isr NOT OUR INTERRUPT


but still no network...

---


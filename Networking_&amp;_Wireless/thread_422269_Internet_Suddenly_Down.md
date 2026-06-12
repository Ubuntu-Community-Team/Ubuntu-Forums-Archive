---
title: "Internet Suddenly Down"
date: 2007-04-25
forum: Networking &amp; Wireless
---

### Post by ravix475 on 2007-04-25
Hey guys, my internet suddenly stopped working in my Edgy install. Its strange, because if I run 'iwlist scan' I can see the my home network come up, but it absolutely won't connect. In windows I am connecting just fine. 

I even tried manually connecting via:* ifconfig eth1 essid 9216ne key ########## mode managed*, to no avail. I just don't understand why it seemingly randomly won't connect. 

Some Info:

[B]
Iwlist scan output  (9216ne is my network):[/B]
eth1      Scan completed :
          Cell 01 - Address: 00:13:10:19:99:0D
                    ESSID:"9216ne"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=73/100  Signal level=-55 dBm  
                    Extra: Last beacon: 5064ms ago



**ifconfig output:**
eth0      Link encap:Ethernet  HWaddr 00:11:43:70:FD:30  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:209 

eth1      Link encap:Ethernet  HWaddr 00:12:F0:38:7B:30  
          inet6 addr: fe80::212:f0ff:fe38:7b30/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:113 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:4201 (4.1 KiB)  TX bytes:348 (348.0 b)
          Interrupt:201 Base address:0x8000 Memory:dfcfd000-dfcfdfff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:70 errors:0 dropped:0 overruns:0 frame:0
          TX packets:70 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5376 (5.2 KiB)  TX bytes:5376 (5.2 KiB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:C0:00:01  
          inet addr:192.168.230.1  Bcast:192.168.230.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:55 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:C0:00:08  
          inet addr:192.168.240.1  Bcast:192.168.240.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:55 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


[B]
Partial dmesg output:[/B]
b44: eth0: BUG!  Timeout waiting for bit 00000002 of register 42c to clear.
[17179605.600000] Installing knfsd (copyright (C) 1996 [email]okir@monad.swb.de[/email]).
[17179605.708000] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[17179605.708000] NFSD: starting 90-second grace period
[17179608.352000] Bluetooth: L2CAP ver 2.8
[17179608.352000] Bluetooth: L2CAP socket layer initialized
[17179608.404000] Bluetooth: RFCOMM socket layer initialized
[17179608.404000] Bluetooth: RFCOMM TTY layer initialized
[17179608.404000] Bluetooth: RFCOMM ver 1.7
[17179609.080000] /dev/vmmon[4496]: Module vmmon: registered with major=10 minor=165
[17179609.080000] /dev/vmmon[4496]: Module vmmon: initialized
[17179609.472000] /dev/vmnet: open called by PID 4521 (vmnet-bridge)
[17179609.472000] /dev/vmnet: hub 0 does not exist, allocating memory.
[17179609.472000] /dev/vmnet: port on hub 0 successfully opened
[17179609.472000] bridge-eth1: enabling the bridge
[17179609.472000] bridge-eth1: is a Wireless Adapter
[17179609.472000] bridge-eth1: up
[17179609.472000] bridge-eth1: already up
[17179609.472000] bridge-eth1: attached
[17179609.524000] /dev/vmnet: open called by PID 4527 (vmnet-netifup)
[17179609.524000] /dev/vmnet: hub 1 does not exist, allocating memory.
[17179609.524000] /dev/vmnet: port on hub 1 successfully opened
[17179609.524000] /dev/vmnet: open called by PID 4534 (vmnet-netifup)
[17179609.528000] /dev/vmnet: hub 8 does not exist, allocating memory.
[17179609.528000] /dev/vmnet: port on hub 8 successfully opened
[17179609.624000] /dev/vmnet: open called by PID 4537 (vmnet-natd)
[17179609.624000] /dev/vmnet: port on hub 8 successfully opened
[17179610.016000] /dev/vmnet: open called by PID 4563 (vmnet-dhcpd)
[17179610.016000] /dev/vmnet: port on hub 1 successfully opened
[17179610.020000] /dev/vmnet: open called by PID 4559 (vmnet-dhcpd)
[17179610.020000] /dev/vmnet: port on hub 8 successfully opened
[17179614.588000] NET: Registered protocol family 10
[17179614.588000] lo: Disabled Privacy Extensions
[17179614.588000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[17179614.588000] IPv6 over IPv4 tunneling driver
[17179624.592000] vmnet8: no IPv6 routers present
[17179625.232000] eth1: no IPv6 routers present
[17179625.436000] vmnet1: no IPv6 routers present
[17179906.264000] bridge-eth1: disabling the bridge
[17179906.276000] bridge-eth1: down
[17179906.308000] ACPI: PCI interrupt for device 0000:03:03.0 disabled
[17179921.672000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.1.4dmprq
[17179921.672000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[17179921.672000] ACPI: PCI Interrupt 0000:03:03.0[A] -> GSI 17 (level, low) -> IRQ 201
[17179921.672000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[17179921.804000] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[17179921.828000] bridge-eth1: enabling the bridge
[17179921.828000] bridge-eth1: is a Wireless Adapter
[17179921.828000] bridge-eth1: up
[17179932.520000] eth1: no IPv6 routers present
[17179986.168000] bridge-eth1: disabling the bridge
[17179986.184000] bridge-eth1: down
[17179986.216000] ACPI: PCI interrupt for device 0000:03:03.0 disabled
[17179986.228000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.1.4dmprq
[17179986.228000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[17179986.232000] ACPI: PCI Interrupt 0000:03:03.0[A] -> GSI 17 (level, low) -> IRQ 201
[17179986.232000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[17179986.420000] bridge-eth1: enabling the bridge
[17179986.420000] bridge-eth1: is a Wireless Adapter
[17179986.420000] bridge-eth1: up
[17179986.420000] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[17179989.512000] ADDRCONF(NETDEV_UP): rtap0: link is not ready
[17179989.528000] device rtap0 entered promiscuous mode
[17179989.528000] audit(1177474944.248:2): dev=rtap0 prom=256 old_prom=0 auid=4294967295
[17179996.500000] eth1: no IPv6 routers present
[17180024.340000] device eth1 entered promiscuous mode
[17180024.340000] audit(1177474979.063:3): dev=eth1 prom=256 old_prom=0 auid=4294967295
[17180269.428000] rtc: lost some interrupts at 1024Hz.
[17180480.396000] sr0: CDROM (ioctl) error, command: <6>Read TOC/PMA/ATIP 43 00 00 00 00 00 00 00 0c 40
[17180480.396000] sr: Current [descriptor]: sense key: No Sense
[17180480.396000]     Additional sense: No additional sense information
[17180600.972000] device eth1 left promiscuous mode
[17180600.972000] audit(1177475555.731:4): dev=eth1 prom=0 old_prom=256 auid=4294967295
[17180605.956000] device rtap0 left promiscuous mode
[17180605.956000] audit(1177475560.715:5): dev=rtap0 prom=0 old_prom=256 auid=4294967295
[17180614.632000] bridge-eth1: disabling the bridge
[17180614.644000] bridge-eth1: down
[17180614.660000] dev_mc_discard: multicast leakage! dmi_users=1
[17180614.660000] dev_mc_discard: multicast leakage! dmi_users=1
[17180614.708000] ACPI: PCI interrupt for device 0000:03:03.0 disabled
[17180614.740000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.1.4dmprq
[17180614.740000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[17180614.744000] ACPI: PCI Interrupt 0000:03:03.0[A] -> GSI 17 (level, low) -> IRQ 201
[17180614.744000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[17180614.928000] bridge-eth1: enabling the bridge
[17180614.928000] bridge-eth1: is a Wireless Adapter
[17180614.928000] bridge-eth1: up
[17180614.928000] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[17180625.344000] eth1: no IPv6 routers present





Please let me know if I posted too much information. I am just trying to make it as easy as possible for you to help. Thanks!

---


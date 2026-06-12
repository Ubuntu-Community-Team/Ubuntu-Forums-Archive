---
title: "Very slow network and &quot;wrong data byte #41 should be 0x29 but was 0xaa&quot; on ping"
date: 2006-10-18
forum: Networking &amp; Wireless
---

### Post by pimeja on 2006-10-18
Hi,

I have very slow network connection on Ubuntu 6.06.
Also I have error "wrong data byte #41 should be 0x29 but was 0x7a" on ping to any computer except myself.
I had try to use default e100 from ubuntu, then was many errors and any internet connection.
Then i had compiled driver from Intel site e100-3.5.14 and made rmmod e100 and "insmod /lib/modules/2.6.15-23-386/kernel/drivers/net/e100/e100.ko" then was smaller count of errors and it's some internet connection but very slow.

I'm sorry for bad english and thank you very much for help.

ping 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
64 bytes from 192.168.0.1: icmp_seq=1 ttl=64 time=0.175 ms
64 bytes from 192.168.0.1: icmp_seq=2 ttl=64 time=0.175 ms
64 bytes from 192.168.0.1: icmp_seq=3 ttl=64 time=0.175 ms
wrong data byte #41 should be 0x29 but was 0x7a
#8      8 9 a b c d e f 10 11 12 13 14 15 16 17 18 19 1a 1b 1c 1d 1e 1f 20 21 22 23 24 25 26 27
#40     28 7a 2a 2b 2c 2d 2e 2f 30 31 32 33 34 35 36 37
64 bytes from 192.168.0.1: icmp_seq=4 ttl=64 time=0.184 ms
64 bytes from 192.168.0.1: icmp_seq=5 ttl=64 time=0.177 ms
64 bytes from 192.168.0.1: icmp_seq=6 ttl=64 time=0.175 ms
64 bytes from 192.168.0.1: icmp_seq=7 ttl=64 time=0.173 ms
wrong data byte #41 should be 0x29 but was 0x93
#8      8 9 a b c d e f 10 11 12 13 14 15 16 17 18 19 1a 1b 1c 1d 1e 1f 20 21 22 23 24 25 26 27
#40     28 93 2a 2b 2c 2d 2e 2f 30 31 32 33 34 35 36 37
64 bytes from 192.168.0.1: icmp_seq=8 ttl=64 time=0.178 ms
64 bytes from 192.168.0.1: icmp_seq=9 ttl=64 time=0.174 ms
64 bytes from 192.168.0.1: icmp_seq=10 ttl=64 time=0.173 ms
wrong data byte #41 should be 0x29 but was 0xa0
#8      8 9 a b c d e f 10 11 12 13 14 15 16 17 18 19 1a 1b 1c 1d 1e 1f 20 21 22 23 24 25 26 27
#40     28 a0 2a 2b 2c 2d 2e 2f 30 31 32 33 34 35 36 37
64 bytes from 192.168.0.1: icmp_seq=11 ttl=64 time=0.173 ms
64 bytes from 192.168.0.1: icmp_seq=12 ttl=64 time=0.174 ms

--- 192.168.0.1 ping statistics ---
12 packets transmitted, 12 received, 0% packet loss, time 11000ms
rtt min/avg/max/mdev = 0.173/0.175/0.184/0.013 ms

netstat -nr
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.0.0     0.0.0.0         255.255.255.0   U         0 0          0 eth1
0.0.0.0         192.168.0.1     0.0.0.0         UG        0 0          0 eth1

ifconfig
eth1      Link encap:Ethernet  HWaddr 00:13:20:CB:4C:95
          inet addr:192.168.0.150  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::213:20ff:fecb:4c95/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9617 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2865 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:4831868 (4.6 MiB)  TX bytes:426916 (416.9 KiB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:266 errors:0 dropped:0 overruns:0 frame:0
          TX packets:266 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:30586 (29.8 KiB)  TX bytes:30586 (29.8 KiB)

lspci
0000:00:00.0 Host bridge: Intel Corporation 915G/P/GV/GL/PL/910GL Processor to I/O Controller
0000:00:01.0 PCI bridge: Intel Corporation 915G/P/GV/GL/PL/910GL PCI Express Root Port
0000:00:1b.0 0403: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
0000:00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
0000:00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03)
0000:00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 03)
0000:00:1c.3 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 (rev 03)
0000:00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
0000:00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
0000:00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
0000:00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
0000:00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
0000:00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
0000:00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
0000:00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03)
0000:00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]
0000:01:00.1 Display controller: ATI Technologies Inc RV370 [Radeon X300SE]
0000:06:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller (rev 01)

uname -a
Linux vvavrychuk 2.6.15-23-386 #1 PREEMPT Tue May 23 13:49:40 UTC 2006 i686 GNU/Linux

[4296864.041000] ACPI: PCI interrupt for device 0000:06:08.0 disabled
[4296878.489000] e100: Intel(R) PRO/100 Network Driver, 3.5.14
[4296878.489000] e100: Copyright(c) 1999-2006 Intel Corporation
[4296878.489000] ACPI: PCI Interrupt 0000:06:08.0[A] -> Link [LNKE] -> GSI 3 (level, low) -> IRQ 3
[4296878.532000] e100: eth0: e100_probe: addr 0xff500000, irq 3, MAC addr 00:13:20:CB:4C:95
[4297042.051000] e100: eth1: e100_watchdog: link up, 100Mbps, full-duplex
[4297052.868000] eth1: no IPv6 routers present

---


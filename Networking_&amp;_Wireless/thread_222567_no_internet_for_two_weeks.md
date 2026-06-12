---
title: "no internet for two weeks"
date: 2006-07-25
forum: Networking &amp; Wireless
---

### Post by kaktos on 2006-07-25
I had googled all the web and ubuntuforum and found no answers](*,) 
My problem is my NIC(RealTek RTL8139) can't grab any IP from my dsl modem's DHCP pool whatever route-mode or dial-mode,but the modem works well in my winXP(dual-boot with ubuntu).I'll list all my config infos and any help will be appreciated.:( 

thx

:~$ dmesg | grep eth0
[4294689.628000] eth0: RealTek RTL8139 at 0xe08b2f00, 00:e0:4c:01:cf:39, IRQ 10
[4294689.628000] eth0:  Identified 8139 chip type 'RTL-8139C'
[4294691.376000] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[4294733.376000] NETDEV WATCHDOG: eth0: transmit timed out
[4294733.376000] eth0: Transmit timeout, status 0c 0005 c07f media 00.
[4294733.376000] eth0: Tx queue start entry 4  dirty entry 0.
[4294733.376000] eth0:  Tx descriptor 0 is 0008a156. (queue head)
[4294733.376000] eth0:  Tx descriptor 1 is 0008a156.
[4294733.376000] eth0:  Tx descriptor 2 is 0008a156.
[4294733.376000] eth0:  Tx descriptor 3 is 0008a156.
[4294733.376000] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1



------------------------------------------------------------
~$ lspci
0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333]0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333 AGP]
0000:00:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8233A ISA Bridge
0000:00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:11.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 23)
0000:00:11.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 23)
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 40)
0000:00:14.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
0000:00:14.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
0000:00:14.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 51)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 MX 440] (rev a3)
----------------------------------------------------------
ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:E0:4C:01:CF:39
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:10 Base address:0x2f00


-----------------------------------------------------------------------

---

### Post by mips on 2006-07-25
Does a static IP address work ?

---

### Post by kaktos on 2006-07-25
> **mips said:**
> Does a static IP address work ?

no.....

---


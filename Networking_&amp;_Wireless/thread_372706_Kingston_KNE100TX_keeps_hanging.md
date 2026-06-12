---
title: "Kingston KNE100TX keeps hanging"
date: 2007-02-28
forum: Networking &amp; Wireless
---

### Post by smisko on 2007-02-28
I'm having problems with a Kingston KNE100TX NIC.  I've used it
for years on a 2.4 kernel (Suse).  Upon switching to Ubuntu 6.10,
I saw the network connection go dead once.  Couldn't repeat, so
I proceeded to set things up.  Now an rsync transfer will hang
the connection in under 30 seconds.  ifdown/ifup will usually
restore the network. Sometimes it can only ping itself; a reboot
is required to restore connectivity.  If I remove the two aliases,
it just takes a little longer to hang.

I am running dhcpd, bind (with ddns), vsftpd, apache2, sshd,
ntpd, and rsync --daemon, along with all the usual daemons.
No firewall/nat/forwarding.

It's using the tulip driver, so I loaded the module with
tulip_debug=6 and got some output (below) when it hangs.  So if
anybody knows this driver, maybe they can tell what has gone wrong.
Thanks.

Dan Smisko


# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:C0:F0:58:D8:ED  
          inet addr:192.168.66.65  Bcast:192.168.66.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:f0ff:fe58:d8ed/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2513 errors:1 dropped:0 overruns:0 frame:2
          TX packets:2363 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2334132 (2.2 MiB)  TX bytes:331253 (323.4 KiB)
          Interrupt:10 Base address:0xd800 

eth0:0    Link encap:Ethernet  HWaddr 00:C0:F0:58:D8:ED  
          inet addr:192.168.2.65  Bcast:192.168.2.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:10 Base address:0xd800 

eth0:1    Link encap:Ethernet  HWaddr 00:C0:F0:58:D8:ED  
          inet addr:192.168.66.2  Bcast:192.168.66.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:10 Base address:0xd800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:364 errors:0 dropped:0 overruns:0 frame:0
          TX packets:364 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:56965 (55.6 KiB)  TX bytes:56965 (55.6 KiB)

# lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333]
00:01.0 PCI bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333 AGP]
00:09.0 Multimedia audio controller: ESS Technology ES1969 Solo-1 Audiodrive (rev 02)
00:0a.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61)
00:0a.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61)
00:0a.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 63)
00:0a.3 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 46)
00:0b.0 Communication controller: Agere Systems LT WinModem
00:0c.0 Ethernet controller: Lite-On Communications Inc LNE100TX (rev 20)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8233 PCI to ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1b)
00:11.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1b)
00:11.4 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1b)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R100 QD [Radeon 7200]

# lspci -vvv -s 00:0c
00:0c.0 Ethernet controller: Lite-On Communications Inc LNE100TX (rev 20)
	Subsystem: Kingston Technologies Unknown device f002
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 32
	Interrupt: pin A routed to IRQ 10
	Region 0: I/O ports at d800 [size=256]
	Region 1: Memory at ef002000 (32-bit, non-prefetchable) [size=256]
	[virtual] Expansion ROM at 40000000 [disabled] [size=256K]

$ tail -20 debug
Feb 28 11:32:56 merlot kernel: [72734.857993] eth0: interrupt  csr5=0x026f0014 new csr5=0x026e0010.
Feb 28 11:32:56 merlot kernel: [72734.857999] eth0: exiting interrupt, csr5=0x26e0010.
Feb 28 11:32:56 merlot kernel: [72734.858062]  In tulip_rx(), entry 19 05ee0300.
Feb 28 11:32:56 merlot kernel: [72734.858065] eth0: In tulip_rx(), entry 19 05ee0300.
Feb 28 11:32:56 merlot kernel: [72734.858071] eth0: interrupt  csr5=0x026f0050 new csr5=0x026e0010.
Feb 28 11:32:56 merlot kernel: [72734.858077] eth0: exiting interrupt, csr5=0x26e0010.
Feb 28 11:32:56 merlot kernel: [72734.858186]  In tulip_rx(), entry 20 05ee0300.
Feb 28 11:32:56 merlot kernel: [72734.858189] eth0: In tulip_rx(), entry 20 05ee0300.
Feb 28 11:32:56 merlot kernel: [72734.858194] eth0: interrupt  csr5=0x026f0050 new csr5=0x026e0010.
Feb 28 11:32:56 merlot kernel: [72734.858199] eth0: exiting interrupt, csr5=0x26e0010.
Feb 28 11:32:56 merlot kernel: [72734.858316] eth0: interrupt  csr5=0x026f4010 new csr5=0x026e0010.
Feb 28 11:32:56 merlot kernel: [72734.858321] eth0: exiting interrupt, csr5=0x26e0010.
Feb 28 11:32:56 merlot kernel: [72734.858350]  In tulip_rx(), entry 21 7fff0200.
Feb 28 11:32:56 merlot kernel: [72734.858353] eth0: In tulip_rx(), entry 21 7fff0200.
Feb 28 11:32:56 merlot kernel: [72734.858359] eth0: In tulip_rx(), entry 22 08018192.
Feb 28 11:32:56 merlot kernel: [72734.858367] eth0: interrupt  csr5=0x02678250 new csr5=0x02660010.
Feb 28 11:32:56 merlot kernel: [72734.858372] eth0: PNIC link changed state 0201f978, CSR5 02678250.
Feb 28 11:32:56 merlot kernel: [72734.858577] eth0: exiting interrupt, csr5=0x2660010.
Feb 28 11:32:56 merlot kernel: [72734.859259] eth0: interrupt  csr5=0x02670014 new csr5=0x02660010.
Feb 28 11:32:56 merlot kernel: [72734.859267] eth0: exiting interrupt, csr5=0x2660010.

---

### Post by smisko on 2007-03-15
Followup:  I bought a new (Intel) NIC.  All is well.

Dan Smisko

---

### Post by 67comet on 2007-11-24
Bump:

and mine seems to be fine for about 5 minutes, then it disconnects from the network and the card shuts off w/out notice. This card is in a headless server so when it does it; what a pain! Gotta drag an old keyboard and monitor down to: sudo /etc/init.d/networking restart .. then it's fine for about 5 minutes.

Help?
Here's my junk:
lspci
03:00.0 Ethernet controller: Lite-On Communications Inc LNE100TX [Linksys EtherFast 10/100] (rev 25)

$ sudo lspci -vvv -s 03:00.0
03:00.0 Ethernet controller: Lite-On Communications Inc LNE100TX [Linksys EtherFast 10/100] (rev 25)
        Subsystem: Kingston Technologies Unknown device 000b
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping+ SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32 (2000ns min, 14000ns max), Cache Line Size: 32 bytes
        Interrupt: pin A routed to IRQ 16
        Region 0: I/O ports at bc00 [size=256]
        Region 1: Memory at dfefff00 (32-bit, non-prefetchable) [size=256]
        Expansion ROM at dda00000 [disabled] [size=256K]
        Capabilities: [44] Power Management version 1
                Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1+,D2+,D3hot+,D3cold+)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-

... Any ideas? I don't have another NIC laying around and money is tight right now.

This server ran "well" with Feisty Server edition, but Gutsy has been a bit troublesome.

Thanks,
Justin

---


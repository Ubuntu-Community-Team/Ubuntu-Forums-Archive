---
title: "Gutsy will not connect to the internet  :O(  Please help!!"
date: 2008-02-23
forum: Networking &amp; Wireless
---

### Post by westcliffed on 2008-02-23
I just installed Gutsy on my desktop computer (wired) and can't connect to the internet.  I'm switching from Vista and am brand new to linux but eager to learn.  I tried reinstalling with the ethernet cable plugged in and not plugged in, tried using a different ethernet cable, tried emptying the cache of my browser (thinking the 'could not connect page' was from the cache), tried rebooting the cable modem, and rebooting the system.  Is there a default firewall that's preventing me from connecting?  


I tried a few commands in the hopes that the outputs would make sense to anyone  :O)

```
ed@ed-desktop:~$ sudo dhclient 
There is already a pid file /var/run/dhclient.pid with pid 6668 
killed old client process, removed PID file 
Internet Systems Consortium DHCP Client V3.0.5 
Copyright 2004-2006 Internet Systems Consortium. 
All rights reserved. 
For info, please visit http://www.isc.org/sw/dhcp/ 
 
Listening on LPF/eth0/00:40:ca:51:27:c6 
Sending on   LPF/eth0/00:40:ca:51:27:c6 
Sending on   Socket/fallback 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13 
No DHCPOFFERS received. 
No working leases in persistent database - sleeping. 
```

```
ed@ed-desktop:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:40:CA:51:27:C6   
          inet6 addr: fe80::240:caff:fe51:27c6/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:25131 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:242 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:1540188 (1.4 MB)  TX bytes:47758 (46.6 KB) 
          Interrupt:16 Base address:0x8000  
 
eth0:avah Link encap:Ethernet  HWaddr 00:40:CA:51:27:C6   
          inet addr:169.254.7.66  Bcast:169.254.255.255  Mask:255.255.0.0 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          Interrupt:16 Base address:0x8000  
 
lo        Link encap:Local Loopback   
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:864 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:864 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0  
          RX bytes:63792 (62.2 KB)  TX bytes:63792 (62.2 KB) 
```

```
ed@ed-desktop:~$ sudo /etc/init.d/networking restart 
 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth0.pid with pid 6413 
killed old client process, removed PID file 
Internet Systems Consortium DHCP Client V3.0.5 
Copyright 2004-2006 Internet Systems Consortium. 
All rights reserved. 
For info, please visit http://www.isc.org/sw/dhcp/ 
 
Listening on LPF/eth0/00:40:ca:51:27:c6 
Sending on   LPF/eth0/00:40:ca:51:27:c6 
Sending on   Socket/fallback 
There is already a pid file /var/run/dhclient.eth0.pid with pid 134519120 
Internet Systems Consortium DHCP Client V3.0.5 
Copyright 2004-2006 Internet Systems Consortium. 
All rights reserved. 
For info, please visit http://www.isc.org/sw/dhcp/ 
 
Listening on LPF/eth0/00:40:ca:51:27:c6 
Sending on   LPF/eth0/00:40:ca:51:27:c6 
Sending on   Socket/fallback 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3 
No DHCPOFFERS received. 
No working leases in persistent database - sleeping. 
```


I'm connecting straight from the computer to my cable modem and don't have a router.
```
ed@ed-desktop:~$ route 
Kernel IP routing table 
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface 
link-local      *               255.255.0.0     U     0      0        0 eth0 
default         *               0.0.0.0         U     1000   0        0 eth0 
```



```
ed@ed-desktop:~$ sudo gedit /etc/network/interfaces 
(network interfaces says:) 
auto lo 
iface lo inet loopback 
 
iface eth0 inet dhcp 
address 169.254.7.66 
netmask 255.255.0.0 
gateway 192.168.1.1 
 
auto eth0 
```

```
ed@ed-desktop:~$ sudo lspci 
00:00.0 Host bridge: VIA Technologies, Inc. VT8375 [KM266/KL266] Host Bridge 
00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP] 
00:08.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07) 
00:08.1 Input device controller: Creative Labs SB Live! Game Port (rev 07) 
00:0a.0 Communication controller: Agere Systems LT WinModem (rev 02) 
00:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10) 
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80) 
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80) 
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80) 
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82) 
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge 
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06) 
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV250 If [Radeon 9000] (rev 01) 
```

```
ed@ed-desktop:~$ sudo lshw 
ed-desktop                 
    description: Desktop Computer 
    product: P8655A-ABA S3000Z NA110 
    vendor: Compaq Presario 06 
    version: 0qr1411RE101SALSA 
    serial: MXP320020R 
    width: 32 bits 
    capabilities: smbios-2.3 dmi-2.3 
    configuration: boot=normal chassis=desktop uuid=00939F6F-3086-D711-8B10-8AE127278698 
  *-core 
       description: Motherboard 
       product: KM266-8235 
       physical id: 0 
       serial: 137928-31127416 
       slot: SECONDARY IDE 
     *-firmware 
          description: BIOS 
          vendor: Phoenix Technologies, LTD 
          physical id: 0 
          version: AM37312 (03/17/2003) 
          size: 128KB 
          capacity: 448KB 
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification netboot 
     *-cpu 
          description: CPU 
          product: AMD Athlon(tm) XP 2600+ 
          vendor: Advanced Micro Devices [AMD] 
          physical id: 4 
          bus info: cpu@0 
          version: 6.8.1 
          slot: Socket A 
          size: 2133MHz 
          width: 32 bits 
          clock: 133MHz 
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mmxext 3dnowext 3dnow up ts 
        *-cache:0 
             description: L1 cache 
             physical id: 9 
             slot: Internal Cache 
             size: 128KB 
             capacity: 128KB 
             capabilities: synchronous internal write-back 
        *-cache:1 
             description: L2 cache 
             physical id: a 
             slot: External Cache 
             size: 256KB 
             capacity: 256KB 
             capabilities: synchronous external write-back 
     *-memory 
          description: System Memory 
          physical id: 1c 
          slot: System board or motherboard 
          size: 1GB 
          capacity: 1536MB 
        *-bank:0 
             description: DIMM 
             product: None 
             vendor: None 
             physical id: 0 
             serial: None 
             slot: A0 
             size: 512MB 
        *-bank:1 
             description: DIMM 
             product: None 
             vendor: None 
             physical id: 1 
             serial: None 
             slot: A1 
             size: 512MB 
        *-bank:2 
             description: DIMM [empty] 
             product: None 
             vendor: None 
             physical id: 2 
             serial: None 
             slot: A2 
     *-pci 
          description: Host bridge 
          product: VT8375 [KM266/KL266] Host Bridge 
          vendor: VIA Technologies, Inc. 
          physical id: 100 
          bus info: pci@0000:00:00.0 
          version: 00 
          width: 32 bits 
          clock: 66MHz 
          configuration: driver=agpgart-via latency=8 module=via_agp 
        *-pci 
             description: PCI bridge 
             product: VT8633 [Apollo Pro266 AGP] 
             vendor: VIA Technologies, Inc. 
             physical id: 1 
             bus info: pci@0000:00:01.0 
             version: 00 
             width: 32 bits 
             clock: 66MHz 
             capabilities: pci pm normal_decode bus_master cap_list 
           *-display 
                description: VGA compatible controller 
                product: Radeon RV250 If [Radeon 9000] 
                vendor: ATI Technologies Inc 
                physical id: 0 
                bus info: pci@0000:01:00.0 
                version: 01 
                width: 32 bits 
                clock: 66MHz 
                capabilities: agp agp-2.0 pm vga bus_master cap_list 
                configuration: latency=32 mingnt=8 
        *-multimedia 
             description: Multimedia audio controller 
             product: SB Live! EMU10k1 
             vendor: Creative Labs 
             physical id: 8 
             bus info: pci@0000:00:08.0 
             version: 07 
             width: 32 bits 
             clock: 33MHz 
             capabilities: pm bus_master cap_list 
             configuration: driver=EMU10K1_Audigy latency=32 maxlatency=20 mingnt=2 module=snd_emu10k1 
        *-input 
             description: Input device controller 
             product: SB Live! Game Port 
             vendor: Creative Labs 
             physical id: 8.1 
             bus info: pci@0000:00:08.1 
             version: 07 
             width: 32 bits 
             clock: 33MHz 
             capabilities: pm bus_master cap_list 
             configuration: driver=Emu10k1_gameport latency=32 module=emu10k1_gp 
        *-communication UNCLAIMED 
             description: Communication controller 
             product: LT WinModem 
             vendor: Agere Systems 
             physical id: a 
             bus info: pci@0000:00:0a.0 
             version: 02 
             width: 32 bits 
             clock: 33MHz 
             capabilities: pm bus_master cap_list 
             configuration: latency=32 maxlatency=14 mingnt=252 
        *-network 
             description: Ethernet interface 
             product: RTL-8139/8139C/8139C+ 
             vendor: Realtek Semiconductor Co., Ltd. 
             physical id: b 
             bus info: pci@0000:00:0b.0 
             logical name: eth0 
             version: 10 
             serial: 00:40:ca:51:27:c6 
             size: 100MB/s 
             capacity: 100MB/s 
             width: 32 bits 
             clock: 33MHz 
             capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
             configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full latency=32 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s 
        *-usb:0 
             description: USB Controller 
             product: VT82xxxxx UHCI USB 1.1 Controller 
             vendor: VIA Technologies, Inc. 
             physical id: 10 
             bus info: pci@0000:00:10.0 
             version: 80 
             width: 32 bits 
             clock: 33MHz 
             capabilities: pm uhci bus_master cap_list 
             configuration: driver=uhci_hcd latency=32 module=uhci_hcd 
        *-usb:1 
             description: USB Controller 
             product: VT82xxxxx UHCI USB 1.1 Controller 
             vendor: VIA Technologies, Inc. 
             physical id: 10.1 
             bus info: pci@0000:00:10.1 
             version: 80 
             width: 32 bits 
             clock: 33MHz 
             capabilities: pm uhci bus_master cap_list 
             configuration: driver=uhci_hcd latency=32 module=uhci_hcd 
        *-usb:2 
             description: USB Controller 
             product: VT82xxxxx UHCI USB 1.1 Controller 
             vendor: VIA Technologies, Inc. 
             physical id: 10.2 
             bus info: pci@0000:00:10.2 
             version: 80 
             width: 32 bits 
             clock: 33MHz 
             capabilities: pm uhci bus_master cap_list 
             configuration: driver=uhci_hcd latency=32 module=uhci_hcd 
        *-usb:3 
             description: USB Controller 
             product: USB 2.0 
             vendor: VIA Technologies, Inc. 
             physical id: 10.3 
             bus info: pci@0000:00:10.3 
             version: 82 
             width: 32 bits 
             clock: 33MHz 
             capabilities: pm ehci bus_master cap_list 
             configuration: driver=ehci_hcd latency=32 module=ehci_hcd 
        *-isa 
             description: ISA bridge 
             product: VT8235 ISA Bridge 
             vendor: VIA Technologies, Inc. 
             physical id: 11 
             bus info: pci@0000:00:11.0 
             version: 00 
             width: 32 bits 
             clock: 33MHz 
             capabilities: isa pm bus_master cap_list 
             configuration: latency=0 
        *-ide 
             description: IDE interface 
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE 
             vendor: VIA Technologies, Inc. 
             physical id: 11.1 
             bus info: pci@0000:00:11.1 
             version: 06 
             width: 32 bits 
             clock: 33MHz 
             capabilities: ide pm bus_master cap_list 
             configuration: driver=VIA_IDE latency=32 module=via82cxxx 
           *-ide:0 
                description: IDE Channel 0 
                physical id: 0 
                bus info: ide@0 
                logical name: ide0 
                clock: 33MHz 
              *-disk:0 
                   description: ATA Disk 
                   product: Maxtor 6Y080L0 
                   vendor: Maxtor 
                   physical id: 0 
                   bus info: ide@0.0 
                   logical name: /dev/hda 
                   version: YAR41VW0 
                   serial: Y3J8CQ1E 
                   size: 76GB 
                   capacity: 76GB 
                   capabilities: ata dma lba iordy smart security pm apm partitioned partitioned:dos 
                   configuration: apm=off mode=udma6 smart=on 
                 *-volume:0 
                      description: Linux filesystem partition 
                      physical id: 1 
                      bus info: ide@0.0,1 
                      logical name: /dev/hda1 
                      capacity: 73GB 
                      capabilities: primary bootable 
                 *-volume:1 
                      description: Extended partition 
                      physical id: 2 
                      bus info: ide@0.0,2 
                      logical name: /dev/hda2 
                      size: 2957MB 
                      capacity: 2957MB 
                      capabilities: primary extended partitioned partitioned:extended 
                    *-logicalvolume 
                         description: Linux swap / Solaris partition 
                         physical id: 5 
                         logical name: /dev/hda5 
                         capacity: 2957MB 
                         capabilities: nofs 
              *-disk:1 
                   description: ATA Disk 
                   product: WDC WD2000JB-32EVA0 
                   vendor: Western Digital 
                   physical id: 1 
                   bus info: ide@0.1 
                   logical name: /dev/hdb 
                   version: 15.05R15 
                   serial: WD-WMAEH1675462 
                   size: 186GB 
                   capabilities: ata dma lba iordy smart security pm partitioned partitioned:dos 
                   configuration: mode=udma5 smart=on 
                 *-volume:0 
                      description: Linux filesystem partition 
                      physical id: 1 
                      bus info: ide@0.1,1 
                      logical name: /dev/hdb1 
                      capacity: 183GB 
                      capabilities: primary bootable 
                 *-volume:1 
                      description: Extended partition 
                      physical id: 2 
                      bus info: ide@0.1,2 
                      logical name: /dev/hdb2 
                      size: 2957MB 
                      capacity: 2957MB 
                      capabilities: primary extended partitioned partitioned:extended 
                    *-logicalvolume 
                         description: Linux swap / Solaris partition 
                         physical id: 5 
                         logical name: /dev/hdb5 
                         capacity: 2957MB 
                         capabilities: nofs 
           *-ide:1 
                description: IDE Channel 1 
                physical id: 1 
                bus info: ide@1 
                logical name: ide1 
                clock: 33MHz 
              *-cdrom:0 
                   description: DVD reader 
                   product: Hewlett-Packard DVD Writer 300 
                   physical id: 0 
                   bus info: ide@1.0 
                   logical name: /dev/hdc 
                   version: 1.25 
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cd-r cd-rw dvd 
                   configuration: mode=udma2 status=nodisc 
              *-cdrom:1 
                   description: DVD reader 
                   product: Toshiba DVD-ROM DSM-1712 
                   vendor: Toshiba 
                   physical id: 1 
                   bus info: ide@1.1 
                   logical name: /dev/hdd 
                   version: 1808 
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio dvd 
                   configuration: mode=udma2 status=nodisc 
     *-scsi 
          physical id: 1 
          bus info: usb@4:5 
          logical name: scsi2 
          capabilities: emulated scsi-host 
          configuration: driver=usb-storage 
        *-disk 
             description: SCSI Disk 
             product: USB Flash Memory 
             physical id: 0.0.0 
             bus info: scsi@2:0.0.0 
             logical name: /dev/sda 
             version: 5.00 
             size: 983MB 
             capabilities: removable 
           *-disc 
                physical id: 0 
                logical name: /dev/sda 
                size: 983MB 
                capabilities: partitioned partitioned:dos 
              *-volume 
                   description: W95 FAT16 (LBA) partition 
                   physical id: 1 
                   logical name: /dev/sda1 
                   capacity: 982MB 
                   capabilities: primary bootable 
```

ANY help would be great appreciated!

---

### Post by Iowan on 2008-02-23
Under System>Administration>Network, click on "Wired connection", then click "Properties".  If connection is set for "Local Zeroconf network", change it to "Automatic configuration (DHCP)".  Then you'll either need to restart (reboot) machine or restart networking.

---

### Post by westcliffed on 2008-02-24
Thanks for the reply.

My configuration is set to DHCP, i unchecked then rechecked the box, rebooted and restarted the network...  still nothing.  :(  Any other ideas?

---

### Post by blastus on 2008-02-24
I have two of those Realtek cards in my machine and they have always worked out of the box in every Linux distribution I have ever tried. Heck, they even worked out of the box with RedHat 5. I have many different Realtek cards; you actually have to try to work to get them NOT to work.

If you are using ADSL, you may have to configure [PPPoE](https://help.ubuntu.com/community/ADSLPPPoE). Note; this is depend on your ISP. The better ISPs don't require any manual PPPoE configuration.

---

### Post by Iowan on 2008-02-24
The **eth0:avah** and **inet addr:169.254.7.66 ** suggests the card is not connected  or "Local Zeroconf network" is selected.  Ordinarily, a DHCP-configured machine doesn't have address/netmask/gateway information in the **/etc/network/interfaces** file.:confused:

---

### Post by blastus on 2008-02-24
> **Iowan said:**
> The **eth0:avah** and **inet addr:169.254.7.66 ** suggests the card is not connected  or "Local Zeroconf network" is selected.  Ordinarily, a DHCP-configured machine doesn't have address/netmask/gateway information in the **/etc/network/interfaces** file.:confused:

Yep the 169.254.* is what is assigned when you can't get an IP address over DHCP. I think the address/netmask/gateway information he has in there is from when he was connected to a router but DHCP is active so there shouldn't be an issue.

---

### Post by westcliffed on 2008-02-24
Thanks for all the responses!  I'm trying to connect without a router...  straight from the machine to the the cable modem.  I used to connect through a router, but that was on Windows about 2 years ago.  How would I go about configuring the PPPoE?  I'll try anything!

---


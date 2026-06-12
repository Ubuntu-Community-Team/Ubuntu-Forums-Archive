---
title: "No network with Edgy"
date: 2006-12-09
forum: Networking &amp; Wireless
---

### Post by adana on 2006-12-09
I had ubuntu breezy installed on my laptop working well. I did a complete reinstall with Edgy and now have no internet connection.

Ifconfig list only lo. No etho. I cannot ping any ip except 127.0.0.1.

Any advice? I've installed ubuntu many times and this has never happened.

---

### Post by Malakia on 2006-12-09
What type of network card do have and how are you connected to the internet, through a modem or router?

---

### Post by adana on 2006-12-09
Thanks for the response!


Gateway solo
creditCard Ethernet 10/100 + modem 56
512M

I connect using dsl with a linksys router. I notice that when I boot using the CD it also doesn't reach the internet, so I guess I installed without the internet. I didn't think to check that before installing. :(

---

### Post by Malakia on 2006-12-09
try checking the ndiswrapper website or the madwifi site to see if you card is supported. You will need to find out what chipset your card uses also.

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List)
[http://madwifi.org/wiki/Compatibility](http://madwifi.org/wiki/Compatibility)

---

### Post by adana on 2006-12-09
I am not using wireless, I am plugged into the router. Seems very strange because with the breezy install ubunutu recognized everything and got right onto the internet.

---

### Post by adaptr on 2006-12-09
The "creditcard" Ethernet adapter you mention is actually in the form of a **PC Card**, AKA a PCMCIA card

You need several things functioning before this will work, starting with PC Card support itself, and the right driver for your laptop.

Search for those terms for more info.

---

### Post by adana on 2006-12-09
Very interesting. If I pop that "creditcard" out and plug it back in, ubuntu auto configures it within 1 minute and I am on the internet. If I reboot, it's gone and I have to pop it out again.

So I have to figure out how what config files might have those settings.

Any ideas?

---

### Post by adana on 2006-12-10
anyone know how to make this etho0 consistent with reboots?

---

### Post by dbott67 on 2006-12-10
Can you post the output of your interfaces file:
```
cat /etc/network/interfaces
```

Thanks,
Dave

---

### Post by adana on 2006-12-11
Here it is:

adana@adana-laptop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

---

### Post by dbott67 on 2006-12-11
Your interfaces file looks okay.

So, if you unplug the card & plug it back in everything works?

Can you try the following:

1. Boot the computer
2. From the command prompt, type:
```
dbott@thedrake:~$ **tail -n20 -f /var/log/messages**
```
You should see output similar to the following:
```
Dec 11 20:41:20 thedrake kernel: [17203626.568000] SMB connection re-established (-5)
Dec 11 20:41:21 thedrake kernel: [17203626.912000] SMB connection re-established (-5)
Dec 11 20:41:21 thedrake kernel: [17203627.036000] SMB connection re-established (-5)
Dec 11 20:41:21 thedrake kernel: [17203627.076000] SMB connection re-established (-5)
Dec 11 20:41:21 thedrake kernel: [17203627.120000] SMB connection re-established (-5)
Dec 11 20:41:21 thedrake kernel: [17203627.168000] SMB connection re-established (-5)
Dec 11 20:41:21 thedrake kernel: [17203627.324000] SMB connection re-established (-5)
Dec 11 20:41:47 thedrake kernel: [17203653.324000] smb_add_request: request [d7d2de80, mid=23936] timed out!
Dec 11 20:41:50 thedrake kernel: [17203656.448000] smb_add_request: request [d7d2dc80, mid=23937] timed out!
Dec 11 20:41:52 thedrake kernel: [17203658.296000] smb_add_request: request [d7d2da80, mid=23942] timed out!
Dec 11 20:42:01 thedrake kernel: [17203667.824000] smb_add_request: request [d7d2d080, mid=23943] timed out!
Dec 11 20:42:02 thedrake kernel: [17203667.860000] SMB connection re-established (-5)
Dec 11 20:42:16 thedrake kernel: [17203682.592000] smb_add_request: request [d7d2db80, mid=23944] timed out!
Dec 11 21:00:55 thedrake -- MARK --
Dec 11 21:20:55 thedrake -- MARK --
Dec 11 21:40:56 thedrake -- MARK --
Dec 11 22:00:56 thedrake -- MARK --
Dec 11 22:15:24 thedrake kernel: [17209269.716000] SMB connection re-established (-5)
Dec 11 22:17:08 thedrake kernel: [17209374.476000] smb_add_request: request [caa32e80, mid=23946] timed out!
Dec 11 22:17:09 thedrake kernel: [17209374.700000] SMB connection re-established (-5)
```
3. Keep the terminal open --- it will display all messages when remove the card & re-insert it.
4. Remove the card & look for any strange messages in the terminal.
5. Re-insert the card & look for any new messages.
6. Post the output here.

Thanks,
Dave

---

### Post by adana on 2006-12-13
yes, just popping the network card out/in restores connectivity which is lost with every reboot.

In the messages below, you can see the where the card is ejected, "card ejected". 

Here is the output:

Dec 13 12:50:45 adana-laptop gconfd (adana-4320): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Dec 13 12:50:45 adana-laptop gconfd (adana-4320): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Dec 13 12:50:58 adana-laptop gconfd (adana-4320): Resolved address "xml:readwrite:/home/adana/.gconf" to a writable configuration source at position 0
Dec 13 12:55:29 adana-laptop kernel: [17179965.800000] pccard: card ejected from slot 1
Dec 13 12:55:40 adana-laptop kernel: [17179977.584000] pccard: PCMCIA card inserted into slot 1
Dec 13 12:55:40 adana-laptop kernel: [17179977.584000] pcmcia: registering new device pcmcia1.0
Dec 13 12:55:43 adana-laptop kernel: [17179979.972000] eth%%d: MII link partner: 45e1
Dec 13 12:55:43 adana-laptop kernel: [17179979.972000] eth%%d: MII selected
Dec 13 12:55:43 adana-laptop kernel: [17179979.996000] eth%%d: media 100BaseT, silicon revision 5
Dec 13 12:55:43 adana-laptop kernel: [17179979.996000] eth0: Xircom: port 0x300, irq 3, hwaddr 00:10:A4:A2:91:1E
Dec 13 12:55:43 adana-laptop kernel: [17179979.996000] pcmcia: registering new device pcmcia1.1
Dec 13 12:55:43 adana-laptop kernel: [17179979.996000] 1.1: ttyS3 at I/O 0x2e8 (irq = 3) is a 16550A
Dec 13 12:55:46 adana-laptop kernel: [17179982.968000] eth0: MII link partner: 45e1
Dec 13 12:55:46 adana-laptop kernel: [17179982.968000] eth0: MII selected
Dec 13 12:55:46 adana-laptop kernel: [17179982.992000] eth0: media 100BaseT, silicon revision 5

---

### Post by AusIV4 on 2006-12-13
I think this problem is being overanalyzed. I had a very similar problem upon upgrading to edgy. Turns out all I had to do was go into the KDE System Settings -> Network Settings, configure eth0, and tell it to enabl eth0 when the computer starts. For some reason, it had defaulted to off.

---

### Post by adana on 2006-12-13
Well, sounds reasonable.  But when I go into Network Settings (I have GNOME) I don't see any setting that enables eth0 at startup. What I see is a "Wired Connection" icon which is checked. Usually checked entries mean they are the default---I think. Right clicking on "Properties" shows some technical entires but nothing about enabling it at startup.

---

### Post by dbott67 on 2006-12-13
> **AusIV4 said:**
> I think this problem is being overanalyzed. I had a very similar problem upon upgrading to edgy. Turns out all I had to do was go into the KDE System Settings -> Network Settings, configure eth0, and tell it to enabl eth0 when the computer starts. For some reason, it had defaulted to off.

I don't think it's being over-analyzed in this case.  On the preceding page, his /etc/network/interfaces file looks correct (everything set to 'auto') and the card works when removed & re-inserted (which leads me to believe that either the NIC driver is not loading correctly or the PCMCIA driver is not loading correctly).

I'd be interested in seeing which drivers are loading.  Can you post the output of the following command:
```
sudo lshw
```

My next step would be to try re-starting the network after a re-boot (but before removing the card):
```
sudo /etc/init.d/networking restart
```

-Dave

---

### Post by adana on 2006-12-15
Here is the output of the networking start command:

 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
eth0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth0.
There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth1.
There is already a pid file /var/run/dhclient.eth2.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
eth2: ERROR while getting interface flags: No such device
eth2: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth2.
There is already a pid file /var/run/dhclient.ath0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: No such device
ath0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up ath0.
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.


############################

After getting the network back, here is the output of sudo lshw

adana@adana-laptop:~$ sudo lshw
adana-laptop              
    description: Notebook
    product: Solo 9300 Pro
    vendor: Gateway
    version: ALASKA15C02
    serial: 0021441495
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: administrator_password=enabled boot=normal chassis=docking frontpanel_password=unknown keyboard_password=unknown uuid=40CAF4DC-DE1D-B211-8000-D3399EF750CC
  *-core
       description: Motherboard
       product: Solo 9300 Pro
       physical id: 0
       slot: M_CN10
     *-firmware
          description: BIOS
          vendor: Gateway
          physical id: 0
          version: 16.86 (11/01/2000)
          size: 101KB
          capacity: 448KB
          capabilities: isa pci pcmcia pnp apm upgrade shadowing cdboot bootselect edd int13floppy720 int5printscreen int9keyboard int14serial int17printer acpi usb agp ls120boot smartbattery biosbootspecification
     *-cpu
          description: CPU
          product: Pentium III (Coppermine)
          vendor: Intel Corp.
          physical id: 5
          bus info: cpu@0
          version: 6.8.3
          slot: M_CN1
          size: 650MHz
          capacity: 650MHz
          width: 32 bits
          clock: 100MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr sse up
        *-cache:0
             description: L1 cache
             physical id: a
             slot: L1 Cache
             size: 32KB
             capacity: 32KB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: b
             slot: L2 Cache
             size: 256KB
             capacity: 512KB
             capabilities: external write-back
     *-memory
          description: System Memory
          physical id: 21
          slot: System board or motherboard
          size: 544MB
          capacity: 1GB
        *-bank:0
             description: DIMM DRAM Synchronous 100 MHz (10.0 ns)
             physical id: 0
             slot: ON BOARD
             size: 32MB
             width: 32 bits
             clock: 100MHz (10ns)
        *-bank:1
             description: DIMM DRAM Synchronous 100 MHz (10.0 ns)
             physical id: 1
             slot: M_CN2
             size: 256MB
             width: 32 bits
             clock: 100MHz (10ns)
        *-bank:2
             description: DIMM DRAM Synchronous 100 MHz (10.0 ns)
             physical id: 2
             slot: M_CN3
             size: 256MB
             width: 32 bits
             clock: 100MHz (10ns)
     *-pci
          description: Host bridge
          product: 440BX/ZX/DX - 82443BX/ZX/DX Host bridge
          vendor: Intel Corporation
          physical id: f8000000
          bus info: pci@00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          resources: iomemory:f8000000-fbffffff
        *-pci
             description: PCI bridge
             product: 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@00:01.0
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
           *-display
                description: VGA compatible controller
                product: Rage Mobility P/M AGP 2x
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@01:00.0
                version: 64
                size: 16MB
                width: 32 bits
                clock: 33MHz
                capabilities: vga bus_master cap_list
                resources: iomemory:f5000000-f5ffffff ioport:9000-90ff iomemory:f4100000-f4100fff irq:11
        *-isa UNCLAIMED
             description: ISA bridge
             product: 82371AB/EB/MB PIIX4 ISA
             vendor: Intel Corporation
             physical id: 7
             bus info: pci@00:07.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
        *-ide
             description: IDE interface
             product: 82371AB/EB/MB PIIX4 IDE
             vendor: Intel Corporation
             physical id: 7.1
             bus info: pci@00:07.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=PIIX_IDE
             resources: ioport:1000-100f
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-disk
                   description: ATA Disk
                   product: TOSHIBA MK1016GAP
                   vendor: Toshiba
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   version: U1.11 A
                   serial: X0534905T
                   size: 9590MB
                   capacity: 9590MB
                   capabilities: ata dma lba iordy smart security pm apm partitioned partitioned:dos
                   configuration: apm=off mode=udma2 smart=on
                 *-volume:0
                      description: Linux filesystem partition
                      physical id: 1
                      bus info: ide@0.0,1
                      logical name: /dev/hda1
                      capacity: 9162MB
                      capabilities: primary bootable
                 *-volume:1
                      description: Extended partition
                      physical id: 2
                      bus info: ide@0.0,2
                      logical name: /dev/hda2
                      capacity: 423MB
                      capabilities: extended partitioned partitioned:extended
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 33MHz
              *-cdrom
                   description: IDE CD-ROM
                   product: CD-224E
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   version: K.0B
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio
                 *-disc
                      physical id: 0
                      logical name: /dev/hdc
        *-usb
             description: USB Controller
             product: 82371AB/EB/MB PIIX4 USB
             vendor: Intel Corporation
             physical id: 7.2
             bus info: pci@00:07.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:1020-103f irq:10
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.17-10-generic uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-bridge
             description: Bridge
             product: 82371AB/EB/MB PIIX4 ACPI
             vendor: Intel Corporation
             physical id: 7.3
             bus info: pci@00:07.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bridge
             configuration: driver=piix4_smbus
             resources: irq:9
        *-multimedia
             description: Multimedia audio controller
             product: ES1978 Maestro 2E
             vendor: ESS Technology
             physical id: 8
             bus info: pci@00:08.0
             version: 10
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ES1968 (ESS Maestro)
             resources: ioport:1400-14ff irq:9
        *-communication UNCLAIMED
             description: Communication controller
             product: WinModem 56k
             vendor: Agere Systems
             physical id: b
             bus info: pci@00:0b.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: cap_list
             resources: iomemory:f4000000-f40000ff irq:255
        *-pcmcia:0
             description: CardBus bridge
             product: PCI1451 PC card Cardbus Controller
             vendor: Texas Instruments
             physical id: c
             bus info: pci@00:0c.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus
             resources: iomemory:38100000-38100fff irq:11
        *-pcmcia:1
             description: CardBus bridge
             product: PCI1451 PC card Cardbus Controller
             vendor: Texas Instruments
             physical id: c.1
             bus info: pci@00:0c.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus
             resources: iomemory:38101000-38101fff irq:9
           *-serial
                description: CreditCard Ethernet 10/100 + Modem 56
                product: CEM56
                vendor: Xircom
                physical id: 0
                version: 1.00
                slot: Socket 1
                resources: irq:3
  *-battery:0
       description: Battery
       product: ME33-17XX
       vendor: SANYO
       physical id: 1
       slot: Bottom
       capacity: 1029mWh
       configuration: voltage=10.8V
  *-battery:1
       physical id: 2
       slot: FDD Bay
  *-network
       description: Ethernet interface
       physical id: 3
       logical name: eth0
       serial: 00:10:a4:a2:91:1e
       capabilities: ethernet physical
       configuration: broadcast=yes driver=xirc2ps_cs ip=192.168.245.105 multicast=yes

---

### Post by adana on 2006-12-19
no way to fix this?

---

### Post by dbott67 on 2006-12-19
I'm a bit perplexed... I don't know why it works when you unplug & then plug it back in, but not when you leave it plugged in.

Perhaps it has to do with the PCMCIA/PC Card driver.  Can you try unloading & re-loading the cardbus driver:

```
sudo rmmod yenta_cardbus && sudo modprobe yenta_cardbus
```
Then check your network settings using ifconfig.

If it works, you could write a little bash script that unloads the drivers and then re-loads them at startup:

```
#!/bin/bash
rmmod yenta_cardbus
modprobe yenta_cardbus

```
Set the script as executable and then run as root.

Just grabbing at straws, really.

-Dave

---

### Post by mtntrx on 2006-12-29
Same problem, same card: Xircom 10/100 PCMCIA card.
Install is 6.06.1 using the server/LAMP install option (unsure what the name of this is)
During install it DID see the network and configured DHCP giving the "success" message.

Each reboot - no eth0;  pull card - reinsert... bingo

Will try that last debug suggestion and get back.

-dan

Ok, I have no module named yenta_carbus
I do have yenta_socket.

Would it have let me rmmod a module in use anyway?
I'm not sure what to try next.  Will search bugs etc.

FYI: this is my first use of ubuntu (was red-hat)  No so sure this was a good idea....

-dan

---

### Post by davethesteam on 2006-12-29
> **adana said:**
> Very interesting. If I pop that "creditcard" out and plug it back in, ubuntu auto configures it within 1 minute and I am on the internet. If I reboot, it's gone and I have to pop it out again.

So I have to figure out how what config files might have those settings.

Any ideas?

As a complete newby, I have a similar problem with my desk top.
Win XP Pro installed on SATA drive 1 using Netgear FA311 v 2 ethernet card.
External modem / router / firewall (GURU GART2 - 4115 (Wired, not Wirelss). Boot manager on SATA 2
Ubuntu 6.10 installed on SATA drive 2,
All works fine on XP/SATA 1
Ethernet card recognised by Ubuntu 6.10 and connection to BTOpenworld showing on 'outside' of modem.
Ubuntu sees no internet or e.mail - any ideas out there please :confused: ???(please treat me gently!!!)

---

### Post by mtntrx on 2006-12-30
> **mtntrx said:**
> Same problem, same card: Xircom 10/100 PCMCIA card.
Install is 6.06.1 using the server/LAMP install option (unsure what the name of this is)
During install it DID see the network and configured DHCP giving the "success" message.

Each reboot - no eth0;  pull card - reinsert... bingo

Will try that last debug suggestion and get back.

-dan

Ok, I have no module named yenta_carbus
I do have yenta_socket.

Would it have let me rmmod a module in use anyway?
I'm not sure what to try next.  Will search bugs etc.

FYI: this is my first use of ubuntu (was red-hat)  No so sure this was a good idea....

-dan

Added debug hints:
Two Knoppix versions work great with this PCMCIA card.

Another question:  I tried switching to a 3com ethernet card (that also works under knoppix) but I have no idea how to get ubuntu to "rescan" for the hardware change and make the adjustment.  Any hints here?

-dan

---

### Post by dbott67 on 2006-12-30
The command is 'discover' (you made need a sudo in front... not too sure):

```
dbott@thedrake:~$ discover all
Intel Corporation 82845 845 (Brookdale) Chipset Host Bridge
Intel Corporation 82845 845 (Brookdale) Chipset AGP Bridge
Intel Corporation 82801 PCI Bridge
Intel Corporation 82801BA ISA Bridge (LPC)
Unknown LITE-ON DVDRW SOHW-1633S
D-Link System Inc RTL8139 Ethernet
Intel Corporation 82801BA IDE U100
Linux IDE-SCSI emulation layer
Intel Corporation 82801BA/BAM AC'97 Audio
Creative Labs SB Live! EMU10k1
Intel Corporation 82801BA/BAM USB (Hub #1)
Intel Corporation 82801BA/BAM USB (Hub #2)
Acer Laboratories Inc. [ALi] USB 1.1 Controller
Acer Laboratories Inc. [ALi] USB 1.1 Controller
Acer Laboratories Inc. [ALi] USB 1.1 Controller
Acer Laboratories Inc. [ALi] USB 2.0 Controller
ATI Technologies, Inc. RV350 AP [Radeon 9600]
ATI Technologies, Inc. RV350 AP [Radeon 9600] (Secondary)
Unknown ST340016A
dbott@thedrake:~$

```

> man discover                                                                                                                                                                        

NAME
       discover - hardware detection utility

SYNOPSIS
       discover [options] [devices]

DESCRIPTION
       discover is a command-line hardware detection utility.

OPTIONS
       In  each of the following options, BUSES is a comma-separated list of bus types to probe, and DEVICES is a blank-separated list of device types. The following bus types are current rec&#8208;
       ognized: pci, isa, pcmcia, usb, ide, scsi, parallel, and serial.  The following device types are currently recognized: bridge, cdrom, disk, ide, scsi, usb, ethernet, modem,  sound,  and
       video.  The word &#8216;all&#8217; may be given as a device type to specify each of the possible devices....


-Dave

---

### Post by mtntrx on 2007-01-01
> **mtntrx said:**
> Added debug hints:
Two Knoppix versions work great with this PCMCIA card.

Another question:  I tried switching to a 3com ethernet card (that also works under knoppix) but I have no idea how to get ubuntu to "rescan" for the hardware change and make the adjustment.  Any hints here?

-dan


OK, i was not able to solve the problem with the xircom card, so I put in another card (a 3com card 3x59x or whatever).

Different problem here:  network never came up. even after eject and re-insert.
ifup eth0 gave:

SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device

this blog gave me the answer:  [http://www.pletscher.org/blog/?p=29](http://www.pletscher.org/blog/?p=29)

This issue was the /etc/iftab file that had the xircom mac address tied to eth0.  This made the new card come up at eth1 and it was not getting appropriately configured.  A 'ifconfig -a' showed the eth1 entry.  My fix was to change the /etc/iftab to tie the new mac address to eth0.  I don't understand much of this, but it worked.

At this point I'm none too impressed with ubuntu.  Multiple redhat and knoppix versions had no issue with this kind of stuff.  Two issues already with my ubuntu install.  Hmmm...

-dan

---


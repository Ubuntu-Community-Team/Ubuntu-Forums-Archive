---
title: "Thinkpad T21 &amp; Jaunty"
date: 2009-04-25
forum: New to Ubuntu
---

### Post by dunbrokin on 2009-04-25
I am having real problems with my T21 and Jaunty....(I had Intrepid on it running well)....it will not maintain internet connection via wire....it keeps dropping the connection....!!!

---

### Post by pytheas22 on 2009-04-25
Please post the output of these commands:
```

lspci -nn
lshw -C Network
dmesg | grep -e eth
uname -rm
```

---

### Post by dunbrokin on 2009-04-25
> **pytheas22 said:**
> Please post the output of these commands:
```

lspci -nn
lshw -C Network
dmesg | grep -e eth
uname -rm
```

$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge [8086:7190] (rev 03)
00:01.0 PCI bridge [0604]: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge [8086:7191] (rev 03)
00:02.0 CardBus bridge [0607]: Texas Instruments PCI1450 [104c:ac1b] (rev 03)
00:02.1 CardBus bridge [0607]: Texas Instruments PCI1450 [104c:ac1b] (rev 03)
00:03.0 Ethernet controller [0200]: 3Com Corporation 3c556B CardBus [Tornado] [10b7:6056] (rev 20)
00:03.1 Communication controller [0780]: 3Com Corporation Mini PCI 56k Winmodem [10b7:1007] (rev 20)
00:05.0 Multimedia audio controller [0401]: Cirrus Logic CS 4614/22/24/30 [CrystalClear SoundFusion Audio Accelerator] [1013:6003] (rev 01)
00:07.0 Bridge [0680]: Intel Corporation 82371AB/EB/MB PIIX4 ISA [8086:7110] (rev 02)
00:07.1 IDE interface [0101]: Intel Corporation 82371AB/EB/MB PIIX4 IDE [8086:7111] (rev 01)
00:07.2 USB Controller [0c03]: Intel Corporation 82371AB/EB/MB PIIX4 USB [8086:7112] (rev 01)
00:07.3 Bridge [0680]: Intel Corporation 82371AB/EB/MB PIIX4 ACPI [8086:7113] (rev 03)
01:00.0 VGA compatible controller [0300]: S3 Inc. 86C270-294 Savage/IX-MV [5333:8c12] (rev 13)

 *-network               
       description: Ethernet interface
       product: 3c556B CardBus [Tornado]
       vendor: 3Com Corporation
       physical id: 3
       bus info: pci@0000:00:03.0
       logical name: eth0
       version: 20
       serial: 00:04:76:60:6f:87
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=full ip=10.1.1.4 latency=64 link=yes maxlatency=10 mingnt=10 module=3c59x multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: ee:24:65:66:6c:33
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

[    4.451105] Driver 'sd' needs updating - please use bus_type methods
[    4.451133] Driver 'sr' needs updating - please use bus_type methods
[   33.633958] eth0:  setting full-duplex.
[   44.520204] eth0: no IPv6 routers present
[ 4385.891299] eth0:  setting full-duplex.
[ 4396.472170] eth0: no IPv6 routers present
[ 5400.511846] eth0:  setting full-duplex.
[ 5411.460214] eth0: no IPv6 routers present


2.6.28-11-generic i686


Actually, my wired system seems to have settled down and is working OK now...but my wireless system seems to be disabled and I cannot seem to find out how to enable it....Thanks

---

### Post by coffeeaddict22 on 2009-04-25
lshw -C network suggests you haven't got a wireless card installed.  If you've plugged something in since, reboot, then run the command again and see if the output has changed.

---

### Post by pytheas22 on 2009-04-25
hmmm, unfortunately I don't see anything that indicates why the connection is dropping, and I can't find anyone else via Google who reports problems with your ethernet card/driver on Ubuntu.  Are you positive there's not a problem with your Internet connection, your router or the ethernet wire?  If you have Windows on the same computer, does the ethernet work there?  You're certain that the failure coincided exactly with your upgrade to Jaunty?

We can try to install a different driver for your card, but first we should rule out hardware failure as the root of the problem.

coffeeaddict22: I think the original poster is trying to get an ethernet card working, not wireless (unless I've misunderstood).

---

### Post by dunbrokin on 2009-04-26
> **coffeeaddict22 said:**
> lshw -C network suggests you haven't got a wireless card installed.  If you've plugged something in since, reboot, then run the command again and see if the output has changed.

*-network               
       description: Ethernet interface 
       product: 3c556B CardBus [Tornado] 
       vendor: 3Com Corporation 
       physical id: 3 
       bus info: pci@0000:00:03.0 
       logical name: eth0 
       version: 20 
       serial: 00:04:76:60:6f:87 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list ethernet physical 
       configuration: broadcast=yes driver=3c59x ip=10.1.1.4 latency=64 maxlatency=10 mingnt=10 module=3c59x multicast=yes 
  *-network 
       description: Wireless interface 
       product: ACX 111 54Mbps Wireless Interface 
       vendor: Texas Instruments 
       physical id: 0 
       bus info: pci@0000:02:00.0 
       logical name: wlan0 
       version: 00 
       serial: 00:0f:3d:57:76:56 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list ethernet physical wireless 
       configuration: broadcast=yes driver=acx_pci latency=64 module=acx multicast=yes wireless=IEEE 802.11b+/g+ 
  *-network DISABLED 
       description: Ethernet interface 
       physical id: 1 
       logical name: pan0 
       serial: ee:24:65:66:6c:33 
       capabilities: ethernet physical 
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

---

### Post by dunbrokin on 2009-04-26
> **pytheas22 said:**
>  Are you positive there's not a problem with your Internet connection, your router or the ethernet wire?  If you have Windows on the same computer, does the ethernet work there?  You're certain that the failure coincided exactly with your upgrade to Jaunty?

We can try to install a different driver for your card, but first we should rule out hardware failure as the root of the problem.

coffeeaddict22: I think the original poster is trying to get an ethernet card working, not wireless (unless I've misunderstood).

Definitelyot not the internet connection as there are two other PCs running off this router. 

What seems to happen is not so much dropping the internet...its that when the internet is dropped the NM seems to lock up everything while it looks again for the line....and it takes ages to find it...if it finds it at all.

I am trying to get a PCMIA wireless card to work...Dlink Air Plus DWL-G650+

---

### Post by pytheas22 on 2009-04-26
Oh, so the problem is with wireless, not wired...

What is the output of:
```

iwconfig
dmesg | grep -e acx -e wlan
sudo iwlist scan
```

---

### Post by dunbrokin on 2009-04-26
> **pytheas22 said:**
> Oh, so the problem is with wireless, not wired...

What is the output of:
```

iwconfig
dmesg | grep -e acx -e wlan
sudo iwlist scan
```

There is a problem with the wired ....well maybe the NM as outlined earlier...I have not manged to get the wireless working yet.Should I do these commands with the wireless or with the wired?

---

### Post by dunbrokin on 2009-04-26
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

pan0      no wireless extensions.

~$ dmesg | grep -e acx -e wlan
[  732.534819] acx: Loaded combined PCI/USB driver, firmware_ver=default
[  732.534836] acx: compiled to use 32bit I/O access. I/O timing issues might occur, such as non-working firmware upload. Report them
[  732.534936] acx_pci 0000:02:00.0: enabling device (0000 -> 0002)
[  732.534962] acx_pci 0000:02:00.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[  732.534977] acx_pci 0000:02:00.0: setting latency timer to 64
[  732.535142] acx: found ACX111-based wireless network card at 0000:02:00.0, irq:11, phymem1:0x34020000, phymem2:0x34000000, mem1:0xe0b1c000, mem1_size:8192, mem2:0xe0a00000, mem2_size:131072
[  732.536191] acx: loading firmware for acx1111 chipset with radio ID 16
[  732.536203] acx_pci 0000:02:00.0: firmware: requesting acx/1.2.1.34/tiacx111c16
[  732.876441] IP: [<e0b5c8ad>] acxpci_s_reset_dev+0x1fd/0x250 [acx]
[  732.876529] Modules linked in: acx(+) nls_iso8859_1 nls_cp437 vfat fat usb_storage binfmt_misc bridge stp bnep input_polldev lp pcmcia ppdev thinkpad_acpi led_class nvram snd_cs46xx gameport snd_ac97_codec ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi psmouse serio_raw pcspkr snd_seq_midi_event snd_seq snd_timer snd_seq_device i2c_piix4 snd intel_agp soundcore yenta_socket snd_page_alloc agpgart rsrc_nonstatic pcmcia_core shpchp parport_pc nsc_ircc video parport output irda crc_ccitt usbhid 3c59x mii floppy fbcon tileblit font bitblit softcursor
[  732.876674] EIP is at acxpci_s_reset_dev+0x1fd/0x250 [acx]
[  732.876766]  [<e0b6026a>] ? acxpci_e_probe+0x42a/0x6a0 [acx]
[  732.877150]  [<e0acd000>] ? acx_e_init_module+0x0/0x41 [acx]
[  732.877176]  [<e0acd000>] ? acx_e_init_module+0x0/0x41 [acx]
[  732.877191]  [<e0acd067>] ? acxpci_e_init_module+0x26/0x28 [acx]
[  732.877208]  [<e0acd020>] ? acx_e_init_module+0x20/0x41 [acx]
[  732.877464] EIP: [<e0b5c8ad>] acxpci_s_reset_dev+0x1fd/0x250 [acx] SS:ESP 0068:deef3b40

: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

irda0     Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

---

### Post by pytheas22 on 2009-04-26
> There is a problem with the wired ....well maybe the NM as outlined earlier...I have not manged to get the wireless working yet.Should I do these commands with the wireless or with the wired?

Alright, so there are actually two separate issues here.  We can probably make the wireless work, but first let's fix the wired.  Please run these commands:
```

sudo /etc/init.d/NetworkManager stop
sudo ifconfig eth0 down
sudo ifconfig eth0 up
sudo dhclient eth0
```

This will stop NetworkManager and get you connected manually via the wire.  If you connect this way, does the connection still drop out?

Probably won't be able to respond again till tomorrow.

---

### Post by dunbrokin on 2009-04-26
> **pytheas22 said:**
> Alright, so there are actually two separate issues here.  We can probably make the wireless work, but first let's fix the wired.  Please run these commands:
```

sudo /etc/init.d/NetworkManager stop
sudo ifconfig eth0 down
sudo ifconfig eth0 up
sudo dhclient eth0
```



Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:04:76:60:6f:87
Sending on   LPF/eth0/00:04:76:60:6f:87
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPOFFER of 10.1.1.4 from 10.1.1.1
DHCPREQUEST of 10.1.1.4 on eth0 to 255.255.255.255 port 67
DHCPACK of 10.1.1.4 from 10.1.1.1
bound to 10.1.1.4 -- renewal in 1524 seconds.

---

### Post by dunbrokin on 2009-04-26
It seems to work much better now on wired....I was unable to get the BBC playylist in Totem earlier but I can get it now (of course that could be a BBC problem and not a NM problem!)

---

### Post by dunbrokin on 2009-04-26
Things have moved on a little...one step forward and one step back.

My problem has something to do with wlan0 and ipw - coz when I used these in wicd I could see my wireless router.....however I still could not connect...wicd does not seem to take Wep 40/120 bit key...and so I cannot get in. NM does allow 40/120 bit key...but now wicd seems to be the default manager...so I am not really sure what to do!!

---

### Post by dunbrokin on 2009-04-26
I am another small step forward....using wicd and ralink legacy as the WPA Supplicant Driver, I have managed to get into my router and on to the net...now however there seems to be some kind of dns problem as the pages of the net will not display properly.....I get an address not found error....

Onwards and upwards...

I have now set static IP and static DNS in both wired and wireless in wicd....but in the case of wired I can log on and view pages on the net, in the case of wireless I can log no but not view pages.....weird or what!!

---

### Post by pytheas22 on 2009-04-26
Can you view pages using wireless if you put the server IP address in your browser rather than the URL?  For example, put 74.125.67.100 in for Google, or 91.189.94.156 for ubuntu.com.

What is the output of these commands while you're connected via wireless:
```

iwconfig
ping -c 5 google.com
ping -c 5. 74.125.67.100
cat /etc/resolv.conf
```

---

### Post by dunbrokin on 2009-04-26
:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

pan0      no wireless extensions.

wlan0     IEEE 802.11b+/g+  ESSID:"DLINK"  Nickname:"acx v0.3.36"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:0F:3D:FC:86:C6   
          Bit Rate:2 Mb/s   Tx-Power=15 dBm   Sensitivity=1/3  
          Retry min limit:7   RTS thr:off   
          Power Management:off
          Link Quality=59/100  Signal level=43/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:~$ ping ~$ ping -c 5 google.com
ping: unknown host google.com
:~$ ping -c5 74.125.67.100
PING 74.125.67.100 (74.125.67.100) 56(84) bytes of data.
From 10.1.1.7 icmp_seq=1 Destination Host Unreachable
From 10.1.1.7 icmp_seq=2 Destination Host Unreachable
From 10.1.1.7 icmp_seq=3 Destination Host Unreachable
From 10.1.1.7 icmp_seq=4 Destination Host Unreachable
From 10.1.1.7 icmp_seq=5 Destination Host Unreachable

--- 74.125.67.100 ping statistics ---
5 packets transmitted, 0 received, +5 errors, 100% packet loss, time 4032ms
, pipe 3
:~$ cat /etc/resolv.conf
nameserver 208.67.222.222

---

### Post by pytheas22 on 2009-04-26
It looks like you can connect on wireless with no problems, but have no connectivity.  According to this old [bug report]("https://bugs.launchpad.net/ubuntu/+source/dhcp3/+bug/58927"), a possible cause of the problem has to do with the interface mtu being too short.  To fix the problem, try opening up your dhclient.conf file by typing:
```

sudo gedit /etc/dhcp3/dhclient.conf
```

Find the section of the file that looks like this:
```

request subnet-mask, broadcast-address, time-offset, routers,
	domain-name, domain-name-servers, domain-search, host-name,
	netbios-name-servers, netbios-scope**, interface-mtu**;
```

Remove the part that's in bold above, so that the section looks like this:

```

request subnet-mask, broadcast-address, time-offset, routers,
	domain-name, domain-name-servers, domain-search, host-name,
	netbios-name-servers, netbios-scope;
```

(Make sure there's a semicolon at the end.)  Save and close the file, and reboot.  Then try connecting on wireless again using dhcp.  Does it work better now?

---

### Post by dunbrokin on 2009-04-26
That worked a treat to start off...as I could see this forum from reboot...but when I clicked on reply to thank you for your help, it could not find the address again....Synaptic will not work either.

On the second reboot, no change from the usual Address Not Found!

---

### Post by pytheas22 on 2009-04-26
hmmm, that's weird.  What if you connect on wireless, then set the mtu manually by typing:
```

sudo ifconfig wlan0 mtu 1400
```

Do you still lose the connection?

---

### Post by dunbrokin on 2009-04-26
> **pytheas22 said:**
> hmmm, that's weird.  What if you connect on wireless, then set the mtu manually by typing:
```

sudo ifconfig wlan0 mtu 1400
```

Do you still lose the connection?

That still churns and churns looking for the address...

---

### Post by pytheas22 on 2009-04-26
I wonder if you'd have better luck if you used ndiswrapper to drive the card instead of the native driver.  What is the exact name of the wireless card?  Also, please unplug it (it's a PCMCIA device, right?), plug it back in, then post the output of:
```

dmesg | tail -50
uname -rm
```

---

### Post by dunbrokin on 2009-04-26
> **pytheas22 said:**
> 
```

dmesg | tail -50
uname -rm
```

~$ dmesg | tail -50
[ 3333.977810]  [<e0a7f695>] acxpci_s_delete_dma_regions+0x45/0x60 [acx]
[ 3333.977827]  [<e0a815e5>] acxpci_e_remove+0x105/0x29d [acx]
[ 3333.977836]  [<c020a39f>] ? sysfs_hash_and_remove+0x5f/0x70
[ 3333.977847]  [<c02dc359>] pci_device_remove+0x19/0x40
[ 3333.977856]  [<c034ed84>] __device_release_driver+0x74/0xb0
[ 3333.977865]  [<c034ee93>] device_release_driver+0x23/0x40
[ 3333.977873]  [<c034e412>] bus_remove_device+0x82/0xb0
[ 3333.977881]  [<c034cb68>] device_del+0xe8/0x190
[ 3333.977888]  [<c034cc1b>] device_unregister+0xb/0x20
[ 3333.977896]  [<c02d8003>] pci_stop_dev+0x23/0x30
[ 3333.977904]  [<c02d8081>] pci_destroy_dev+0x11/0x80
[ 3333.977912]  [<c02d8180>] pci_remove_bus_device+0x30/0x40
[ 3333.977920]  [<c02d81b9>] pci_remove_behind_bridge+0x29/0x40
[ 3333.977937]  [<e084c0a3>] cb_free+0x43/0x50 [pcmcia_core]
[ 3333.977953]  [<e0848691>] socket_shutdown+0x81/0xf0 [pcmcia_core]
[ 3333.977963]  [<c0500ac6>] ? printk+0x18/0x1a
[ 3333.977980]  [<e08488b4>] socket_remove+0x44/0x50 [pcmcia_core]
[ 3333.977998]  [<e0849157>] pccardd+0x1d7/0x290 [pcmcia_core]
[ 3333.978015]  [<e0848f80>] ? pccardd+0x0/0x290 [pcmcia_core]
[ 3333.978024]  [<c014e90c>] kthread+0x3c/0x70
[ 3333.978031]  [<c014e8d0>] ? kthread+0x0/0x70
[ 3333.978040]  [<c0105477>] kernel_thread_helper+0x7/0x10
[ 3333.978045] ---[ end trace fa3900775a6e4cbc ]---
[ 3333.978095] acx_pci 0000:02:00.0: PCI INT A disabled
[ 3338.208076] pcmcia_socket pcmcia_socket0: pccard: CardBus card inserted into slot 0
[ 3338.208134] pci 0000:02:00.0: reg 10 32bit mmio: [0x000000-0x001fff]
[ 3338.208148] pci 0000:02:00.0: reg 14 32bit mmio: [0x000000-0x01ffff]
[ 3338.208200] pci 0000:02:00.0: supports D1 D2
[ 3338.208207] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot
[ 3338.208217] pci 0000:02:00.0: PME# disabled
[ 3338.214572] acx_pci 0000:02:00.0: enabling device (0000 -> 0002)
[ 3338.214603] acx_pci 0000:02:00.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[ 3338.214618] acx_pci 0000:02:00.0: setting latency timer to 64
[ 3338.214746] acx: found ACX111-based wireless network card at 0000:02:00.0, irq:11, phymem1:0x34020000, phymem2:0x34000000, mem1:0xe08e0000, mem1_size:8192, mem2:0xe0bc0000, mem2_size:131072
[ 3338.215790] acx: loading firmware for acx1111 chipset with radio ID 16
[ 3338.215802] acx_pci 0000:02:00.0: firmware: requesting acx/1.2.1.34/tiacx111c16
[ 3338.944557] NVS_vendor_offs:01CD probe_delay:200 eof_memory:1114112
[ 3338.944569] CCAModes:04 Diversity:01 ShortPreOpt:01 PBCC:01 ChanAgil:00 PHY:05 Temp:01
[ 3338.944576] AntennaID:00 Len:02 Data:01 02 
[ 3338.944584] PowerLevelID:01 Len:02 Data:001E 000A 
[ 3338.944592] DataRatesID:02 Len:05 Data:02 04 11 22 44 
[ 3338.944604] DomainID:03 Len:06 Data:30 20 30 31 32 40 
[ 3338.944617] ProductID:04 Len:09 Data:TI ACX100
[ 3338.944623] ManufacturerID:05 Len:07 Data:TI Test
[ 3339.004056] acx: === chipset TNETW1130, radio type 0x16 (Radia), form factor 0x01 ((mini-)PCI / CardBus), EEPROM version 0x05: uploaded firmware 'Rev 1.2.1.34' ===
[ 3339.015582] acx v0.3.36: net device wlan0, driver compiled against wireless extensions 22 and Linux 2.6.28-11-generic
[ 3340.100271] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3344.400370] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3346.156301] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 3356.512034] wlan0: no IPv6 routers present

:~$ uname -rm
2.6.28-11-generic i686

---

### Post by pytheas22 on 2009-04-26
Please run these commands to bring the device up under ndiswrapper:
```

sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9
wget http://www.ovislink.fr/administration/pilotes/wifi/wl8000pci/8000PCI.zip
unzip 8000PCI.zip
sudo ndiswrapper -i Driver/winxp/TNET1130.INF
sudo rmmod acx
sudo depmod -a
sudo modprobe ndiswrapper
```

Wait a few seconds and try connecting on wireless again.  If it doesn't work, please post the output of:
```

lshw -C Network
sudo iwlist scan
dmesg | grep -e ndis -e wlan
ndiswrapper -l
```

---

### Post by dunbrokin on 2009-04-26
~$ sudo lshw -C Network
  *-network               
       description: Ethernet interface
       product: 3c556B CardBus [Tornado]
       vendor: 3Com Corporation
       physical id: 3
       bus info: pci@0000:00:03.0
       logical name: eth0
       version: 20
       serial: 00:04:76:60:6f:87
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=full ip=10.1.1.7 latency=64 link=yes maxlatency=10 mingnt=10 module=3c59x multicast=yes port=MII speed=100MB/s
  *-network
       description: Wireless interface
       product: ACX 111 54Mbps Wireless Interface
       vendor: Texas Instruments
       physical id: 1
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       serial: 00:0f:3d:57:76:56
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+tnet1130 driverversion=1.53+OvisLink,03/10/2004,6.0.0.1 latency=64 link=no module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 9e:e3:f2:5e:d5:2d
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
fitz@fitz-laptop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

irda0     Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:0F:3D:FC:86:C6
                    ESSID:"DLINK"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:100/100  Signal level:-19 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

~$ dmesg | grep -e ndis -e wlan
[   18.951048] acx v0.3.36: net device wlan0, driver compiled against wireless extensions 22 and Linux 2.6.28-11-generic
[   29.048274] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   36.680315] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   38.808362] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   48.824035] wlan0: no IPv6 routers present
[ 1004.868886] wlan0: got deauth frame with reason 2 (prev auth is not valid)
[ 2240.114219] wlan0: got deauth frame with reason 2 (prev auth is not valid)
[ 3339.015582] acx v0.3.36: net device wlan0, driver compiled against wireless extensions 22 and Linux 2.6.28-11-generic
[ 3340.100271] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3344.400370] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3346.156301] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 3356.512034] wlan0: no IPv6 routers present
[ 3399.156303] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3401.216293] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 3411.332037] wlan0: no IPv6 routers present
[ 4093.062485] wlan0: got deauth frame with reason 2 (prev auth is not valid)
[ 4409.107522] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[ 4409.181262] ndiswrapper: driver tnet1130 (OvisLink,03/10/2004,6.0.0.18) loaded
[ 4409.196097] ndiswrapper 0000:02:00.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[ 4409.812755] ndiswrapper: using IRQ 11
[ 4410.050890] wlan0: ethernet device 00:0f:3d:57:76:56 using NDIS driver: tnet1130, version: 0x5000200, NDIS version: 0x501, vendor: 'TNET1130', 104C:9066.5.conf
[ 4410.051122] wlan0: encryption modes supported: WEP; TKIP with WPA
[ 4410.051468] usbcore: registered new interface driver ndiswrapper
[ 4437.727742] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4444.651942] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4511.490639] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4537.096600] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4559.454782] ADDRCONF(NETDEV_UP): wlan0: link is not ready

:~$ ndiswrapper -l
tnet1130 : driver installed
	device (104C:9066) present (alternate driver: acx)

This was run while the wired was live but the wireless card was still plugged in.

---

### Post by pytheas22 on 2009-04-26
It looks like ndiswrapper brought the card up without a problem.  Can you try connecting to see if it works better now?  If you can't see networks in wicd, make sure the correct interface named is specified in 'Preferences'.  The wireless interface name should be 'wlan0'.

---

### Post by dunbrokin on 2009-04-26
> **pytheas22 said:**
> It looks like ndiswrapper brought the card up without a problem.  Can you try connecting to see if it works better now?  If you can't see networks in wicd, make sure the correct interface named is specified in 'Preferences'.  The wireless interface name should be 'wlan0'.

hmmm...it brings up the card after a fashion...there is no green bar in wicd like there was without ndiswrapper...and it still cannot access any pages on the net.

The wireless interface is set at wlan0

---

### Post by dunbrokin on 2009-04-26
For want of anything better to do, I restarted the machine with the wire disconnected but with the wireless card plugged in. I got full green bars in wicd (instead of the usual amber one) and it could see the first page of this forum (assuming it was not a cached image) but, again, when i clicked on Reply, the whole thing just churned and churned and lost connection with the addresses.

Apart from the fact that it cannot see the addresses, it does seem to be more stable now under ndiswrapper.

---

### Post by pytheas22 on 2009-04-27
With the cable unplugged and the wireless connected under ndiswrapper, what is the output of:
```

host google.com
ping -c 5 74.125.67.100
wget 74.125.67.100
```
> 
Apart from the fact that it cannot see the addresses, it does seem to be more stable now under ndiswrapper.

How is it more stable now...do you mean it feels faster or something?  Also, what do you mean when you say it can't see addresses?  Are you just referring to the way it times out when you press the reply button in the forum?

Also, note that if you restart your computer, you will need to run these commands for ndiswrapper to take effect:
```

sudo rmmod acx
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
```

Otherwise, the card will be driven by the old driver.  If ndiswrapper proves to solve the problem, we can make it drive the card permanently, but for now you will have to load it manually.

---

### Post by dunbrokin on 2009-04-27
~$ host google.com
;; connection timed out; no servers could be reached

~$ ping -c 5 74.125.67.100
PING 74.125.67.100 (74.125.67.100) 56(84) bytes of data.
From 10.1.1.7 icmp_seq=1 Destination Host Unreachable
From 10.1.1.7 icmp_seq=2 Destination Host Unreachable
From 10.1.1.7 icmp_seq=3 Destination Host Unreachable
From 10.1.1.7 icmp_seq=4 Destination Host Unreachable
From 10.1.1.7 icmp_seq=5 Destination Host Unreachable

--- 74.125.67.100 ping statistics ---
5 packets transmitted, 0 received, +5 errors, 100% packet loss, time 4023ms
, pipe 3

:~$ wget 74.125.67.100
--2009-04-27 16:42:26--  [http://74.125.67.100/](http://74.125.67.100/)
Connecting to 74.125.67.100:80... failed: No route to host.


Ah, if you have to load the ndiswrapper by hand then I guess my comments must apply to the old driver which will have been loaded when I restarted....so in fact the old driver is better than ndiswrapper. Better in that it gives green bars in wicd whereas ndiswrapper onlby gave an amber one. And yes you are correct in your understanding of what I mean by cannot see the address....when I click on the reply button, I get a time out as address is not found/recognised.

---

### Post by dunbrokin on 2009-04-27
> **pytheas22 said:**
> 


```

sudo rmmod acx
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
```

.

:~$ sudo rmmod acx
[sudo] password for : 
:~$ sudo rmmod ndiswrapper
ERROR: Module ndiswrapper does not exist in /proc/modules
~$ sudo modprobe ndiswrapper
~$

---

### Post by willingc on 2009-04-27
Dunbrokin,

pytheas22 is doing a great job of walking you through this issue. I wish I had posted a similar issue with a PCMCIA wireless card during the testing of Jaunty. Hopefully, you will get your wireless working soon.

For what it is worth, I switched from a PCMCIA wireless card (never was able to get it stable with Jaunty during testing as it would not hold a connection more than a few seconds) to a USB wireless adaptor (Edimax EW-7318USg). The Edimax works on my T21 under Jaunty (and also 8.10) with no additional configuration (other than entering the WPA password).

Best of luck getting your PCMCIA card working. If you get it working, I will try to replicate the steps with my PCMCIA card.

---

### Post by pytheas22 on 2009-04-27
Sorry to ask for yet more output, but I'm still not sure what could be going on.  Could you please connect under ndiswrapper once again, then post the output of:
```

lshw -C Network
dmesg | grep -i -e ndis -e wlan -e error
ping -c 5 74.125.67.100
ping -c 5 10.1.1.1
```

And just to be clear: you're using dhcp, not static IP, correct?

---

### Post by dunbrokin on 2009-04-27
No, I am using static IP.

---

### Post by dunbrokin on 2009-04-27
> **pytheas22 said:**
> Sorry to ask for yet more output, but I'm still not sure what could be going on.  Could you please connect under ndiswrapper once again, then post the output of:
```

lshw -C Network
dmesg | grep -i -e ndis -e wlan -e error
ping -c 5 74.125.67.100
ping -c 5 10.1.1.1
```

And just to be clear: you're using dhcp, not static IP, correct?

No problem in giving you more output...I am happy and keen to get this fixed and I am very appreciative of your help.

When I try to start under ndiswrapper as you suggested above, get the following error

:~$ sudo rmmod ndiswrapper
ERROR: Module ndiswrapper does not exist in /proc/modules

---

### Post by dunbrokin on 2009-04-27
Having carried out these commands, the wireless card is no longer found. No lights are on and wicd cannot see it.

---

### Post by dunbrokin on 2009-04-27
> **willingc said:**
> Dunbrokin,

pytheas22 is doing a great job of walking you through this issue. I wish I had posted a similar issue with a PCMCIA wireless card during the testing of Jaunty. Hopefully, you will get your wireless working soon.



I strongly second that!

---

### Post by pytheas22 on 2009-04-27
> sudo rmmod ndiswrapper
ERROR: Module ndiswrapper does not exist in /proc/modules

Don't worry about this error; it's not a problem.
> 
Having carried out these commands, the wireless card is no longer found. No lights are on and wicd cannot see it.

Please run these commands and post all output:
```

sudo modprobe -r ndiswrapper acx
sudo modprobe ndiswrapper
```

At this point, your wireless should be up and you should be able to connect.  Please do so, then continue with:

```
dmesg | grep -e ndis -e wlan
sudo iwlist scan
ping -c 5 google.com
```

Also, please try this with dhcp instead of static IP.  It might work better.

---

### Post by dunbrokin on 2009-04-27
There is no connection under the ndiswrapper.

It gives an amber bar in wicd and the following. I will reboot - thus eliminating the ndiswrapper and try without it...

~$ dmesg | grep -e ndis -e wlan
[   19.002931] acx v0.3.36: net device wlan0, driver compiled against wireless extensions 22 and Linux 2.6.28-11-generic
[   29.048228] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   38.012446] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   39.008439] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   49.064056] wlan0: no IPv6 routers present
[  210.432293] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  212.492376] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  222.808037] wlan0: no IPv6 routers present
[ 1363.459331] wlan0: got deauth frame with reason 2 (prev auth is not valid)
[ 2598.774963] wlan0: got deauth frame with reason 2 (prev auth is not valid)
[ 3834.050534] wlan0: got deauth frame with reason 2 (prev auth is not valid)
[ 5070.726119] wlan0: got deauth frame with reason 2 (prev auth is not valid)
[ 6307.291720] wlan0: got deauth frame with reason 2 (prev auth is not valid)
[ 7542.307494] wlan0: got deauth frame with reason 2 (prev auth is not valid)
[ 8777.493153] wlan0: got deauth frame with reason 2 (prev auth is not valid)
[10012.198816] wlan0: got deauth frame with reason 2 (prev auth is not valid)
[11248.774478] wlan0: got deauth frame with reason 2 (prev auth is not valid)
[12488.690032] wlan0: got deauth frame with reason 2 (prev auth is not valid)
[13726.115525] wlan0: got deauth frame with reason 2 (prev auth is not valid)
[14971.610953] wlan0: got deauth frame with reason 2 (prev auth is not valid)
[16209.398363] wlan0: got deauth frame with reason 2 (prev auth is not valid)
[17445.502137] wlan0: got deauth frame with reason 2 (prev auth is not valid)
[18682.597764] wlan0: got deauth frame with reason 2 (prev auth is not valid)
[19918.383375] wlan0: got deauth frame with reason 2 (prev auth is not valid)
[21156.391616] wlan0: got deauth frame with reason 2 (prev auth is not valid)
[22392.784393] wlan0: got deauth frame with reason 2 (prev auth is not valid)
[23628.339673] wlan0: got deauth frame with reason 2 (prev auth is not valid)
[24866.967336] wlan0: got deauth frame with reason 2 (prev auth is not valid)
[26111.019938] wlan0: got deauth frame with reason 2 (prev auth is not valid)
[27350.855027] wlan0: got deauth frame with reason 2 (prev auth is not valid)
[28588.629980] wlan0: got deauth frame with reason 2 (prev auth is not valid)
[29825.514932] wlan0: got deauth frame with reason 2 (prev auth is not valid)
[31061.949700] wlan0: got deauth frame with reason 2 (prev auth is not valid)
[32298.524522] wlan0: got deauth frame with reason 2 (prev auth is not valid)
[33534.759246] wlan0: got deauth frame with reason 2 (prev auth is not valid)
[34774.233565] wlan0: got deauth frame with reason 2 (prev auth is not valid)
[49877.795581] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[49877.932262] ndiswrapper: driver tnet1130 (OvisLink,03/10/2004,6.0.0.18) loaded
[49877.948093] ndiswrapper 0000:02:00.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[49878.562195] ndiswrapper: using IRQ 11
[49878.798820] wlan0: ethernet device 00:0f:3d:57:76:56 using NDIS driver: tnet1130, version: 0x5000200, NDIS version: 0x501, vendor: 'TNET1130', 104C:9066.5.conf
[49878.799053] wlan0: encryption modes supported: WEP; TKIP with WPA
[49878.799398] usbcore: registered new interface driver ndiswrapper
[49895.786581] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[49903.852361] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[49977.961728] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[49997.114465] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[50014.107135] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[50031.186735] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[50048.101332] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[50066.989626] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[50084.133463] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[50101.110514] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[50105.664296] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[50118.171014] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[50135.133761] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[50152.147729] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[50169.127160] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[50186.138669] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[50203.136877] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[50220.135187] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[50237.138116] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[50254.157790] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[50301.680976] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[50339.308581] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[50396.852464] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[50608.255981] ADDRCONF(NETDEV_UP): wlan0: link is not ready
:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

irda0     Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:0F:3D:FC:86:C6
                    ESSID:"DLINK"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:100/100  Signal level:-20 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

:~$ ping -c 5 google.com
ping: unknown host google.com

---

### Post by dunbrokin on 2009-04-27
Having restarted now (presumably without ndiswrapper) there is a light on in the card but wicd does not see the card.



I lie...it does now...

---

### Post by dunbrokin on 2009-04-27
With static ip turned off and no ndiswrapper, we get a much better signal in wicd.

Here are the readouts:

~$ dmesg | grep -e ndis -e wlan
[   18.946893] acx v0.3.36: net device wlan0, driver compiled against wireless extensions 22 and Linux 2.6.28-11-generic
[   28.884227] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  202.067283] acx v0.3.36: net device wlan0, driver compiled against wireless extensions 22 and Linux 2.6.28-11-generic
[  213.708241] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  388.980382] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  390.828290] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  400.924036] wlan0: no IPv6 routers present

~$ sudo iwlist scan
 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

irda0     Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:0F:3D:FC:86:C6
                    ESSID:"DLINK"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=55/100  Signal level=37/100  Noise level=0/100
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 22 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s

~$ ping -c 5 google.com
ping: unknown host google.com

---

### Post by pytheas22 on 2009-04-27
After some more research on what those lines in dmesg about 'wlan0: got deauth frame with reason 2 (prev auth is not valid)' mean, I found these [two]("http://sidux.com/PNphpBB2-viewtopic-t-1569.html") [threads]("http://www.linuxforen.de/forums/showthread.php?t=206761"), which suggest that the problem may have to do with a bad firmware file.  One of the threads links to better firmware, but to install it, I need to know which version you're using now.  What is the output of:
```

dmesg | grep -i firmware -A 10 -B 10
```

---

### Post by dunbrokin on 2009-04-27
> **pytheas22 said:**
> :
```

dmesg | grep -i firmware -A 10 -B 10
```

$ dmesg | grep -i firmware -A 10 -B 10
[   17.271457] Registered led device: tpacpi::power
[   17.271574] Registered led device: tpacpi:orange:batt
[   17.271678] Registered led device: tpacpi:green:batt
[   17.271808] Registered led device: tpacpi::dock_active
[   17.271914] Registered led device: tpacpi::bay_active
[   17.272079] Registered led device: tpacpi::dock_batt
[   17.272191] Registered led device: tpacpi::unknown_led
[   17.272297] Registered led device: tpacpi::standby
[   17.274131] input: ThinkPad Extra Buttons as /devices/virtual/input/input8
[   17.599958] ppdev: user-space parallel port driver
[   17.600289] IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   17.646607] input: TPPS/2 IBM TrackPoint as /devices/platform/i8042/serio1/input/input9
[   17.882935] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x100-0x3af: clean.
[   17.883764] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   17.884277] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x820-0x8ff: clean.
[   17.884633] pcmcia_socket pcmcia_socket1: cs: IO port probe 0xc00-0xcf7: clean.
[   17.885308] pcmcia_socket pcmcia_socket1: cs: IO port probe 0xa00-0xaff: clean.
[   17.941643] acx: Loaded combined PCI/USB driver, firmware_ver=default
[   17.941655] acx: compiled to use 32bit I/O access. I/O timing issues might occur, such as non-working firmware upload. Report them
[   17.941760] acx_pci 0000:02:00.0: enabling device (0000 -> 0002)
[   17.941785] acx_pci 0000:02:00.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[   17.941800] acx_pci 0000:02:00.0: setting latency timer to 64
[   17.941927] acx: found ACX111-based wireless network card at 0000:02:00.0, irq:11, phymem1:0x34020000, phymem2:0x34000000, mem1:0xe0a48000, mem1_size:8192, mem2:0xe0c40000, mem2_size:131072
[   17.942973] acx: loading firmware for acx1111 chipset with radio ID 16
[   17.942984] acx_pci 0000:02:00.0: firmware: requesting acx/1.2.1.34/tiacx111c16
[   18.351064] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
[   18.351900] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   18.352379] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   18.352774] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   18.353452] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   18.884567] NVS_vendor_offs:01CD probe_delay:200 eof_memory:1114112
[   18.884580] CCAModes:04 Diversity:01 ShortPreOpt:01 PBCC:01 ChanAgil:00 PHY:05 Temp:01
[   18.884587] AntennaID:00 Len:02 Data:01 02 
[   18.884595] PowerLevelID:01 Len:02 Data:001E 000A 
[   18.884603] DataRatesID:02 Len:05 Data:02 04 11 22 44 
[   18.884614] DomainID:03 Len:06 Data:30 20 30 31 32 40 
[   18.884628] ProductID:04 Len:09 Data:TI ACX100
[   18.884633] ManufacturerID:05 Len:07 Data:TI Test
[   18.944055] acx: === chipset TNETW1130, radio type 0x16 (Radia), form factor 0x01 ((mini-)PCI / CardBus), EEPROM version 0x05: uploaded firmware 'Rev 1.2.1.34' ===
[   18.946893] acx v0.3.36: net device wlan0, driver compiled against wireless extensions 22 and Linux 2.6.28-11-generic
[   18.949670] usbcore: registered new interface driver acx_usb
[   19.215761] lp0: using parport0 (interrupt-driven).
[   19.525832] Adding 1502036k swap on /dev/sda5.  Priority:-1 extents:1 across:1502036k
[   20.178389] EXT3 FS on sda1, internal journal
[   22.087556] type=1505 audit(1240878828.452:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=1993
[   22.259834] type=1505 audit(1240878828.624:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=1997
[   22.260583] type=1505 audit(1240878828.628:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=1997
[   22.260896] type=1505 audit(1240878828.628:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=1997
[   22.261096] type=1505 audit(1240878828.628:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=1997
--
[  201.252086] pcmcia_socket pcmcia_socket0: pccard: CardBus card inserted into slot 0
[  201.252144] pci 0000:02:00.0: reg 10 32bit mmio: [0x000000-0x001fff]
[  201.252158] pci 0000:02:00.0: reg 14 32bit mmio: [0x000000-0x01ffff]
[  201.252210] pci 0000:02:00.0: supports D1 D2
[  201.252217] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot
[  201.252227] pci 0000:02:00.0: PME# disabled
[  201.260693] acx_pci 0000:02:00.0: enabling device (0000 -> 0002)
[  201.260723] acx_pci 0000:02:00.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[  201.260738] acx_pci 0000:02:00.0: setting latency timer to 64
[  201.260862] acx: found ACX111-based wireless network card at 0000:02:00.0, irq:11, phymem1:0x34020000, phymem2:0x34000000, mem1:0xe08a4000, mem1_size:8192, mem2:0xe0a40000, mem2_size:131072
[  201.261911] acx: loading firmware for acx1111 chipset with radio ID 16
[  201.261922] acx_pci 0000:02:00.0: firmware: requesting acx/1.2.1.34/tiacx111c16
[  202.000560] NVS_vendor_offs:01CD probe_delay:200 eof_memory:1114112
[  202.000572] CCAModes:04 Diversity:01 ShortPreOpt:01 PBCC:01 ChanAgil:00 PHY:05 Temp:01
[  202.000580] AntennaID:00 Len:02 Data:01 02 
[  202.000587] PowerLevelID:01 Len:02 Data:001E 000A 
[  202.000595] DataRatesID:02 Len:05 Data:02 04 11 22 44 
[  202.000606] DomainID:03 Len:06 Data:30 20 30 31 32 40 
[  202.000620] ProductID:04 Len:09 Data:TI ACX100
[  202.000626] ManufacturerID:05 Len:07 Data:TI Test
[  202.060059] acx: === chipset TNETW1130, radio type 0x16 (Radia), form factor 0x01 ((mini-)PCI / CardBus), EEPROM version 0x05: uploaded firmware 'Rev 1.2.1.34' ===
[  202.067283] acx v0.3.36: net device wlan0, driver compiled against wireless extensions 22 and Linux 2.6.28-11-generic
[  213.708241] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  382.496321] eth0:  setting full-duplex.
[  388.980382] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  390.828290] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  392.720038] eth0: no IPv6 routers present
[  400.924036] wlan0: no IPv6 routers present
[  542.804289] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  544.534882] eth0:  setting full-duplex.
[  544.760269] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

---

### Post by pytheas22 on 2009-04-28
Thanks for the output.  Please try running these commands to get better firmware:
```

wget ftp://ftp.dlink.co.uk/wireless/dwl-g650+_rev_Ax/dwl-g650+_rev_ax_drv_v204.zip
unzip dwl-g650+_rev_ax_drv_v204.zip
sudo cp driver/WinXP/FwRad1*bin /lib/firmware/acx/1.2.1.34/
sudo mv /lib/firmware/acx/1.2.1.34/FwRad16.bin /lib/firmware/acx/1.2.1.34/tiacx111c16
sudo mv /lib/firmware/acx/1.2.1.34/FwRad17.bin /lib/firmware/acx/1.2.1.34/tiacx111c17
```

Then reboot and give the card another try (using the native driver, not ndiswrapper).  If it still fails, please post the output of:
```

lshw -C Network
dmesg | grep -i -e firmware -e acx -e wlan
```

---

### Post by dunbrokin on 2009-04-28
Upon boot up, it showed the first page of the forum - but, again it could not access anything past that first page,

Then I disconnected the wireless and went to the wired to write the reply. Half way through, I decided to go back to the wireless. When I clicked connect, it could not find an IP address. I then changed it back to static IP and it connected without a problem. However, it still could not access the net.


~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 3c556B CardBus [Tornado]
       vendor: 3Com Corporation
       physical id: 3
       bus info: pci@0000:00:03.0
       logical name: eth0
       version: 20
       serial: 00:04:76:60:6f:87
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=3c59x latency=64 maxlatency=10 mingnt=10 module=3c59x multicast=yes
  *-network
       description: Wireless interface
       product: ACX 111 54Mbps Wireless Interface
       vendor: Texas Instruments
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       serial: 00:0f:3d:57:76:56
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=acx_pci ip=10.1.1.7 latency=64 module=acx multicast=yes wireless=IEEE 802.11b+/g+
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: ea:86:de:0f:9d:35
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes


:~$ dmesg | grep -i -e firmware -e acx -e wlan
[   17.536328] IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   17.896130] acx: Loaded combined PCI/USB driver, firmware_ver=default
[   17.896142] acx: compiled to use 32bit I/O access. I/O timing issues might occur, such as non-working firmware upload. Report them
[   17.896245] acx_pci 0000:02:00.0: enabling device (0000 -> 0002)
[   17.896270] acx_pci 0000:02:00.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[   17.896285] acx_pci 0000:02:00.0: setting latency timer to 64
[   17.896413] acx: found ACX111-based wireless network card at 0000:02:00.0, irq:11, phymem1:0x34020000, phymem2:0x34000000, mem1:0xe0a58000, mem1_size:8192, mem2:0xe0b40000, mem2_size:131072
[   17.897459] acx: loading firmware for acx1111 chipset with radio ID 16
[   17.897469] acx_pci 0000:02:00.0: firmware: requesting acx/1.2.1.34/tiacx111c16
[   18.824623] ProductID:04 Len:09 Data:TI ACX100
[   18.884057] acx: === chipset TNETW1130, radio type 0x16 (Radia), form factor 0x01 ((mini-)PCI / CardBus), EEPROM version 0x05: uploaded firmware 'Rev 1.2.0.30' ===
[   18.886892] acx v0.3.36: net device wlan0, driver compiled against wireless extensions 22 and Linux 2.6.28-11-generic
[   18.889716] usbcore: registered new interface driver acx_usb
[   29.572290] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   37.600382] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   39.736329] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   50.624055] wlan0: no IPv6 routers present
[  113.440335] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  115.193947] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  125.660035] wlan0: no IPv6 routers present
[  330.912427] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  332.564378] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  342.756039] wlan0: no IPv6 routers present
[  390.904267] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  392.964286] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  403.504050] wlan0: no IPv6 routers present

---

### Post by pytheas22 on 2009-04-28
hmmm, any change if you run these commands:
```

sudo mv /lib/firmware/acx/1.2.1.34/tiacx111c16 /lib/firmware/acx/1.2.0.30/tiacx111c16
sudo mv /lib/firmware/acx/1.2.1.34/tiacx111c17 /lib/firmware/acx/1.2.0.30/tiacx111c17
```

then reboot?  Also, what is the output of:
```

ping -c 5 10.1.1.1
```

By the way, you're positive this device actually works properly, right?  You've used it on a different operating system recently without problems?

---

### Post by dunbrokin on 2009-04-28
~$ ping -c 5 10.1.1.1
PING 10.1.1.1 (10.1.1.1) 56(84) bytes of data.
From 10.1.1.7 icmp_seq=1 Destination Host Unreachable
From 10.1.1.7 icmp_seq=2 Destination Host Unreachable
From 10.1.1.7 icmp_seq=3 Destination Host Unreachable
From 10.1.1.7 icmp_seq=4 Destination Host Unreachable
From 10.1.1.7 icmp_seq=5 Destination Host Unreachable

--- 10.1.1.1 ping statistics ---
5 packets transmitted, 0 received, +5 errors, 100% packet loss, time 4024ms
, pipe 3


Hmmmm  Actually, I have not tried this with any other system, I bought it specifically for this machine. All my other machines have built in wireless.

I will try it tomorrow on a Windows system.

---

### Post by dunbrokin on 2009-04-30
I checked out this card on a friends windows PC and it did not work....I think it must be broken. I am sincerely thankful for the help you have given me and I profusely apologise for wasting your precious time.

---

### Post by pytheas22 on 2009-05-02
Ah.  Sorry to hear the card itself is broken, but I'm glad it finally explains why it wasn't working--I was pretty puzzled, because everything indicated that it should have worked.

---


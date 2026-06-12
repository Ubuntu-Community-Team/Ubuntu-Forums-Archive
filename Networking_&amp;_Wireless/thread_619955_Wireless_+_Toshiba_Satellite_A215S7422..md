---
title: "Wireless + Toshiba Satellite A215S7422."
date: 2007-11-22
forum: Networking &amp; Wireless
---

### Post by Roasted on 2007-11-22
I just bought a new Toshiba Satellite. I've never once touched Ubuntu and wireless internet. I've always done things wired and they just worked.

I don't have a clue where to start. I seriously am completely lost. I tried to look up in the hardware manager to see what kind of wireless adapter I had, but I couldn't find it. All I know is I have a new laptop that is unable to connect to my wireless and fully functional network. Even in networking tools, I see NOTHING for wireless options. All I can select is modem or wired dhcp. WTF?

---

### Post by MrFSL on 2007-11-22
First, make sure that the wireless adapter is turned on. I.E. a switch on the outside of the computer to enable the antenna etc.

From a terminal I would recommend a:

```
lspci | grep -i net
``` to find out what type of wireless adapter we are dealing with.

---

### Post by Roasted on 2007-11-22
08 :00.0 ethernet controller: realtek semiconductor co., ltd. rtl8101e pxi express fast ethernet controller (rev 01)

---

### Post by raiwo on 2007-11-22
are you sure your wireless is turned on?

---

### Post by Roasted on 2007-11-22
100% positive. I had some trouble finding the switch on the laptop cause it's hidden a good bit. But it's on now and the indicator light is solid on the switch.

wireless is also enabled for G-only on my linksys router's configuration setup. I tried at first with it "mixed" (b and g) but I got no luck and switched it to G hoping it'd change something, which it didn't.

---

### Post by raiwo on 2007-11-22
in my case lspci | grep -i net gives me:
04:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)

where atheros is the wireless card & RTL8101E is wired card. try to update your id's```
sudo update-pciids
``` & then again lspci |...

---

### Post by Roasted on 2007-11-22
jason@jason:~$ lspci | grep -i net
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
jason@jason:~$

---

### Post by raiwo on 2007-11-22
what ```
lspci
``` gives?

---

### Post by Roasted on 2007-11-22
jason@jason:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:04.0 PCI bridge: ATI Technologies Inc Unknown device 7914
00:05.0 PCI bridge: ATI Technologies Inc Unknown device 7915
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
14:06.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
14:06.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
14:06.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
14:06.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
14:06.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
jason@jason:~$

---

### Post by raiwo on 2007-11-22
it's like you don't have a wireless card in your system!?

---

### Post by Roasted on 2007-11-22
I do. I don't know what's up with it. I talked to my cousin, who's literally a Linux Guru in quite a few different distros. He recommended I try out Fedora, so I'm giving that a shot. I've always wanted to try out different distros, so here's my shot.

Still frustrated at wtf is going on, but I'm going another flavor a shot.

---

### Post by MrFSL on 2007-11-22
A "Guru" and he suggested you try a different distro to fix your problem? That doesn't sound very guru-ish ;)

---

### Post by Roasted on 2007-11-22
> **MrFSL said:**
> A "Guru" and he suggested you try a different distro to fix your problem? That doesn't sound very guru-ish ;)

He was helping me fix the problem, and he said "This is why I stick to Fedora." From there I decided, ya know, maybe it's time I try something else. So we talked more about Fedora. 

It's also kind of difficult for him to help diagnose the problems I was having when he's 710 miles away. ;) 

He messes with Ubuntu in his free time. He prides in Fedora, Red Hat, and 2 others but I can't remember their names. He works for a company that deals heavily with security and unix structures.

---

### Post by Roasted on 2007-11-22
Okay, Fedora is pissing me off for the time being. I'm going back to Ubuntu.

For the love of God, does anybody know how to get this wireless adapter working????

---

### Post by nik62790 on 2007-11-22
im having somewhat the same problem on my satellite A135S4565. i have the switch turned on the light is solid and it will recognize wireless networks in the area but it wont connect to any.  it'll show that cool little icon that spins and has the two circles that turn green....after about a minute of that and one turning green it stops and goes back to the no network icon

---

### Post by alienatom on 2007-11-22
i found this forum page helpful. I have a Toshiba A215 S4697 and I am using my wireless card as I write this thanks to my fellow Ubuntu users.

[http://ubuntuforums.org/showthread.php?t=512828&highlight=ath_pci](http://ubuntuforums.org/showthread.php?t=512828&highlight=ath_pci)


As far as having Linux on the laptop however, the only drawback I have found so far is the suspend/hibernate issue with ati graphics drivers.  I am still waiting for fix to come out.  It seems like so far, as long as I stick with the basic VESA settings, I can put my laptop into suspend and start it back up without a hitch.  If want to use the restricted drivers everything still works except for suspending the power.

Good luck

---

### Post by Zack McCool on 2007-11-22
> **Roasted said:**
> jason@jason:~$ lspci | grep -i net
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
jason@jason:~$

Not sure why you aren't seeing it.  The A215 line uses the Atheros adapter.  It will work in 32 Bit Gutsy with an NDISwrapper.  But your listing isn't showing the adapter at all, which makes me think that it will not work no matter what driver you use.

---

### Post by nik62790 on 2007-11-22
that didnt help me at all.  still having the same problems.

---

### Post by Roasted on 2007-11-22
> **Zack McCool said:**
> Not sure why you aren't seeing it.  The A215 line uses the Atheros adapter.  It will work in 32 Bit Gutsy with an NDISwrapper.  But your listing isn't showing the adapter at all, which makes me think that it will not work no matter what driver you use.

That really makes no sense to me. The hardware is there. The hardware is functional. Vista runs that piece of hardware flawlessly. (ooooo, buuurn)

Why in the world wouldn't Ubuntu even realize a piece of hardware is there?!

---

### Post by raiwo on 2007-11-23
check on restricted drivers manager that atheros hardware access layer is enabled & try turn the wireless on & off from switch when ubuntu is on.

---

### Post by Roasted on 2007-11-23
How do I do that? When I go to restricted drivers manager, I see my ATI display driver. That's it. I can't do anything else. How do I get to the access layer or whatever to check the other one for wireless??

---

### Post by raiwo on 2007-11-23
hmm.. perhaps you don't have atheros card? Can you check the type of the in xp or vista? does anything happened when trying to switch wireless on & off when ubuntu is on?```
 lspci | grep -i n
```

---

### Post by Roasted on 2007-11-23
jason@jason:~$ lspci | grep -i n
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:04.0 PCI bridge: ATI Technologies Inc Unknown device 7914
00:05.0 PCI bridge: ATI Technologies Inc Unknown device 7915
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon X1200 Series
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
14:06.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
14:06.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
14:06.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
14:06.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
jason@jason:~$ 



I don't have XP. In Vista, it just says "Realtek high defintition audio."

---

### Post by xeth_delta on 2007-11-23
Have you issued this command?

```
sudo lshw -C net
```

Xeth

---

### Post by Roasted on 2007-11-23
jason@jason:~$ sudo lshw -C net
[sudo] password for jason:
  *-network               
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 01
       serial: 00:a0:d1:88:cb:25
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=half latency=0 link=no module=r8169 multicast=yes port=twisted pair
jason@jason:~$

---

### Post by xeth_delta on 2007-11-23
This is rather unusual. It is as if your wireless card was not present. This [http://www.toshibadirect.com/td/b2c/rdet.jsp?poid=393782&seg=HHO]("http://www.toshibadirect.com/td/b2c/rdet.jsp?poid=393782&seg=HHO") is your laptop, isn't it?

It seems to indeed have a realtek card. As far as I know, their hardware sometimes can be not that linux friendly.

I think that there is a couple of realtek modules (r818x and r8187) that are blacklisted.

```
nano /etc/modprobe.d/blacklist
```

and comment the lines referring to those modules, each in turn. Then, either reboot or

```
sudo modprobe r818x
```
or
```
sudo modprobe r8187
```

Then check what dmesg says.

Xeth

---

### Post by Roasted on 2007-11-23
Realtek RTL8187B Wireless 802.11G USB 2.0

---

### Post by MrFSL on 2007-11-23
USB?

Interesting... output of:
```
lsusb
```

please.

---

### Post by xeth_delta on 2007-11-23
This link might explain the problems you've had with your card [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsRealTek]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsRealTek"). It seems that you will have to use Ndiswrapper. In that case you should blacklist r818x and r8187 again.

Xeth

---

### Post by Roasted on 2007-11-23
So, once again, followed the directions, and I must be missing something.

I downloaded the 98 driver from a zip file. I extracted the net8187b.inf file that is supposedly the driver I need to work with.

The directions told me that he got it from a cd, so he did sudo ndiswrapper -i /cdrom/driver/blah/blah. I of course had to change my path due to the fact that I wasn't running it off of a CD.

Okay, fine. So I change the path. /Destop/net8187b.inf. 

"Error: no ndiswrapper utils found!" 

Following the directions here! What's up with this?? Detailed instructions would be nice! :)

---

### Post by xeth_delta on 2007-11-23
> **Roasted said:**
> 
"Error: no ndiswrapper utils found!"

You have to install the ndiswrapper utils. Some instructions here: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?highlight=%28ndiswrapper%29]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?highlight=%28ndiswrapper%29")

You can find the package with
```
aptitude search ndiswrapper
```
Then install, for example, version 1.9:
```
sudo aptitude install ndiswrapper-utils-1.9
```

Xeth

---

### Post by Roasted on 2007-11-23
Okay I have all 3 of the packages installed that you find when searching ndiswrapper in synaptic. 

So I started to redo the directions again. I went through the setup and it asked me to select which inf file to use, so I selected the rtl8187b.inf file which is the 98 driver for my exact wireless adapter. 

Then it says I'm supposed to make sure it went through by typing ndiswrapper -l in the terminal. I did.

I get back net8187b: invalid driver!!

Sounds like I'm halfway there...

---

### Post by xeth_delta on 2007-11-23
I am sorry for not being able to provide any more help on ndiswrapper, but I used just once, a couple of years ago. Hopefully someone who kbows more than me on this will lend a hand. Try searching in the forums, too.

Xeth

---

### Post by Roasted on 2007-11-23
Now I have the Windows 98 driver installed via ndiswrapper. However, it says "Hardware present: No"

How do I get around this?

---

### Post by xeth_delta on 2007-11-23
What is the result of

```
lsusb
```

---

### Post by Roasted on 2007-11-23
jason:~$ lsusb
Bus 001 Device 003: ID 09da:0006 A4 Tech Co., Ltd Optical Mouse WOP-35 / Trust 450L Optical Mouse
Bus 001 Device 001: ID 0000:0000  
Bus 006 Device 003: ID 0bda:8197 Realtek Semiconductor Corp. 
Bus 006 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
jason@jason:~$

---

### Post by raiwo on 2007-11-23
[http://www.datanorth.net/~cuervo/blog/2007/09/26/no-more-vista/](http://www.datanorth.net/~cuervo/blog/2007/09/26/no-more-vista/) patched driver for your card,

 found here: [http://ubuntuforums.org/showthread.php?t=571046&page=5](http://ubuntuforums.org/showthread.php?t=571046&page=5)

---

### Post by Roasted on 2007-11-23
Mhm, I've seen that. But when I run the command to run the tarball, I always get errors. I know I'm doing something wrong, I know it. Yet when I ask for detailed instructions on what to do, I don't get them.

Could you possibly give me step by step instructions on how to run that fully patched driver that you just linked me? I can handle the gui stuff okay, but when I'm using tarballs on the CLI I get confused and nothing seems to work. That'd be a HUGE help, my friend.

---

### Post by xeth_delta on 2007-11-23
Ok, you should be almost there, the wireless card is listed by **lsusb**, ndiswrapper is installed.
Just be a bit patient. Most of us do not have exactly the same hardware as you do, and as such we might not be able to give you exact procedures to follow right now, but to tell you where you can find more information. :)

Interesting, this is the first *internal* wireless card that I can remember of as being a USB device and not PCI.

Perhaps there is an option to give ndiswrapper to look for a USB device instead of PCI?
```
ndiswrapper --help
```
```
man ndiswrapper
```

I don't use ndiswrapper myself, so I cannot tell you that much about it. If nobody with ndiswrapper experience answers you could try starting a new thread on this specifically. 

Xeth

---

### Post by Roasted on 2007-11-24
Okay, I kind of took your advice and checked out the help command.

This is what I found.




jason@jason:~$ ndiswrapper --help
install/manage Windows drivers for ndiswrapper

usage: ndiswrapper OPTION
-i inffile       install driver described by 'inffile'
-a devid driver  use installed 'driver' for 'devid' (dangerous)
-r driver        remove 'driver'
-l               list installed drivers
-m               write configuration for modprobe
-ma              write module alias configuration for all devices
-mi              write module install configuration for all devices
-v               report version information

where 'devid' is either PCIID or USBID of the form XXXX:XXXX,
as reported by 'lspci -n' or 'lsusb' for the card
-------------------------------------------------------------------------------------------------------------------------
**I couldn't help but to notice the -a devid, so I ran an lsusb**
-------------------------------------------------------------------------------------------------------------------------
jason@jason:~$ lsusb
Bus 006 Device 003: ID 0bda:8197 Realtek Semiconductor Corp. 
Bus 006 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 046d:c019 Logitech, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
-------------------------------------------------------------------------------------------------------------------------
**Hmm, there's the DEVID I need. Right? I figured I'd give it a shot.**
-------------------------------------------------------------------------------------------------------------------------
jason@jason:~$ sudo ndiswrapper -a 0bda:8197 net8187b
[sudo] password for jason:
WARNING: Driver 'net8187b' will be used for '0BDA:8197'
This is safe _only_ if driver net8187b is meant for chip in device 0BDA:8197
jason@jason:~$ 
-------------------------------------------------------------------------------------------------------------------------
Needless to say, I thought I fixed it. But nothing at all changed. I'm trying here, I really am, but omgosh this is so frustrating.

---

### Post by xeth_delta on 2007-11-24
Hi, too bad it didn;t work. I know it an be frustrating at times.
What was the last error. from what you wrote ndiswrapper associated correctly the driver and issued a warning.

Are the ndiswrapper modules loaded? What do **dmesg**, **iwconfig** and **ifconfig** say?

---

### Post by Roasted on 2007-11-24
[    6.740000] ohci_hcd 0000:00:13.2: OHCI Host Controller
[    6.740000] ohci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 4
[    6.740000] ohci_hcd 0000:00:13.2: irq 20, io mem 0xf8606000
[    6.796000] usb usb4: configuration #1 chosen from 1 choice
[    6.796000] hub 4-0:1.0: USB hub found
[    6.796000] hub 4-0:1.0: 2 ports detected
[    6.900000] ACPI: PCI Interrupt 0000:00:13.3[B] -> GSI 17 (level, low) -> IRQ 17
[    6.900000] ohci_hcd 0000:00:13.3: OHCI Host Controller
[    6.900000] ohci_hcd 0000:00:13.3: new USB bus registered, assigned bus number 5
[    6.900000] ohci_hcd 0000:00:13.3: irq 17, io mem 0xf8607000
[    6.956000] usb usb5: configuration #1 chosen from 1 choice
[    6.956000] hub 5-0:1.0: USB hub found
[    6.956000] hub 5-0:1.0: 2 ports detected
[    6.980000] usb 3-6: new high speed USB device using ehci_hcd and address 2
[    7.056000]  sda1 sda2 sda3 sda4
[    7.060000] ACPI: PCI Interrupt 0000:00:13.4[C] -> GSI 18 (level, low) -> IRQ 20
[    7.060000] ohci_hcd 0000:00:13.4: OHCI Host Controller
[    7.060000] ohci_hcd 0000:00:13.4: new USB bus registered, assigned bus number 6
[    7.060000] ohci_hcd 0000:00:13.4: irq 20, io mem 0xf8608000
[    7.072000] sd 0:0:0:0: [sda] Attached SCSI disk
[    7.076000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    7.116000] usb usb6: configuration #1 chosen from 1 choice
[    7.116000] hub 6-0:1.0: USB hub found
[    7.116000] hub 6-0:1.0: 2 ports detected
[    7.116000] usb 3-6: configuration #1 chosen from 1 choice
[    7.220000] SB600_PATA: IDE controller at PCI slot 0000:00:14.1
[    7.220000] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 16
[    7.220000] SB600_PATA: chipset revision 0
[    7.220000] SB600_PATA: not 100% native mode: will probe irqs later
[    7.220000]     ide0: BM-DMA at 0x8420-0x8427, BIOS settings: hda:DMA, hdb:pio
[    7.220000] Probing IDE interface ide0...
[    7.344000] Attempting manual resume
[    7.344000] swsusp: Resume From Partition 8:2
[    7.344000] PM: Checking swsusp image.
[    7.344000] PM: Resume from disk failed.
[    7.372000] kjournald starting.  Commit interval 5 seconds
[    7.372000] EXT3-fs: mounted filesystem with ordered data mode.
[    7.956000] hda: TSSTcorp CDDVDW TS-L632H, ATAPI CD/DVD-ROM drive
[    8.628000] hda: selected mode 0x42
[    8.628000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[    8.644000] ACPI: PCI Interrupt 0000:14:06.0[A] -> GSI 20 (level, low) -> IRQ 21
[    8.696000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[21]  MMIO=[f8300000-f83007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    9.972000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00080da0d188cb25]
[   13.288000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   13.292000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   13.788000] Linux agpgart interface v0.102 (c) Dave Jones
[   13.800000] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
[   14.124000] hda: ATAPI 24X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(33)
[   14.124000] Uniform CD-ROM driver Revision: 3.20
[   14.136000] input: PC Speaker as /class/input/input2
[   14.276000] sdhci: Secure Digital Host Controller Interface driver
[   14.276000] sdhci: Copyright(c) Pierre Ossman
[   14.276000] sdhci: SDHCI controller found at 0000:14:06.1 [1180:0822] (rev 22)
[   14.276000] ACPI: PCI Interrupt 0000:14:06.1[B] -> GSI 21 (level, low) -> IRQ 22
[   14.276000] mmc0: SDHCI at 0xf8300800 irq 22 DMA
[   14.548000] ACPI: PCI Interrupt 0000:00:14.2[A] -> GSI 16 (level, low) -> IRQ 16
[   14.848000] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x9280b1, caps: 0xa04713/0x204000
[   14.848000] synaptics: Toshiba Satellite A215 detected, limiting rate to 40pps.
[   14.884000] input: SynPS/2 Synaptics TouchPad as /class/input/input3
[   15.276000] hda_codec: Unknown model for ALC268, trying auto-probe from BIOS...
[   15.500000] si3054: cannot initialize. EXT MID = 0000
[   15.788000] lp: driver loaded but no devices found
[   16.048000] Adding 1534196k swap on /dev/sda2.  Priority:-1 extents:1 across:1534196k
[   16.516000] EXT3 FS on sda3, internal journal
[   17.228000] kjournald starting.  Commit interval 5 seconds
[   17.232000] EXT3 FS on sda4, internal journal
[   17.232000] EXT3-fs: mounted filesystem with ordered data mode.
[   18.220000] ACPI: Battery Slot [BAT0] (battery present)
[   18.360000] input: Power Button (FF) as /class/input/input4
[   18.360000] ACPI: Power Button (FF) [PWRF]
[   18.396000] input: Power Button (CM) as /class/input/input5
[   18.400000] ACPI: Power Button (CM) [PWRB]
[   18.400000] input: Lid Switch as /class/input/input6
[   18.400000] ACPI: Lid Switch [LID]
[   18.432000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   18.456000] ACPI: AC Adapter [ADP0] (on-line)
[   18.684000] No dock devices found.
[   19.120000] powernow-k8: Found 2 AMD Turion(tm) 64 X2 Mobile Technology TL-58 processors (version 2.00.00)
[   19.136000] powernow-k8:    0 : fid 0xb (1900 MHz), vid 0x11
[   19.136000] powernow-k8:    1 : fid 0xa (1800 MHz), vid 0x12
[   19.136000] powernow-k8:    2 : fid 0x8 (1600 MHz), vid 0x13
[   19.136000] powernow-k8:    3 : fid 0x0 (800 MHz), vid 0x1e
[   20.380000] r8169: eth0: link down
[   20.424000] ppdev: user-space parallel port driver
[   20.596000] audit(1195923000.713:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4962 profile="/usr/sbin/cupsd"
[   20.652000] apm: BIOS not found.
[   21.004000] Failure registering capabilities with primary security module.
[   21.384000] Bluetooth: Core ver 2.11
[   21.384000] NET: Registered protocol family 31
[   21.384000] Bluetooth: HCI device and connection manager initialized
[   21.384000] Bluetooth: HCI socket layer initialized
[   21.400000] Bluetooth: L2CAP ver 2.8
[   21.400000] Bluetooth: L2CAP socket layer initialized
[   21.468000] Bluetooth: RFCOMM socket layer initialized
[   21.468000] Bluetooth: RFCOMM TTY layer initialized
[   21.468000] Bluetooth: RFCOMM ver 1.8
[   33.000000] Clocksource tsc unstable (delta = -152827681 ns)
[   33.448000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   33.456000] [fglrx] Maximum main memory to use for locked dma buffers: 802 MBytes.
[   33.456000] [fglrx] module loaded - fglrx 8.37.6 [May 25 2007] on minor 0
[   33.488000] ACPI: PCI Interrupt 0000:01:05.0[A] -> GSI 18 (level, low) -> IRQ 20
[   35.760000] [fglrx] total      GART = 130023424
[   35.760000] [fglrx] free       GART = 114032640
[   35.760000] [fglrx] max single GART = 114032640
[   35.760000] [fglrx] total      LFB  = 134217728
[   35.760000] [fglrx] free       LFB  = 119828480
[   35.760000] [fglrx] max single LFB  = 119828480
[   35.760000] [fglrx] total      Inv  = 0
[   35.760000] [fglrx] free       Inv  = 0
[   35.760000] [fglrx] max single Inv  = 0
[   35.760000] [fglrx] total      TIM  = 0
[   41.920000] hda-intel: Invalid position buffer, using LPIB read method instead.
[ 1244.752000] usb 3-2: new high speed USB device using ehci_hcd and address 4
[ 1244.968000] usb 3-2: configuration #1 chosen from 1 choice
[ 1245.372000] usbcore: registered new interface driver libusual
[ 1245.400000] Initializing USB Mass Storage driver...
[ 1245.404000] scsi4 : SCSI emulation for USB Mass Storage devices
[ 1245.404000] usb-storage: device found at 4
[ 1245.404000] usb-storage: waiting for device to settle before scanning
[ 1245.404000] usbcore: registered new interface driver usb-storage
[ 1245.404000] USB Mass Storage support registered.
[ 1250.412000] usb-storage: device scan complete
[ 1250.416000] scsi 4:0:0:0: Direct-Access     Kingston DataTraveler 2.0 1.00 PQ: 0 ANSI: 2
[ 1250.424000] sd 4:0:0:0: [sdb] 1001472 512-byte hardware sectors (513 MB)
[ 1250.424000] sd 4:0:0:0: [sdb] Write Protect is off
[ 1250.424000] sd 4:0:0:0: [sdb] Mode Sense: 0b 00 00 08
[ 1250.424000] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 1250.432000] sd 4:0:0:0: [sdb] 1001472 512-byte hardware sectors (513 MB)
[ 1250.432000] sd 4:0:0:0: [sdb] Write Protect is off
[ 1250.432000] sd 4:0:0:0: [sdb] Mode Sense: 0b 00 00 08
[ 1250.432000] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 1250.432000]  sdb: sdb1
[ 1250.432000] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[ 1250.432000] sd 4:0:0:0: Attached scsi generic sg1 type 0
jason@jason:~$ 


jason@jason:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

jason@jason:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:A0:D1:88:CB:25  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:400 (400.0 b)  TX bytes:400 (400.0 b)

jason@jason:~$ 


My laptop froze terminal about 5 times just trying to type in these 3 commands. Maybe I should just do a fresh install?

btw I had to erase the top part of the dmesg command because of there being too many smilies in there from random characters.

---

### Post by xeth_delta on 2007-11-24
> btw I had to erase the top part of the dmesg command because of there being too many smilies in there from random characters.

You can place the output between code statements, that way you can avoid characters being interpreted as smileys and it will be easier to read.

I am having a look at your dmesg ritght now. iwconfig and ifconfig did not find the network interfce, from what I can see. That would mean there's something wrong with ndiswrapper. Try
```
cat /var/log/messages
```
```
dmesg | grep -i ndis
```
```
lsmod
```
Please post the output (maybe the one from messages not complete, as it will be quite large, the last part).

---

### Post by Roasted on 2007-11-24
I'm reinstalling Ubuntu. It freezes after every 1-2 commands I issue to the terminal. It was just acting so erratic that there was no reason for it so I figured I'd start fresh and pray something worked this time. It's halfway done installing already, I'll report back after I get it up and running.

---

### Post by Roasted on 2007-11-24
Okay. I've made a decision. I'm just going to go buy a wireless adapter for the notebook. I mean, this can be a huge advantage to me. I have the cardbus slot open, and I found a belkin at staples for 35 bucks (wireless g) so why the hell not? 

But... I do have one question for you folks. I want to research wireless devices (like the pcmcia card I am looking at from staples) and see if it is 100% supported with ubuntu. Is there some kind of documentation web site I can find that says, YES, THIS BELKIN IS FULLY SUPPORTED. FACT. Is there any of those around? Because I'd like to browse online at like newegg, bestbuy, circuitcity, staples, officemax, etc and find an actual (cheaper) card that they sell that IS POSITIVELY supported.

Is there such a web site for ubuntu??

---

### Post by xeth_delta on 2007-11-25
> But... I do have one question for you folks. I want to research wireless devices (like the pcmcia card I am looking at from staples) and see if it is 100% supported with ubuntu. Is there some kind of documentation web site I can find that says, YES, THIS BELKIN IS FULLY SUPPORTED. FACT. Is there any of those around? Because I'd like to browse online at like newegg, bestbuy, circuitcity, staples, officemax, etc and find an actual (cheaper) card that they sell that IS POSITIVELY supported.


Have a look at this page: [https://wiki.ubuntu.com/HardwareSupport]("https://wiki.ubuntu.com/HardwareSupport"), and more specifically for wireless: [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported#head-603c9481d6c6288b6b674cc50132d21f6d539c53]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported#head-603c9481d6c6288b6b674cc50132d21f6d539c53")

Xeth

---

### Post by buccaneere on 2007-11-25
Wow.

Shuttin' down the school. And quittin'.:(

Chalk up another one for BGates.

This is extremely disappointing roasted.


Good job there xeth delta - you DID try there............................

---

### Post by xeth_delta on 2007-11-25
Hehe, thanks buccaneere, but one has to see that Roasted has tried a lot. I understand his point, too. It seems a bit unusual to me to have an internal wireless adapter placed on the USB bus rather than PCI. This together with the fact that (as far as I remember) Realtek is not always that FOSS friendly with its network cards might have contributed to Roasted's problem.

I don't think M$ has won this battle, though. Roasted seems determined to continue using Ubuntu, even if it is with another network card. I, for one, am glad I can just use the Madwifi drivers for my wireless Atheros based card :)

---

### Post by Roasted on 2007-11-25
> **buccaneere said:**
> Wow.

Shuttin' down the school. And quittin'.:(

Chalk up another one for BGates.

This is extremely disappointing roasted.


Good job there xeth delta - you DID try there............................

Pardon me... 

Let's reiterate something here. I love linux. I really do.

But in this situation, something is blatantly obvious here.

Vista works.
Ubuntu doesn't.

Yes. I agree. I am disappointed as well. But as we speak I am trying to get my new wireless card to work. We'll see if a new (and supported) PCMCIA wireless adapter will work!

---

### Post by xeth_delta on 2007-11-25
What card did you get? Let me know how it goes? I am really curious about why this has not been working.

---

### Post by Roasted on 2007-11-25
Dlink WNA 2330.

Is it possible that your PCMCIA slot can be disabled by default? Because I tried a Belkin F5D7010 last night, returned it this morning, as well as this Dlink WNA 2330, and neither one lit up in Linux OR Vista. In fact, I'm struggling now to get this Dlink working in Vista.

I've disabled the internal card in device manager hoping I could at least get the new Dlink one to detect without any interference. I've got a 32 bit version of Vista, and I downloaded the Vista-32 bit version of the driver from Dlink. Yet when I plug the card in, I get no response. No lights. Nothing. During the setup it asks me to plug in the card, so I do, and it just keeps popping up saying "Please plug in hardware device now." ITS IN DAMNIT! 

Can PCMCIA be disabled by default? I've checked bios, nothing there. I've checked device manager and didn't really notice anything that was relevant.

---

### Post by Roasted on 2007-11-25
Oh my gosh. Total brain fart. I can't believe I'm this stupid.

My laptop only supports ExpressCards 34/54. This is a PCMCIA. Wow I suck.

I just may go jump off a bridge now! :lolflag:......................

---

### Post by xeth_delta on 2007-11-25
> **Roasted said:**
> Dlink WNA 2330.

Is it possible that your PCMCIA slot can be disabled by default? Because I tried a Belkin F5D7010 last night, returned it this morning, as well as this Dlink WNA 2330, and neither one lit up in Linux OR Vista. In fact, I'm struggling now to get this Dlink working in Vista.

I've disabled the internal card in device manager hoping I could at least get the new Dlink one to detect without any interference. I've got a 32 bit version of Vista, and I downloaded the Vista-32 bit version of the driver from Dlink. Yet when I plug the card in, I get no response. No lights. Nothing. During the setup it asks me to plug in the card, so I do, and it just keeps popping up saying "Please plug in hardware device now." ITS IN DAMNIT! 

Can PCMCIA be disabled by default? I've checked bios, nothing there. I've checked device manager and didn't really notice anything that was relevant.

Now that is strange. Haven't heard before of a hardware disabled pc-card slot. Maybe there is a button to enable/disable on your laptop, like for wireless.

I am not sure what advice to give you about the Windows issue. As far as I remember if a device or bus is presen it would be listed in **device manager**, somewhere maybe in the last item of the list. You might also want to try asking windows to search again for new hardware, once you placed the card in the slot.

Do the LEDs on the card not light up at all, not even when powering on the computer?

Now to the Linux part. There are a number of modules that are needed by the pc-card slot. Issue an **lsmod** and see if the following modules are loaded: **pcmcia**, **pcmcia_core** and **yenta_socket**.

If they are not present you can load them with **modprobe**. They should load automatically when needed, but you can force loading at startup by adding the module names in **/etc/modules**.

---

### Post by xeth_delta on 2007-11-25
> My laptop only supports ExpressCards 34/54. This is a PCMCIA
Hehe, no problem, these things can happen. I was writing my post while you discovered the problem with the slot and wrote your post. Disregard some of my advice in my previous post :p

---

### Post by Roasted on 2007-11-25
This is just so frustrating now. Now I have to find an expresscard 34/54 that's supported by ubuntu. I've found ONE carried by all of the local stores in my area, bestbuy, circuitcity, etc... and it's not compatible. At least not according to the wiki, it's not even listed.

So I think I'm going to look at getting a USB adapter...

---

### Post by colonels1020 on 2007-11-25
I'm in the same boat as you, Roasted. I have the same Toshiba model and my wireless card is also not recognized. :(

---

### Post by Roasted on 2007-11-25
Colonels, perhaps you can do the same thing I just did.

I went to staples this evening and picked up a Wireless G USB adapter. It's a Linksys WUSB54GC. It was like 54.99 at staples.

I took it home and tested it with vista first. I ran the CD, plugged it in, bam... worked.
I rebooted to linux and went into the windows wireless driver manager. I explored the linksys cd that came with the package and I selected the 32 bit vista driver... I forget the exact file name.

I then went to configuration settings and... bam. Wireless connection was there. 

At first, I got scared, because it didn't work at first. I was hitting google and yahoo and nothing would appear. So I was like, well damnit, nothing worked! Then I felt stupid... I went to the upper right corner where my connection icon was. I clicked once and there was an empty dot next to "Household" (the name of my LAN) listed. I clicked the dot, counted to 5, hit refresh... google appeared.

This Linksys thing is kind of nice. It's just a big USB jumpdrive, more or less. And it even came with a USB extension cord if I don't want it to be sticking out of the side, which is handy to have. I'll throw that in my laptop case. I also tested the connectivity by logging into Ultima Online (an online RPG, similar to World of Warcraft) and ran around a bit in the world of Britannia... worked fine, just like my wired desktop.

Overall, it sucks that the wireless device inside didn't work... but it IS nice that there are options like this, such as PCMCIA, ExpressCard, and USB devices that can help us through.

And overall... I learned some things. I learned that ExpressCard is out now and NOT the same as PCMCIA. LOL. Anyway, I'm done rambling. It's time to get my sound card to work now! That's the last thing on the list...

I know I'm not the best expert for this kind of stuff, as I can make simple mistakes easily when I get flustered with working with these things, but I'll check back in this thread if you have anymore questions, Colonel. Take it e-z. And THANK YOU to everybody who did their best to help me. Especially you, xeth. :guitar:

---

### Post by xeth_delta on 2007-11-26
> Colonel. Take it e-z. And THANK YOU to everybody who did their best to help me. Especially you, xeth. 

You are welcome Roasted. Glad you now have wireless on your laptop. Should I understand you used Ndiswrapper also for your Linksys card? I am pondering whether this thread should be marked as solved, as the original problem was not solved. It's probably better to leave it open untill someone comes with a solution for that Realtek onboard wireless card.

Xeth

---

### Post by Roasted on 2007-11-26
Problem not solved.

The Linksys I have currently causes my system to freeze after a few minutes use. 

Trying to figure out what else I can do...

:(

---

### Post by xeth_delta on 2007-11-26
> **Roasted said:**
> Problem not solved.

The Linksys I have currently causes my system to freeze after a few minutes use. 

Trying to figure out what else I can do...

:(

What chipset does it have? Maybe you can use proper drivers instead of Ndiswrapper. What's the output for **lspci**, **lsusb** and **dmesg**?

---

### Post by buccaneere on 2007-11-26
> **xeth_delta said:**
> Now that is strange. Haven't heard before of a hardware disabled pc-card slot. Maybe there is a button to enable/disable on your laptop, like for wireless.

I am not sure what advice to give you about the Windows issue. [COLOR="Red"]**As far as I remember if a device or bus is presen it would be listed in [B]device manager**, somewhere maybe in the last item of the list. [/B][/COLOR]You might also want to try asking windows to search again for new hardware, once you placed the card in the slot.

Do the LEDs on the card not light up at all, not even when powering on the computer?

Now to the Linux part. There are a number of modules that are needed by the pc-card slot. Issue an **lsmod** and see if the following modules are loaded: **pcmcia**, **pcmcia_core** and **yenta_socket**.

If they are not present you can load them with **modprobe**. They should load automatically when needed, but you can force loading at startup by adding the module names in **/etc/modules**.

Deleted; read further post...

---

### Post by bradmayne on 2007-11-28
ive got a toshiba also and am having major problems with my atheros and madiwifi.  i have to go to a terminal window after booting up every time.  i can't figure out what to type in the /etc/network.

---

### Post by xeth_delta on 2007-11-28
> **bradmayne said:**
> ive got a toshiba also and am having major problems with my atheros and madiwifi.  i have to go to a terminal window after booting up every time.  i can't figure out what to type in the /etc/network.

Hi bradmayne, What exactly is the problem with your card? Does it work after using /etc/network?
I'd be glad to help you out, but I think it would be better if you start a new thread about your problem, as it is not exactly related to the one Roasted has.

I also have an Atheros card so, start the new thread and I will try to help you there.

---

### Post by Fran89 on 2007-11-29
i have a Toshiba Satellite L45-S7423 and i have the cant read the realtek issue, but im not that willing to give up... if anyone has any ideas please tell me... meanwhile ill try to keep loking for a fix...

---

### Post by xeth_delta on 2007-11-29
> **Fran89 said:**
> i have a Toshiba Satellite L45-S7423 and i have the cant read the realtek issue, but im not that willing to give up... if anyone has any ideas please tell me... meanwhile ill try to keep loking for a fix...

The first thing I could suggest is to find out what card is exactly installed on your computer with lspci or lsusb.

Then have a look at [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported#head-603c9481d6c6288b6b674cc50132d21f6d539c53]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported#head-603c9481d6c6288b6b674cc50132d21f6d539c53") to find out what might be the support status.

If it is supported without ndiswrapper you could try removing from the black list one of the two drivers for the card.

---

### Post by Fran89 on 2007-11-30
well it a realtek 8187b type  one and with ndiswrapper ive gotten as far as detecting it  and detecting wirelles signals, but when i try to connect it just wont... :( in going to keep tring

---

### Post by Fran89 on 2007-11-30
ok I made it work, but i still have a few things to sort out

---

### Post by Roasted on 2007-11-30
Wait... you got the Realtek 8187B integrated wireless card to work with ndiswrapper in Ubuntu 7.10?! ARE YOU KIDDING ME?! HOW?

---

### Post by Fran89 on 2007-12-01
ohh sorry if that las post was confusing.. i mde it work but through a patch... im still having trouble (will not boot at start up, but i will fix soon, afetr that its easy..:) im just lazy >_> still i belive it is possible to make it wor through ndiswrapper it just needs tweaking here and there but im not up for it

---

### Post by Roasted on 2007-12-02
For the life of me, I cannot get it to work. I've tried it on SEVERAL fresh installs. Tell me your secret!! :(

---

### Post by edward_the_iv on 2007-12-02
> For the life of me, I cannot get it to work. I've tried it on SEVERAL fresh installs. Tell me your secret!! 
Try the native driver detailed [here]("http://www.datanorth.net/~cuervo/blog/linux-on-the-satellite-a215-s7407/"). 
If you have problems with it, please paste the problems you are getting.

Off the top of my head, have you installed the linux headers?  build-essentials?
```
sudo apt-get install build-essential linux-headers-`uname -r`
```
Those two are needed for compiling..

---

### Post by Roasted on 2007-12-02
I installed the headers and build essentials with the command you gave me. Then I downloaded the driver and followed the directions closely.

This is the entire output of the terminal from start to finish. I believe the only errors are at the very end but I pasted everything so you folks can see it from the beginning...




jason@jason:~$ cd Desktop
jason@jason:~/Desktop$ ls
rtl8187b-modified  rtl8187b-modified-dist.tar.gz
jason@jason:~/Desktop$ cd rtl8187b-modified
jason@jason:~/Desktop/rtl8187b-modified$ ./makedrv
rm -fr *.mod.c *.mod *.o .*.cmd *.mod.* *.ko *.o *~
make -C /lib/modules/2.6.22-14-generic/build M=/home/jason/Desktop/rtl8187b-modified/ieee80211 CC=gcc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /home/jason/Desktop/rtl8187b-modified/ieee80211/ieee80211_softmac.o
/home/jason/Desktop/rtl8187b-modified/ieee80211/ieee80211_softmac.c: In function ‘ieee80211_softmac_scan_wq’:
/home/jason/Desktop/rtl8187b-modified/ieee80211/ieee80211_softmac.c:433: warning: initialization from incompatible pointer type
/home/jason/Desktop/rtl8187b-modified/ieee80211/ieee80211_softmac.c:432: warning: unused variable ‘dwork’
/home/jason/Desktop/rtl8187b-modified/ieee80211/ieee80211_softmac.c: In function ‘ieee80211_probe_resp’:
/home/jason/Desktop/rtl8187b-modified/ieee80211/ieee80211_softmac.c:710: warning: ISO C90 forbids mixed declarations and code
/home/jason/Desktop/rtl8187b-modified/ieee80211/ieee80211_softmac.c:1554:4: warning: #warning CHECK_LOCK_HERE
/home/jason/Desktop/rtl8187b-modified/ieee80211/ieee80211_softmac.c:1594:2: warning: #warning CHECK_LOCK_HERE
/home/jason/Desktop/rtl8187b-modified/ieee80211/ieee80211_softmac.c: In function ‘ieee80211_associate_retry_wq’:
/home/jason/Desktop/rtl8187b-modified/ieee80211/ieee80211_softmac.c:2253: warning: initialization from incompatible pointer type
/home/jason/Desktop/rtl8187b-modified/ieee80211/ieee80211_softmac.c:2252: warning: unused variable ‘dwork’
/home/jason/Desktop/rtl8187b-modified/ieee80211/ieee80211_softmac.c: In function ‘ieee80211_softmac_init’:
/home/jason/Desktop/rtl8187b-modified/ieee80211/ieee80211_softmac.c:2475: warning: assignment from incompatible pointer type
/home/jason/Desktop/rtl8187b-modified/ieee80211/ieee80211_softmac.c:2476: warning: assignment from incompatible pointer type
/home/jason/Desktop/rtl8187b-modified/ieee80211/ieee80211_softmac.c:2477: warning: assignment from incompatible pointer type
/home/jason/Desktop/rtl8187b-modified/ieee80211/ieee80211_softmac.c:2478: warning: assignment from incompatible pointer type
/home/jason/Desktop/rtl8187b-modified/ieee80211/ieee80211_softmac.c:2479: warning: assignment from incompatible pointer type
/home/jason/Desktop/rtl8187b-modified/ieee80211/ieee80211_softmac.c:2480: warning: assignment from incompatible pointer type
/home/jason/Desktop/rtl8187b-modified/ieee80211/ieee80211_softmac.c: In function ‘ieee80211_rx_frame_softmac’:
/home/jason/Desktop/rtl8187b-modified/ieee80211/ieee80211_softmac.c:1666: warning: ‘chlen’ may be used uninitialized in this function
/home/jason/Desktop/rtl8187b-modified/ieee80211/ieee80211_softmac.c:1554:4: warning: #warning CHECK_LOCK_HERE
/home/jason/Desktop/rtl8187b-modified/ieee80211/ieee80211_softmac.c:1594:2: warning: #warning CHECK_LOCK_HERE
  CC [M]  /home/jason/Desktop/rtl8187b-modified/ieee80211/ieee80211_rx.o
  CC [M]  /home/jason/Desktop/rtl8187b-modified/ieee80211/ieee80211_tx.o
  CC [M]  /home/jason/Desktop/rtl8187b-modified/ieee80211/ieee80211_wx.o
  CC [M]  /home/jason/Desktop/rtl8187b-modified/ieee80211/ieee80211_module.o
  CC [M]  /home/jason/Desktop/rtl8187b-modified/ieee80211/ieee80211_softmac_wx.o
  CC [M]  /home/jason/Desktop/rtl8187b-modified/ieee80211/ieee80211_crypt.o
  CC [M]  /home/jason/Desktop/rtl8187b-modified/ieee80211/ieee80211_crypt_ccmp.o
/home/jason/Desktop/rtl8187b-modified/ieee80211/ieee80211_crypt_ccmp.c: In function ‘ieee80211_ccmp_aes_encrypt’:
/home/jason/Desktop/rtl8187b-modified/ieee80211/ieee80211_crypt_ccmp.c:87: warning: passing argument 1 of ‘crypto_cipher_encrypt_one’ from incompatible pointer type
/home/jason/Desktop/rtl8187b-modified/ieee80211/ieee80211_crypt_ccmp.c: In function ‘ieee80211_ccmp_init’:
/home/jason/Desktop/rtl8187b-modified/ieee80211/ieee80211_crypt_ccmp.c:109: warning: assignment from incompatible pointer type
/home/jason/Desktop/rtl8187b-modified/ieee80211/ieee80211_crypt_ccmp.c:125: warning: passing argument 1 of ‘crypto_free_cipher’ from incompatible pointer type
/home/jason/Desktop/rtl8187b-modified/ieee80211/ieee80211_crypt_ccmp.c: In function ‘ieee80211_ccmp_deinit’:
/home/jason/Desktop/rtl8187b-modified/ieee80211/ieee80211_crypt_ccmp.c:141: warning: passing argument 1 of ‘crypto_free_cipher’ from incompatible pointer type
/home/jason/Desktop/rtl8187b-modified/ieee80211/ieee80211_crypt_ccmp.c: In function ‘ieee80211_ccmp_set_key’:
/home/jason/Desktop/rtl8187b-modified/ieee80211/ieee80211_crypt_ccmp.c:423: warning: passing argument 1 of ‘crypto_cipher_setkey’ from incompatible pointer type
  CC [M]  /home/jason/Desktop/rtl8187b-modified/ieee80211/ieee80211_crypt_tkip.o
  CC [M]  /home/jason/Desktop/rtl8187b-modified/ieee80211/ieee80211_crypt_wep.o
  LD [M]  /home/jason/Desktop/rtl8187b-modified/ieee80211/ieee80211-rtl.o
  LD [M]  /home/jason/Desktop/rtl8187b-modified/ieee80211/ieee80211_crypt-rtl.o
  LD [M]  /home/jason/Desktop/rtl8187b-modified/ieee80211/ieee80211_crypt_wep-rtl.o
  LD [M]  /home/jason/Desktop/rtl8187b-modified/ieee80211/ieee80211_crypt_tkip-rtl.o
  LD [M]  /home/jason/Desktop/rtl8187b-modified/ieee80211/ieee80211_crypt_ccmp-rtl.o
  Building modules, stage 2.
  MODPOST 5 modules
  CC      /home/jason/Desktop/rtl8187b-modified/ieee80211/ieee80211-rtl.mod.o
  LD [M]  /home/jason/Desktop/rtl8187b-modified/ieee80211/ieee80211-rtl.ko
  CC      /home/jason/Desktop/rtl8187b-modified/ieee80211/ieee80211_crypt-rtl.mod.o
  LD [M]  /home/jason/Desktop/rtl8187b-modified/ieee80211/ieee80211_crypt-rtl.ko
  CC      /home/jason/Desktop/rtl8187b-modified/ieee80211/ieee80211_crypt_ccmp-rtl.mod.o
  LD [M]  /home/jason/Desktop/rtl8187b-modified/ieee80211/ieee80211_crypt_ccmp-rtl.ko
  CC      /home/jason/Desktop/rtl8187b-modified/ieee80211/ieee80211_crypt_tkip-rtl.mod.o
  LD [M]  /home/jason/Desktop/rtl8187b-modified/ieee80211/ieee80211_crypt_tkip-rtl.ko
  CC      /home/jason/Desktop/rtl8187b-modified/ieee80211/ieee80211_crypt_wep-rtl.mod.o
  LD [M]  /home/jason/Desktop/rtl8187b-modified/ieee80211/ieee80211_crypt_wep-rtl.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
rm -fr *.mod.c *.mod *.o .*.cmd *.ko *~
make -C /lib/modules/2.6.22-14-generic/build M=/home/jason/Desktop/rtl8187b-modified/rtl8187 CC=gcc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /home/jason/Desktop/rtl8187b-modified/rtl8187/r8187_core.o
/home/jason/Desktop/rtl8187b-modified/rtl8187/r8187_core.c: In function ‘rtl8187_rx_urbsubmit’:
/home/jason/Desktop/rtl8187b-modified/rtl8187/r8187_core.c:934: warning: passing argument 6 of ‘usb_fill_bulk_urb’ from incompatible pointer type
/home/jason/Desktop/rtl8187b-modified/rtl8187/r8187_core.c: In function ‘rtl8187_rx_manage_urbsubmit’:
/home/jason/Desktop/rtl8187b-modified/rtl8187/r8187_core.c:954: warning: passing argument 6 of ‘usb_fill_bulk_urb’ from incompatible pointer type
/home/jason/Desktop/rtl8187b-modified/rtl8187/r8187_core.c: In function ‘rtl8180_rtx_disable’:
/home/jason/Desktop/rtl8187b-modified/rtl8187/r8187_core.c:1255: warning: format ‘%d’ expects type ‘int’, but argument 2 has type ‘long unsigned int’
/home/jason/Desktop/rtl8187b-modified/rtl8187/r8187_core.c: In function ‘rtl8180_tx’:
/home/jason/Desktop/rtl8187b-modified/rtl8187/r8187_core.c:2220: warning: passing argument 6 of ‘usb_fill_bulk_urb’ from incompatible pointer type
/home/jason/Desktop/rtl8187b-modified/rtl8187/r8187_core.c:2227: warning: passing argument 6 of ‘usb_fill_bulk_urb’ from incompatible pointer type
/home/jason/Desktop/rtl8187b-modified/rtl8187/r8187_core.c: In function ‘rtl8187_usb_initendpoints’:
/home/jason/Desktop/rtl8187b-modified/rtl8187/r8187_core.c:2277: warning: ISO C90 forbids mixed declarations and code
/home/jason/Desktop/rtl8187b-modified/rtl8187/r8187_core.c:2281: warning: ISO C90 forbids mixed declarations and code
/home/jason/Desktop/rtl8187b-modified/rtl8187/r8187_core.c:2310: warning: assignment from incompatible pointer type
/home/jason/Desktop/rtl8187b-modified/rtl8187/r8187_core.c:2256: warning: unused variable ‘i’
/home/jason/Desktop/rtl8187b-modified/rtl8187/r8187_core.c: In function ‘rtl8187_usb_deleteendpoints’:
/home/jason/Desktop/rtl8187b-modified/rtl8187/r8187_core.c:2328: warning: format ‘%d’ expects type ‘int’, but argument 2 has type ‘long unsigned int’
/home/jason/Desktop/rtl8187b-modified/rtl8187/r8187_core.c: At top level:
/home/jason/Desktop/rtl8187b-modified/rtl8187/r8187_core.c:2435: warning: ‘struct struct_work’ declared inside parameter list
/home/jason/Desktop/rtl8187b-modified/rtl8187/r8187_core.c:2435: warning: its scope is only this definition or declaration, which is probably not what you want
/home/jason/Desktop/rtl8187b-modified/rtl8187/r8187_core.c: In function ‘rtl8180_wmm_param_update’:
/home/jason/Desktop/rtl8187b-modified/rtl8187/r8187_core.c:2437: warning: initialization from incompatible pointer type
/home/jason/Desktop/rtl8187b-modified/rtl8187/r8187_core.c:2439: warning: initialization from incompatible pointer type
/home/jason/Desktop/rtl8187b-modified/rtl8187/r8187_core.c: In function ‘rtl8180_init’:
/home/jason/Desktop/rtl8187b-modified/rtl8187/r8187_core.c:2654: warning: assignment from incompatible pointer type
/home/jason/Desktop/rtl8187b-modified/rtl8187/r8187_core.c:2702: warning: assignment from incompatible pointer type
/home/jason/Desktop/rtl8187b-modified/rtl8187/r8187_core.c: In function ‘rtl8180_adapter_start’:
/home/jason/Desktop/rtl8187b-modified/rtl8187/r8187_core.c:3054: warning: unused variable ‘bInvalidWirelessMode’
/home/jason/Desktop/rtl8187b-modified/rtl8187/r8187_core.c:3053: warning: unused variable ‘SupportedWirelessMode’
/home/jason/Desktop/rtl8187b-modified/rtl8187/r8187_core.c:3052: warning: unused variable ‘InitWirelessMode’
/home/jason/Desktop/rtl8187b-modified/rtl8187/r8187_core.c:3051: warning: unused variable ‘ieee’
/home/jason/Desktop/rtl8187b-modified/rtl8187/r8187_core.c: In function ‘rtl8180_irq_rx_tasklet’:
/home/jason/Desktop/rtl8187b-modified/rtl8187/r8187_core.c:3769: warning: ISO C90 forbids mixed declarations and code
  CC [M]  /home/jason/Desktop/rtl8187b-modified/rtl8187/r8180_93cx6.o
  CC [M]  /home/jason/Desktop/rtl8187b-modified/rtl8187/r8180_wx.o
  CC [M]  /home/jason/Desktop/rtl8187b-modified/rtl8187/r8180_rtl8225.o
  CC [M]  /home/jason/Desktop/rtl8187b-modified/rtl8187/r8180_rtl8225z2.o
  LD [M]  /home/jason/Desktop/rtl8187b-modified/rtl8187/r8187.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: "ieee80211_wx_get_freq" [/home/jason/Desktop/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_softmac_start_protocol" [/home/jason/Desktop/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "free_ieee80211_rtl" [/home/jason/Desktop/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wlan_frequencies" [/home/jason/Desktop/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wake_queue_rtl" [/home/jason/Desktop/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_rx_rtl" [/home/jason/Desktop/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_is_shortslot" [/home/jason/Desktop/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wx_get_name_rtl" [/home/jason/Desktop/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wx_get_wap" [/home/jason/Desktop/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wx_set_scan" [/home/jason/Desktop/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wx_get_rate" [/home/jason/Desktop/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_is_54g" [/home/jason/Desktop/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_stop_queue_rtl" [/home/jason/Desktop/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_softmac_stop_protocol" [/home/jason/Desktop/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wx_set_rawtx" [/home/jason/Desktop/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wx_get_scan_rtl" [/home/jason/Desktop/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wpa_supplicant_ioctl" [/home/jason/Desktop/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_get_beacon" [/home/jason/Desktop/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wx_get_essid" [/home/jason/Desktop/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wx_set_mode" [/home/jason/Desktop/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wx_get_mode" [/home/jason/Desktop/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wx_set_encode_rtl" [/home/jason/Desktop/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wx_set_freq" [/home/jason/Desktop/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wx_set_rate" [/home/jason/Desktop/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wx_set_wap" [/home/jason/Desktop/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wx_get_encode_rtl" [/home/jason/Desktop/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wx_set_essid" [/home/jason/Desktop/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "alloc_ieee80211_rtl" [/home/jason/Desktop/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_reset_queue" [/home/jason/Desktop/rtl8187b-modified/rtl8187/r8187.ko] undefined!
  CC      /home/jason/Desktop/rtl8187b-modified/rtl8187/r8187.mod.o
  LD [M]  /home/jason/Desktop/rtl8187b-modified/rtl8187/r8187.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
jason@jason:~/Desktop/rtl8187b-modified$ ./wlan0up
insmod: error inserting 'ieee80211_crypt-rtl.ko': -1 Operation not permitted
insmod: error inserting 'ieee80211_crypt_wep-rtl.ko': -1 Operation not permitted
insmod: error inserting 'ieee80211_crypt_tkip-rtl.ko': -1 Operation not permitted
insmod: error inserting 'ieee80211_crypt_ccmp-rtl.ko': -1 Operation not permitted
insmod: error inserting 'ieee80211-rtl.ko': -1 Operation not permitted
insmod: error inserting 'r8187.ko': -1 Operation not permitted
jason@jason:~/Desktop/rtl8187b-modified$

---

### Post by edward_the_iv on 2007-12-02
You must be either root, or use sudo - it looks like only for the wlan0up command, but I didn't read through all of that,  completely.

```
sudo ./makedrv
sudo ./wlan0up
```
I believe there is also an installation script, which would also need to be used as root.

Also, if you could help me out, a bit.  I have the same laptop as you, and I am having some strange behaviour.  If you could,
```
sudo grep 'APIC error' /var/log/messages
```
and tell me if it gives any output.
I am getting a APIC error, and I want to see if you are as well.

---

### Post by xeth_delta on 2007-12-02
Roasted, you can insert modules into the kernel only as root.

In your case I suppose it youd be:
```
sudo ./wlan0up
```

In general, when you want to load a module:

```
sudo modprobe module_name
```

I think you also need to install those modules that you just compiled. From what I can see, there were no errors, sonly some warnings. That has to be done also as root, since they will be placed under /lib/...

---

### Post by Fran89 on 2007-12-03
well roasted kinda told you all i did, but i did:

sudo ./makedrv
sudo ./install
sudo ./wlan0up

the only thing ive been meaning to fix is that every time i want internet i have to go and do ./wlan0up, i have to go and make it executalbe and put it in the boot load modules file...
if your having to many "i have to be root problems" right click on the menu bar and hit edit menus, once there go to system tools and enable root terminal, you only need to put the password once:) and another thing the light will not turn on, on the wireless indicator but this dont mean you dont have wireless, and you wont see the signal strength graphical bar  but the signal is there, but the wireless works thats all you need..

---

### Post by Roasted on 2007-12-04
Well, thank you everybody who helped me... but this is Roasted posting from his laptop wirelessly on Fedora Core 8 with a 3Com CRUSB10075 Wireless G USB Adapter. Good distro, I think I'll tinker with it a bit more and keep it as my main linux flavor on the laptop. But I'll always have a place for Ubuntu on my beefy desktop.

I am currently trying to get an older Pentium III Sony Vaio online via wireless by a PCMCIA card I have laying around that is running Gutsy. So you folks may see me around here some more with Sony questions! But the Toshiba questions are hereby over with. :)

---

### Post by xeth_delta on 2007-12-04
That's Great! So, slightly offtopic, does the sound work under Fedora?

---

### Post by Roasted on 2007-12-10
> **xeth_delta said:**
> That's Great! So, slightly offtopic, does the sound work under Fedora?

Nope. Go figure. :( 

In Fedora, I don't get the error that I get in Ubuntu. Ubuntu prompts me with an error about having missing plugins or having a sound card that isn't configured. Fedora doesn't prompt me with any errors. It just flat out doesn't work. I can adjust the volume (Ubuntu I couldn't) it just didn't have any output.

Out of curiosity, I installed Ubuntu earlier, formatting my Fedora Core 8 partition on the laptop. Ubuntu gave me so much trouble. It wouldn't restart, it wouldn't connect, it kept shutting things off randomly... it got me so pissed I just threw Fedora back on. Now I'm getting curious to try it again and see if I get the same errors. If I do, back to Fedora for good and I'll probably change my desktop to Fedora at that point too. If not, I'll keep with the Ubuntu flavor.

I'm also curious to try out the OSSv4 that was recommended to me to see if it'll work. *shrug*

---

### Post by fortinbras on 2007-12-10
I got my A215-7422 working following the directions in the now infamous:

[http://www.datanorth.net/~cuervo/blog/2007/09/26/no-more-vista/](http://www.datanorth.net/~cuervo/blog/2007/09/26/no-more-vista/)

I tried for three days during my time off to get it to work.  Then I spent another two days search for alternatives as the above did not work.  Finally, I did a clean install and tried the above.  Mind you, I followed the directions found in the README included in the download.  While the process is a bit long, it worked flawlessly and on the first try on the clean install.

Hope this helps someone.  Sorry that I got to this thread so late.

Also got the sound working but I cannot find the page with the directions on that.

fortinbras

P.S.  I'm a complete noob at Linux and I am currently teaching myself the OS.  I also would like to learn script writing so that I can automate some functions.  If you can point me to some good tutorials please PM me.  Thanks.

---

### Post by Roasted on 2007-12-15
I don't know, I mean I'm looking at this and wondering what exactly am I supposed to do. I mean, it says I need to edit my rtl8187/r8187_core.c... what is it? Where is it? How do I open it to edit it? Can you help me?

---

### Post by xeth_delta on 2007-12-15
> **Roasted said:**
> I don't know, I mean I'm looking at this and wondering what exactly am I supposed to do. I mean, it says I need to edit my rtl8187/r8187_core.c... what is it? Where is it? How do I open it to edit it? Can you help me?

Roasted, from what I see there, you should unpack the source code package and look for a file called r8187_core.c under the directory rtl8187.

Edit it bu making the changes described and then recompile.

---

### Post by Fran89 on 2007-12-17
Hmm
better tell you what worked for me just in case...

First Download the rtl8187b-modified-dist.tar.gz, Second extract it, just in case make sure its in a path without spaces, then open a terminal(Root Terminal is best) and CD into that folder... after you get in that folder type: ```
./makedrv its going to output alot of warnigs this is normal
then ./install (i did this just in case (supposedly you dont have to do this)
and finally ./wlan0up to inyect the driver into the kernel(or so i think)
``` this is all i did the only problem is that you have to CD into the folder and run ./wlan0up on every boot up... if anyone finds a way around this then please im eager to stop doing this...

---

### Post by dlowerre on 2007-12-25
I was having the same problem.  I downloaded the modfied realtek driver, compiled,and then activated.  This worked!  I recommend it.

I still have to make it active at boot.  I tried editing /etc/network/interfaces but I got that wrong.

---

### Post by bemused0 on 2007-12-26
Roasted:  First off, thanks for this thread man, and thanks to all who've replied -- I have the same laptop, same problems.

I've followed everyones posts here as well as a few other Toshiba/wireless related threads and am happy to have everything on this laptop working at last (except for the headphones/sound thing -- bah) -

That said, I did actually find a way to get wlan0up automatically (someone posted a solution on the same site as the modified driver)
 
Edit /etc/network/interfaces and add:
```

pre-up wlan0up   
```


Assuming that wlan0up is in your path, otherwise provide the full path on that line.
Here's what my /etc/network/interfaces    looks like, if anyone wants to scope it:
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

pre-up wlan0up

auto wlan0
iface wlan0 inet dhcp
```



Also, it might be worth mentioning that I've given up on nm-applet.  Why? I never could get connected to an encrypted network using it with the modified drivers.  I'm sure I was doing something wrong, however I'm back onto WICD and having no problems getting on the WEP 64bit encryption at my Parent's house. I'll try later on my own, slightly different setup when I'm back home.

Thanks again -- to everyone.

---

### Post by Fran89 on 2007-12-26
THANK YOU!

now i don't have to run wlan0up at startup anymore THANKS!

---

### Post by Roasted on 2007-12-26
This is interesting to hear about.

Now if only the sound issue may be fixed, I might consider putting Ubuntu back on my laptop as my main partition. For the time being, however, I have to admit I'm enjoying Vista and actually looking forward to SP1... But, alas, Ubuntu is home territory to me. :) (as I post this from my desktop which is running gutsy. muahahaha)

---

### Post by t5noel on 2007-12-26
Oh it's there. I have the same challenge. If you run lsusb the Realtek device listed is the wireless device. It's a built-in USB device. I have no idea how to get the so called drivers to work. I've tried the linux drivers and ndiswrapper with no luck so far. Toshiba has some drivers on their site and so does Realtek. Good Luck.

---

### Post by buccaneere on 2007-12-26
> **t5noel said:**
>  I have no idea how to get the so called drivers to work. .

see post #40, for manual install options to install to network card that has a usb address...

---

### Post by t5noel on 2007-12-26
I have the same laptop. The wireless is a built-in usb device. Run lsusb. The Realtek one is your wireless device. I found this site useful: [http://www.datanorth.net/~cuervo/rtl8187b/](http://www.datanorth.net/~cuervo/rtl8187b/). I can see it listed with ifconfig and iwconfig. I haven't gotten it connected yet.

---

### Post by Roasted on 2007-12-26
I'm half tempted to go out and buy a copy of XP. This Vista, despite it having some nice features, is really bogged down. This computer should fkin fly and it like... doesn't.

---

### Post by bemused0 on 2007-12-27
I'll fully encourage that -- First thing I did was wipe Vista off of this thing, didnt take too long to track down all of the XP drivers needed (Although 3 Bus devices still show as 'unknown' in winXP).  Also, I havent really tried using the media keys at the top -- everything seems to work as it should in XP) -- So now its just Ubuntu/XP (not really using XP now)

---

### Post by t5noel on 2007-12-27
Try upgrading your memory to 2GB. I have the same model laptop and upgraded the memory. It seems to work better. 2GB is cheaper than buying XP.

---

### Post by Roasted on 2007-12-27
I did upgrade. 

See this is weird. Maybe I just was rushing it or something, I don't know, cause now every time I boot it's booting in 55ish seconds. 

See I was timing the boot process from the time I put my password in until I saw the widgets appear. I guess the widgets are just slow or something, because I noticed that the system would appear to be fully booted and ready to roll yet the widgets would take another minute to show. I have since turned them off, and now the system looks ready in a minute's time.

I guess I'm keeping Vista. I gotta admit, there are some things I like about it. But maybe I'm not giving it a fair chance... after all, SP1 isn't even out yet, and I remember XP being hell until it's service packs got out there. 

Currently I put on openSuSE 10.3 to try and see if I would have any better luck with the wireless + sound issue. This is depressing. I wonder if gOS would offer anything else? I just can't find a distro that seems to work. :(

---

### Post by buccaneere on 2007-12-27
> **Roasted said:**
> I'm half tempted to go out and buy a copy of XP. This Vista, despite it having some nice features, is really bogged down. This computer should fkin fly and it like... doesn't.

MS is allowin' users to trade-in their COA for vista, for a copy of XP, for just $20.

Ask me, MS should pay the user $20 for the trade.

Un-tellectual property rights.:roll:

---

### Post by Roasted on 2007-12-27
Hm. I don't know. Using Vista more has gotten a bit attached to me. I mean, I'm a technology guy, so I want to be using the latest out there for the sake of being knowledgable on it. On top of that, Vista isn't that bad the more I use it. In fact I kind of like it... plus with SP1 being in the near future, why downgrade? I'm not really having any issues with it, I just wish it would be a little slimmer when it comes to booting up and whatnot. Which, 1 minute boot time that I'm experiencing now isn't that bad at all, really.

---

### Post by Roasted on 2007-12-28
Roasted checking in again... Trying to get these issues ironed out simply because it enrages me to know I wasn't able to fix it.

Thinking slow this time. I just wiped openSuSE 10.3 off my machine. I tried it out just to see if I'd have any luck with sound over there. Nope! 

Anyway, back to wireless for the time being.

I downloaded and unpacked the tarball for the modified driver on that datanorth web site that everybody here has been talking about. I CD'd into the directory and ran ./makedrv. I then ran ./wlan0up. Now, if I go to my connection icon in the upper right by the clock, I see my wireless network listed there. However, it detects 0 signal. By clicking on it and attempting to connect (it has no encryption by the way), it just cycles for a minute and then comes back as being unable to connect.

What can I do now?

edit - I also just rebooted. Wireless isn't listed now, I assume because I have to do wlan0up. Yet in the terminal, I've tried ./wlanup, wlan0up, sudo wlan0up, and sudo ./wlan0up. Nothing worked.

---

### Post by bemused0 on 2007-12-28
@Roasted:

For the modified driver, 
The install script just seems to place the kernel module, but doesn't copy over any of the executables. I copied wlan0up, wlan0dhcp, wlan0down, wlan0rmv etc. into /usr/bin   so that when   the pre-up wlan0up line is added to /etc/network/interfaces the exec(s) can be found; solving the 'auto' part.

Also, after you've run (manually or automatically) wlan0up, try:
```
sudo iwlist wlan0 scan
```

Check this thread (maybe you have already) to see some options for testing:
[http://ubuntuforums.org/showthread.php?t=571188&highlight=atheros+wireless](http://ubuntuforums.org/showthread.php?t=571188&highlight=atheros+wireless)

---

### Post by buccaneere on 2007-12-28
> **Roasted said:**
> Hm. I don't know. Using Vista more has gotten a bit attached to me. I mean, I'm a technology guy, so I want to be using the latest out there for the sake of being knowledgable on it. On top of that, Vista isn't that bad the more I use it. In fact I kind of like it... plus with SP1 being in the near future, why downgrade? I'm not really having any issues with it, I just wish it would be a little slimmer when it comes to booting up and whatnot. Which, 1 minute boot time that I'm experiencing now isn't that bad at all, really.

Have you tried to network a vistabox at your house?

---

### Post by buccaneere on 2007-12-28
> **bemused0 said:**
> @Roasted:


Also, after you've run (manually or automatically) wlan0up, try:
```
sudo iwlist wlan0 scan
```


That's where I say go also... I bet the wireless interface returns no scan.

I suggest not limiting the scan parameter to interface wlan0 tho'...

---

### Post by nsegative on 2007-12-29
> **bemused0 said:**
> @Roasted:

For the modified driver, 
The install script just seems to place the kernel module, but doesn't copy over any of the executables. I copied wlan0up, wlan0dhcp, wlan0down, wlan0rmv etc. into /usr/bin   so that when   the pre-up wlan0up line is added to /etc/network/interfaces the exec(s) can be found; solving the 'auto' part.

(Maybe the proper path is /usr/local/bin since these execs require root/sudo to run? I'm not entirely sure)

Also, after you've run (manually or automatically) wlan0up, try:
```
sudo iwlist wlan0 scan
```

Check this thread (maybe you have already) to see some options for testing:
[http://ubuntuforums.org/showthread.php?t=571188&highlight=atheros+wireless](http://ubuntuforums.org/showthread.php?t=571188&highlight=atheros+wireless)
Can anyone help out with this part? I've managed to get wireless working, but after every reboot it does not recognize that wireless is on. I have to go into the R2 folder (where I compiled driver) and type sudo ./wlan0up every time. I tried to modify the file given and also etc/rc.local but no luck,

---

### Post by bemused0 on 2007-12-30
nsegative:

The way to avoid having to run sudo wlan0up manually is to add a line to,
/etc/network/interfaces
```
pre-up wlan0up
```
Also, move wlan0up and the other executables from that compile folder into /usr/bin or create links. (The addition to rc.local might work just as well for all I know, but wlan0up won't be found if it's not in your path, or not explicitly provided)

---

### Post by TheAncientMariner on 2007-12-30
I've been trying to get this to work on my A215-S7437 for days. I finally gave up after none of the instructions here worked (and when it wouldn't work under OpenSUSE, Fedora, Slackware, Puppy, SAM Linux, and who knows what else I tried and am forgetting), and installed XP on it. When I tried to use the Windows XP driver from Realtek's site (posted earlier in this thread), it didn't work. I finally found a driver specifically for the Toshiba A215 models, which installed and worked without a hitch.

That's gotten me curious, and I'm going to try ndiswrapper in Ubuntu again using this driver. In the meantime, I've uploaded a ZIP archive of the drivers I used under XP to MegaUpload in case anyone else wants to have a go. They can be found [here]("http://www.megaupload.com/?d=5RU84QB7").

---

### Post by ADloser on 2008-01-01
can you let me know how this goes. I have the same problem

---

### Post by D_invictus on 2008-01-03
dave@dave-laptop:~$ lspci | grep -i net
0e:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
14:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)
dave@dave-laptop:~$ 

Someone help me?

=/

---

### Post by TheAncientMariner on 2008-01-03
> **ADloser said:**
> can you let me know how this goes. I have the same problem

 No dice with those drivers. I'm doing what I said I wouldn't do and resorted to a USB adapter.

---

### Post by Roasted on 2008-01-05
Man... I can't wait for the day when I can install Linux on anything and 99% of the time it'll work flawlessly.

So far, every desktop I've installed Ubuntu on it's worked great. No issues. The only time I ran into issues was with this laptop.

I guess Linux has pretty well established support for desktops, eh? Just need to get those laptops on the list...

---

### Post by TheAncientMariner on 2008-01-05
I hear you.

Although, to be fair, this appears to be a fairly ridiculous wi-fi implementation.

---

### Post by Roasted on 2008-01-05
But to throw out a curve ball back at linux, even vista doesn't have an issue supporting this thing. It's hardly an excuse...

---

### Post by TheAncientMariner on 2008-01-05
I did try to load XP onto this machine, and had even more issues there than I did with Ubuntu. The wireless worked, but I spent an hour trying to find some other drivers before I threw my hands up and reinstalled Ubuntu.

I might eventually go back to Vista, but it's gonna take a lot more than a cantankerous wireless card to get me to switch back.

---

### Post by Roasted on 2008-01-06
I installed XP on this machine. I had no issues... :confused:

The only driver I didn't get working (but then again I barely even tried) was the ethernet controller. I hardly need that on a laptop... So I just kinda... yeah... don't care, lol.

---

### Post by TheAncientMariner on 2008-01-06
Well, I have a different model (though it's still in the A215 series) and none of the components have XP drivers on Toshiba's site (or Realtek's, for that matter). The driver I had the most trouble with was the video driver. Neither ATI's drivers nor Omega drivers wanted to install. I would rather deal with a lack of wireless than a lack of a usable resolution.

---

### Post by Roasted on 2008-01-09
Just FYI. I found this link... no idea if it works. Somebody want to be the test subject and try it? I would but I'm trying out Debian for the next couple days...

[http://collin.moerman.googlepages.com/toshiba_ubuntu_7.10](http://collin.moerman.googlepages.com/toshiba_ubuntu_7.10)

---

### Post by TheAncientMariner on 2008-01-09
Was there supposed to be a link in that post, or am I missing something (the usual culprit in my confusion)?

Nevermind, just saw the edit. =)

---

### Post by keylime on 2008-01-14
Quick question - when I try chmod command to get the files into the /usr/bin it will not let me do so, since it's root. Anyway around this?

---

### Post by xeth_delta on 2008-01-14
> **keylime said:**
> Quick question - when I try chmod command to get the files into the /usr/bin it will not let me do so, since it's root. Anyway around this?

What exactly are you trying to do? "chmod" is used to change the permissions of a file or directory. To move them you have to use "mv" or cp to copy them.

---

### Post by keylime on 2008-01-15
OK I got it in there - lack of Coca-Cola with the cp command, duh....

---

### Post by Roasted on 2008-04-22
Does anybody happen to know if the newest version of Ubuntu will be able to support this wireless card (the one on the Toshiba Satellite A215S7422) by default, out of the box? I'm curious to know...

---

### Post by Mincher on 2008-04-22
O.K.

I have a Toshiba Satellite L40-18Z. I have Ubuntu 7.10 on a seperate partition all installed and ready to go.

Now, to see if I can get this Realtek RTL8187B usb wireless adapter to work...wait...what's this.. [a linux driver on the realtek site!]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true")

I'll report back with my findings! Adios amigos.

---

### Post by Roasted on 2008-04-23
Regardless of whether or not the wireless driver is available, that still doesn't help the insane sound issues I had with this damn laptop.

It'd be niiiiiiiiiiiice if both issues were fixed with Hardy, though!!

---

### Post by Fran89 on 2008-04-28
Nevermind... i got it to work, use the patch Mr. Leung made, its at [http://www.datanorth.net/~cuervo/rtl8187b/](http://www.datanorth.net/~cuervo/rtl8187b/)

---

### Post by fabietto0102 on 2008-05-01
> **Mincher said:**
> O.K.

I have a Toshiba Satellite L40-18Z. I have Ubuntu 7.10 on a seperate partition all installed and ready to go.

Now, to see if I can get this Realtek RTL8187B usb wireless adapter to work...wait...what's this.. [a linux driver on the realtek site!]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true")

I'll report back with my findings! Adios amigos.

Just a sec! it seems there is a linux driver for this! I have the same problem of Roaster: a realtek chipset RTL8187L which is not detected as PCI but as a USB in 
Bus 003 Device 003: ID 0bda:0158 Realtek Semiconductor Corp.

HOw can I install that driver? I can't use the installation commands inside the tar.gz, they won't work in terminal..

---

### Post by fabietto0102 on 2008-05-02
Why is Ubuntu so crap with WiFi drivers?!?

---

### Post by TheAncientMariner on 2008-05-04
Hey hey, what do you know, it's working in Hardy with a little persuasion!

Grab the "jadams" drivers from our old friend Mr. Cuervo:

[http://www.datanorth.net/~cuervo/rtl8187b/](http://www.datanorth.net/~cuervo/rtl8187b/)

```
$ sudo apt-get install build-essential
$ tar -xzvf rtl8187b-modified-jadams-2-1-2008.tar.gz
$ cd rtl8187b-modified
$ chmod +x ./makedrv
$ sudo ./makedrv
$ chmod +x wlan0*
$ sudo ./wlan0up
```

I almost got teary-eyed when I saw Network Manager start searching for wireless networks.

In case you've forgotten the auto-start steps, just put this in /etc/rc.local:

```
[path of the driver]/wlan0up
ifconfig wlan0 up
dhclient wlan0
```

---

### Post by pedromagnus on 2008-06-11
Thanks a lot to all of you!!!! I've got FINALLY a f*cking signal in my Toshiba A215-s7428!!! I'm so happy!!!:guitar:
Next time I'll start looking backwards from the last page of the thread jaja :lolflag:
By the way, what a race!! Getting to the solution was quite hard even for the non-newbees like me. It's a little tedious to learn this way, but it's very usefull too, it stimulates the brain :P
Well, greetings from Argentina. Bye
Pedromagnus

---

### Post by ADloser on 2008-06-12
Almost got it with the steps from TheAncientMariner.
It detects my wireless card and finds wireless networks for me to connect to, but it crashes/freezes my computer as soon as I try to connect. :(.

SO CLOSE!!

(I'm on a a215-s7422)

---

### Post by pedromagnus on 2008-06-14
I'm sadly had te same issues than ADloser. But after restart a few times it seems to be fixed, I don't know why or how.
I've purchased a router Linksys WRT54G, in Win$hop$ XP it works perfect but in linux is where the problems are...
At first, the signal seems to be so much poor than with windows (¿¿??), at 2 meters the signal is about 25 %, how could this happened???
And finally, I can't connect using the SAME protocol, and the SAME password than what I use in Win$$...
I think the problem is in the patched .inf and the ndiswrapper thing... I probably screwed up in some step or something like that.
Is there any GOOD driver yet for the Realtek 8101E, without any patch or "fix"?? I think it is kind of "dirty" the way it is used...
Greetings from Argentina, (my apologies for the bad english)
Pedromagnus
PS: I'm on a toshiba a215-s7428 with hardy heron (I'll try reinstalling it)

---

### Post by mbarvian on 2008-06-30
> **ADloser said:**
> Almost got it with the steps from TheAncientMariner.
It detects my wireless card and finds wireless networks for me to connect to, but it crashes/freezes my computer as soon as I try to connect. :(.

SO CLOSE!!

(I'm on a a215-s7422)


this is probably because the hacked drivers do not support any sort of encryption.

---

### Post by arktype on 2008-07-01
i have been having some wireless networking problems with my toshiba and hardy heron. i get the following:

05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
07:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 02)

upon entering the first command in terminal. i have no pluggable wireless card.

ark

---

### Post by onewithnature83 on 2008-07-20
Here is my solution:

[https://help.ubuntu.com/community/WifiDocs/Device/RealtekRTL8187b](https://help.ubuntu.com/community/WifiDocs/Device/RealtekRTL8187b)

--TJ (creator)

---


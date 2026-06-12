---
title: "Linksys Wireless problems"
date: 2006-12-15
forum: Networking &amp; Wireless
---

### Post by Subw00fer on 2006-12-15
I just got Ubuntu 6.10 installed on a second hard drive and I am having problems connecting to the internet with my wireless Linksys card. 

I have disabled WEP on my router and I tried connecting by using the SSID that I gave my router in the Network settings under administration but that didn't work.  I don't think that I need to install any drivers since if I go into Network Devices under Administration, I can see both a Wired and Wireless options.  I think that I must have it set up wrong or I need to do something that I am unfamilar with.  I couldnt even ping my router so something must be really wrong that I am doing. Other than that, I am completely lost about this and I can't get my wired card to reach my router so I have to rely only on the wireless.

I hope that someone can kinda walk me through this since I hate having to reboot back into Windows just to post this.

thanks

---

### Post by Subw00fer on 2006-12-15
I went back to Ubuntu and here is some more information from what I have read:

I typed IWconfig and the only device that showed anything was eth1.  lo, eth0 and sit0 each said "no wireless extensions".

When I typed "ping -c 4 www.yahoo.com" it says "ping = unknown hosts www.yahoo.com"

Any ideas?

---

### Post by taurus on 2006-12-15
What is the output of this command then?

```
ifconfig
```

---

### Post by Subw00fer on 2006-12-15
> **taurus said:**
> What is the output of this command then?

```
ifconfig
```

Sorry that I can't cut and paste it in here since I had to reboot back to WinXP:

lo               

link encap: local loopback
inet addr: 127.0.0.1 Mask 255.0.0.0
inet6 addr: ::1/128   Scope: Host
UP LOOKBACK RUNNING MTU: 16436 Metro: 1


and then it had a few other lines.  Do I need to edit this to point to my router addr and mask?

---

### Post by taurus on 2006-12-15
Looks to me like you need to use ndiswrapper to install a driver for your Linksys wireless card!  What model is it anyway?

---

### Post by Subw00fer on 2006-12-15
> **taurus said:**
> Looks to me like you need to use ndiswrapper to install a driver for your Linksys wireless card!  What model is it anyway?

Its the Linksys Wireless-G PCI Adapter with SpeedBooster (WMP54GS)

[http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1115416826820&pagename=Linksys%2FCommon%2FVisitorWrapper](http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1115416826820&pagename=Linksys%2FCommon%2FVisitorWrapper)

I've read on how to do ndiswrapper but I need some help.  This thread seems to help but it also is long and might be more than I need to do: [http://forums.windrivers.com/showthread.php?t=67640](http://forums.windrivers.com/showthread.php?t=67640)

---

### Post by Subw00fer on 2006-12-16
I'm not sure if this is the best way to get my wireless linksys card working, but i tried building ndiswrapper just now but it was giving me errors for stdlib.h.  I'm not doing too good here with this.  Any tips on how the heck i can get my internet working with ubuntu?  I wish this was easier.

---

### Post by Subw00fer on 2006-12-16
I decided to find some other links on the web rather than building ndiswrapper.  I am following this site [http://ubuntuforums.org/showthread.php?t=197102&highlight=install+ndiswrapper](http://ubuntuforums.org/showthread.php?t=197102&highlight=install+ndiswrapper)  and it is very close to the chipset that I have in my PC.  When I run the lspci command and grep for Broadcom, I get the same model as the link but mine is 4306.  I'm not sure if the "ndiswrapper_setup" command is completing or not.  I can't seem to find that executable on my system and when I check System > Admin > Networking, I can no longer see my wireless option in there unless I reboot.

Any ideas on how to get ndiswrapper to work since it seems like the method that most poeple use to get these Linksys cards working.

Thanks!

---

### Post by Subw00fer on 2006-12-16
> **taurus said:**
> What is the output of this command then?

```
ifconfig
```


I did a few more commands, not sure which one did it....but now when I type "ifconfig" i get information for eth0 and lo.  The eth0 says the correct HWaddr but it does not give an IP address.  I also noticed that now I can see a "wireless connection" under Network Settings but it doesnt work if I change the Essid to my router and enable that connection.

I also tried "sudo ifup eth0" and it went thru a few lines and got to:

No DHCOFFERS received
No working leases in persistent database - sleeping

Not sure what they means but maybe I am on the right track.  I really really want to get my internet working in Ubuntu soon or I feel that I am going no where with this new OS.

Any ideas?

---

### Post by taurus on 2006-12-16
Maybe this link helps...

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by Subw00fer on 2006-12-16
> **taurus said:**
> Maybe this link helps...

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

I must be missing something because when I type "sudo apt-get install bcm43xx-fwcutter", I get:

Reading package lists....Done
Building dependency tree
Reading state information...Done
E: Couldn't find package bcm43xx-fwcutter


What am I doing wrong?

Also, I checked "ifconfig" and now eth1 is gone.  I need to figure out how to get this back because I added the Network Connection tool to my top toolback and I changed it from lo to eth0 and it only says disconnected with no signal stregth.  Maybe I am onto something but I still need help.  Perhaps I have everything already set up correctly and all I need to do is activate something else.  I'm not sure but it appears that eth1 (my wireless broadcom 4306) is being found.

thanks

---

### Post by taurus on 2006-12-16
Well, do you have both universe and multiverse enable in /etc/apt/sources.list???

```
After enabling the Universe repository (see Repositories), install the bcm43xx-fwcutter package.
```

---

### Post by Subw00fer on 2006-12-16
> **taurus said:**
> Well, do you have both universe and multiverse enable in /etc/apt/sources.list???

```
After enabling the Universe repository (see Repositories), install the bcm43xx-fwcutter package.
```

I commented out the lines in that file for unverse but I don't think it will matter because I don't even have a wired connection on my Ubuntu system.  What should I try now?  The best I can do is copy files to a USB thumb drive on my laptop that I have right here and copy them to the Ubuntu system.

---

### Post by Subw00fer on 2006-12-16
Do I need to install any files since I can see that iwconfig shows my wireless card at eth1 and the Network Settings brings up eth1 but has the status at Disconnected and no signal?

---

### Post by houstonbofh on 2006-12-16
Having been through this many times, it is so much easier just to buy a supported card.  They can be had for less than $20 USD, and it will save your sanity.  For hints try this page. [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

---

### Post by Subw00fer on 2006-12-16
> **houstonbofh said:**
> Having been through this many times, it is so much easier just to buy a supported card.  They can be had for less than $20 USD, and it will save your sanity.  For hints try this page. [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)


I don't think I need to use that link because I believe that my card is already activated and supported.  It shows up in the network settings and also by typing iwconfig.

Any ideas or step-by-step instructions on how to get my card working or testing to see where I am in this crazy process.

I can't believe Ubuntu is this difficult to just get a wireless card set up.  I can't wait to see what problems I run into when I try to build some code in this OS.

thanks for your help everyone one.

---

### Post by houstonbofh on 2006-12-16
> **Subw00fer said:**
> I don't think I need to use that link because I believe that my card is already activated and supported.  It shows up in the network settings and also by typing iwconfig.

Any ideas or step-by-step instructions on how to get my card working or testing to see where I am in this crazy process.

I can't believe Ubuntu is this difficult to just get a wireless card set up.  I can't wait to see what problems I run into when I try to build some code in this OS.

thanks for your help everyone one.
It is not Ubuntu, but Linksys.  Your card (I believe...  That was the case with the last Linksys I used showing these problems) does not have a firmware.  It is loaded by the driver.  You have to find the right firmware, and get it loaded at the right time.  It is a big headache all to save 15 cents on a flash chip.  I spent 4 hours one night, then drive to Fry's.  It was up 3 minutes after I got back.  And yes it would detect.  (Detected on the Live CD so I thought I was OK)  But it will never connect because there is no firmware telling the card how to do it.  (Note that some Linksys cards have the firmware on the chip, but it is not documented by Linksys which ones do...)

---

### Post by Subw00fer on 2006-12-17
> **houstonbofh said:**
> It is not Ubuntu, but Linksys.  Your card (I believe...  That was the case with the last Linksys I used showing these problems) does not have a firmware.  It is loaded by the driver.  You have to find the right firmware, and get it loaded at the right time.  It is a big headache all to save 15 cents on a flash chip.  I spent 4 hours one night, then drive to Fry's.  It was up 3 minutes after I got back.  And yes it would detect.  (Detected on the Live CD so I thought I was OK)  But it will never connect because there is no firmware telling the card how to do it.  (Note that some Linksys cards have the firmware on the chip, but it is not documented by Linksys which ones do...)

Which card did you get that worked so well?  about 1/2 of the DLink cards look just right and even one Trendnet card was called the easiest setup.  But I would hate to have to buy a new card, although I do plan on buying a new system in the fall and have it dual boot.  And I guess if the card works perfect with Edgy v6.10 then it should definitely work great in future Ubuntu releases.

I still want to get this Linksys card working since I could always goto another Linux distro but I rather not.  Any tips on how to get this lousy card workin?

---

### Post by houstonbofh on 2006-12-17
For my laptop I ended up with an SMC 2532 W-B, an 802.11b high power card with a Prism chipset and detachable antenna.  Expensive, but well worth it.  Amazing range, and works perfect with everything. (Including kismet)  I also had an old Prism PCI card, but it got hit mb a power spike.  Looking for a replacement now...

---

### Post by wieman01 on 2006-12-17
Before you go ahead and install "ndiswrapper", please run these commands & post the results:
> iwlist scan
> lshw
Just to see if your card has been recognized & can scan for wireless networks.

---

### Post by Subw00fer on 2006-12-17
Doesn't seem to be scanning for the iwlist command but I am not sure what to look for in the second command you gave me.

```

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

sit0      Interface doesn't support scanning.

eth1      No scan results

```

and

```

WARNING: you should run this program as super-user.
m-linux
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 2026MB
     *-cpu:0
          product: Intel(R) Pentium(R) 4 CPU 3.00GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 15.2.9
          size: 18EHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe cid xtpr
          configuration: id=1
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             width: 32 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             width: 32 bits
             capabilities: logical
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 8KB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KB
     *-cpu:1
          product: Intel(R) Pentium(R) 4 CPU 3.00GHz
          vendor: Intel Corp.
          physical id: 2
          bus info: cpu@1
          version: 15.2.9
          size: 18EHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe cid xtpr
          configuration: id=1
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             width: 32 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             width: 32 bits
             capabilities: logical
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 8KB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KB
     *-pci
          description: Host bridge
          product: 82875P/E7210 Memory Controller Hub
          vendor: Intel Corporation
          physical id: e8000000
          bus info: pci@00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          resources: iomemory:e8000000-efffffff
        *-pci:0
             description: PCI bridge
             product: 82875P Processor to AGP Controller
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@00:01.0
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
           *-display
                description: VGA compatible controller
                product: NV38 [GeForce FX 5950 Ultra]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@01:00.0
                version: a1
                size: 256MB
                width: 32 bits
                clock: 66MHz
                capabilities: vga bus_master cap_list
                resources: iomemory:fd000000-fdffffff iomemory:c0000000-cfffffff irq:10
        *-pci:1
             description: PCI bridge
             product: 82875P/E7210 Processor to PCI to CSA Bridge
             vendor: Intel Corporation
             physical id: 3
             bus info: pci@00:03.0
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
           *-network
                description: Ethernet interface
                product: 82547EI Gigabit Ethernet Controller (LOM)
                vendor: Intel Corporation
                physical id: 1
                bus info: pci@02:01.0
                logical name: eth0
                version: 00
                serial: 00:0e:a6:4e:fe:f0
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=e1000 multicast=yes
                resources: iomemory:fe9e0000-fe9fffff ioport:cf80-cf9f irq:169
        *-usb:0
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:ef00-ef1f irq:185
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.17-10-generic uhci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
              *-usb
                   description: Printer
                   product: Photosmart 8100 series
                   vendor: HP
                   physical id: 1
                   bus info: usb@2:1
                   version: 1.00
                   serial: MY4AM2M1MZ0485
                   capabilities: usb-2.00 bidirectional
                   configuration: driver=usb-storage maxpower=2mA speed=12.0MB/s
        *-usb:1
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:ef20-ef3f irq:193
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.17-10-generic uhci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
              *-usb
                   description: Mouse
                   product: Microsoft 5-Button Mouse with IntelliEye(TM)
                   vendor: Microsoft
                   physical id: 2
                   bus info: usb@3:2
                   version: 3.00
                   capabilities: usb-1.10
                   configuration: driver=usbhid maxpower=100mA speed=1.5MB/s
        *-usb:2
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:ef40-ef5f irq:169
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.17-10-generic uhci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
              *-usb
                   description: Mass storage device
                   product: Flash Disk
                   vendor: USB
                   physical id: 2
                   bus info: usb@4:2
                   version: 1.10
                   serial: A4176B414B2DEFDA
                   capabilities: usb-1.10 scsi
                   configuration: driver=usb-storage maxpower=100mA speed=12.0MB/s
        *-usb:3
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:ef80-ef9f irq:185
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.17-10-generic uhci_hcd
                physical id: 1
                bus info: usb@5
                logical name: usb5
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:4
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd
             resources: iomemory:febffc00-febfffff irq:177
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 2.6.17-10-generic ehci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-2.00
                configuration: driver=hub maxpower=0mA slots=8 speed=480.0MB/s
        *-pci:2
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@00:1e.0
             version: c2
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
           *-firewire:0
                description: FireWire (IEEE 1394)
                product: IEEE 1394 Host Controller
                vendor: VIA Technologies, Inc.
                physical id: 3
                bus info: pci@03:03.0
                version: 46
                width: 32 bits
                clock: 33MHz
                capabilities: ohci bus_master cap_list
                configuration: driver=ohci1394
                resources: iomemory:feaff800-feafffff ioport:dc00-dc7f irq:201
           *-multimedia
                description: Multimedia audio controller
                product: SB Audigy
                vendor: Creative Labs
                physical id: b
                bus info: pci@03:0b.0
                version: 04
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=EMU10K1_Audigy
                resources: ioport:df00-df3f irq:177
           *-input
                description: Input device controller
                product: SB Audigy MIDI/Game port
                vendor: Creative Labs
                physical id: b.1
                bus info: pci@03:0b.1
                version: 04
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=Emu10k1_gameport
                resources: ioport:dfe0-dfe7
           *-firewire:1
                description: FireWire (IEEE 1394)
                product: SB Audigy FireWire Port
                vendor: Creative Labs
                physical id: b.2
                bus info: pci@03:0b.2
                version: 04
                width: 32 bits
                clock: 33MHz
                capabilities: ohci bus_master cap_list
                configuration: driver=ohci1394
                resources: iomemory:feaff000-feaff7ff iomemory:feaf8000-feafbfff irq:201
           *-network DISABLED
                description: Wireless interface
                product: BCM4306 802.11b/g Wireless LAN Controller
                vendor: Broadcom Corporation
                physical id: c
                bus info: pci@03:0c.0
                logical name: eth1
                version: 03
                serial: 00:0f:66:6e:b0:04
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master ethernet physical wireless
                configuration: broadcast=yes driver=bcm43xx multicast=yes wireless=IEEE 802.11b/g
                resources: iomemory:feafc000-feafdfff irq:201
        *-isa UNCLAIMED
             description: ISA bridge
             product: 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
        *-ide:0
             description: IDE interface
             product: 82801EB/ER (ICH5/ICH5R) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@00:1f.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=PIIX_IDE
             resources: ioport:fc00-fc0f iomemory:88000000-880003ff irq:169
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-disk
                   product: Maxtor 90913D4
                   vendor: Maxtor
                   physical id: 1
                   bus info: ide@0.1
                   logical name: /dev/hdb
                   capacity: 8709MB
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 33MHz
              *-cdrom
                   product: JLMS XJ-HD166S
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   capabilities: packet
        *-ide:1
             description: IDE interface
             product: 82801EB (ICH5) SATA Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@00:1f.2
             logical name: scsi0
             logical name: scsi1
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master scsi-host
             configuration: driver=ata_piix
             resources: ioport:efe0-efe7 ioport:efac-efaf ioport:efa0-efa7 ioport:efa8-efab ioport:ef60-ef6f irq:169
        *-serial UNCLAIMED
             description: SMBus
             product: 82801EB/ER (ICH5/ICH5R) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             resources: ioport:400-41f irq:10
  *-scsi:0
       physical id: 1
       bus info: scsi@2
       logical name: scsi2
       capabilities: scsi-host
       configuration: driver=usb-storage
  *-scsi:1
       physical id: 2
       bus info: scsi@4
       logical name: scsi4
       capabilities: scsi-host
       configuration: driver=usb-storage


```

---

### Post by Subw00fer on 2006-12-17
weiman,  I was looking at the second link in your sig and I noticed that you mentioned one of your requirements is to use ESSID.  I have my Linksys router broadcast my SSID, would that be causing any problems?  I also use DHCP since it is easier to use in my opinion.  One other thing is that I am having a heck of a time getting ndiswrapper to build on my fresh install of Ubuntu 6.10.  When I run "sudo make" I gives me an error for "stdlib.h: No such file or directory".  This seems to be a path problem but should I focus on getting this built or do I need to fix something else?

thanks and I can't wait to get this PC up and running on the web so that I can actually use it.

---

### Post by Subw00fer on 2006-12-17
well I can get on my wired internet now with no configurations so I at least now don't have to use my laptop or reboot to post something.

So if I need to download anything or use Synaptic, please let me know.

thanks!

---

### Post by Subw00fer on 2006-12-17
FIXED IT!!!  Yay!

I connected my wired connection to my PC and followed this page:

[http://www.ubuntuforums.org/showthread.php?t=95380](http://www.ubuntuforums.org/showthread.php?t=95380)

It took a while to get some stuff downloaded but now it works.  PM me if you have any questions.

---

### Post by wieman01 on 2006-12-17
Alright... So we can close this thread the, correct? If you need wireless security (e.g. WPA), take a look at the links in my signature.

---

### Post by Subw00fer on 2006-12-20
> **wieman01 said:**
> Alright... So we can close this thread the, correct? If you need wireless security (e.g. WPA), take a look at the links in my signature.

I will sometime soon since I need to get some type of security on my router now.

I also need to know how to run the "sudo modprobe bcm43xx" command at the start up.  How can this be done?

---

### Post by wieman01 on 2006-12-20
Open this file:
> sudo gedit /etc/modules
Then add "bcm43xx" at the bottom. Save & restart the computer.

---

### Post by goggleBOX on 2006-12-21
> **wieman01 said:**
> Open this file:

Then add "bcm43xx" at the bottom. Save & restart the computer.

Thanks, this was the same problem I was having, thank you for forum search.

I have a Compaq 2418AU Presario 

I tried the "ndiswrapper" way and no luck, following the guild here ( [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Edgy](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Edgy) ). I had no problems except for needing to run "sudo modprobe bcm43xx" after a reboot.

Thanks for the info.

---

### Post by gcarelli on 2007-03-05
Sorry for the long message I will try to keep them shorter next time.


Hello this is my first time on a message board, and first time using Ubuntu, well linux. I installed edubuntu, for my five year old daughter who is good in windows, paint, and loading her web site shortcuts I put on the desk top.  Someone told me about edubuntu, I installed the latest version, and have the same problem with my WMP54GS Wireless-G PCI Adapter. I cant get the internet. I have no idea how linux works.  I like the education programs on it, but I would like to get the web up and running.  iwconfig shows ip address, mask and gatway. it is the same as in the windows ( when I use the grub to dual boot.) but it I can't get the internet.  Since the pc is far from a router I don't want to disconect and hard wire it to the router. How did you get it running with out a net connection.

I do have full bars in windows so the signal is great.

---

### Post by wieman01 on 2007-03-05
Hello, 

What does "iwlist scan" say?
> iwlist scan
Is your wireless network listed?

---

### Post by gcarelli on 2007-03-05
Sorry I am not home. I am new to Linux so I will try tonight. My current time is 11:30am in Montreal, Canada.  I don't know the comands in linux. I did manage to activate the root user to log in to edubuntu xwindow. I will be using this account to do my work, and have two users setup one form me and one for my daughter. Thank you for the answering I will try what subwoofer did with the windows driver. I will let you know.

Do I need a internet connection to do what he did, with the windows driver.

Is there a util. that show wireless networks in range like windows.

---

### Post by wieman01 on 2007-03-05
> **gcarelli said:**
> Sorry I am not home. I am new to Linux so I will try tonight. My current time is 11:30am in Montreal, Canada.  I don't know the comands in linux. I did manage to activate the root user to log in to edubuntu xwindow. I will be using this account to do my work, and have two users setup one form me and one for my daughter. Thank you for the answering I will try what subwoofer did with the windows driver. I will let you know.

Do I need a internet connection to do what he did, with the windows driver.

Is there a util. that show wireless networks in range like windows.
You don't really need a working internet connection... That'd be a catch-22 situation. As for the wireless networks in range, that's the command I have given you. Just execute it and see if it spits out any information with regard to your own network. If there is no output at all, then your card is probably not working. I am trying to find out exactly that.

Let's talk later then.

---

### Post by gcarelli on 2007-03-05
Ok so i tried what subwoofer did and it did not work for me. when I did the


root@emily:/# ndiswrapper -i /opt/wireless/bcmwl5.inf
Installing bcmwl5

root@emily:/# ndiswrapper -l
Installed ndis drivers:
bcmwl5  driver present, hardware present 

root@emily:/# ndiswrapper -m
modprobe config already contains alias directive

root@emily:/# modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.17-10-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument


root@emily:/# iwlist scanlo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning : No such device

sit0      Interface doesn't support scanning.


now I'm lost. I am now hard wired to the router. so I have net access.  but the computer needs to be in different room. What to do.

---

### Post by wieman01 on 2007-03-06
Please do this and post the results:
> cat /etc/modprobe.d/ndiswrapper
This file contains the name of your wireless network interface.

---

### Post by gcarelli on 2007-03-06
I will try it to night thank you. Sorry I work during the day and don't have time until the night.

---

### Post by wieman01 on 2007-03-06
> **gcarelli said:**
> I will try it to night thank you. Sorry I work during the day and don't have time until the night.
Don't worry. See you tomorrow then (MET).

---

### Post by AnalBeard on 2007-03-06
hi there, i'm new to Ubuntu, and i'm having the same problems. i have the 43xx version of the Linksys WPC54G, and i was attempting to use this quide - [http://ubuntuforums.org/showthread.php?t=185174](http://ubuntuforums.org/showthread.php?t=185174) however, when i try to install fwcutter via the terminal i get the error "couldn't find package bcm43xx-fwcutter". if i try to find it in Synaptic, there's no packages listed. obviously i'm a bit stuck, any help would be appreciated :)

---

### Post by gcarelli on 2007-03-06
wieman01
Thank you for your time and help.

root@emily:~# cat /etc/modprobe.d/ndiswrapper 
alias wlan0 ndiswrapper
root@emily:~# 

What does it mean I am new to this.

---

### Post by wieman01 on 2007-03-07
> **gcarelli said:**
> wieman01
Thank you for your time and help.

root@emily:~# cat /etc/modprobe.d/ndiswrapper 
alias wlan0 ndiswrapper
root@emily:~# 

What does it mean I am new to this.
Alright. Please open this file (all from command line):
> sudo gedit /etc/network/interfaces
Now paste the following:
> auto lo
iface lo inet loopback

# ethernet adapter
auto eth0
iface eth0 inet dhcp

# wireless adapter 
auto wlan0
iface wlan0 inet dhcp
Please make sure that the contents of the file look exactly like that, then save the file & close the window.

Now scan once again:
> iwlist scan
Any output? If so, then you should be able to use GNOME's networking applet to configure your wireless network.

---

### Post by gcarelli on 2007-03-08
Thank you for everything it did not work. I reinstalled edubuntu just in case all the thing I did messed up the system. And all that you have said it did not work.  I used a different computer with the same card and it worked there.

Then because this computer is to good for a five year old I tried it again.  I re-installed 
edubunt on the computer for a third time and followed the link below, it worked perfectly. 

[http://www.ubuntuforums.org/showthread.php?t=185174&highlight=bcm43xx-fwcutter](http://www.ubuntuforums.org/showthread.php?t=185174&highlight=bcm43xx-fwcutter)


The only problem I have is that the network manager does not show the wireless network bars or that a wireless network is present but it works. The computer is back in its place with no rj45 connection just wireless.

Thank you again.

---


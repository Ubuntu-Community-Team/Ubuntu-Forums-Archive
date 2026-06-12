---
title: "[SOLVED] Ethernet loss (reinstall and configure network packages?)"
date: 2007-12-31
forum: Networking &amp; Wireless
---

### Post by Danieljh75 on 2007-12-31
I broke my internet connection by removing 4 packages (I don't recall which ones) while using Adept. I downloaded a wireless utility, kwlan I believe, and it unstalled 4 packages before I realized what happened. Network manager was disabled and my internet connectivity was obliterated! I have been ready to kick the tar out of my box because wireless is disabled and then I went and really hosed myself.:confused:

I have a Mac OS X Powerbook that I'm using and my Linux box is a separate machine, thus, I have access to forums.

This is what I need: **I need my wired connection functional again.** 

I will undoubtedly have time to self-destruct my system again at a later date, while in pursuit of a wireless connection.

I have Ubuntu 7.10 and I also installed the KDE packages (install kubuntu-desktop) via command line. Ethernet originally worked. I opened Adept, tried to find everything related to networking ad network-manager but I could not install everything from the CD. (original Ubuntu CD ISO was 7.04 & I upgraded to 7.10 via update feature). One of the updates (have no idea what repository or local location it was found in) removed kwlan and reactivated my 'network manager.' I enabled eth0 via network manager but I have no status indication; however, both of the green and amber LEDs on the ethernet card (integrated into mother board) are steadily illuminated.

Here are the commands and the respective outputs I pulled from the terminal. If there is anything else to do, please tell me.


**lspc1**

dan@DanUbuntu:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:09.0 Multimedia audio controller: Creative Labs SB Audigy (rev 03)
00:09.1 Input device controller: Creative Labs SB Audigy Game Port (rev 03)
00:09.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port
00:0a.0 CardBus bridge: Ricoh Co Ltd RL5c475 (rev 80)
00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter (rev 01)
02:00.0 Ethernet controller: Atheros Communications, Inc. AR5416 802.11a/b/g/n Wireless PCI Adapter (rev 01)


**lshw -c network**

dan@DanUbuntu:~$ lshw -c network
Hardware Lister (lshw) - B.02.10
usage: lshw [-format] [-options ...]
       lshw -version

        -version        print program version (B.02.10)

format can be
        -html           output hardware tree as HTML
        -xml            output hardware tree as XML
        -short          output hardware paths
        -businfo        output bus information

options can be
        -class CLASS    only show a certain class of hardware
        -C CLASS        same as '-class CLASS'
        -disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
        -enable TEST    enable a test (like pci, isapnp, cpuid, etc. )
        -quiet          don't display status


**lshw**

dan@DanUbuntu:~$ lshw
WARNING: you should run this program as super-user.
danubuntu                 
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 1
          size: 959MB
     *-cpu
          product: AMD Athlon(tm) 64 Processor 3000+
          vendor: Advanced Micro Devices [AMD]
          physical id: 2
          bus info: cpu@0
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext x86-64 3dnowext 3dnow up
     *-pci:0
          description: Host bridge
          product: K8M800 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
          configuration: driver=agpgart-amd64 latency=8 module=amd64_agp
        *-pci
             description: PCI bridge
             product: VT8237 PCI bridge [K8T800/K8T890 South]
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master cap_list
           *-display
                description: VGA compatible controller
                product: S3 Unichrome Pro VGA Adapter
                vendor: VIA Technologies, Inc.
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 01
                width: 32 bits
                clock: 66MHz
                capabilities: vga bus_master cap_list
                configuration: latency=32 mingnt=2
        *-multimedia
             description: Multimedia audio controller
             product: SB Audigy
             vendor: Creative Labs
             physical id: 9
             bus info: pci@0000:00:09.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=EMU10K1_Audigy latency=32 maxlatency=20 mingnt=2 module=snd_emu10k1
        *-input
             description: Input device controller
             product: SB Audigy Game Port
             vendor: Creative Labs
             physical id: 9.1
             bus info: pci@0000:00:09.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=Emu10k1_gameport latency=32 module=emu10k1_gp
        *-firewire
             description: FireWire (IEEE 1394)
             product: SB Audigy FireWire Port
             vendor: Creative Labs
             physical id: 9.2
             bus info: pci@0000:00:09.2
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master cap_list
             configuration: driver=ohci1394 latency=32 maxlatency=4 mingnt=2 module=ohci1394
        *-pcmcia
             description: CardBus bridge
             product: RL5c475
             vendor: Ricoh Co Ltd
             physical id: a
             bus info: pci@0000:00:0a.0
             version: 80
             width: 64 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus latency=176 maxlatency=5 module=yenta_socket
             resources: iomemory:b00502000-b00501fff
        *-storage
             description: RAID bus controller
             product: VIA VT6420 SATA RAID Controller
             vendor: VIA Technologies, Inc.
             physical id: f
             bus info: pci@0000:00:0f.0
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: storage bus_master cap_list
             configuration: driver=sata_via latency=32 module=sata_via
        *-ide
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: f.1
             bus info: pci@0000:00:0f.1
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master cap_list
             configuration: driver=VIA_IDE latency=32 module=via82cxxx
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-disk
                   product: Maxtor 6Y120P0
                   vendor: Maxtor
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   capacity: 114GB
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 33MHz
              *-cdrom:0
                   product: Pioneer DVD-ROM ATAPIModel DVD-500M 010
                   vendor: Pioneer
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   capacity: 699MB
                   capabilities: packet
              *-cdrom:1
                   product: PLEXTOR CD-R PX-W1610A
                   physical id: 1
                   bus info: ide@1.1
                   logical name: /dev/hdd
                   capabilities: packet
        *-usb:0
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10
             bus info: pci@0000:00:10.0
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.1
             bus info: pci@0000:00:10.1
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.2
             bus info: pci@0000:00:10.2
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.3
             bus info: pci@0000:00:10.3
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: USB 2.0
             vendor: VIA Technologies, Inc.
             physical id: 10.4
             bus info: pci@0000:00:10.4
             version: 86
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=32 module=ehci_hcd
        *-isa
             description: ISA bridge
             product: VT8237 ISA bridge [KT600/K8T800/K8T890 South]
             vendor: VIA Technologies, Inc.
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-network
             description: Ethernet interface
             product: VT6102 [Rhine-II]
             vendor: VIA Technologies, Inc.
             physical id: 12
             bus info: pci@0000:00:12.0
             logical name: eth0
             version: 78
             serial: 00:11:09:02:99:12
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical
             configuration: broadcast=yes driver=via-rhine driverversion=1.4.3 latency=32 maxlatency=8 mingnt=3 module=via_rhine multicast=yes
     *-pci:1
          description: Host bridge
          product: K8M800 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 101
          bus info: pci@0000:00:00.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: K8M800 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 102
          bus info: pci@0000:00:00.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: K8M800 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 103
          bus info: pci@0000:00:00.3
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K8M800 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 104
          bus info: pci@0000:00:00.4
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: K8M800 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 105
          bus info: pci@0000:00:00.7
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 106
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 107
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:8
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 108
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:9
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 109
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp module=k8temp
     *-network UNCLAIMED
          description: Ethernet controller
          product: AR5416 802.11a/b/g/n Wireless PCI Adapter
          vendor: Atheros Communications, Inc.
          physical id: 0
          bus info: pci@0000:02:00.0
          version: 01
          width: 32 bits
          clock: 66MHz
          capabilities: cap_list
          configuration: latency=0


**ifconfig**

dan@DanUbuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:09:02:99:12  
          inet6 addr: fe80::211:9ff:fe02:9912/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:306 errors:0 dropped:0 overruns:0 frame:0
          TX packets:66 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:101171 (98.7 KB)  TX bytes:10342 (10.0 KB)
          Interrupt:23 Base address:0xe100


PS

I've read for hours. Please, someone just help me.

---

### Post by Predator[23rd] on 2007-12-31
what does your /etc/network/interfaces file say?

should have something like this:

[I]auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp[/I]

or in case you don't use a DHCP server eth0 will look like this here:

[I]auto eth0
iface eth0 inet static
address 192.168.2.2
netmask 255.255.255.0
network 192.168.2.0
broadcast 192.168.2.255
gateway 192.168.2.1[/I]

if these are missing add them and restart your network (sudo /etc/init.d/network restart)

if all of this is there I am afraid I can't help you. sorry.

---

### Post by Danieljh75 on 2007-12-31
i looked at the interfaces file and I recall that I had commented this file previously, though it had never impacted my ability to connect via ethernet. At any rate, I navigated there via gui because i forgot how to open the file with the terminal. Here is what the file says:

auto lo
1face lo 1net loopback

#1face eth0 1net dhcp


//auto eth2
//#1face eth2 1net dhcp

//auto ath0
//#1face ath0 1net dhcp

//auto wlan0
//#1face wlan0 1net dhcp


//auto eth0



1face eth0 1net dhcp

auto eth0



~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
I tried the sudo command to restart the network and through various combinations (in case the space between 'network restart' was an issue) the only response I had was, 'command not found'

I'm originally familiar with Mac and the Terminal for the Darwin BSD underpinnings. Linux is a little different for me so please forgive my learning curve I forget where to navigate and how to do things via command line (although, I do like the command line). 

Dan

---

### Post by Predator[23rd] on 2007-12-31
I guess the correct command is NETWORKING, sorry, I always use auto completion (TAB) and make such mistakes all the time when I have to actually write it down. sorry.

I recommend editing your interfaces file to look like this here:
[I]
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp[/I]

I am a noob and like mc (midnight commander - a norton commander clone for linux) when I open the terminal. Always loved Norton Commander / Norton Utilities in the good old DOS days :)

anyway, edit it with whatever editor you like (vi?). and restart your network: 
**sudo /etc/init.d/networking restart**

hope that solves your problem ...

---

### Post by Danieljh75 on 2007-12-31
Ooorah!!!!

I recalled that I could use sudo gedit (file path) to edit the interfaces file. I tweaked it so that it looks like this:

auto lo
iface lo inet loopback


#iface eth0 inet dhcp


auto eth2
#iface eth2 inet dhcp

auto ath0
#iface ath0 inet dhcp

auto wlan0
#iface wlan0 inet dhcp


auto eth0
#iface eth0 inet dhcp





iface eth0 inet dhcp

I did the network restart and got this messaage in the terminal:

dan@DanUbuntu:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          Ignoring unknown interface eth2=eth2.
Ignoring unknown interface ath0=ath0.
Ignoring unknown interface wlan0=wlan0.
Ignoring unknown interface eth0=eth0.


Didn't know what to do so I opened Firfox and googled something. Yay, it worked! 

I'm sorry I took your time on something silly, but thank you for helping me get this fixed. Have a happy New Year! It was my mistake with the numeral 1 by the way. It was the font in the text editor and I thought it was a 1 when it was really an i. Still, thank you.

Dan

PS.

Maybe I'll message you when I crash my system again... heh heh. :)

---

### Post by Predator[23rd] on 2007-12-31
anytime mate!

happy new year too. :D

To make sure your interfaces file is in good shape check again what interfaces you have (just type "ifconfig" and read through the output) and remove every entry you don't have. they are useless and will be ignored anyway ...

---


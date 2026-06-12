---
title: "Intel I217-V wired ethernet not working"
date: 2015-06-03
forum: Networking &amp; Wireless
---

### Post by Anthon_Williamson on 2015-06-03
Background: 
I am mostly new to Linux. Never had a permanent install before only worked with portable or VM installs for the duration of school projects. So I do know a few basics but very little beyond that. Also oddly enough I am trying to get this working for my wife who is completely new to Linux but wants to dive into programming and feels it makes more sense to do it on an open source platform. She is brand new to programming too but is the type that only does something if she can fully throw herself into it. I did try installing Ubuntu and several other Debian distros like Mint and older versions of Ubuntu like 14..04.2 LTS and even CentOS all with same result. At the moment running from live USB flash drive while having Windows 10 tech preview installed as the main OS until I can get this working. Any help would be greatly appreciated. I am just hoping this motherboard doesn't have some critical issue with Linux.
Since this doesn't yet have any active programs or personal data attached I am willing to do whatever is needed and destructive changes aren't an issue. She prefers Ubuntu's style having used a Mac a few years ago and liking that in some areas and hating it in others. I know this is an Ubuntu forum but If someone knows the only/best fix is to move to a different distro that is acceptable but trying to be avoided.



Issue:
Currently trying to work with Ubuntu 15.04 64bit. I have a [COLOR=#111111][FONT=Arial]GA-Z97X-UD3H-BK motherboard Intel Z97 with a built in [/FONT][/COLOR]I217-V wired ethernet. Works fine in windows 10. It doesn't work with default settings or anything I have tired yet. All I know enough, or have found suggestions, to have tried so far are
1. To try applying static IPv4 addresses. I don't know how to turn off IPv6 if that is interfering and ideally would of course like to have both.
2. To disable auto speed negotiation and force the speed down to 100Mbit. Don't remember the terminal command but it did show as forcing it down on the lights on the ethernet switch so worked as advertised but didn't fix the connection.
3. To compile the e1000e driver that I think I found as the right one for this device but doesn't compile as far as I can tell. 



Diagnostic info:
The info from [COLOR=#000000][FONT=Ubuntu Mono]lspci[/FONT][/COLOR] and [COLOR=#000000][FONT=Ubuntu Mono]sudo lshw[/FONT][/COLOR] that seem to be for this effected device are

```
00:19.0 Ethernet controller: Intel Corporation Ethernet Connection I217-V

and

*-network
             description: Ethernet interface
             product: Ethernet Connection I217-V
             vendor: Intel Corporation
             physical id: 19
             bus info: pci@0000:00:19.0
             logical name: eth0
             version: 00
             serial: fc:aa:14:7e:57:c0
             size: 1Gbit/s
             capacity: 1Gbit/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=2.3.2-k duplex=full firmware=0.13-4 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
             resources: irq:27 memory:f7c00000-f7c1ffff memory:f7c3c000-f7c3cfff ioport:f080(size=32)


In case the full info is needed here you go.

lspci - 


00:00.0 Host bridge: Intel Corporation 4th Gen Core Processor DRAM Controller (rev 06)
00:02.0 VGA compatible controller: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller (rev 06)
00:03.0 Audio device: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller (rev 06)
00:14.0 USB controller: Intel Corporation 9 Series Chipset Family USB xHCI Controller
00:16.0 Communication controller: Intel Corporation 9 Series Chipset Family ME Interface #1
00:19.0 Ethernet controller: Intel Corporation Ethernet Connection I217-V
00:1a.0 USB controller: Intel Corporation 9 Series Chipset Family USB EHCI Controller #2
00:1b.0 Audio device: Intel Corporation 9 Series Chipset Family HD Audio Controller
00:1c.0 PCI bridge: Intel Corporation 9 Series Chipset Family PCI Express Root Port 1 (rev d0)
00:1c.3 PCI bridge: Intel Corporation 9 Series Chipset Family PCI Express Root Port 4 (rev d0)
00:1d.0 USB controller: Intel Corporation 9 Series Chipset Family USB EHCI Controller #1
00:1f.0 ISA bridge: Intel Corporation 9 Series Chipset Family Z97 LPC Controller
00:1f.2 SATA controller: Intel Corporation 9 Series Chipset Family SATA Controller [AHCI Mode]
00:1f.3 SMBus: Intel Corporation 9 Series Chipset Family SMBus Controller
02:00.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 41)


sudo lshw  - 

ubuntu                    
    description: Computer
    width: 64 bits
    capabilities: smbios-2.7 vsyscall32
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 7845MiB
     *-cpu
          product: Intel(R) Celeron(R) CPU G1820 @ 2.70GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          size: 2700MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp x86-64 constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 movbe popcnt tsc_deadline_timer xsave rdrand lahf_lm abm arat pln pts dtherm tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust erms invpcid xsaveopt cpufreq
     *-pci
          description: Host bridge
          product: 4th Gen Core Processor DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 06
          width: 32 bits
          clock: 33MHz
          configuration: driver=hsw_uncore
          resources: irq:0
        *-display
             description: VGA compatible controller
             product: Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 06
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:29 memory:f7800000-f7bfffff memory:e0000000-efffffff ioport:f000(size=64)
        *-multimedia:0
             description: Audio device
             product: Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller
             vendor: Intel Corporation
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 06
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:31 memory:f7c34000-f7c37fff
        *-usb:0
             description: USB controller
             product: 9 Series Chipset Family USB xHCI Controller
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:26 memory:f7c20000-f7c2ffff
           *-usbhost:0
                product: xHCI Host Controller
                vendor: Linux 3.19.0-15-generic xhci-hcd
                physical id: 0
                bus info: usb@2
                logical name: usb2
                version: 3.19
                capabilities: usb-3.00
                configuration: driver=hub slots=6 speed=5000Mbit/s
           *-usbhost:1
                product: xHCI Host Controller
                vendor: Linux 3.19.0-15-generic xhci-hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 3.19
                capabilities: usb-2.00
                configuration: driver=hub slots=14 speed=480Mbit/s
              *-usb:0
                   description: Mass storage device
                   product: Cruzer Glide
                   vendor: SanDisk
                   physical id: 1
                   bus info: usb@1:1
                   logical name: scsi6
                   version: 1.26
                   serial: 4C530199920222110274
                   capabilities: usb-2.00 scsi emulated scsi-host
                   configuration: driver=usb-storage maxpower=200mA speed=480Mbit/s
                 *-disk
                      description: SCSI Disk
                      product: Cruzer Glide
                      vendor: SanDisk
                      physical id: 0.0.0
                      bus info: scsi@6:0.0.0
                      logical name: /dev/sda
                      version: 1.26
                      serial: 4C530199920222110274
                      size: 29GiB (32GB)
                      capabilities: partitioned partitioned:dos
                      configuration: ansiversion=6 logicalsectorsize=512 sectorsize=512 signature=0ca475df
                    *-volume
                         description: Windows FAT volume
                         vendor: SYSLINUX
                         physical id: 1
                         bus info: scsi@6:0.0.0,1
                         logical name: /dev/sda1
                         logical name: /cdrom
                         version: FAT32
                         serial: 7a52-67f7
                         size: 29GiB
                         capacity: 29GiB
                         capabilities: primary bootable fat initialized
                         configuration: FATs=2 filesystem=fat label=UBUNTU 15_0 mount.fstype=vfat mount.options=ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro state=mounted
              *-usb:1
                   description: Generic USB device
                   product: 802.11 n WLAN
                   vendor: Ralink
                   physical id: 2
                   bus info: usb@1:2
                   version: 1.01
                   serial: 1.0
                   capabilities: usb-2.00
                   configuration: driver=rt2800usb maxpower=450mA speed=480Mbit/s
              *-usb:2
                   description: Mouse
                   product: USB-PS/2 Optical Mouse
                   vendor: Logitech
                   physical id: 5
                   bus info: usb@1:5
                   version: 11.10
                   capabilities: usb-2.00
                   configuration: driver=usbhid maxpower=98mA speed=2Mbit/s
              *-usb:3
                   description: Keyboard
                   product: ActiveJet K-2024 Multimedia Keyboard
                   vendor: Elan Microelectronics Corp.
                   physical id: e
                   bus info: usb@1:e
                   version: 1.05
                   capabilities: usb-1.10
                   configuration: driver=usbhid maxpower=100mA speed=2Mbit/s
        *-communication
             description: Communication controller
             product: 9 Series Chipset Family ME Interface #1
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei_me latency=0
             resources: irq:30 memory:f7c3d000-f7c3d00f
        *-network
             description: Ethernet interface
             product: Ethernet Connection I217-V
             vendor: Intel Corporation
             physical id: 19
             bus info: pci@0000:00:19.0
             logical name: eth0
             version: 00
             serial: fc:aa:14:7e:57:c0
             size: 1Gbit/s
             capacity: 1Gbit/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=2.3.2-k duplex=full firmware=0.13-4 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
             resources: irq:27 memory:f7c00000-f7c1ffff memory:f7c3c000-f7c3cfff ioport:f080(size=32)
        *-usb:1
             description: USB controller
             product: 9 Series Chipset Family USB EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:16 memory:f7c3b000-f7c3b3ff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 3.19.0-15-generic ehci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 3.19
                capabilities: usb-2.00
                configuration: driver=hub slots=2 speed=480Mbit/s
              *-usb
                   description: USB hub
                   vendor: Intel Corp.
                   physical id: 1
                   bus info: usb@3:1
                   version: 0.00
                   capabilities: usb-2.00
                   configuration: driver=hub slots=6 speed=480Mbit/s
        *-multimedia:1
             description: Audio device
             product: 9 Series Chipset Family HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:32 memory:f7c30000-f7c33fff
        *-pci:0
             description: PCI bridge
             product: 9 Series Chipset Family PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: d0
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24
        *-pci:1
             description: PCI bridge
             product: 9 Series Chipset Family PCI Express Root Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: d0
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25
           *-pci
                description: PCI bridge
                product: 82801 PCI Bridge
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 41
                width: 32 bits
                clock: 33MHz
                capabilities: pci pm subtractive_decode bus_master cap_list
        *-usb:2
             description: USB controller
             product: 9 Series Chipset Family USB EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:f7c3a000-f7c3a3ff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 3.19.0-15-generic ehci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 3.19
                capabilities: usb-2.00
                configuration: driver=hub slots=2 speed=480Mbit/s
              *-usb
                   description: USB hub
                   vendor: Intel Corp.
                   physical id: 1
                   bus info: usb@4:1
                   version: 0.00
                   capabilities: usb-2.00
                   configuration: driver=hub slots=8 speed=480Mbit/s
        *-isa
             description: ISA bridge
             product: 9 Series Chipset Family Z97 LPC Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-storage
             description: SATA controller
             product: 9 Series Chipset Family SATA Controller [AHCI Mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:28 ioport:f0d0(size=8) ioport:f0c0(size=4) ioport:f0b0(size=8) ioport:f0a0(size=4) ioport:f060(size=32) memory:f7c39000-f7c397ff
        *-serial UNCLAIMED
             description: SMBus
             product: 9 Series Chipset Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 00
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:f7c38000-f7c380ff ioport:f040(size=32)
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:2
       logical name: wlan0
       serial: c8:3a:35:c9:e9:b4
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt2800usb driverversion=3.19.0-15-generic firmware=0.29 ip=10.0.0.3 link=yes multicast=yes wireless=IEEE 802.11abgn
```

---

### Post by wildmanne39 on 2015-06-03
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by Anthon_Williamson on 2015-06-03
Thank you. I wasn't aware of how to do that. I'll make sure to do that for future responses.

---

### Post by chili555 on 2015-06-03
Is this helpful? [https://bbs.archlinux.org/viewtopic.php?id=191981](https://bbs.archlinux.org/viewtopic.php?id=191981)> Turns out that the problem is related to WoL, and the solution is to turn of all the WoL features in the Windows Intel driver. 

---

### Post by Anthon_Williamson on 2015-06-03
Good question considering I am currently using both but no that doesn't help. When I first put the PC together a few days ago I put Linux on it first and it had the same issue so not related to windows dual-boot. Windows was only installed a few days later when I couldn't figure out the ethernet issue myself and wanted to make sure it worked under windows.

---

### Post by chili555 on 2015-06-03
Please tell us what you mean by 'doesn't work.' The system recognizes it. Does it try to connect and fail? Does it connect and drop? Or...what?

Are there any clues in the log?```
dmesg | grep -e e100 -e eth0
```For what it's worth, Mrs. Chili has an e1000e device and I can tell you many things that *don't* work!

---

### Post by Anthon_Williamson on 2015-06-03
Well It does recognize the device and list it in the network connections. It does recognize the physical cable being connected or not and displays what I assume are normal notifications for that. Then it just seems again as far as I can tell to be in an infinite loop of trying to connect to anything else on the network. I have had Windows PCs that refuse to pull DHCP in the past so I tried manually assigning the address information for IPv4 but it didn't change the behavior at all. Currently I don't have the manual addresses applied. It is in DHCP mode right now. No internet connection and continues to show the wi-fi symbol with upward radiating pluses. I assume that means it is still trying to connect.
Also as a curiosity I tried disconnecting the router that is working as the internet gateway from the switch to see if that would change the results below and it didn't have any effect.


```
[    3.880275] e1000e: Intel(R) PRO/1000 Network Driver - 2.3.2-k
[    3.880277] e1000e: Copyright(c) 1999 - 2014 Intel Corporation.
[    3.881875] e1000e 0000:00:19.0: Interrupt Throttling Rate (ints/sec) set to dynamic conservative mode
[    4.058154] e1000e 0000:00:19.0 eth0: registered PHC clock
[    4.058157] e1000e 0000:00:19.0 eth0: (PCI Express:2.5GT/s:Width x1) fc:aa:14:7e:57:c0
[    4.058158] e1000e 0000:00:19.0 eth0: Intel(R) PRO/1000 Network Connection
[    4.058195] e1000e 0000:00:19.0 eth0: MAC: 11, PHY: 12, PBA No: FFFFFF-0FF
[   18.645637] e1000e: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx
[ 8174.928462] e1000e: eth0 NIC Link is Down
[ 8189.292803] e1000e: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx

```
Currently having to post this from my other PC after pulling stuff over on flash drive. I do have an external Wi-Fi dongle that works if I need to do updates but it is primarily used by a different device so it can't be used long term here. I always prefer wired connections anyway. Sorry I am new with this and not better able to describe the behavior. It is quite strange because I feel like I am new to PCs even through I have been working with them since DOS. Oh and I am off to work so I won't be able to run test for awhile but will definitely keep working with you. Thank you very much for your help so far.

---

### Post by chili555 on 2015-06-03
You said:> disable auto speed negotiation and force the speed down to 100Mbit. Don't remember the terminal command but it did show as forcing it down on the lights on the ethernet switch so worked as advertised but didn't fix the connection.However, the log reports:> [   18.645637] e1000e: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/TxPlease do:```
sudo ethtool -s eth0  speed 100 autoneg off
```Then, with the wireless detached, let it simmer for a few moments and check:```
dmesg | grep -e e100 -e eth0
```Unless you have rebooted, we are interested in messages after the 8189.xx timestamp.

---

### Post by Anthon_Williamson on 2015-06-04
The new lines when trying that are.

```
[83385.273680] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: None
[83385.273685] e1000e 0000:00:19.0 eth0: 10/100 speed: disabling TSO
```

Oh and just noticed that there was a new version of the driver code pushed out to the sourceforge repo. I might try seeing if I can figure out how to compile that and what result that causes later.

---

### Post by chili555 on 2015-06-05
We're you able to compile the newer version? Given a choice, I'd rather try the code from Intel rather than any second party including Sourceforge.

What is NM doing all this time?```
cat /var/log/syslog | grep -e etwork -e eth0 | tail -n20
```

---

### Post by Anthon_Williamson on 2015-06-06
Ok so several things.
First is that the new Intel driver did compile with only a catman error that according to what I found should be a issue with documentation or logs or something like that.
I loaded the new driver with modprobe and it didn't initially look to be behaving any different when I tried DHCP or manual assignment with the built in network connections GUI.
When I manually set the IP address and gateway with ifconfig I was then able to ping internal and external IPs for the first time on the wired connection. So I tried going to googles IP address in chrome and it successfully loaded their search. 
I am stuck with how to get DNS setup. Again the GUI isn't working and when I tried putting it manually into [COLOR=#000000][FONT=verdana]/etc/resolv.conf[/FONT][/COLOR] or [COLOR=#000000][FONT=verdana]/etc/network/interfaces i[/FONT][/COLOR]t wouldn't let me edit them. DHCP would be great of course but I don't mind manually assigning everything if I can do it and have it stay through reboots.

---

### Post by chili555 on 2015-06-06
You can certainly set up static IP addresses in the GUI, also known as Network Manager. Here is an example: [http://ubuntulinuxmint.org/wp-content/uploads/2010/09/setup-static-ip.jpg](http://ubuntulinuxmint.org/wp-content/uploads/2010/09/setup-static-ip.jpg)

As for DNS, usually the router's address is sufficient. I usually add a backup; 8.8.8.8, which is Google's DNS nameserver. 

Be sure to select a static IP address outside the range used by the router's DHCP server. In this example: [http://www.mindspacesolutions.com/assets/images/D-Link_Router_Config_-_DHCP.jpg](http://www.mindspacesolutions.com/assets/images/D-Link_Router_Config_-_DHCP.jpg)  the DHCP server assigns addresses from 10.1.1.2 to 10.1.1.32. I'd use a static address of x.33 or above. If you are an OCD nervous nellie like me, I'd use 10.1.1.100. Of course, substitute your details here.

---

### Post by Anthon_Williamson on 2015-06-06
I know the GUI should let you manually assign IP and DNS but it doesn't work. When I put them in using the GUI nothing happened and pings didn't work. When I assigned addresses in terminal with ifconfig it took it. The issue is that I don't think I can use ifconfig to assign DNS or at least I haven't figured out how yet. I was trying to put the 8.8.8.8 and 8.8.4.4 in either of the files for it manually but they don't seem to be editable even through all the stuff I have read elsewhere says that they should be.

---

### Post by chili555 on 2015-06-06
After you plug the details into the GUI, did you try retarting NM or the computer?```
sudo systemctl restart networking
sudo systemctl restart network-manager
```

---

### Post by Anthon_Williamson on 2015-06-07
Thank you very much. Got it solved now. Being new to Linux I didn't even think of forcing the service to restart. That worked and pulled what I had statically assigned in the GUI and it works great now gigabit and all.

So for anyone with similar problem I had to grab the driver from Intel and compile it according to the readme that comes with it. Then assign network addresses manually in the network configuration with an IP outside the range DHCP will assign and also including DNS with 8.8.8.8 being an easy one. Force the network manager service to restart with
```
sudo service network-manager restart
```
and it works from there. Sadly DHCP seems to still be missing in action but since this is an error with a desktop motherboard manual assignment isn't a big issue. I would take time to figure out DHCP if it were a mobile device.

---


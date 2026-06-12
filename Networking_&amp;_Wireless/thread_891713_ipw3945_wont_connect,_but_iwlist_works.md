---
title: "ipw3945 wont connect, but iwlist works"
date: 2008-08-16
forum: Networking &amp; Wireless
---

### Post by mkdigital on 2008-08-16
hi folks, i got a tricky wlan problem.

i got a laptop with an iwl3945 wlan card. its driver is loaded (lsmod) and also iwconfig lists it correctly.

however, if i try to get an connection with my accesspoint, it fails.

i entered:
iwconfig wlan0 essid MYAP 

and it doesnt connect. (iwconfig says zero on signal quality, link speed ...)

also i get no ip via dhclient wlan0

but now comes the interesting part:
iwlist wlan0 scanning 
correctly shows a list with nearby access points including my own.

so why cant i connect? anyone an idea?

ubuntu=8.04

---

### Post by pytheas22 on 2008-08-16
Is your network encrypted?  If so, please try disabling the encryption to see if it makes a difference.  If you still can't connect, please leave encryption disabled, try to connect again and immediately open a terminal and run these commands:
```

dmesg | grep -e iwl -e eth -e wlan
iwlist scan
```

That will help to figure out what's going on.

---

### Post by mkdigital on 2008-08-16
i tried it both: encrypted and not-encrypted, i will post the output as soon as i can

sorry, got something wrong: the driver in lsmod is not ipW, but iwl3945

---

### Post by dsr4866 on 2008-08-17
I am having the same problem with my 3945 in a gateway notebook ..it just won't connect with wpa but will connect unsecure just fine, I installed wicd and updraded the backport and tried all the fixes on the forums but no luck..it sees all the access points but won't get an i.p.   very frustrating. does any body know if I go back to an older version of Ubuntu the 3945 will work?

---

### Post by pytheas22 on 2008-08-17
> does any body know if I go back to an older version of Ubuntu the 3945 will work?

Possibly.  If the problem is a bug in the driver, then going back to a different version, or recompiling with the latest source from [http://intellinuxwireless.org/](http://intellinuxwireless.org/), should fix it.  But you should check first that the iwl3945 problem is actually the problem.  You can do so by looking at the output of:
```

dmesg | grep iwl
```

That should return error messages from the kernel related to the iwl3945 driver.  If you see anything that looks pertinent, google it.  Some of the iwl3945 problems can be solved by reloading the module with certain arguments; others are just the result of a bad build of the module.

Another solution is of course to use ndiswrapper instead of the iwl3945 driver.

---

### Post by dsr4866 on 2008-08-17
here is what I get from grep commanddsr@dsr-laptop:~$ sudo dmesg | grep iwl
[sudo] password for dsr: 
[   38.616657] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.25
[   38.616661] iwl3945: Copyright(c) 2003-2007 Intel Corporation
[   38.676425] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   38.748350] wmaster0: Selected rate control algorithm 'iwl-3945-rs'
[   39.611383] iwl3945: Tunable channels: 11 802.11bg, 13 802.11a channels
[   39.613645] Registered led device: iwl-phy0:RX
[   39.613662] Registered led device: iwl-phy0:TX
[   63.938097] Registered led device: iwl-phy0:RX
[   63.938136] Registered led device: iwl-phy0:TX
[   64.249821] Registered led device: iwl-phy0:RX
[   64.249861] Registered led device: iwl-phy0:TX
[  104.885191] Registered led device: iwl-phy0:RX
[  104.885210] Registered led device: iwl-phy0:TX
[  352.122098] Registered led device: iwl-phy0:RX
[  352.122119] Registered led device: iwl-phy0:TX
[  375.382585] Registered led device: iwl-phy0:RX
[  375.382605] Registered led device: iwl-phy0:TX
[  409.033831] Registered led device: iwl-phy0:RX
[  409.033852] Registered led device: iwl-phy0:TX
[  620.021087] Registered led device: iwl-phy0:RX
[  620.021109] Registered led device: iwl-phy0:TX
[  620.301385] Registered led device: iwl-phy0:RX
[  620.301407] Registered led device: iwl-phy0:TX
[  683.323225] Registered led device: iwl-phy0:RX
[  683.323258] Registered led device: iwl-phy0:TX
[  683.637892] Registered led device: iwl-phy0:RX
[  683.637911] Registered led device: iwl-phy0:TX
[ 2175.237562] Registered led device: iwl-phy0:RX
[ 2175.237582] Registered led device: iwl-phy0:TX
[ 2175.653287] Registered led device: iwl-phy0:RX
[ 2175.653308] Registered led device: iwl-phy0:TX
[ 2312.310528] Registered led device: iwl-phy0:RX
[ 2312.310550] Registered led device: iwl-phy0:TX
[ 2312.689379] Registered led device: iwl-phy0:RX
[ 2312.689399] Registered led device: iwl-phy0:TX
[ 2330.041628] Registered led device: iwl-phy0:RX
[ 2330.041649] Registered led device: iwl-phy0:TX
[ 2358.286803] Registered led device: iwl-phy0:RX
[ 2358.286844] Registered led device: iwl-phy0:TX
[    1.678760] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.25
[    1.678765] iwl3945: Copyright(c) 2003-2007 Intel Corporation
[    1.679373] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[    1.741437] wmaster0: Selected rate control algorithm 'iwl-3945-rs'
[    1.786108] iwl3945: Tunable channels: 11 802.11bg, 13 802.11a channels
[    1.786893] Registered led device: iwl-phy0:RX
[    1.786922] Registered led device: iwl-phy0:TX
[    2.274568] Registered led device: iwl-phy0:RX
[    2.274587] Registered led device: iwl-phy0:TX
dsr@dsr-laptop:~$ 

I am running ndis wrapper with the xp driver...Thanks for all your help as I fumble around.

---

### Post by dsr4866 on 2008-08-17
Maybe I am not running the ndis driver, is there a way to switch from the iwl3945 to ndis wrapper or am i very confused on what the system is using? or do I have to remove the iwl3945 and if so how? 


Thanks
dsr

---

### Post by pytheas22 on 2008-08-18
> Maybe I am not running the ndis driver, is there a way to switch from the iwl3945 to ndis wrapper or am i very confused on what the system is using? or do I have to remove the iwl3945 and if so how?

To see which driver you're using, run the command:
```

lshw -C Network
```

It will say something like "driver=ndiswrapper+[windows driver]" or "driver=iwl3945."  For example, here is the lshw output for my wireless card, which uses the ath_pci (madwifi) driver (which works on Atheros cards, not on Intel like you have):
```

  *-network:0             
       description: [CODE]Wireless interface
```
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications Inc.
       physical id: 1
       bus info: pci@0000:01:01.0
       logical name: wifi0
       version: 01
       serial: 00:19:e0:67:8a:f1
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes ```
driver=ath_pci
``` ip=192.168.1.3 latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g[/CODE]

If you can't figure it out, post your "lshw -C Network" output here.  When we figure out which driver your system is actually using, we can try to straighten things out.

---

### Post by dsr4866 on 2008-08-18
here is my dmesg output- thanks to all for helping this is the a nightmare. I don't have the $ to buy another card for this piece of junk!     -laptop:~$ sudo dmesg | grep iwl
[sudo] password for dsr: 
[   39.751280] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.25
[   39.751283] iwl3945: Copyright(c) 2003-2007 Intel Corporation
[   39.751949] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   39.829911] wmaster0: Selected rate control algorithm 'iwl-3945-rs'
[   40.818912] iwl3945: Tunable channels: 11 802.11bg, 13 802.11a channels
[   40.821743] Registered led device: iwl-phy0:RX
[   40.821760] Registered led device: iwl-phy0:TX
dsr@dsr-laptop:~$

---

### Post by dsr4866 on 2008-08-18
And this is what I get from lshw output:                                    dsr@dsr-laptop:~$ sudo lshw -c network
Hardware Lister (lshw) - B.02.12.01
usage: lshw [-format] [-options ...]
       lshw -version

	-version        print program version (B.02.12.01)

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
	-sanitize       sanitize output (remove sensitive information like serial numbers, etc.)

dsr@dsr-laptop:~$

---

### Post by dsr4866 on 2008-08-18
Here is my output from just lshw and it seems to me that the card is there with the linux driver?

dsr@dsr-laptop:~$ lshw 
WARNING: you should run this program as super-user.
dsr-laptop                
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 2550MiB
     *-cpu
          product: Intel(R) Core(TM)2 Duo CPU     T7100  @ 1.80GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          size: 1801MHz
          capacity: 1801MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx x86-64 constant_tsc arch_perfmon pebs bts rep_good pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm ida cpufreq
     *-pci
          description: Host bridge
          product: Mobile PM965/GM965/GL960 Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-display:0 UNCLAIMED
             description: VGA compatible controller
             product: Mobile GM965/GL960 Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: vga_controller bus_master cap_list
             configuration: latency=0
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile GM965/GL960 Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0
        *-network
             description: Ethernet interface
             product: 82566MC Gigabit Network Connection
             vendor: Intel Corporation
             physical id: 19
             bus info: pci@0000:00:19.0
             logical name: eth0
             version: 03
             serial: 00:e0:b8:cb:f6:b5
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical
             configuration: broadcast=yes driver=e1000 driverversion=7.3.20-k2-NAPI firmware=0.3-0 ip=192.168.1.103 latency=0 module=e1000 multicast=yes
        *-usb:0
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-multimedia
             description: Audio device
             product: 82801H (ICH8 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel
        *-pci:0
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Wireless interface
                product: PRO/Wireless 3945ABG Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wmaster0
                version: 02
                serial: 00:1b:77:40:5a:d1
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g
        *-usb:3
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:5
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:6
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:1
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: f3
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
           *-pcmcia
                description: CardBus bridge
                product: PCIxx12 Cardbus Controller
                vendor: Texas Instruments
                physical id: 9
                bus info: pci@0000:03:09.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192 module=yenta_socket
           *-firewire
                description: FireWire (IEEE 1394)
                product: PCIxx12 OHCI Compliant IEEE 1394 Host Controller
                vendor: Texas Instruments
                physical id: 9.1
                bus info: pci@0000:03:09.1
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: ohci bus_master cap_list
                configuration: driver=ohci1394 latency=32 maxlatency=4 mingnt=2 module=ohci1394
           *-storage
                description: Mass storage controller
                product: 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
                vendor: Texas Instruments
                physical id: 9.2
                bus info: pci@0000:03:09.2
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: storage bus_master cap_list
                configuration: driver=tifm_7xx1 latency=57 maxlatency=4 mingnt=7 module=tifm_7xx1
           *-system
                description: SD Host controller
                product: PCIxx12 SDA Standard Compliant SD Host Controller
                vendor: Texas Instruments
                physical id: 9.3
                bus info: pci@0000:03:09.3
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=sdhci latency=57 maxlatency=4 mingnt=7 module=sdhci
           *-communication UNCLAIMED
                description: Communication controller
                product: PCIxx12 GemCore based SmartCard controller
                vendor: Texas Instruments
                physical id: 9.4
                bus info: pci@0000:03:09.4
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: cap_list
                configuration: latency=0
        *-isa
             description: ISA bridge
             product: 82801HEM (ICH8M) LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0 module=ata_piix
        *-storage
             description: SATA controller
             product: 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: storage ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0 module=ahci
        *-serial UNCLAIMED
             description: SMBus
             product: 82801H (ICH8 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 03
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
dsr@dsr-laptop:~$ sudo l

---

### Post by pytheas22 on 2008-08-18
> *-network
description: Wireless interface
product: PRO/Wireless 3945ABG Network Connection
vendor: Intel Corporation
physical id: 0
bus info: pci@0000:02:00.0
logical name: wmaster0
version: 02
serial: 00:1b:77:40:5a:d1
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list logical ethernet physical wireless
configuration: broadcast=yes **driver=iwl3945** latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g

Alright, so you're using iwl3945 now, not ndiswrapper.  With iwl3945 are you still unable to connect to WPA?  If so, could you please try connecting, and then (and only then, because we need to see the information after you try to connect) post the output of:
```

dmesg | grep -e iwl -e wlan -e eth -e ndis
```

Also, you may want to see if you have better luck connecting using [wicd]("http://wicd.sourceforge.net").  A lot of people do.

---

### Post by micder on 2008-08-19
Have exactly the same problem with iwl3945.
iwlist wlan0 scan and wpa_passphrase essid passwrd make clear that I get signal and show my psk.
I'm not familiar with Ubuntu.
In Slack I could edit the req'rd script files to get my wireless up.
Which files define networking in Ubuntu, that I could edit?

---

### Post by pytheas22 on 2008-08-19
> Which files define networking in Ubuntu, that I could edit?

If you're using Network Manager (the default wireless client), there are no files you can edit as it does WPA negotiation on-the-fly.  You can edit /etc/wpa_supplicant.conf if you want to connect to WPA manually, but you shouldn't have to do that.

You may want to try [wicd]("http://wicd.sourceforge.net") to see if that will connect you.  If not, please try connecting, and then immediately post the output of:
```

dmesg | grep iwl
```

---

### Post by micder on 2008-08-19
Thank you.
> You can edit /etc/wpa_supplicant.conf if you want to connect to WPA manually
Thats my problem: did not find this file.
Which packages do I have to download, transfer to Ubuntu and install on the commandline?

---

### Post by pytheas22 on 2008-08-19
> Thats my problem: did not find this file.
Which packages do I have to download, transfer to Ubuntu and install on the commandline?

The file actually may not exist by default, because nothing that comes by default on Ubuntu actually uses /etc/wpa_supplicant.conf, since Network Manager does the WPA negotiation on-the-fly, without looking at any configuration file.

But wpa_supplicant should be installed by default, I think.  Type "wpa_supplicant" at a command-prompt to check.  If it's not installed, you can get it with:
```

sudo apt-get install wpasupplicant
```

(there's no underscore in the name of the package, even though there is an underscore in the executable's name)

Once you get wpa_supplicant installed, create the configuration file for your network at /etc/wpa_supplicant.conf, then try connecting from the command-line with a command like:
```

sudo wpa_supplicant -w -Dwext -iwlan0 -c/etc/wpa_supplicant.conf
sudo dhclient wlan0
```

I imagine that wpa_supplicant works mostly the same in Ubuntu as in other distributions, but there's a guide [here]("http://ubuntuforums.org/showthread.php?t=571188") that might help you if not. 

If you do manage to connect from the command-line, you'll have to write a script or something if you want to connect automatically, because as far as I know there's no way to tell Network Manager to use the wpa_supplicant configuration that you specify.  Or use wicd (which might solve the whole problem to begin with, and which I would recommend at least trying once before you dive in to the wpa_supplicant hacking).

---

### Post by dsr4866 on 2008-08-20
here is the ouput  -e with the iwl after trying to connect  dsr@dsr-laptop:~$ sudo dmesg | grep -e iwl -e wlan -e eth
[   29.393820] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
[   32.188999] Driver 'sd' needs updating - please use bus_type methods
[   32.811132] Driver 'sr' needs updating - please use bus_type methods
[   41.431017] e1000: eth0: e1000_watchdog: NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[   41.431022] e1000: eth0: e1000_watchdog: 10/100 speed: disabling TSO
[   42.022766] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.25
[   42.022770] iwl3945: Copyright(c) 2003-2007 Intel Corporation
[   42.174235] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   42.277503] wmaster0: Selected rate control algorithm 'iwl-3945-rs'
[   43.932967] iwl3945: Tunable channels: 11 802.11bg, 13 802.11a channels
[   43.935221] Registered led device: iwl-phy0:RX
[   43.935238] Registered led device: iwl-phy0:TX
[   46.044773] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   56.702699] eth0: no IPv6 routers present
[ 1100.556966] Registered led device: iwl-phy0:RX
[ 1100.556986] Registered led device: iwl-phy0:TX
[ 1100.568537] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1100.832893] Registered led device: iwl-phy0:RX
[ 1100.832913] Registered led device: iwl-phy0:TX
[ 1100.844383] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1729.104845] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 1730.658945] e1000: eth0: e1000_watchdog: NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1730.658956] e1000: eth0: e1000_watchdog: 10/100 speed: disabling TSO
[ 1730.671870] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 1735.356111] Registered led device: iwl-phy0:RX
[ 1735.356132] Registered led device: iwl-phy0:TX
[ 1735.368175] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1740.894436] eth0: no IPv6 routers present
[ 1816.281867] Registered led device: iwl-phy0:RX
[ 1816.281886] Registered led device: iwl-phy0:TX
[ 1816.294337] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1816.561603] Registered led device: iwl-phy0:RX
[ 1816.561624] Registered led device: iwl-phy0:TX
[ 1816.574082] ADDRCONF(NETDEV_UP): wlan0: link is not ready
dsr@dsr-laptop:~$

---

### Post by micder on 2008-08-20
Thank you Pytheas22.

Installed wpasupplicant and created wpa_supplicant.conf.
Contents of that file equal to the one in Slack.
```
sudo wpa_supplicant -w -Dwext -iwlan0 -c/etc/wpa_supplicant.conf
Trying to associate with 00:1d:7e:fb:59:08 (SSID='linksys' freq=2462 MHz)
Associated with 00:1d:7e:fb:59:08
WPA: Key negotiation completed with 00:1d:7e:fb:59:08 [PTK=CCMP GTK=TKIP]
CTRL-EVENT-CONNECTED - Connection to 00:1d:7e:fb:59:08 completed (auth) [id=0 id_str=]

```
Command prompt does not come back after a minute; So Ctrl+C.
```
dhclient wlan0:

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:1f:3c:16:7b:5a
Sending on   LPF/wlan0/00:1f:3c:16:7b:5a
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```
DHCP_TIMEOUT problem?

---

### Post by dsr4866 on 2008-08-20
I have changed to Wicd and find it better than netmanager but still can't connect to wpa. I watch with Kwifi and i can see the it scans  and see all access points and gets channel 6 which is what my router is on  and then fails to get ip address .

---

### Post by pytheas22 on 2008-08-20
micder,

Yeah, that's strange.  It looks like the WPA authentication completes without a problem so I don't know why it doesn't want to get an IP.  Did you try dhclient a few times, and are you sure that you're within good range of the router?  You may also want to try using dhclient3, another dhcp client that comes with Ubuntu by default.

Did you use dhclient under Slackware or something else?

dsr4866,

You're able to connect to non-encrypted networks and WEP, right?  Also, could you please post the output of:
```

iwlist scan
```

and tell us what the name of the network you're trying to connect to is?

I unfortunately don't see anything in dmesg indicating what's wrong.  Maybe using ndiswrapper again would help but I don't know.  I'm wondering if the issue is with your router--you're sure it's set up properly to serve IP addresses via dhcp, right?

You could also try [connecting manually from the command-line]("http://ubuntuforums.org/showthread.php?t=571188") if you have the time to invest in that.  Doing WPA manually is not really a good time, in my opinion, but at least it would help figure out whether the problem lies with the wireless clients (NM and wicd) that you're trying to use to connect, or something else.

---

### Post by kiloraw on 2008-08-20
He guys I am fairly new to Ubuntu too. But i do mess around with the wireless's cards alot.  I have the 3945 to...and it sucks over all. But with Ubuntu's Network manager it gave me hell to connect with the 3945. So I purged out the network manager and started using Wicd manager and the next thing I know I am connected. Just google wicd and the site should give you complete set of instruction of how to install it. Plus I think its on Ubuntu forums too. I would try that out first before loading a older kernel.

---

### Post by pdk on 2008-08-20
I have just loaded Hardy Heron 8.04. I have an rt2500 compatable wireless card which is working when I boot from windows 2000, so I can see signal strength etc. I also had minimal problems with Ubuntu 6.01. 
I have checked that all the correct drivers are present and the network manager beacon is a shining Blue. ifconfig shows the wlan0 details including the mac address. No signal atall, cannor connect.
Do I have to resort to ndiswrapper to solve this problem ????
Tt seems there must be a sneaky problem here and I don't know the answer. Incidently iwlist scan gives  ,,, 'no scan'
Any more help ????
Peter

---

### Post by pytheas22 on 2008-08-20
> 
I have just loaded Hardy Heron 8.04. I have an rt2500 compatable wireless card which is working when I boot from windows 2000, so I can see signal strength etc. I also had minimal problems with Ubuntu 6.01.
I have checked that all the correct drivers are present and the network manager beacon is a shining Blue. ifconfig shows the wlan0 details including the mac address. No signal atall, cannor connect.
Do I have to resort to ndiswrapper to solve this problem ????
Tt seems there must be a sneaky problem here and I don't know the answer. Incidently iwlist scan gives ,,, 'no scan'
Any more help ????
Peter

Peter,

You may want to start a new thread since your card has an rt2500 (Ralink) chipset; the iwl3945 (Intel) of the other posters here is very different.

Anyway, the reason your card won't work is probably that there are two sets of Ralink drivers--legacy and next-generation.  By default Ubuntu uses the next-generation ones, which will have fancy features (like support for master mode, so you can use your computer as a router) when they're done, but they're still being developed and therefore aren't always as stable as we'd like.  The legacy drivers, however, are tried and true and usually work very well for normal managed connections.  To switch to them, run these commands (they assume that you are connected via ethernet for the time being; if you can't do that, let me know and we can work around it):
```

sudo -s
apt-get install build-essential rutilt
echo 'blacklist rt2500usb' >> /etc/modprobe.d/blacklist
echo 'blacklist rt2500pci' >> /etc/modprobe.d/blacklist
echo 'blacklist rt61pci' >> /etc/modprobe.d/blacklist
echo 'blacklist rt2x00pci' >> /etc/modprobe.d/blacklist
echo 'blacklist rt2400pci' >> /etc/modprobe.d/blacklist
echo 'blacklist rt2x00lib' >> /etc/modprobe.d/blacklist
echo 'blacklist rt2x00usb' >> /etc/modprobe.d/blacklist
wget http://rt2x00.serialmonkey.com/rt2500-cvs-daily.tar.gz
tar -xzvf rt*
cd rt*/Module
make
make install
```

Then reboot; the wireless should work.  However note that you can't use Network Manager to connect because it doesn't like the Ralink legacy drivers.  You need to use Rutilt, which will be installed at System>Administration>Rutilt WLAN Manager.

If that doesn't solve the problem, please start a new thread and let us know the URL.  In the new thread, please include the output of the following:
```

lshw -C Network
lsusb | grep -i ralink
lspci -nn | grep -i ralink
```

You could use ndiswrapper as well, but there shouldn't be a reason to, as Ralink has very good native Linux support (Ralink released documentation and drivers under the GPL a long time ago).

---

### Post by micder on 2008-08-21
Thank you Pytheas22.

Wireless works perfect with Slack, Mandriva and Windooz.
Installed dhcommon3 and dhclient3 and upgraded to the latest iwl3945 from Intel to no avail.
Started then to work according How To: Manual Network Configuration without the need for Network Manager.
Executed following script
```
# By default this script does nothing.
ifconfig eth0 down
ifconfig wlan0 down
dhclient -r wlan0
iwconfig wlan0 essid "linksys"
iwconfig wlan0 mode Managed
ifconfig wsultlan0 up
dhclient wlan0

wpa_supplicant -w -Dwext -iwlan0 -c/etc/wpa_supplicant.conf
dhclient wlan0

exit 0

```
Result:
```
eth0: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:1f:3c:16:7b:5a
Sending on   LPF/wlan0/00:1f:3c:16:7b:5a
Sending on   Socket/fallback
There is already a pid file /var/run/dhclient.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:1f:3c:16:7b:5a
Sending on   LPF/wlan0/00:1f:3c:16:7b:5a
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
Trying to associate with 00:1d:7e:fb:59:08 (SSID='linksys' freq=2462 MHz)
Associated with 00:1d:7e:fb:59:08
WPA: Key negotiation completed with 00:1d:7e:fb:59:08 [PTK=CCMP GTK=TKIP]
CTRL-EVENT-CONNECTED - Connection to 00:1d:7e:fb:59:08 completed (auth) [id=0 id_str=]
CTRL-EVENT-TERMINATING - signal 2 received

```

ifconfig -a is different then
```
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:376 (376.0 B)  TX bytes:376 (376.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1f:3c:16:7b:5a
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:9 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1227 (1.1 KB)  TX bytes:1723 (1.6 KB)

wlan0:avahi Link encap:Ethernet  HWaddr 00:1f:3c:16:7b:5a
          inet addr:169.254.4.136  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

wmaster0  Link encap:UNSPEC  HWaddr 00-1F-3C-16-7B-5A-00-00-00-00-00-00-00-00-00-00
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```
:confused:

---

### Post by pytheas22 on 2008-08-21
Try changing the script to this:
```

# By default this script does nothing.
ifconfig eth0 down
ifconfig wlan0 down
dhclient -r wlan0
iwconfig wlan0 essid "linksys"
iwconfig wlan0 mode Managed
ifconfig wlan0 up
killall dhclient
dhclient wlan0

wpa_supplicant -w -Dwext -iwlan0 -c/etc/wpa_supplicant.conf
dhclient wlan0

exit 0
```

And let it run all the way--it looks from the output above like you stopped it with control-C after the WPA negotiation.  It needs to run dhclient after the WPA negotiation.

Please let me know if that makes a difference.

---

### Post by dsr4866 on 2008-08-21
Hey Pytheas22, Thanks again for the help.. I worked on this too late into the morning was somewhere with the ndis driver and doing some commands when it finally locked on to my router with access point and ip  ( watching Kwifiman.) I think it has something to do with network man with iwl3945  vs. wicd and ndis  anyway I started cleaning up the stuff all over and erased netman and lost the whole game, just too tired..I couldnt seem to load back just netman and gave up and reloading 8.04  all over. [I] am sure that the key is to get rid of this iwl3945 driver thats bugged up and run with ndis and wcid . My question is will the ndis take over if i load it up now or do I have to manually remove iwl3945. I am not sure of what proccesses are going on and if I bring up the package with wicd will it take over from netmanger or do I have to remove it also..thats what iwas trying to do when I screwed everything thing up last time. 

thanks

---

### Post by pdk on 2008-08-21
> **pytheas22 said:**
> Peter,

You may want to start a new thread since your card has an rt2500 (Ralink) chipset; the iwl3945 (Intel) of the other posters here is very different.

Anyway, the reason your card won't work is probably that there are two sets of Ralink drivers--legacy and next-generation.  By default Ubuntu uses the next-generation ones, which will have fancy features (like support for master mode, so you can use your computer as a router) when they're done, but they're still being developed and therefore aren't always as stable as we'd like.  The legacy drivers, however, are tried and true and usually work very well for normal managed connections.  To switch to them, run these commands (they assume that you are connected via ethernet for the time being; if you can't do that, let me know and we can work around it):
```

sudo -s
apt-get install build-essential rutilt
echo 'blacklist rt2500usb' >> /etc/modprobe.d/blacklist
echo 'blacklist rt2500pci' >> /etc/modprobe.d/blacklist
echo 'blacklist rt61pci' >> /etc/modprobe.d/blacklist
echo 'blacklist rt2x00pci' >> /etc/modprobe.d/blacklist
echo 'blacklist rt2400pci' >> /etc/modprobe.d/blacklist
echo 'blacklist rt2x00lib' >> /etc/modprobe.d/blacklist
echo 'blacklist rt2x00usb' >> /etc/modprobe.d/blacklist
wget http://rt2x00.serialmonkey.com/rt2500-cvs-daily.tar.gz
tar -xzvf rt*
cd rt*/Module
make
make install
```

Then reboot; the wireless should work.  However note that you can't use Network Manager to connect because it doesn't like the Ralink legacy drivers.  You need to use Rutilt, which will be installed at System>Administration>Rutilt WLAN Manager.

If that doesn't solve the problem, please start a new thread and let us know the URL.  In the new thread, please include the output of the following:
```

lshw -C Network
lsusb | grep -i ralink
lspci -nn | grep -i ralink
```

You could use ndiswrapper as well, but there shouldn't be a reason to, as Ralink has very good native Linux support (Ralink released documentation and drivers under the GPL a long time ago).

Thanks for that fabulous and prompt reply. I had downloaded a document from the ubuntu forums when I first loaded ubuntu 6.06 well over a year ago. I have just downloaded the driver and compiled it. Then I wanted to try and get some response from the web. It seemed that a new version would have solved my wireless problem.
I will follow your instruction and although I am not connected using ubuntu 8.04 but can reboot and get there via windows (it is useful sometimes). I think I can figure out what you are saying.
There was a thread started and ended in sept 2007 which is very relevant  HOWTO: RT2500, etc. wireless cards so perhaps I should start a new one and reference the old one ? I'm not clued up on how to use the forum as yet.
Rather than clutter the forum you could mail me at [email]pdk.knight@gmail.com[/email], and when I have got it going I will set up the new thread with the info.
Peter

---

### Post by pytheas22 on 2008-08-21
> My question is will the ndis take over if i load it up now or do I have to manually remove iwl3945. I am not sure of what proccesses are going on and if I bring up the package with wicd will it take over from netmanger or do I have to remove it also..thats what iwas trying to do when I screwed everything thing up last time.

Good questions.  By default, the iwl3945 driver will control your card, even if ndiswrapper is installed and properly configured.  If you want to drive the card with ndiswrapper instead, you have to add iwl3945 to the blacklist:
```
echo 'blacklist iwl3945' | sudo tee -a /etc/modprobe.d/blacklist
```

Then, after a reboot, ndiswrapper should be in charge of your card.  You can check with the command:
```

lsmod | grep iwl3945
```

If that returns nothing but a blank line, then iwl3945 has been successfully blacklisted.  Sometimes weird stuff happens and iwl3945 stays active even though it's on the blacklist; if that's your case, let me know; there are other ways to get rid of iwl3945.

As for wicd vs. Network Manager: when you install wicd, it should force you to uninstall NM, and vice versa.  If for some reason it doesn't, you can uninstall NM with:
```

sudo apt-get remove network-manager
```

(to reinstall: "sudo apt-get install network-manager-gnome" or "sudo apt-get install network-manager-kde")

I hope this helps.  If you were connected successfully before with ndiswrapper, I'd try these steps to get back to there:

1. install ndiswrapper and load the Windows drivers for your card
2. blacklist iwl3945
3. install wicd
4. reboot and try connecting via wicd

---

### Post by dsr4866 on 2008-08-21
here is what is driving me nuts! ..it looks like iwl3945 is working  0726 is my router   is there a problem with my wpa supplicant? or should I quit screwing around and go with ndis...I just hate it when there is some little thing messing up the whole works and I can't find it. I just don't know how this stuff works.          dsr@dsr-laptop:~$ sudo wpa_supplicant
wpa_supplicant v0.5.8
Copyright (c) 2003-2007, Jouni Malinen <j@w1.fi> and contributors

This program is free software. You can distribute it and/or modify it
under the terms of the GNU General Public License version 2.

Alternatively, this software may be distributed under the terms of the
BSD license. See README and COPYING for more details.

This product includes software developed by the OpenSSL Project
for use in the OpenSSL Toolkit ([http://www.openssl.org/](http://www.openssl.org/))

usage:
  wpa_supplicant [-BddehLqquvwW] [-P<pid file>] [-g<global ctrl>] \
        -i<ifname> -c<config file> [-C<ctrl>] [-D<driver>] [-p<driver_param>] \
        [-b<br_ifname> [-N -i<ifname> -c<conf> [-C<ctrl>] [-D<driver>] \
        [-p<driver_param>] [-b<br_ifname>] ...]

drivers:
  wext = Linux wireless extensions (generic)
  hostap = Host AP driver (Intersil Prism2/2.5/3)
  madwifi = MADWIFI 802.11 support (Atheros, etc.)
  atmel = ATMEL AT76C5XXx (USB, PCMCIA)
  ndiswrapper = Linux ndiswrapper
  ipw = Intel ipw2100/2200 driver (old; use wext with Linux 2.6.13 or newer)
  wired = wpa_supplicant wired Ethernet driver
  test = wpa_supplicant test driver
options:
  -b = optional bridge interface name
  -B = run daemon in the background
  -c = Configuration file
  -C = ctrl_interface parameter (only used if -c is not)
  -i = interface name
  -d = increase debugging verbosity (-dd even more)
  -D = driver name
  -g = global ctrl_interface
  -K = include keys (passwords, etc.) in debug output
  -t = include timestamp in debug messages
  -h = show this help text
  -L = show license (GPL and BSD)
  -p = driver parameters
  -P = PID file
  -q = decrease debugging verbosity (-qq even less)
  -u = enable DBus control interface
  -v = show version
  -w = wait for interface to be added, if needed
  -W = wait for a control interface monitor before starting
  -N = start describing new interface
example:
  wpa_supplicant -Dwext -iwlan0 -c/etc/wpa_supplicant.conf
dsr@dsr-laptop:~$ sudo wpa_supplicant -w -Dwext -iwlan0 -c/ect/wpa_supplicant.conf
Failed to read or parse configuration '/ect/wpa_supplicant.conf'.
dsr@dsr-laptop:~$ sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

dsr@dsr-laptop:~$ sudo iwlist scandsr@dsr-laptop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1D:7E:BE:B2:BB
                    ESSID:"0726"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=97/100  Signal level:-28 dBm  Noise level=-69 dBm
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=0000008c6a6624d6
                    Extra: Last beacon: 8ms ago
          Cell 02 - Address: 00:14:95:05:96:E1
                    ESSID:"2WIRE659"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=35/100  Signal level:-88 dBm  Noise level=-69 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=00000017e98ba181
                    Extra: Last beacon: 3612ms ago
          Cell 03 - Address: 00:1C:B3:AF:86:EB
                    ESSID:"Apple Network af86eb"
                    Mode:Master
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=38/100  Signal level:-86 dBm  Noise level=-69 dBm
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=0000019f4c7c5180
                    Extra: Last beacon: 2652ms ago

dsr@dsr-laptop:~$ 


lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1D:7E:BE:B2:BB
                    ESSID:"0726"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=97/100  Signal level:-28 dBm  Noise level=-69 dBm
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=0000008c6a6624d6
                    Extra: Last beacon: 8ms ago
          Cell 02 - Address: 00:14:95:05:96:E1
                    ESSID:"2WIRE659"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=35/100  Signal level:-88 dBm  Noise level=-69 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=00000017e98ba181
                    Extra: Last beacon: 3612ms ago
          Cell 03 - Address: 00:1C:B3:AF:86:EB
                    ESSID:"Apple Network af86eb"
                    Mode:Master
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=38/100  Signal level:-86 dBm  Noise level=-69 dBm
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=0000019f4c7c5180
                    Extra: Last beacon: 2652ms ago

dsr@dsr-laptop:~$

---

### Post by pytheas22 on 2008-08-21
Yes, sometimes it happens that you can see networks without a problem but you can't really connect for some reason--so don't assume that because the iwl3945 driver can see your router that it can also necessarily connect to it.  It may be possible to make iwl3945 connect by hand if you hack wpa_supplicant, but take my word for it that fighting with wpa_supplicant is not a good time (if you really want to try, [this thread]("ubuntuforums.org/showthread.php?t=571188") shows how to do wpa_supplicant manually).

If you're sure that you were using ndiswrapper when you were able to connect successfully yesterday, then I'd stick with that--at least you know that ndiswrapper works.  I think it would be a simpler solution.  Make sure that iwl3945 is blacklisted and that ndiswrapper is loaded with the Windows drivers, and see if you can connect then.

---

### Post by dsr4866 on 2008-08-21
Pytheas22...you sir are my hero..I am now online wireless! the combination of Wicd and ndis with the correct win driver worked. I guess the iwl3945 is too bugged right now.  I didn't have to blacklist iwl3945 just had to makesure I rebooted after loading wicd and add my passphrase to it's config. there was a problem getting the inf driver w29n51.inf because there are two versions it seems one from intel and one for this junkbox Gateway m475. it was a long hard slog but i learned alot...my thanks again

David

---

### Post by pytheas22 on 2008-08-21
I'm glad it worked.

There seems to be a plethora of issues with iwl3945 on the forums lately, so it seems that something is going on.  I think we need to make sure that updates are getting tested before we push them out, because this seems to be a recurring problem with the iwl3945 and iwl4965 drivers.  But at least ndiswrapper is there to fall back on.

---

### Post by micder on 2008-08-22
Writing this post from Ubuntu:)
Thank you very much Pytheas22!

rc.local with the addition as you suggested is executed at startup and does not change anything:no wireless.
I then execute rc.local again from konsole.```
sudo sh rc.local
[sudo] password for giel:
eth0: ERROR while getting interface flags: No such device
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:1f:3c:16:7b:5a
Sending on   LPF/wlan0/00:1f:3c:16:7b:5a
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 192.168.1.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
dhclient: no process killed
There is already a pid file /var/run/dhclient.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:1f:3c:16:7b:5a
Sending on   LPF/wlan0/00:1f:3c:16:7b:5a
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
Trying to associate with 00:1d:7e:fb:59:08 (SSID='linksys' freq=2462 MHz)
Associated with 00:1d:7e:fb:59:08
WPA: Key negotiation completed with 00:1d:7e:fb:59:08 [PTK=CCMP GTK=TKIP]

```

The script does not exit and there is no wireless.
I then execute dhclient wlan0 from another konsole:
ifconfig gives```
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:376 (376.0 B)  TX bytes:376 (376.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1f:3c:16:7b:5a
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1649 (1.6 KB)  TX bytes:4897 (4.7 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1F-3C-16-7B-5A-00-00-00-00-00-00-00-00-00-00
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```
Now I have connection
ps aux gives```
root      6109  0.0  0.0   1772   488 pts/2    S+   11:55   0:00 sh rc.local
root      6185  0.0  0.0   4096  1712 pts/2    S+   11:56   0:00 wpa_supplicant -w -Dwext -iwlan0 -c/etc/wpa_supplicant.conf
giel      6755  0.0  0.4  32120 14148 ?        R    12:08   0:00 konsole [kdeinit]
giel      6756  0.0  0.0   5644  3048 pts/3    Ss   12:08   0:00 /bin/bash
dhcp      6912  0.0  0.0   2440   548 ?         Ss   12:11   0:00 dhclient wlan0
```
See what happens when I kill rc.local
Closed browser, killed rc.local and I'm back again.
Will now kill wap_supplicant.
Back again :-)
Any idea how to connect automatically at startup?

Anyhow thanks alot!

---

### Post by micder on 2008-08-22
This Ubuntu is LTS;so I like to keep trying.
I was online as said above and used the opportunity to update and upgrade.
After booting again executed rc.local and dhclient wlan0.
Have connection and can ping my provider:
```
wlan0     Link encap:Ethernet  HWaddr 00:1f:3c:16:7b:5a
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1649 (1.6 KB)  TX bytes:4136 (4.0 KB)

ping -c 2 212.115.192.195
PING 212.115.192.195 (212.115.192.195) 56(84) bytes of data.
64 bytes from 212.115.192.195: icmp_seq=1 ttl=60 time=40.4 ms
64 bytes from 212.115.192.195: icmp_seq=2 ttl=60 time=10.0 ms

``` 
but can't use my browser: > Try again:confused:
Thank you.

---

### Post by pytheas22 on 2008-08-22
@micder,

So just to clarify: you run this script:
```

# By default this script does nothing.
ifconfig eth0 down
ifconfig wlan0 down
dhclient -r wlan0
iwconfig wlan0 essid "linksys"
iwconfig wlan0 mode Managed
ifconfig wlan0 up
killall dhclient
dhclient wlan0

wpa_supplicant -w -Dwext -iwlan0 -c/etc/wpa_supplicant.conf
dhclient wlan0

exit 0
```

and then in another terminal, you run:
```

sudo dhclient wlan0
```

and you get connected?  Does this command work to connect you:

```
sudo wpa_supplicant -w -Dwext -iwlan0 -c/etc/wpa_supplicant.conf && sudo dhclient wlan0
```

---

As for the inability to open web pages: it sounds like a DNS issue.  What is the output of:
```

cat /etc/resolv.conf
```

And if you type "72.14.207.99" into your browser address bar, what happens?

I think we're close to a solution but just need to clean a few things up; then we can write a script to deal with all this stuff automatically and you should not have to think about wireless anymore :)

---

### Post by micder on 2008-08-23
Thank you for your patience Pytheas22!
Yes I run exactly that script and dhclient wlan0 (in another term) and get connection.
Running
```
sudo wpa_supplicant -w -Dwext -iwlan0 -c/etc/wpa_supplicant.conf && sudo dhclient wlan0
```
gives:
```
Trying to associate with 00:1d:7e:fb:59:08 (SSID='linksys' freq=2462 MHz)
Associated with 00:1d:7e:fb:59:08
WPA: Key negotiation completed with 00:1d:7e:fb:59:08 [PTK=CCMP GTK=TKIP]
CTRL-EVENT-CONNECTED - Connection to 00:1d:7e:fb:59:08 completed (auth) [id=0 id_str=]


```ifconfig gives no connection.
I then run dhclient wlan0 in another terminal,with this result:
```
wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:1f:3c:16:7b:5a
Sending on   LPF/wlan0/00:1f:3c:16:7b:5a
Sending on   Socket/fallback
DHCPREQUEST of 192.168.1.101 on wlan0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.101 from 192.168.1.1
bound to 192.168.1.101 -- renewal in 40535 seconds.
```
and ifconfig gives```
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:100 (100.0 B)  TX bytes:100 (100.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1f:3c:16:7b:5a
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:999 (999.0 B)  TX bytes:4076 (3.9 KB)

```
However no internet with Firefox
My resolv.conf reads:
```
search zeelandnet.nl
nameserver 212.115.192.195
nameserver 62.238.255.196

```zeelandnet is my provider
and
```
ping -c 2 212.115.192.195
PING 212.115.192.195 (212.115.192.195) 56(84) bytes of data.
64 bytes from 212.115.192.195: icmp_seq=1 ttl=60 time=24.8 ms
64 bytes from 212.115.192.195: icmp_seq=2 ttl=60 time=15.1 ms

--- 212.115.192.195 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 15.185/20.009/24.833/4.824 ms

```
Firefox gives no connection with [http://72.14.207.99/](http://72.14.207.99/)

---

### Post by pytheas22 on 2008-08-23
There are still some strange things going on, but give these things a try.

First, does this command get you connected?
```

sudo wpa_supplicant -w -Dwext -iwlan0 -c/etc/wpa_supplicant.conf; sleep 30; sudo dhclient wlan0
```

Second, I don't know why you can't access web pages.  Can you ping sites by name (not IP), e.g.:
```

ping google.com
ping ubuntu.com
```

Also, are you sure that your http port (80) is open?  Unless you explicitly closed it for some reason, it should be.

Finally, can you use other Internet services, like ssh or ftp?  If you don't have any ssh servers to connect to, send me a private message and I'll give you credentials to try connecting to mine.

---

### Post by micder on 2008-08-23
```
sudo wpa_supplicant -w -Dwext -iwlan0 -c/etc/wpa_supplicant.conf; sleep 30; sudo dhclient wlan0
```
does not change anything, ps aux shows (after more than a minute) only wpa_supplicant, no dhclient.
"As usual:-)" dhclient has to be started separately.
I can ping sites by name:```
ping -c 2 google.com
PING google.com (64.233.187.99) 56(84) bytes of data.
64 bytes from jc-in-f99.google.com (64.233.187.99): icmp_seq=1 ttl=245 time=111 ms
64 bytes from jc-in-f99.google.com (64.233.187.99): icmp_seq=2 ttl=245 time=109 ms

--- google.com ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 109.315/110.584/111.853/1.269 ms
giel@giel-laptop:~$ ping -c 2 ubuntu.com
PING ubuntu.com (91.189.94.250) 56(84) bytes of data.
64 bytes from jujube.canonical.com (91.189.94.250): icmp_seq=1 ttl=52 time=27.1 ms
64 bytes from jujube.canonical.com (91.189.94.250): icmp_seq=2 ttl=52 time=24.1 ms

--- ubuntu.com ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 24.189/25.694/27.199/1.505 ms
```Yes I connected succesfully with [ftp://ftp.de-mirror.org/linuxpackages/Slackware/Slackware-12.1](ftp://ftp.de-mirror.org/linuxpackages/Slackware/Slackware-12.1)
And surprise surprise.., while using Konqueror with the history sidebar on, I clicked on ubuntuforums and am posting now:-)
:confused:

After closing Konqueror,I started Firefox(3.0.1), but could not connect.
Before pinging I used Firefox (100% sure).
Used Firefox in attempts to connect upto now.
So something must be wrong with Firefox, I guess.
Using Konqueror now again
Concluding (correct me if I'm wrong):
Wireless is on after running wpa_supplicant and dhclient.
A more elegant way to get connection would be nice.

Anyhow, Thanks again Pytheas22!

---

### Post by pytheas22 on 2008-08-24
micder,

I thought about this for a while.  It seems like you can only get an IP address via dhclient when dhclient is run in a separate shell from wpa_supplicant.  I have no idea why this would be necessary, but it's the only thing that makes sense to me.

If that conclusion is correct, then the trick to scripting an automatic solution for you to get online is going to be to figure out how to call wpa_supplicant in one shell and dhclient in another, at the same (or approximately same) time.

I don't know very much about bash programming, but I think that if you call a script from a terminal, it executes the script in a subshell of that terminal.  So, in principle, if you wrote two scripts: 1) to call wpa_supplicant; and 2) to call dhclient, and ran them both from within an x-terminal at the same time, then they would each execute in separate shells, which would hopefully allow dhclient to work.  So give this a try:

First, create two scripts, wpa_supplicant.sh and dhclient.sh.  Fill them in appropriately to run the commands you need, and remember to chmod +x them so they're executable (I assume you know how to write scripts since you seem to have quite a bit of Linux experience, but if you need help let me know).  You may want to start the dhclient script with "sleep 20" or something so that it will pause for a little while, giving wpa_supplicant time to negotiate an association.

Then open a terminal, log in as root ('sudo -s') (just for the time being, to keep things simpler), cd to the path where your scripts are located, and call them with:
```

./wpa_supplicant.sh && ./dhclient.sh
```

or, if that doesn't work, try:

```
./wpa_supplicant.sh &
./dhclient.sh &
```

and see if that connects you.

As for the issue with Firefox, it does indeed seem to be a problem with Firefox, not your connection in general.  You could try reinstalling Firefox:
```

sudo apt-get remove --purge firefox
sudo apt-get install firefox
```

or playing around with the connection settings in Firefox.

---

### Post by micder on 2008-08-24
Thank you Pytheas22.

I'll try your idea of starting the processes in subshells.
My experience in bash is more related to adapting scripts in slack.
Hope this will do.

Removed Firefox 3 completely and reinstalled to no avail.
Have version 2 now without any problems.
Will try next update of version 3.

Anyhow, my multimedia and graphics are now as I like.
So I can show my fellow seniors, who I guide with their first steps in computerland, that there is more than windooz.

cheers

---

### Post by micder on 2008-08-25
I now start following script from konsole and get connected```
#!/bin/sh -e
# script to start wireless connection
wpa_supplicant -w -Dwext -iwlan0 -c/etc/wpa_supplicant.conf & sleep 10 && dhclient wlan0
```
The & before sleep places wpa_supplicant to the backgrond and frees my konsole.

Thanks alot Pytheas22 for your patience:KS

---

### Post by pytheas22 on 2008-08-25
Alright, great; I'm glad you figured out the scripting stuff.  Does everything work now as you need it to?

By the way, in case you don't know, you can write a KDE launcher to run the script when you click on it, or you could have init run it at boot.  That way you won't have to open a konsole every time to run it manually.

And kudos to you for helping make seniors aware that Microsoft (and Apple) are not their only choices!

---

### Post by micder on 2008-08-27
Put above script in rc.local and everything goes automatically:)

---


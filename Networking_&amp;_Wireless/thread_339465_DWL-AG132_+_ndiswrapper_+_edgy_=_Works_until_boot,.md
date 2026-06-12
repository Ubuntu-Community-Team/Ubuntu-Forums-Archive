---
title: "DWL-AG132 + ndiswrapper + edgy = Works until boot, then disapears."
date: 2007-01-15
forum: Networking &amp; Wireless
---

### Post by OldGaf on 2007-01-15
Hi all,
 
 First I would like to say AHHHHHHHHHHHHHHHHHH  ](*,) 
 
 OK..... I am trying to get my DWL-AG132 to play nice with Edgy using ndiswrapper.
 
 I have a fresh install of edgy and dist-upgrade done.
 I am using ndisrapper 1.34
 This is the process I follow:
 
 1.Make sure I have the headers:
 
 2.Grab the latest version of Ndiswrapper: 
 [http://sourceforge.net/projects/ndiswrapper](http://sourceforge.net/projects/ndiswrapper)
 
 3.Go to the downloaded file and extract it:
 
 4.Change to that directory:
 
 5.Once in the source-directory run:
 make distclean
 
 6.Then run:
 make
 
 7. As root, run:
 make install
 
 8. Then run the following to install the drivers (put in the full path)
 ndiswrapper -i neta5agu.inf
 
 $ ndiswrapper -l 
 
 Installed ndis drivers:
 neta5agu driver present, hardware present
 
 $ lsusb
 Bus 005 Device 005: ID 2001:3a01 D-Link Corp. [hex]
 
 $ ndiswrapper -d 2001:3a01 neta5agu
 $ ndiswrapper -m 
 $ sudo depmod -a
 $ sudo modprobe ndiswrapper
 
 ndiswrapper -l
 neta5agu : driver installed
 device (2001:3A01) present
 
 All this works the first time and I am able to activate and surf the net........
 
 BUT....... as soon as I reboot the box, it will not work. I can't even see the device. No matter what I do, I am unable to get it to work again. I have un-installed the drivers and run "make un-install, removed all evidence and re-installed.... no good. The only thing I can do is install the OS again and repeat the above procedures, but again it only works until I reboot.
 
 The only thing I noticed is that the device number was 2001:3a00 on one install, and the device changed to 2001:3a01 on boot. I un-installed the driver and put it back with the right number (which it accepted) but it still would not work or show up.
 
 ANY help would be GREATLY appreciated.

---

### Post by OldGaf on 2007-01-16
Update...
I turned on the PC this morning and my wifi was there..... just had to inable it.
Rebooted the pc...... no wifi  >:(

dmesg with working wifi:

[17179597.640000] ndiswrapper version 1.34 loaded (preempt=no,smp=yes)
[17179597.804000] usb 1-1: reset full speed USB device using uhci_hcd and address 2
[17179597.972000] ndiswrapper: driver neta5agu (D-Link,05/08/2006,1.5.202.2) loaded
[17179597.972000] ndiswrapper (ZwQueryValueKey:2557): not fully implemented (yet)
[17179599.260000] wlan0: ethernet device 00:11:95:fa:a9:d6 using NDIS driver: neta5agu, version: 0x10005, NDIS version: 0x501, vendor: '', 2001:3A01.F.conf
[17179599.260000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[17179599.260000] usbcore: registered new driver ndiswrapper
[17179600.408000] NET: Registered protocol family 17
[17179600.636000] NET: Registered protocol family 10
[17179600.636000] lo: Disabled Privacy Extensions
[17179600.636000] IPv6 over IPv4 tunneling driver
[17179603.120000] ACPI: Power Button (FF) [PWRF]
[17179603.120000] ACPI: Sleep Button (CM) [SBTN]
[17179603.388000] ibm_acpi: ec object not found
[17179603.444000] pcc_acpi: loading...
[17179606.856000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[17179606.856000] apm: overridden by ACPI.
[17179610.728000] wlan0: no IPv6 routers present
[17179618.864000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[17179619.824000] Bluetooth: Core ver 2.8
[17179619.824000] NET: Registered protocol family 31
[17179619.824000] Bluetooth: HCI device and connection manager initialized
[17179619.824000] Bluetooth: HCI socket layer initialized
[17179619.860000] Bluetooth: L2CAP ver 2.8
[17179619.860000] Bluetooth: L2CAP socket layer initialized
[17179619.904000] Bluetooth: RFCOMM socket layer initialized
[17179619.904000] Bluetooth: RFCOMM TTY layer initialized
[17179619.904000] Bluetooth: RFCOMM ver 1.7
[17179629.684000] eth1: no IPv6 routers present
[17179750.064000] wlan0: no IPv6 routers present

dmesg with wifi NOT working:

 [17179595.488000] ndiswrapper version 1.34 loaded (preempt=no,smp=yes)
[17179595.652000] usb 1-1: reset full speed USB device using uhci_hcd and address 2
[17179595.820000] ndiswrapper: driver neta5agu (D-Link,05/08/2006,1.5.202.2) loaded
[17179595.820000] ndiswrapper (ZwQueryValueKey:2557): not fully implemented (yet)
[17179610.936000] ndiswrapper (NdisWriteErrorLogEntry:230): log: C0001389, count: 4, return_address: d8b479fb
[17179610.936000] ndiswrapper (NdisWriteErrorLogEntry:233): code: 0xd44e4800
[17179610.936000] ndiswrapper (NdisWriteErrorLogEntry:233): code: 0x28
[17179610.936000] ndiswrapper (NdisWriteErrorLogEntry:233): code: 0xd8a90000
[17179610.936000] ndiswrapper (NdisWriteErrorLogEntry:233): code: 0xd8a90000
[17179610.936000] ndiswrapper (miniport_init:270): couldn't initialize device: C0000001
[17179610.936000] ndiswrapper (pnp_start_device:426): Windows driver couldn't initialize the device (C0000001)
[17179610.936000] unregister_netdevice: device eth%d/d44e4000 never was registered
[17179610.936000] ndiswrapper (miniport_halt:326): device d44e4400 is not initialized - not halting
[17179610.936000] ndiswrapper: device eth%d removed
[17179610.936000] ndiswrapper: probe of 1-1:1.0 failed with error -22
[17179610.936000] usbcore: registered new driver ndiswrapper
[17179612.100000] NET: Registered protocol family 17
[17179613.968000] ACPI: Power Button (FF) [PWRF]
[17179613.968000] ACPI: Sleep Button (CM) [SBTN]
[17179614.240000] ibm_acpi: ec object not found
[17179614.292000] pcc_acpi: loading...
[17179617.620000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[17179617.620000] apm: overridden by ACPI.
[17179629.060000] Bluetooth: Core ver 2.8
[17179629.060000] NET: Registered protocol family 31
[17179629.060000] Bluetooth: HCI device and connection manager initialized
[17179629.060000] Bluetooth: HCI socket layer initialized
[17179629.092000] Bluetooth: L2CAP ver 2.8
[17179629.092000] Bluetooth: L2CAP socket layer initialized
[17179629.136000] Bluetooth: RFCOMM socket layer initialized
[17179629.136000] Bluetooth: RFCOMM TTY layer initialized
[17179629.136000] Bluetooth: RFCOMM ver 1.7
[17179800.592000] NET: Registered protocol family 10
[17179800.596000] lo: Disabled Privacy Extensions
[17179800.596000] IPv6 over IPv4 tunneling driver
[17179810.652000] eth1: no IPv6 routers presentUpdate...

---

### Post by OldGaf on 2007-01-20
No takers eh?

Well, just to let you know, it does work if I shut the computer down completely, just not if I do a reboot.

-N-

---

### Post by brolin on 2007-01-24
Which Linux architecture are you using?  I am guessing i386, because D-Link only has i386 Windows drivers for the DWL-AG132 on their Web site.  I tried following your steps with a DWL-AG132 on Kubuntu 6.10 x86_64.  I did not achieve success because I get a message saying that the Windows driver is 32-bit, but the Linux kernel is 64-bit when I modprobed the ndiswrapper module.  The PC with the DWL-AG132 has only an x86_64 Linux installation.  The PC has no wired ethernet connection, so I cannot copy and paste the exact messages.

---

### Post by OldGaf on 2007-01-24
> **brolin said:**
> Which Linux architecture are you using?  I am guessing i386, because D-Link only has i386 Windows drivers for the DWL-AG132 on their Web site.  I tried following your steps with a DWL-AG132 on Kubuntu 6.10 x86_64.  I did not achieve success because I get a message saying that the Windows driver is 32-bit, but the Linux kernel is 64-bit when I modprobed the ndiswrapper module.  The PC with the DWL-AG132 has only an x86_64 Linux installation.  The PC has no wired ethernet connection, so I cannot copy and paste the exact messages.

I don't have the notebook with me but I believe it has 2.6.17-10-generic. I know for sure it is NOT 64....... still too many issues with 64 bit to make it worth it (for me).

---

### Post by brolin on 2007-01-25
I asked for the Linux architecture, not kernel version.  If you do not know then it is most likely i386 for an IBM-compatible PC.

Anyway, I am using the same kernel version (default Edgy kernel), but on x86_64 instead of i386.

---

### Post by OldGaf on 2007-01-29
> **brolin said:**
> I asked for the Linux architecture, not kernel version.  If you do not know then it is most likely i386 for an IBM-compatible PC.

Anyway, I am using the same kernel version (default Edgy kernel), but on x86_64 instead of i386.

Sorry..... misread. It is 386.

---

### Post by brolin on 2007-02-14
Did you ever get your DWL-AG132 working, OldGaf?

My solution was to get an APC WMR1000G.  This device can function as a bridge so that any computer with wired Ethernet can connect to a WiFi access point. :)

---

### Post by OldGaf on 2007-02-14
> **brolin said:**
> Did you ever get your DWL-AG132 working, OldGaf?

My solution was to get an APC WMR1000G.  This device can function as a bridge so that any computer with wired Ethernet can connect to a WiFi access point. :)

This one is on one of my kids PC. It is still the same....... it works fine. If you need to boot for some reason, you must turn the PC completely off then on again...... not a quick reboot. I have it working on two other PC's and don't have this problem. Not a real biggy. Probably will go away the next time I install the OS (will be Feisty)

---

### Post by mattymattysidebyeach on 2007-04-29
in the case that I can prevent someone else from having the same problems:
[B]
yes, DO install ndiswrapper from source[/B], and beforehand **ensure** that one is **thorough** in removing any files having to do with ndiswrapper that are already installed; make uninstall warns of this

after issuing make uninstall, one might try this to find other ndiswrapper files:
sudo find / -name *ndisw*

**equally as important, i think : **
**the v100 inf files that i was using had to be edited, they contained inconsistently named (mixed upper/lower case) references to the hardware *.sys files.

once I had performed these two tasks i had no issues whatsoever with getting connected 

i've posted instrux @ the old ndiswrapper wiki: [COLOR="DarkOrange"][http://ndiswrapper.wiki.sourceforge.net/DWL-AG132](http://ndiswrapper.wiki.sourceforge.net/DWL-AG132)[/COLOR]

---

### Post by brolin on 2007-04-29
**mattymattysidebyeach:**

You did not say which Linux architecture you are using.  I am guessing i386 because I could find only i386 Windows drivers for the DWL-AG132 on D-Link's Web site the last time I checked.

Your find(1) invocation would perform a more comprehensive search if you used -iname instead of -name.  You also need to quote the pattern or escape the asterisks to protect them from expansion by the shell.

---


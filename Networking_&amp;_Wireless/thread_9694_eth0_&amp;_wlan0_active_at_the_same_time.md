---
title: "eth0 &amp; wlan0 active at the same time"
date: 2004-12-30
forum: Networking &amp; Wireless
---

### Post by leviathon on 2004-12-30
Is there anyway to do this?  When both interfaces are active, communications hang. Win & os x handle the situation gracefully, so it would seem linux should be able to also. Am I missing something or is this not possible?

---

### Post by costoa on 2004-12-31
*Is there anyway to do this? When both interfaces are active, communications hang. Win & os x handle the situation gracefully, so it would seem linux should be able to also. Am I missing something or is this not possible?*

It's very possible and somewhat common. Could you please post what type of wireless card you're using and a dump of ifconfig? Are both ethernet and wireless functioning properly when they're used along?

---

### Post by leviathon on 2004-12-31
[QUOTE=costoa]*Is there anyway to do this? When both interfaces are active, communications hang. Win & os x handle the situation gracefully, so it would seem linux should be able to also. Am I missing something or is this not possible?*

It's very possible and somewhat common. Could you please post what type of wireless card you're using and a dump of ifconfig? Are both ethernet and wireless functioning properly when they're used along?[/QUOTE]


I'm using the built in wireless card on my HP zd7010. It uses the broadcom bcmwl5 driver via ndiswrapper. Both work great independently of each other. Here is the results of ifconfig (I turned the wireless card on and ran the command, but I had to turn it back off to post this reply.) after the ifconfig is the results of route.

rick@Leviathon:~ $ sudo ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:C0:9F:32:67:E9
          inet addr:192.168.0.191  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:9fff:fe32:67e9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:699 errors:0 dropped:0 overruns:0 frame:0
          TX packets:720 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:274012 (267.5 KiB)  TX bytes:104055 (101.6 KiB)
          Interrupt:217 Base address:0x3000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8684 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8684 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1247259 (1.1 MiB)  TX bytes:1247259 (1.1 MiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:90:4B:4A:37:B6
          inet addr:192.168.0.171  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::290:4bff:fe4a:37b6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:26 errors:0 dropped:0 overruns:0 frame:0
          TX packets:42 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3909 (3.8 KiB)  TX bytes:4233 (4.1 KiB)
          Interrupt:225 Memory:e2004000-e2005fff


rick@Leviathon:~ $ sudo route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan0
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0

---

### Post by costoa on 2004-12-31
Ok, what we know **isn't** the problem: misconfigured devices, conflicting IP settings or conflicting IRQs. These are the most common problems. I'm still researching it.

Could you please fire up both devices (to create the failure) and post the tail of your message log ("tail -100 /var/log/messages")? Anything stand out?

---

### Post by leviathon on 2005-01-01
[QUOTE=costoa]Ok, what we know **isn't** the problem: misconfigured devices, conflicting IP settings or conflicting IRQs. These are the most common problems. I'm still researching it.

Could you please fire up both devices (to create the failure) and post the tail of your message log ("tail -100 /var/log/messages")? Anything stand out?[/QUOTE]

Nothing is added to the log by activating/deactivating. Here is the log after a reboot with shows both devices being activated. Thanks for your help.

rick@Leviathon:~ $ tail -100 /var/log/messages
Jan  1 09:00:36 localhost kernel: ehci_hcd 0000:00:1d.7: new USB bus registered,  assigned bus number 4
Jan  1 09:00:36 localhost kernel: ehci_hcd 0000:00:1d.7: USB 2.0 enabled, EHCI 1 .00, driver 2004-May-10
Jan  1 09:00:36 localhost kernel: hub 4-0:1.0: USB hub found
Jan  1 09:00:36 localhost kernel: hub 4-0:1.0: 6 ports detected
Jan  1 09:00:36 localhost kernel: hw_random hardware driver 1.0.0 loaded
Jan  1 09:00:36 localhost kernel: usb 4-4: new high speed USB device using addre ss 2
Jan  1 09:00:36 localhost kernel: usb 4-6: new high speed USB device using addre ss 3
Jan  1 09:00:36 localhost kernel: hub 4-6:1.0: USB hub found
Jan  1 09:00:36 localhost kernel: hub 4-6:1.0: 4 ports detected
Jan  1 09:00:36 localhost kernel: Initializing USB Mass Storage driver...
Jan  1 09:00:36 localhost kernel: scsi0 : SCSI emulation for USB Mass Storage de vices
Jan  1 09:00:36 localhost kernel:   Vendor:           Model: USB DISK 20X      R ev: 1.00
Jan  1 09:00:36 localhost kernel:   Type:   Direct-Access                      A NSI SCSI revision: 02
Jan  1 09:00:36 localhost kernel: SCSI device sda: 253952 512-byte hdwr sectors (130 MB)
Jan  1 09:00:36 localhost kernel: sda: Write Protect is off
Jan  1 09:00:36 localhost kernel:  /dev/scsi/host0/bus0/target0/lun0: unknown pa rtition table
Jan  1 09:00:36 localhost kernel: Attached scsi removable disk sda at scsi0, cha nnel 0, id 0, lun 0
Jan  1 09:00:36 localhost kernel: usbcore: registered new driver usb-storage
Jan  1 09:00:36 localhost kernel: USB Mass Storage support registered.
Jan  1 09:00:36 localhost kernel: usb 4-6.1: new high speed USB device using add ress 4
Jan  1 09:00:36 localhost kernel: usb 4-6.2: new full speed USB device using add ress 5
Jan  1 09:00:36 localhost kernel: hub 4-6.2:1.0: USB hub found
Jan  1 09:00:36 localhost kernel: hub 4-6.2:1.0: 4 ports detected
Jan  1 09:00:36 localhost kernel: usb 4-6.3: new high speed USB device using add ress 6
Jan  1 09:00:36 localhost kernel: scsi1 : SCSI emulation for USB Mass Storage de vices
Jan  1 09:00:36 localhost kernel:   Vendor: IC35L080  Model: AVVA07-0          R ev: VA4O
Jan  1 09:00:36 localhost kernel:   Type:   Direct-Access                      A NSI SCSI revision: 02
Jan  1 09:00:36 localhost kernel: SCSI device sdb: 160836480 512-byte hdwr secto rs (82348 MB)
Jan  1 09:00:36 localhost kernel:  /dev/scsi/host1/bus0/target0/lun0: [mac] p1 p 2 p3 p4 p5 p6 p7 p8 p9 p10 p11 p12 p13
Jan  1 09:00:36 localhost kernel: Attached scsi disk sdb at scsi1, channel 0, id  0, lun 0
Jan  1 09:00:36 localhost kernel: usb 4-6.4: new high speed USB device using add ress 7
Jan  1 09:00:36 localhost kernel: hub 4-6.4:1.0: USB hub found
Jan  1 09:00:36 localhost kernel: hub 4-6.4:1.0: 3 ports detected
Jan  1 09:00:36 localhost kernel: usb 4-6.2.3: new full speed USB device using a ddress 8
Jan  1 09:00:36 localhost kernel: scsi2 : hpusbscsi
Jan  1 09:00:36 localhost kernel: usb 4-6.4.2: new low speed USB device using ad dress 9
Jan  1 09:00:36 localhost kernel:   Vendor: HP        Model: ScanJet 5300C     R ev: 6.00
Jan  1 09:00:36 localhost kernel:   Type:   Scanner                            A NSI SCSI revision: 02
Jan  1 09:00:36 localhost kernel: usbcore: registered new driver hpusbscsi
Jan  1 09:00:36 localhost kernel: ACPI: PCI interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 209
Jan  1 09:00:36 localhost kernel: usb 4-6.4.3: new low speed USB device using ad dress 10
Jan  1 09:00:36 localhost kernel: intel8x0_measure_ac97_clock: measured 350477 u secs
Jan  1 09:00:36 localhost kernel: intel8x0: measured clock 1275 rejected
Jan  1 09:00:36 localhost kernel: intel8x0: clocking to 48000
Jan  1 09:00:36 localhost kernel: usbcore: registered new driver hiddev
Jan  1 09:00:36 localhost kernel: input: USB HID v1.10 Keyboard [Chicony USB Key board] on usb-0000:00:1d.7-6.4.2
Jan  1 09:00:36 localhost kernel: input,hiddev96: USB HID v1.10 Device [Chicony USB Keyboard] on usb-0000:00:1d.7-6.4.2
Jan  1 09:00:36 localhost kernel: input: USB HID v1.10 Mouse [Kensington      US B/PS2 Wheel Mouse] on usb-0000:00:1d.7-6.4.3
Jan  1 09:00:36 localhost kernel: usbcore: registered new driver usbhid
Jan  1 09:00:36 localhost kernel: drivers/usb/input/hid-core.c: v2.0:USB HID cor e driver
Jan  1 09:00:36 localhost kernel: ACPI: PCI interrupt 0000:00:1f.6[B] -> GSI 17 (level, low) -> IRQ 209
Jan  1 09:00:36 localhost kernel: 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 2 2, 2004)
Jan  1 09:00:36 localhost kernel: 8139too Fast Ethernet driver 0.9.27
Jan  1 09:00:36 localhost kernel: ACPI: PCI interrupt 0000:02:00.0[A] -> GSI 20 (level, low) -> IRQ 217
Jan  1 09:00:36 localhost kernel: eth0: RealTek RTL8139 at 0x3000, 00:c0:9f:32:6 7:e9, IRQ 217
Jan  1 09:00:36 localhost kernel: Linux Kernel Card Services
Jan  1 09:00:36 localhost kernel:   options:  [pci] [cardbus] [pm]
Jan  1 09:00:36 localhost kernel: ACPI: PCI interrupt 0000:02:01.0[A] -> GSI 17 (level, low) -> IRQ 209
Jan  1 09:00:36 localhost kernel: Yenta: CardBus bridge found at 0000:02:01.0 [1 03c:006a]
Jan  1 09:00:36 localhost kernel: Yenta: ISA IRQ mask 0x0000, PCI irq 209
Jan  1 09:00:36 localhost kernel: Socket status: 30000006
Jan  1 09:00:36 localhost kernel: ohci1394: $Rev: 1223 $ Ben Collins <bcollins@d ebian.org>
Jan  1 09:00:36 localhost kernel: ACPI: PCI interrupt 0000:02:02.0[A] -> GSI 19 (level, low) -> IRQ 185
Jan  1 09:00:36 localhost kernel: ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[ 185]  MMIO=[e2007000-e20077ff]  Max Packet=[2048]
Jan  1 09:00:36 localhost kernel: usb 4-6.2.3: control timeout on ep0in
Jan  1 09:00:36 localhost kernel: usb 4-6.2.3: control timeout on ep0in
Jan  1 09:00:36 localhost kernel: eth0: link up, 100Mbps, full-duplex, lpa 0x45E 1
Jan  1 09:00:36 localhost kernel: NET: Registered protocol family 17
Jan  1 09:00:36 localhost kernel: ndiswrapper version 0.10 loaded (preempt=yes,s mp=no)
Jan  1 09:00:36 localhost kernel: ACPI: PCI interrupt 0000:02:03.0[A] -> GSI 21 (level, low) -> IRQ 225
Jan  1 09:00:36 localhost kernel: ndiswrapper: using irq 225
Jan  1 09:00:36 localhost kernel: wlan0: ndiswrapper ethernet device 00:90:4b:4a :37:b6 using driver bcmwl5.sys
Jan  1 09:00:36 localhost kernel: ndiswrapper device wlan0 supports WPA with AES /CCMP and TKIP ciphers
Jan  1 09:00:36 localhost kernel: ndiswrapper: driver bcmwl5.sys (Broadcom,06/13 /2003, 3.20.23.0) added
Jan  1 09:00:36 localhost kernel: ACPI: Battery Slot [BAT1] (battery present)
Jan  1 09:00:36 localhost kernel: ACPI: AC Adapter [ACAD] (on-line)
Jan  1 09:00:36 localhost kernel: ACPI: Power Button (FF) [PWRF]
Jan  1 09:00:36 localhost kernel: ACPI: Sleep Button (CM) [SBTN]
Jan  1 09:00:36 localhost kernel: ACPI: Lid Switch [LID]
Jan  1 09:00:37 localhost kernel: lp0: ECP mode
Jan  1 09:00:39 localhost kernel: cs: IO port probe 0x0100-0x04ff: clean.
Jan  1 09:00:39 localhost kernel: cs: IO port probe 0x0800-0x08ff: clean.
Jan  1 09:00:39 localhost kernel: cs: IO port probe 0x0c00-0x0cff: clean.
Jan  1 09:00:39 localhost kernel: cs: IO port probe 0x0a00-0x0aff: clean.
Jan  1 09:00:41 localhost kernel: NET: Registered protocol family 10
Jan  1 09:00:41 localhost kernel: Disabled Privacy Extensions on device c02cc0c0 (lo)
Jan  1 09:00:41 localhost kernel: IPv6 over IPv4 tunneling driver
Jan  1 09:00:45 localhost kernel: agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
Jan  1 09:00:45 localhost kernel: agpgart: Putting AGP V3 device at 0000:00:00.0  into 8x mode
Jan  1 09:00:45 localhost kernel: agpgart: Putting AGP V3 device at 0000:01:00.0  into 8x mode
Jan  1 09:00:47 localhost kernel: agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
Jan  1 09:00:47 localhost kernel: agpgart: Putting AGP V3 device at 0000:00:00.0  into 8x mode
Jan  1 09:00:47 localhost kernel: agpgart: Putting AGP V3 device at 0000:01:00.0  into 8x mode
Jan  1 09:00:49 localhost kernel: drivers/usb/input/hid-input.c: event field not  found
Jan  1 09:00:49 localhost kernel: drivers/usb/input/hid-input.c: event field not  found
Jan  1 09:09:57 localhost gconfd (rick-5826): starting (version 2.8.1), pid 5826  user 'rick'
Jan  1 09:09:57 localhost gconfd (rick-5826): Resolved address "xml:readonly:/et c/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Jan  1 09:09:57 localhost gconfd (rick-5826): Resolved address "xml:readwrite:/h ome/rick/.gconf" to a writable configuration source at position 1
Jan  1 09:09:57 localhost gconfd (rick-5826): Resolved address "xml:readonly:/et c/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Jan  1 09:10:11 localhost gconfd (rick-5826): Resolved address "xml:readwrite:/h ome/rick/.gconf" to a writable configuration source at position 0

---

### Post by costoa on 2005-01-03
[QUOTE=leviathon]Nothing is added to the log by activating/deactivating. Here is the log after a reboot with shows both devices being activated. Thanks for your help.

rick@Leviathon:~ $ tail -100 /var/log/messages
Jan  1 09:00:36 localhost kernel: ehci_hcd 0000:00:1d.7: new USB bus registered,  assigned bus number 4
Jan  1 09:00:36 localhost kernel: ehci_hcd 0000:00:1d.7: USB 2.0 enabled, EHCI 1 .00, driver 2004-May-10
Jan  1 09:00:36 localhost kernel: hub 4-0:1.0: USB hub found
Jan  1 09:00:36 localhost kernel: hub 4-0:1.0: 6 ports detected
Jan  1 09:00:36 localhost kernel: hw_random hardware driver 1.0.0 loaded
Jan  1 09:00:36 localhost kernel: usb 4-4: new high speed USB device using addre ss 2
Jan  1 09:00:36 localhost kernel: usb 4-6: new high speed USB device using addre ss 3
Jan  1 09:00:36 localhost kernel: hub 4-6:1.0: USB hub found
Jan  1 09:00:36 localhost kernel: hub 4-6:1.0: 4 ports detected
Jan  1 09:00:36 localhost kernel: Initializing USB Mass Storage driver...
Jan  1 09:00:36 localhost kernel: scsi0 : SCSI emulation for USB Mass Storage de vices
Jan  1 09:00:36 localhost kernel:   Vendor:           Model: USB DISK 20X      R ev: 1.00
Jan  1 09:00:36 localhost kernel:   Type:   Direct-Access                      A NSI SCSI revision: 02
Jan  1 09:00:36 localhost kernel: SCSI device sda: 253952 512-byte hdwr sectors (130 MB)
Jan  1 09:00:36 localhost kernel: sda: Write Protect is off
Jan  1 09:00:36 localhost kernel:  /dev/scsi/host0/bus0/target0/lun0: unknown pa rtition table
Jan  1 09:00:36 localhost kernel: Attached scsi removable disk sda at scsi0, cha nnel 0, id 0, lun 0
Jan  1 09:00:36 localhost kernel: usbcore: registered new driver usb-storage
Jan  1 09:00:36 localhost kernel: USB Mass Storage support registered.
Jan  1 09:00:36 localhost kernel: usb 4-6.1: new high speed USB device using add ress 4
Jan  1 09:00:36 localhost kernel: usb 4-6.2: new full speed USB device using add ress 5
Jan  1 09:00:36 localhost kernel: hub 4-6.2:1.0: USB hub found
Jan  1 09:00:36 localhost kernel: hub 4-6.2:1.0: 4 ports detected
Jan  1 09:00:36 localhost kernel: usb 4-6.3: new high speed USB device using add ress 6
Jan  1 09:00:36 localhost kernel: scsi1 : SCSI emulation for USB Mass Storage de vices
Jan  1 09:00:36 localhost kernel:   Vendor: IC35L080  Model: AVVA07-0          R ev: VA4O
Jan  1 09:00:36 localhost kernel:   Type:   Direct-Access                      A NSI SCSI revision: 02
Jan  1 09:00:36 localhost kernel: SCSI device sdb: 160836480 512-byte hdwr secto rs (82348 MB)
Jan  1 09:00:36 localhost kernel:  /dev/scsi/host1/bus0/target0/lun0: [mac] p1 p 2 p3 p4 p5 p6 p7 p8 p9 p10 p11 p12 p13
Jan  1 09:00:36 localhost kernel: Attached scsi disk sdb at scsi1, channel 0, id  0, lun 0
Jan  1 09:00:36 localhost kernel: usb 4-6.4: new high speed USB device using add ress 7
Jan  1 09:00:36 localhost kernel: hub 4-6.4:1.0: USB hub found
Jan  1 09:00:36 localhost kernel: hub 4-6.4:1.0: 3 ports detected
Jan  1 09:00:36 localhost kernel: usb 4-6.2.3: new full speed USB device using a ddress 8
Jan  1 09:00:36 localhost kernel: scsi2 : hpusbscsi
Jan  1 09:00:36 localhost kernel: usb 4-6.4.2: new low speed USB device using ad dress 9
Jan  1 09:00:36 localhost kernel:   Vendor: HP        Model: ScanJet 5300C     R ev: 6.00
Jan  1 09:00:36 localhost kernel:   Type:   Scanner                            A NSI SCSI revision: 02
Jan  1 09:00:36 localhost kernel: usbcore: registered new driver hpusbscsi
Jan  1 09:00:36 localhost kernel: ACPI: PCI interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 209
Jan  1 09:00:36 localhost kernel: usb 4-6.4.3: new low speed USB device using ad dress 10
Jan  1 09:00:36 localhost kernel: intel8x0_measure_ac97_clock: measured 350477 u secs
Jan  1 09:00:36 localhost kernel: intel8x0: measured clock 1275 rejected
Jan  1 09:00:36 localhost kernel: intel8x0: clocking to 48000
Jan  1 09:00:36 localhost kernel: usbcore: registered new driver hiddev
Jan  1 09:00:36 localhost kernel: input: USB HID v1.10 Keyboard [Chicony USB Key board] on usb-0000:00:1d.7-6.4.2
Jan  1 09:00:36 localhost kernel: input,hiddev96: USB HID v1.10 Device [Chicony USB Keyboard] on usb-0000:00:1d.7-6.4.2
Jan  1 09:00:36 localhost kernel: input: USB HID v1.10 Mouse [Kensington      US B/PS2 Wheel Mouse] on usb-0000:00:1d.7-6.4.3
Jan  1 09:00:36 localhost kernel: usbcore: registered new driver usbhid
Jan  1 09:00:36 localhost kernel: drivers/usb/input/hid-core.c: v2.0:USB HID cor e driver
Jan  1 09:00:36 localhost kernel: ACPI: PCI interrupt 0000:00:1f.6[B] -> GSI 17 (level, low) -> IRQ 209
Jan  1 09:00:36 localhost kernel: 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 2 2, 2004)
Jan  1 09:00:36 localhost kernel: 8139too Fast Ethernet driver 0.9.27
Jan  1 09:00:36 localhost kernel: ACPI: PCI interrupt 0000:02:00.0[A] -> GSI 20 (level, low) -> IRQ 217
Jan  1 09:00:36 localhost kernel: eth0: RealTek RTL8139 at 0x3000, 00:c0:9f:32:6 7:e9, IRQ 217
Jan  1 09:00:36 localhost kernel: Linux Kernel Card Services
Jan  1 09:00:36 localhost kernel:   options:  [pci] [cardbus] [pm]
Jan  1 09:00:36 localhost kernel: ACPI: PCI interrupt 0000:02:01.0[A] -> GSI 17 (level, low) -> IRQ 209
Jan  1 09:00:36 localhost kernel: Yenta: CardBus bridge found at 0000:02:01.0 [1 03c:006a]
Jan  1 09:00:36 localhost kernel: Yenta: ISA IRQ mask 0x0000, PCI irq 209
Jan  1 09:00:36 localhost kernel: Socket status: 30000006
Jan  1 09:00:36 localhost kernel: ohci1394: $Rev: 1223 $ Ben Collins <bcollins@d ebian.org>
Jan  1 09:00:36 localhost kernel: ACPI: PCI interrupt 0000:02:02.0[A] -> GSI 19 (level, low) -> IRQ 185
Jan  1 09:00:36 localhost kernel: ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[ 185]  MMIO=[e2007000-e20077ff]  Max Packet=[2048]
Jan  1 09:00:36 localhost kernel: usb 4-6.2.3: control timeout on ep0in
Jan  1 09:00:36 localhost kernel: usb 4-6.2.3: control timeout on ep0in
Jan  1 09:00:36 localhost kernel: eth0: link up, 100Mbps, full-duplex, lpa 0x45E 1
Jan  1 09:00:36 localhost kernel: NET: Registered protocol family 17
Jan  1 09:00:36 localhost kernel: ndiswrapper version 0.10 loaded (preempt=yes,s mp=no)
Jan  1 09:00:36 localhost kernel: ACPI: PCI interrupt 0000:02:03.0[A] -> GSI 21 (level, low) -> IRQ 225
Jan  1 09:00:36 localhost kernel: ndiswrapper: using irq 225
Jan  1 09:00:36 localhost kernel: wlan0: ndiswrapper ethernet device 00:90:4b:4a :37:b6 using driver bcmwl5.sys
Jan  1 09:00:36 localhost kernel: ndiswrapper device wlan0 supports WPA with AES /CCMP and TKIP ciphers
Jan  1 09:00:36 localhost kernel: ndiswrapper: driver bcmwl5.sys (Broadcom,06/13 /2003, 3.20.23.0) added
Jan  1 09:00:36 localhost kernel: ACPI: Battery Slot [BAT1] (battery present)
Jan  1 09:00:36 localhost kernel: ACPI: AC Adapter [ACAD] (on-line)
Jan  1 09:00:36 localhost kernel: ACPI: Power Button (FF) [PWRF]
Jan  1 09:00:36 localhost kernel: ACPI: Sleep Button (CM) [SBTN]
Jan  1 09:00:36 localhost kernel: ACPI: Lid Switch [LID]
Jan  1 09:00:37 localhost kernel: lp0: ECP mode
Jan  1 09:00:39 localhost kernel: cs: IO port probe 0x0100-0x04ff: clean.
Jan  1 09:00:39 localhost kernel: cs: IO port probe 0x0800-0x08ff: clean.
Jan  1 09:00:39 localhost kernel: cs: IO port probe 0x0c00-0x0cff: clean.
Jan  1 09:00:39 localhost kernel: cs: IO port probe 0x0a00-0x0aff: clean.
Jan  1 09:00:41 localhost kernel: NET: Registered protocol family 10
Jan  1 09:00:41 localhost kernel: Disabled Privacy Extensions on device c02cc0c0 (lo)
Jan  1 09:00:41 localhost kernel: IPv6 over IPv4 tunneling driver
Jan  1 09:00:45 localhost kernel: agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
Jan  1 09:00:45 localhost kernel: agpgart: Putting AGP V3 device at 0000:00:00.0  into 8x mode
Jan  1 09:00:45 localhost kernel: agpgart: Putting AGP V3 device at 0000:01:00.0  into 8x mode
Jan  1 09:00:47 localhost kernel: agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
Jan  1 09:00:47 localhost kernel: agpgart: Putting AGP V3 device at 0000:00:00.0  into 8x mode
Jan  1 09:00:47 localhost kernel: agpgart: Putting AGP V3 device at 0000:01:00.0  into 8x mode
Jan  1 09:00:49 localhost kernel: drivers/usb/input/hid-input.c: event field not  found
Jan  1 09:00:49 localhost kernel: drivers/usb/input/hid-input.c: event field not  found
Jan  1 09:09:57 localhost gconfd (rick-5826): starting (version 2.8.1), pid 5826  user 'rick'
Jan  1 09:09:57 localhost gconfd (rick-5826): Resolved address "xml:readonly:/et c/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Jan  1 09:09:57 localhost gconfd (rick-5826): Resolved address "xml:readwrite:/h ome/rick/.gconf" to a writable configuration source at position 1
Jan  1 09:09:57 localhost gconfd (rick-5826): Resolved address "xml:readonly:/et c/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Jan  1 09:10:11 localhost gconfd (rick-5826): Resolved address "xml:readwrite:/h ome/rick/.gconf" to a writable configuration source at position 0[/QUOTE]
 Oh man, I far as I can see there's nothing there that says there's a problem. No IRQ issues, drivers loading ok. We know the devices work fine alone. From the lack of responses I guess no one has a guess what's wrong. It's the first time I've heard of a problem like this. My guess is it has something to do with a conflict with the NDIS wrappers (hairy area) since it's not in the general log. Are there native GNU/Linux drivers for the wireless card? If so, that might just fix it.

IMO, it's time to talk to the experts: [http://www.ubuntulinux.org/support/paidsupport](http://www.ubuntulinux.org/support/paidsupport)

I'm sorry I'm out of ideas. I'll still subscribe to the thread and hopefully someone else might have an idea.

---

### Post by leviathon on 2005-01-03
Thanks for your help! I'll see how much it annoys me over the next week before I go for support.

---

### Post by leviathon on 2005-01-08
I wanted to post my solution to this issue in case anyone else experiences this problem. I installed the laptop-net package. Laptop-net detects whether a network cable is plugged in and activates/deactivates the interface as necessary. Perhaps not the correct solution, as I still cannot have both interfaces active at the same time. But this gives me the results I was looking for.

---

### Post by HankB on 2005-01-16
[QUOTE=leviathon]

rick@Leviathon:~ $ sudo route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan0
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0[/QUOTE]

IANANE (but I sometimes try to play one on the Internet  :mrgreen: )

Both interfaces are on the same LAN and both have identical settings. How would the kernel know which to use for outbound traffic? Wouldn't you want to take one down to use the other? I wonder if that is what the laptop-net package does?

---


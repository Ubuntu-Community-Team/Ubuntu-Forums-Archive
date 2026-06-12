---
title: "Intel 3945 wireless issue : Kill Switch"
date: 2006-08-28
forum: Networking &amp; Wireless
---

### Post by UltraMathMan on 2006-08-28
Intel 3945 wireless issue

I have an Inspiron E1505 notebook, with an Intel 3945 internal wireless card. This card worked "out of box" when I installed Ubuntu a month or so ago. Now however, it has for some reason stopped working (I turned it off a couple days ago with Fn+F2 and now it won't come back on). I assume I messed something up but I have no idea what.

from output of lspci -v (not sure if this is wireless)
```
0000:0b:00.0 Network controller: Intel Corporation: Unknown device 4222 (rev 02)
        Subsystem: Intel Corporation: Unknown device 1020
        Flags: bus master, fast devsel, latency 0, IRQ 169
        Memory at dfcff000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

```

iwconfig
```
lo        no wireless extensions.

sit0      no wireless extensions.

eth0      no wireless extensions.

```

ifconfig -a
```
eth0      Link encap:Ethernet  HWaddr 00:15:C5:21:0E:43  
          inet addr:128.180.215.129  Bcast:128.180.215.255  Mask:255.255.252.0
          inet6 addr: fe80::215:c5ff:fe21:e43/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:94354 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9052 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:20399456 (19.4 MiB)  TX bytes:1549504 (1.4 MiB)
          Interrupt:217 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:69 errors:0 dropped:0 overruns:0 frame:0
          TX packets:69 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2944 (2.8 KiB)  TX bytes:2944 (2.8 KiB)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

from dmesg
```
[17179586.788000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.0.5m
[17179586.788000] ipw3945: Copyright(c) 2003-2006 Intel Corporation
...
[17179587.144000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection
...
[17179588.272000] ipw3945: Detected geography ABG (11 802.11bg channels, 13 802.11a channels)
...
[17179659.620000] ipw3945: Radio Frequency Kill Switch is On:
[17179659.620000] Kill switch must be turned off for wireless networking to work.

```
I think the drivers are installed but I don't know how to turn the Kill Switch off.

Any suggestions?

So...

---

### Post by UltraMathMan on 2006-08-28
Booting into XP (yuck) then rebooting into Ubuntu fixed this for me - at least for now...

---

### Post by UltraMathMan on 2006-09-22
Ok, some more info. Fn+F2 (toggle switch for wireless on E1505) was working ok, I put the computer to sleep and on resume it doesn't work so maybe something that should be turning off isn't (actually it looks that way to me from the output of dmesg below). It also then seems that the Fn+F2 keycode becomes unmapped as well.

Output of dmesg from just prioe to shutdown for sleep to EOF
```
[17207061.212000] atkbd.c: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
[17207061.212000] atkbd.c: Use 'setkeycodes e008 <keycode>' to make it known.
**[17207061.560000] ipw3945: Detected geography ABG (11 802.11bg channels, 13 802.11a channels)**
[17207061.868000] usb 4-2: new full speed USB device using uhci_hcd and address 2
[17207061.976000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[17207062.216000] Bluetooth: HCI USB driver ver 2.9
[17207062.220000] usbcore: registered new driver hci_usb
[B][17207063.812000] ipw3945: Radio Frequency Kill Switch is On:
[17207063.812000] Kill switch must be turned off for wireless networking to work[/B].
[17207063.816000] atkbd.c: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
[17207063.816000] atkbd.c: Use 'setkeycodes e008 <keycode>' to make it known.
[17207063.896000] usb 4-2: USB disconnect, address 2
[B][17207065.608000] ipw3945: Error sending ADD_STA: time out after 500ms.
[17207066.108000] ipw3945: Error sending RATE_SCALE: time out after 500ms.
[17207066.608000] ipw3945: Error sending LEDS_CMD: time out after 500ms.
[/B][17208101.228000] usbcore: deregistering driver hci_usb
[17208101.280000] uhci_hcd 0000:00:1d.3: remove, state 1
[17208101.280000] usb usb4: USB disconnect, address 1
[17208101.288000] uhci_hcd 0000:00:1d.3: USB bus 4 deregistered
[17208101.292000] ACPI: PCI interrupt for device 0000:00:1d.3 disabled
[17208101.292000] uhci_hcd 0000:00:1d.2: remove, state 1
[17208101.292000] usb usb3: USB disconnect, address 1
[17208101.300000] uhci_hcd 0000:00:1d.2: USB bus 3 deregistered
[17208101.300000] ACPI: PCI interrupt for device 0000:00:1d.2 disabled
[17208101.300000] uhci_hcd 0000:00:1d.1: remove, state 1
[17208101.300000] usb usb2: USB disconnect, address 1
[17208101.300000] uhci_hcd 0000:00:1d.1: USB bus 2 deregistered
[17208101.300000] ACPI: PCI interrupt for device 0000:00:1d.1 disabled
[17208101.304000] uhci_hcd 0000:00:1d.0: remove, state 1
[17208101.304000] usb usb1: USB disconnect, address 1
[17208101.304000] uhci_hcd 0000:00:1d.0: USB bus 1 deregistered
[17208101.304000] ACPI: PCI interrupt for device 0000:00:1d.0 disabled
[17208101.332000] ehci_hcd 0000:00:1d.7: remove, state 1
[17208101.332000] usb usb5: USB disconnect, address 1
[17208101.336000] ehci_hcd 0000:00:1d.7: USB bus 5 deregistered
[17208101.336000] ACPI: PCI interrupt for device 0000:00:1d.7 disabled
[17208101.452000] ACPI: PCI interrupt for device 0000:03:00.0 disabled
**[17208102.004000] ipw3945: Error sending LEDS_CMD: time out after 500ms.**
[17208102.104000] ACPI: PCI interrupt for device 0000:0b:00.0 disabled
[17208102.116000] ieee80211_crypt: unregistered algorithm 'NULL'
[17208102.120000] ieee80211_1_1_13_crypt: unregistered algorithm 'NULL'
[17208105.780000] Freezing cpus ...
[17208105.896000] CPU 1 is now offline
[17208105.896000] SMP alternatives: switching to UP code
[17208106.096000] CPU1 is down
[17208106.096000] Stopping tasks: =======================================================================================|
[17208106.104000] ata2: suspend device
[17208106.104000] ata1: suspend device
[17208108.540000] ACPI: PCI interrupt for device 0000:01:00.0 disabled
[17208108.540000] ata_piix 0000:00:1f.2: suspend PCI device
[17208108.540000] ACPI: PCI interrupt for device 0000:00:1f.2 disabled
[17208108.572000] ACPI: PCI interrupt for device 0000:00:1b.0 disabled
[17208108.572000] Back to C!
[17237879.572000] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 169
[17237879.572000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[17237879.572000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 21 (level, low) -> IRQ 233
[17237879.572000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[17237879.760000] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 169
[17237879.760000] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[17237879.760000] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 177
[17237879.760000] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[17237879.760000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[17237879.760000] ata_piix 0000:00:1f.2: resume PCI device
[17237879.776000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 17 (level, low) -> IRQ 217
[17237879.776000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[17237879.776000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 169
[17237879.776000] PCI: Setting latency timer of device 0000:01:00.0 to 64
[17237879.804000] PCI: Enabling device 0000:03:01.0 (0000 -> 0002)
[17237879.804000] ACPI: PCI Interrupt 0000:03:01.0[A] -> GSI 19 (level, low) -> IRQ 177
[17237879.804000] ACPI: PCI Interrupt 0000:03:01.1[B] -> GSI 18 (level, low) -> IRQ 66
[17237880.392000] ata1: resume device
[17237880.724000] pata_get_dev_handle: ENTER: dev->bus_id='0000:00:1f.2'
[17237880.724000] pata_get_dev_handle: dev_handle: 0xdffe6360, parent_handle: 0xc2332e40
[17237880.724000] pata_get_dev_handle: for dev=0x1f.2, addr=0x1f0002, parent=0xdff64200, *handle=0xdffe6360
[17237880.724000] do_drive_get_GTF:   drive w/ adr=0: v: 0x00000000
[17237880.744000] ata1: dev 0 configured for UDMA/100
[17237880.744000] ata2: resume device
[17237880.900000] pata_get_dev_handle: ENTER: dev->bus_id='0000:00:1f.2'
[17237880.900000] pata_get_dev_handle: dev_handle: 0xdffe6360, parent_handle: 0xc2332e40
[17237880.900000] pata_get_dev_handle: for dev=0x1f.2, addr=0x1f0002, parent=0xdff64200, *handle=0xdffe6360
[17237880.900000] do_drive_get_GTF:   drive w/ adr=0: v: 0x00000000
[17237880.900000] ata2: dev 0 configured for UDMA/33
[17237880.900000] Restarting tasks... done
[17237881.036000] Thawing cpus ...
[17237881.036000] SMP alternatives: switching to SMP code
[17237881.036000] Booting processor 1/1 eip 3000
[17237881.040000] Initializing CPU#1
[17237881.120000] Calibrating delay using timer specific routine.. 3990.35 BogoMIPS (lpj=7980716)
[17237881.120000] CPU: After generic identify, caps: bfe9fbff 00100000 00000000 00000000 0000c1a9 00000000 00000000
[17237881.120000] CPU: After vendor identify, caps: bfe9fbff 00100000 00000000 00000000 0000c1a9 00000000 00000000
[17237881.120000] monitor/mwait feature present.
[17237881.120000] CPU: L1 I cache: 32K, L1 D cache: 32K
[17237881.120000] CPU: L2 cache: 2048K
[17237881.120000] CPU: Hyper-Threading is disabled
[17237881.120000] CPU: After all inits, caps: bfe9fbff 00100000 00000000 00000040 0000c1a9 00000000 00000000
[17237881.120000] CPU1: Intel Genuine Intel(R) CPU           T2500  @ 2.00GHz stepping 08
[17237881.140000] APIC error on CPU1: 00(40)
[17237881.140000] CPU1 is up
[17237881.620000] Bluetooth: HCI USB driver ver 2.9
[17237881.620000] usbcore: registered new driver hci_usb
[17237881.656000] usbcore: registered new driver hiddev
[17237881.656000] usbcore: registered new driver usbhid
[17237881.656000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17237881.672000] USB Universal Host Controller Interface driver v2.3
[17237881.672000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 20 (level, low) -> IRQ 225
[17237881.672000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[17237881.672000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[17237881.676000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[17237881.676000] uhci_hcd 0000:00:1d.0: irq 225, io base 0x0000bf80
[17237881.676000] hub 1-0:1.0: USB hub found
[17237881.676000] hub 1-0:1.0: 2 ports detected
[17237881.780000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 21 (level, low) -> IRQ 233
[17237881.780000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[17237881.780000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[17237881.780000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[17237881.780000] uhci_hcd 0000:00:1d.1: irq 233, io base 0x0000bf60
[17237881.780000] hub 2-0:1.0: USB hub found
[17237881.780000] hub 2-0:1.0: 2 ports detected
[17237881.884000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 22 (level, low) -> IRQ 50
[17237881.884000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[17237881.884000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[17237881.884000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[17237881.884000] uhci_hcd 0000:00:1d.2: irq 50, io base 0x0000bf40
[17237881.884000] hub 3-0:1.0: USB hub found
[17237881.884000] hub 3-0:1.0: 2 ports detected
[17237881.988000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 23 (level, low) -> IRQ 58
[17237881.988000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[17237881.988000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[17237881.988000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[17237881.988000] uhci_hcd 0000:00:1d.3: irq 58, io base 0x0000bf20
[17237881.988000] hub 4-0:1.0: USB hub found
[17237881.988000] hub 4-0:1.0: 2 ports detected
[17237882.112000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 20 (level, low) -> IRQ 225
[17237882.112000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[17237882.112000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[17237882.112000] ehci_hcd 0000:00:1d.7: debug port 1
[17237882.112000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[17237882.112000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[17237882.112000] ehci_hcd 0000:00:1d.7: irq 225, io mem 0xffa80000
[17237882.124000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17237882.124000] hub 5-0:1.0: USB hub found
[17237882.124000] hub 5-0:1.0: 8 ports detected
[17237882.260000] b44.c:v0.97 (Nov 30, 2005)
[17237882.260000] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 217
[17237882.264000] eth0: Broadcom 4400 10/100BaseT Ethernet 00:15:c5:21:0e:43
[17237882.272000] ieee80211_1_1_13_crypt: registered algorithm 'NULL'
[17237882.272000] ieee80211_1_1_13: 802.11 data/management/control stack, 1.1.13
[17237882.272000] ieee80211_1_1_13: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[17237882.276000] ieee80211_crypt: registered algorithm 'NULL'
[17237882.276000] ieee80211: 802.11 data/management/control stack, git-1.1.7
[17237882.276000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
**[17237882.300000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.0.5m**
**[17237882.300000] ipw3945: Copyright(c) 2003-2006 Intel Corporation**
[17237882.300000] ACPI: PCI Interrupt 0000:0b:00.0[A] -> GSI 16 (level, low) -> IRQ 169
[17237882.300000] PCI: Setting latency timer of device 0000:0b:00.0 to 64
**[17237882.304000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection**
[17237882.336000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[17237886.704000] ACPI: Lid Switch [LID]
[17237886.704000] ACPI: Power Button (CM) [PBTN]
[17237886.704000] ACPI: Sleep Button (CM) [SBTN]
[17237886.776000] ACPI: Thermal Zone [THM] (25 C)
[17237886.836000] ACPI: AC Adapter [AC] (on-line)
[17237886.880000] ACPI: Battery Slot [BAT0] (battery present)
[B][17237894.704000] atkbd.c: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
[17237894.704000] atkbd.c: Use 'setkeycodes e008 <keycode>' to make it known.[/B]
[17237895.252000] usb 4-2: new full speed USB device using uhci_hcd and address 2
[B][17237906.652000] atkbd.c: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
[17237906.652000] atkbd.c: Use 'setkeycodes e008 <keycode>' to make it known.[/B]
[17237906.856000] usb 4-2: USB disconnect, address 2

```

---

### Post by UltraMathMan on 2006-09-22
Anyone know if there is a way to turn off the kill switch (ie. do what Fn+F2 does) from the terminal?

---

### Post by lifeperfecti0n on 2006-09-22
hey how did u get the card to work I have the same card on Ubuntu Dapper and Dell Inspiron E1505 but it didn't work...Well I dunno if it did because I don't know how to check that but I couldn't setup my university's wireless network anyway. I have given up im too busy with other things but do you know Intel has released proprietary drivers for this card? Some people told me to compile the drivers that may get the network up I used ndiswrapper to setup the card but when I started wpa_supplicant it just gave an authentication timed out error. Any ideas or suggestions?
Oh and btw I couldn't get bluetooth working either so do you know how I could do that?

---

### Post by UltraMathMan on 2006-09-22
My card was configured out of box, the kill switch toggle obviously is misbehaving but you may need to configure wpasupplicant for connect to the university's network. Check out my config [here]("http://www.ubuntuforums.org/showthread.php?t=249654&highlight=PEAP")

-Hope this helps :)

---

### Post by sadrak on 2006-09-26
i have the same problem! after many times working FN + F2 now i cant turn on the wifi :(

here are the description:
[http://www.ubuntuforums.org/showthread.php?t=250638](http://www.ubuntuforums.org/showthread.php?t=250638) 

looks exactly like UltraMathMan problem :(

UPDATE:
[http://www.ubuntuforums.org/showthread.php?t=182639&highlight=ipw3945%3A+Radio+Frequency+Kill+Switch](http://www.ubuntuforums.org/showthread.php?t=182639&highlight=ipw3945%3A+Radio+Frequency+Kill+Switch)

that *must* help *hope*

i will check it later ...

---

### Post by UltraMathMan on 2006-09-26
Iirc I have the restricted modules kernal installed and running (I'll definitly check next time the wireless goes out). I had done some more googling on this problem and [this]("http://www.linuxquestions.org/questions/showthread.php?p=2423080") was/is going to be my next move (if sadrak's updated link fails). Will keep everyone posted.

---

### Post by KjetilK on 2006-12-06
Im also stuck on the kill switch on 3945. Ive got the restricted modules and a patched driver (to avoid the CPU freeze issue), and Im trying the different keys to turn it off. The box is a HGL31. Bought from whitebox.no, who knows who made it... :-)

I have also tried to set 

```
root@owl:/sys/bus/pci/drivers/ipw3945/0000:02:00.0# echo 0 > rf_kill

```
in the hope that would turn it off, but it didnt work, thus I suspect this is a hardware switch. 

If I use the fron switch to turn it on and then off, and press Fn+F2, the log says:
```

Dec  6 17:05:25 owl kernel: [17183791.372000] atkbd.c: Unknown key pressed (translated set 2, code 0xf1 on isa0060/serio0).
Dec  6 17:05:25 owl kernel: [17183791.372000] atkbd.c: Use 'setkeycodes e071 <keycode>' to make it known.
Dec  6 17:05:25 owl kernel: [17183791.380000] atkbd.c: Unknown key released (translated set 2, code 0xf1 on isa0060/serio0).
Dec  6 17:05:25 owl kernel: [17183791.380000] atkbd.c: Use 'setkeycodes e071 <keycode>' to make it known.
Dec  6 17:05:26 owl kernel: [17183792.176000] atkbd.c: Unknown key pressed (translated set 2, code 0xf1 on isa0060/serio0).
Dec  6 17:05:26 owl kernel: [17183792.176000] atkbd.c: Use 'setkeycodes e071 <keycode>' to make it known.
Dec  6 17:05:26 owl kernel: [17183792.184000] atkbd.c: Unknown key released (translated set 2, code 0xf1 on isa0060/serio0).
Dec  6 17:05:26 owl kernel: [17183792.184000] atkbd.c: Use 'setkeycodes e071 <keycode>' to make it known.
Dec  6 17:05:30 owl kernel: [17183796.492000] atkbd.c: Unknown key pressed (translated set 2, code 0x84 on isa0060/serio0).
Dec  6 17:05:30 owl kernel: [17183796.492000] atkbd.c: Use 'setkeycodes e004 <keycode>' to make it known.
Dec  6 17:05:30 owl kernel: [17183796.532000] atkbd.c: Unknown key released (translated set 2, code 0x84 on isa0060/serio0).
Dec  6 17:05:30 owl kernel: [17183796.532000] atkbd.c: Use 'setkeycodes e004 <keycode>' to make it known.

```

So, setkeycodes is the way to go, but I do need to know what to set it to, and it doesnt seem to be just echoing to the rf_kill thing either...


I dont have windows, and I intend to not try that. There doesnt seem to be a BIOS setting for this on my box either.

Good advices are greatly appreciated!

---

### Post by Olen on 2007-03-17
Kjetil:
I have the exact same laptop, and the exact same problem - even though I am running Fedora, not Ubuntu.

If you (or anyone else) find a solution on how to turn the kill switch off, I'll be really happy.

Btw. The laptop is made by compal.  There are a few BIOS updates here: 
[http://www.asimobile.com/notebook_vbi_support.htm](http://www.asimobile.com/notebook_vbi_support.htm)
But none of these will give any options for the wireless card in BIOS.

Unfortunately Whitebox.no are out of business, so there is not much we can do to get support from them either.

---

### Post by chili555 on 2007-03-17
My shiny new Lenovo T60 is en route with an Intel 3945 on board. You guys have me very worried!

Any of you guys check in the BIOS to see if there is an ENABLE-DISABLE for the wireless switch? If you disable the switch, does the 3945 love you again?

---

### Post by KjetilK on 2007-04-18
After much ado, with whitebox.no going belly-up and some BIOS problems causing me to send it back, I have now a nearly working Compal HGL30.

Still, the kill switch problem remains. It is clearly a hardware switch, that is how it is documented. cat /sys/bus/pci/drivers/ipw3945/0000\:02\:00.0/rf_kill returns 2

And I just can't find any way to toggle it...

Has anybody got any progress on this topic?

---

### Post by KjetilK on 2007-04-18
OMG, I found that [AcerHK]("http://www.cakey.de/acerhk/") would do the trick in many cases, but when I try, it says that it doesn't support this system.

So this seems really bad...

---

### Post by Olen on 2007-05-24
One step closer!
:D:D:D

Today, I managed to get past the "Kill switch"-problem.
Thanks to the tip about acerhk, I read the docs there, and found the right keycode.

With a "setkeycodes e004 147" I managed to turn off the kill switch with Fn-F2

Then I could rmmod iwl3945 (this is Fedora Development, mind you) and modprobe iwl3945 again:

```

iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 0.0.16kd
iwl3945: Copyright(c) 2003-2007 Intel Corporation
ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 19
PCI: Setting latency timer of device 0000:02:00.0 to 64
iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
iwl3945: Channel 14 [2.4GHz] is Tx only -- skipping.
iwl3945: Channel 183 [5.2GHz] is Tx only -- skipping.
iwl3945: Channel 184 [5.2GHz] is Tx only -- skipping.
iwl3945: Channel 185 [5.2GHz] is Tx only -- skipping.
iwl3945: Channel 187 [5.2GHz] is Tx only -- skipping.
iwl3945: Channel 188 [5.2GHz] is Tx only -- skipping.
iwl3945: Channel 189 [5.2GHz] is Tx only -- skipping.
iwl3945: Channel 192 [5.2GHz] is Tx only -- skipping.
iwl3945: Channel 196 [5.2GHz] is Tx only -- skipping.
iwl3945: Channel 7 [5.2GHz] is Tx only -- skipping.
iwl3945: Channel 8 [5.2GHz] is Tx only -- skipping.
iwl3945: Channel 11 [5.2GHz] is Tx only -- skipping.
iwl3945: Channel 12 [5.2GHz] is Tx only -- skipping.
iwl3945: Channel 16 [5.2GHz] is Tx only -- skipping.
iwl3945: Channel 145 [5.2GHz] is Tx only -- skipping.
iwl3945: Channel 149 [5.2GHz] is Tx only -- skipping.
iwl3945: Channel 153 [5.2GHz] is Tx only -- skipping.
iwl3945: Channel 157 [5.2GHz] is Tx only -- skipping.
iwl3945: Channel 161 [5.2GHz] is Tx only -- skipping.
iwl3945: Channel 165 [5.2GHz] is Tx only -- skipping.
iwl3945: Tunable channels: 13 802.11bg, 23 802.11a channels
wmaster0: Selected rate control algorithm 'iwl-3945-rs'
iwl3945: Error sending POWER_TABLE_CMD: time out after 500ms.
iwl3945: Error sending POWER_TABLE_CMD: time out after 500ms.
iwl3945: Error sending BT_CONFIG: time out after 500ms.
iwl3945: Error sending RXON: time out after 500ms.
iwl3945: Error setting new configuration (-110).

```

I am still not able to actually use the wireless card, as "ifconfig wlan0 up" just gives me an
```

SIOCSIFFLAGS: Input/output error

```

But at least I believe I am on the right track here.

I'll do a few more reboots and tests here, to see if I can actually get it up as well

---

### Post by KjetilK on 2007-06-12
Oh, that's interesting! Did you get all the way, Olen? Hmmm, it doesn't look like I have the iwl3945 module...

---

### Post by neptho on 2007-06-17
On the E1505, at least, you can just enter your BIOS, go down to the bottom for 'hot keys', and disable the hot keys.  This effectively disables the 'kill switch.'

---

### Post by KjetilK on 2007-06-18
Thanks neptho, but I'm afraid there isn't an option for that on my system...

---

### Post by torpedo on 2007-06-19
If you have this problem on a lenovo thinkpad x60s:

hi all. I am posting because this may help somebody. It's ludicrous.

I have been having problems similar to those reported here with my wireless on thinkpad x60s. All of a sudden the wireless was not on network manager. But my wireless device was ok, the driver was loaded, kept on getting no wireless when typing iwconfig. I won't bother you with all the things I tried, but basically it has to do with the

Kill switch must be turned off for wireless networking to work.

business. Well, if you got there, turns out the thinkpad x60s has a f**king physical switch that turns the wireless on and off, it's a tiny thing located in front of the machine, very front towards you, just under the keyboard. For some reason that switch had moved, but I wasn't even aware of its existence. It must have happened while travelling. Turn it on, and ubuntu (at least Feisty) will work beautifully like before.

Unbelievable.

---

### Post by technomaniac on 2007-06-25
I have a [COLOR="Red"][SIZE="5"]Sony Vaio VGN c15.[/SIZE][/COLOR] It has [COLOR="Red"][SIZE="5"]Intel Pro Wireless 3945[/SIZE][/COLOR] on board. EarlierI had installed ubuntu without any problem but now I am getting a strange problem. I have installed Ubuntu with the restricted drivers(for Intel Pro Wirelss) but it refuses to boot.I have been able to boot only once. The [COLOR="Red"][SIZE="5"]problem seems to be related to the IPW 3945[/SIZE][/COLOR]. I have a switch to turn off Wireless. Now when the boot freezes I switch off wireless I get a message "[COLOR="Red"][SIZE="6"]Radio Frequency kill switch is on".[/SIZE][/COLOR] And thats it. Booting does not continue any further. What do I do? I want to run Ubuntu on my system.

---

### Post by darwin_te on 2007-07-16
Hi,

For 7.04 using the latest kernel 2.6.22, I found the following script responsible for setting rf_kill to 2 (hardware radio frequecny off):

/etc/init.d/acpi-support which called:
/usr/share/acpi-support/state-funcs

The script state-funcs checked /sys/class/net/$DEVICE/device/power/state, which has different directory structure in latest kernel, and will flag wireless state as disabled if not found, which in turn will set rf_kill to 2.

Just modify the script state-funcs and it will now work.

---

### Post by Olen on 2007-07-25
Back to square one.
I am no longer able to get past the kill switch problem again.  Not sure when that happened, as I have updated the kernel and iwlwifi-stuff several times since then, but have not tested the wireless card for a while.
:confused:
No matter what position the front switch is in before or after booting, I am told that the Kill Switch is on. And the "setkeycodes"-trick from a few posts back does not seem to work any longer.

I found a new bios on compals website: [http://www.compal.com/asp/driver_dnd/index.htm](http://www.compal.com/asp/driver_dnd/index.htm) (ver. 115A) but there is still nothing in the bios settings to enable or disable anything related to wireless.

---

### Post by KjetilK on 2007-08-08
> **Olen said:**
> Back to square one.
I

Weirdness... I'm going to try to compile myself and see what happens...

---

### Post by AiO/NoCrew on 2007-09-11
Hi there.

I just wanted to share with you that I have solved the problem with the "Kill Switch" on my HP nx9420.

It seems it was just a matter of reseting the BIOS to factory defaults.

Note: This will (obviously) not make the ipw3945 module handle this "feature" any better. But at least you can get your wireless networking up and running.

I hope this will be useful to someone else. Good luck!

//AiO

---

### Post by dogsthat on 2008-02-17
> **torpedo said:**
> If you have this problem on a lenovo thinkpad x60s:
posting because this may help somebody. It's ludicrous... turns out the thinkpad x60s has a f**king physical switch that turns the wireless on and off, ...Turn it on, and ubuntu (at least Feisty) will work beautifully like before.

**Thank you :)** have spent a few hours trying to turn the card on: didn't realise it was a manual switch, explains a helluva lot!!!

---

### Post by GameManK on 2008-03-18
> **darwin_te said:**
> Hi,

For 7.04 using the latest kernel 2.6.22, I found the following script responsible for setting rf_kill to 2 (hardware radio frequecny off):

/etc/init.d/acpi-support which called:
/usr/share/acpi-support/state-funcs

The script state-funcs checked /sys/class/net/$DEVICE/device/power/state, which has different directory structure in latest kernel, and will flag wireless state as disabled if not found, which in turn will set rf_kill to 2.

Just modify the script state-funcs and it will now work.
As of yesterday my killswitch has been stuck ON on hardy.  Editing that script to always return 0 in the first function worked to get wireless back, though it is of course a hack.
Any LP bugs on this?

---


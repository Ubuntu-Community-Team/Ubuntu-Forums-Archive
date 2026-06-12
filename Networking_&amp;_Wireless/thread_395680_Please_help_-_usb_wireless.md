---
title: "Please help - usb wireless"
date: 2007-03-28
forum: Networking &amp; Wireless
---

### Post by mwells on 2007-03-28
Hi all,

I think I am just about at my last stand now :( .. I have followed [this]("http://ubuntuforums.org/showthread.php?p=2352451#post2352451") excellent howto, to install my Linksys WUSB54GSv2.1.

It seemed to be going ok, The power light comes on, the thing connects (Network manager wont work with it, buts that ok I can configure manually) . .so all is sitting pretty . . however then, after an indiscriminate time it will all of a sudden stop working!! . . I have googled and googled and googled but no avail!

This is the output of dmesg on startup;

```

[17179593.036000] ndiswrapper version 1.39 loaded (smp=yes)
[17179593.188000] usb 4-6: reset high speed USB device using ehci_hcd and address 3
[17179593.340000] ndiswrapper: driver wusb54gsv2 (Linksys,01/25/2005, 4.01.20.0) loaded
[17179593.852000] wlan0: ethernet device 00:18:39:0e:9e:88 using NDIS driver: wusb54gsv2, version: 0x4011405, NDIS version: 0x501, vendor: 'Linksys Wireless-G USB Network Adapter with SpeedBooster', 13B1:0014.F.conf
[17179593.868000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[17179593.880000] usbcore: registered new driver ndiswrapper
[17179593.924000] Adding 1510068k swap on /dev/disk/by-uuid/bc418f06-6cd9-4507-8a2d-3f176761db46.  Priority:-1 extents:1 across:1510068k
[17179594.008000] EXT3 FS on hdb1, internal journal
[17179594.252000] NTFS driver 2.1.27 [Flags: R/O MODULE].
[17179594.304000] NTFS volume version 3.1.
[17179594.332000] NTFS volume version 3.1.
[17179595.056000] NET: Registered protocol family 17
[17179595.580000] ACPI: Power Button (FF) [PWRF]
[17179595.580000] ACPI: Power Button (CM) [PWRB]
[17179595.704000] ibm_acpi: ec object not found
[17179595.736000] pcc_acpi: loading...
[17179598.112000] [drm] Initialized drm 1.0.1 20051102
[17179598.152000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 209
[17179598.156000] [drm] Initialized radeon 1.25.0 20060524 on minor 0
[17179598.820000] mtrr: 0xe0000000,0x8000000 overlaps existing 0xe0000000,0x4000000
[17179598.824000] mtrr: 0xe0000000,0x8000000 overlaps existing 0xe0000000,0x4000000
[17179598.824000] mtrr: 0xe0000000,0x8000000 overlaps existing 0xe0000000,0x4000000
[17179598.824000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[17179598.824000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 1x mode
[17179598.824000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 1x mode
[17179599.164000] [drm] Setting GART location based on new memory map
[17179599.164000] [drm] Loading R200 Microcode
[17179599.164000] [drm] writeback test succeeded in 1 usecs
[17179602.812000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[17179602.812000] apm: overridden by ACPI.
[17179606.340000] eth0: link down
[17179681.080000] hda: cdrom_pc_intr: The drive appears confused (ireason = 0x01)

```

Below is the syslog over the time period that it dies . 

```

Mar 28 19:58:43 server1 kernel: [17181614.048000] usb 4-6: USB disconnect, address 3
Mar 28 19:59:26 server1 kernel: [17181657.880000] ndiswrapper (miniport_reset:72): wlan0 is being reset
Mar 28 19:59:34 server1 kernel: [17181665.880000] ndiswrapper (miniport_reset:72): wlan0 is being reset
Mar 28 19:59:42 server1 kernel: [17181673.880000] ndiswrapper (miniport_reset:72): wlan0 is being reset
Mar 28 19:59:50 server1 kernel: [17181681.880000] ndiswrapper (miniport_reset:72): wlan0 is being reset
Mar 28 19:59:58 server1 kernel: [17181689.880000] ndiswrapper (miniport_reset:72): wlan0 is being reset
Mar 28 20:00:06 server1 kernel: [17181697.880000] ndiswrapper (miniport_reset:72): wlan0 is being reset
Mar 28 20:00:14 server1 kernel: [17181705.880000] ndiswrapper (miniport_reset:72): wlan0 is being reset
Mar 28 20:00:22 server1 kernel: [17181713.880000] ndiswrapper (miniport_reset:72): wlan0 is being reset
Mar 28 20:00:30 server1 kernel: [17181721.880000] ndiswrapper (miniport_reset:72): wlan0 is being reset
Mar 28 20:00:38 server1 kernel: [17181729.880000] ndiswrapper (miniport_reset:72): wlan0 is being reset

```

I note in the syslog (after the connection has broken) that there is a note saying that the USB has disconnected . .AH! so this is the problem? . .so i google around and find some possible solutions to this . .[like here]("http://ubuntuforums.org/showthread.php?t=81153") . .

But still nothing . .

So please guys, id appreciate some help on this so badly, as i really need this to work :(

Cheers

/Matt

---

### Post by wieman01 on 2007-03-29
What exactly do you mean by "it stops working"? Does the adapter disconnect? Once that happens, please post the results of these commands (save the output in a text file and post it after a network restart):
> iwlist scan
> route
> iwconfig
> sudo /etc/init.d/networking restart

---

### Post by mwells on 2007-03-29
Hi wieman,

Thanks for your reply, I am just about to head off to work now so I shall post these results up when I get back . .

When I say stop working though, i see the "usb disconnected" output in the dmesg/syslog at which point there is no Internet and I have to do a full computer restart to get it back up (though I havn't tried restarting networking)

So I will post them up tonight,

Thanks again

/Matt

---

### Post by wieman01 on 2007-03-29
> **mwells said:**
> Hi wieman,

Thanks for your reply, I am just about to head off to work now so I shall post these results up when I get back . .

When I say stop working though, i see the "usb disconnected" output in the dmesg/syslog at which point there is no Internet and I have to do a full computer restart to get it back up (though I havn't tried restarting networking)

So I will post them up tonight,

Thanks again

/Matt
I see. Perhaps this question is out of my league then, I don't think the requested output will make much of a difference in this case.

---

### Post by mwells on 2007-04-03
Hi all,

Ok . .I have made a bit of a break through, after much much searching I have come accross a number of bugs which hint at ehci_hcd issues . .AHA! . .so I scurry away and hit my box with a 

> 
sudo modprobe -r ehci_hcd


at this point I can now leave my computer and it will stay online without any random disconnects . . . great . .BUT . . i think I could employ some sort of carrier pidgeon relay system which would allow networked computers to comunicate quicker as its frankly god awfully slow . 

So i go away and read a bit about this and discover that I am infact removing the USB2.0 drivers and thus making the system use the USB1.0 drivers to run the card . .this is why its so slow

So my questions to anyone that understands this is . .

1) Why is the usb2.0 driver suddenly disconnecting after a period of time
2) Is there any more diagnostics I can run to try and get any more information

Many thanks

/Matt

---


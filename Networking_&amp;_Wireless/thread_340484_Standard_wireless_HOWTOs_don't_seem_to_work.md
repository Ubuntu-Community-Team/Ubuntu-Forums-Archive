---
title: "Standard wireless HOWTOs don't seem to work"
date: 2007-01-17
forum: Networking &amp; Wireless
---

### Post by coady on 2007-01-17
Hi, I have spend quite a bit of time (following all the information in this forum) trying to get my wireless card to work. But no luck so far. I am not sure if I am doing something wrong, if my hardware is not compatible, or if I have not found the appropriate HOWTO for my hardware. I would really appreciate some guidance.

Here is some relevant information:

```
~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. P4M800CE Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. P4M800CE Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. P4M800CE Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. P4M800CE Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. P4M800CE Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:06.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
00:0c.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
00:0c.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
01:00.0 VGA compatible controller: VIA Technologies, Inc. UniChrome Pro IGP (rev 01)
```
```
~$ sudo iwconfig

lo        no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4318"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.
```
I have tried these wiki/howto's:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Edgy]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Edgy")
[http://ubuntuforums.org/showthread.php?t=185174]("http://ubuntuforums.org/showthread.php?t=185174")

I am using a Fujitsu Siemens Amilo Pro V2030 laptop and a Deutsche Telekom Speedport W 501V router. It uses WPA encryption, so that will be a problem once I get the broadcom wireless card working.

Finally, assuming I get wireless access working, which app do I need to add to show/scan/connect to wireless networks when I am out and about?

Thanks to anyone who can help :)

---

### Post by deejaylinux on 2007-01-17
Try "dmesg" command (as root, that is doing sudo dmesg) after reboot and look for some errors related to your card.

Sometimes, critical errors appears in dmesg output (like problems with firmware).

So, try this and tell us again.

---

### Post by coady on 2007-01-17
I have posted (below) what seems to be the relevant information from"dmesg" (I did not post the full text, just the section that looks like it relates to the wireless card). I can't see any firmware errors (although I recall that if I boot from the Ubuntu LiveCD I get firmware errors relating to the broadcom card).

```
[17179588.056000] ieee80211_crypt: registered algorithm 'NULL'
[17179588.068000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[17179588.068000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[17179588.264000] ACPI: PCI Interrupt 0000:00:0c.0[A] -> GSI 19 (level, low) -> IRQ 177
[17179588.264000] Yenta: CardBus bridge found at 0000:00:0c.0 [1734:109b]
[17179588.264000] Yenta: Enabling burst memory read transactions
[17179588.264000] Yenta: Using CSCINT to route CSC interrupts to PCI
[17179588.264000] Yenta: Routing CardBus interrupts to PCI
[17179588.264000] Yenta TI: socket 0000:00:0c.0, mfunc 0x01ac1b22, devctl 0x64
[17179588.280000] Linux agpgart interface v0.101 (c) Dave Jones
[17179588.412000] bcm43xx driver
[17179588.500000] Yenta: ISA IRQ mask 0x0cf8, PCI irq 177
[17179588.500000] Socket status: 30000411
[17179588.520000] agpgart: Detected VIA P4M800CE chipset
[17179588.540000] agpgart: AGP aperture is 256M @ 0xe0000000
[17179588.540000] PCI: Enabling device 0000:00:06.0 (0000 -> 0002)
[17179588.540000] ACPI: PCI Interrupt 0000:00:06.0[A] -> GSI 18 (level, low) -> IRQ 193
[17179588.844000] via-rhine.c:v1.10-LK1.2.0-2.6 June-10-2004 Written by Donald Becker
[17179588.844000] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 23 (level, low) -> IRQ 209
[17179588.844000] PCI: Via IRQ fixup for 0000:00:12.0, from 10 to 1
[17179588.848000] eth1: VIA Rhine II at 0x12000, 00:40:ca:d8:35:d0, IRQ 209.
[17179588.848000] eth1: MII PHY found at address 1, status 0x786d advertising 05e1 Link 41e1.
[17179588.896000] PCI: Enabling device 0000:00:11.6 (0000 -> 0001)
[17179588.896000] ACPI: PCI Interrupt Link [ALKC] disabled and referenced, BIOS bug
[17179588.896000] ACPI: PCI Interrupt Link [ALKC] BIOS reported IRQ 0, using IRQ 22
[17179588.896000] ACPI: PCI Interrupt Link [ALKC] enabled at IRQ 22
[17179588.896000] ACPI: PCI Interrupt 0000:00:11.6[C] -> Link [ALKC] -> GSI 22 (level, low) -> IRQ 217
[17179588.896000] PCI: Via IRQ fixup for 0000:00:11.6, from 255 to 9
[17179588.900000] PCI: Setting latency timer of device 0000:00:11.6 to 64
[17179589.228000] usbcore: registered new driver hiddev
[17179589.268000] pccard: PCMCIA card inserted into slot 0
[17179589.272000] input: Microsoft Microsoft Optical Mouse with Tilt Wheel as /class/input/input1
[17179589.272000] input: USB HID v1.11 Mouse [Microsoft Microsoft Optical Mouse with Tilt Wheel] on usb-0000:00:10.0-1
[17179589.272000] usbcore: registered new driver usbhid
[17179589.272000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179589.292000] input: PC Speaker as /class/input/input2
[17179589.412000] PCI: Enabling device 0000:00:11.5 (0000 -> 0001)
[17179589.412000] ACPI: PCI Interrupt 0000:00:11.5[C] -> Link [ALKC] -> GSI 22 (level, low) -> IRQ 217
[17179589.412000] PCI: Via IRQ fixup for 0000:00:11.5, from 255 to 9
[17179589.412000] PCI: Setting latency timer of device 0000:00:11.5 to 64
[17179589.652000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[17179589.736000] input: PS/2 Mouse as /class/input/input3
[17179589.756000] input: AlpsPS/2 ALPS GlidePoint as /class/input/input4
[17179589.824000] ts: Compaq touchscreen protocol output
[17179590.188000] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[17179590.336000] cs: IO port probe 0x100-0x3af: clean.
[17179590.336000] cs: IO port probe 0x3e0-0x4ff: clean.
[17179590.336000] cs: IO port probe 0x820-0x8ff: clean.
[17179590.340000] cs: IO port probe 0xc00-0xcf7: clean.
[17179590.340000] cs: IO port probe 0xa00-0xaff: clean.
[17179590.340000] cs: memory probe 0xa0000000-0xa0ffffff: clean.
[17179590.344000] pcmcia: registering new device pcmcia0.0
[17179590.904000] aha152x: resetting bus...
[17179591.260000] aha152x2: vital data: rev=1, io=0x340 (0x340/0x340), irq=3, scsiid=7, reconnect=enabled, parity=enabled, synchronous=enabled, delay=100, extended translation=disabled
[17179591.316000] aha152x2: trying software interrupt, ok.
[17179592.316000] NET: Registered protocol family 17
[17179592.316000] scsi2 : Adaptec 152x SCSI driver; $Revision: 2.7 $
[17179592.592000] NET: Registered protocol family 10
[17179592.592000] lo: Disabled Privacy Extensions
[17179592.592000] IPv6 over IPv4 tunneling driver
[17179592.652000] lp: driver loaded but no devices found
[17179592.680000] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
[17179592.680000] ieee1394: sbp2: Try serialize_io=0 for better performance
```
Thanks, coady

---

### Post by coady on 2007-01-18
Hi, I have continued reading the posts in this forum and discovered that there is a very long and ongoing post about the dreaded bcm4318 wireless chipset (which I have).

Once I have read this in detail and tried the various options, I will re-post if I need to. Sorry for posting the above question too quickly :) 
coady

---

### Post by fancyydk on 2007-01-19
hi coady

I feel your pain mate. I have that infamous chip as well. After days and days of failure, I finally got mine working though. I knew it had to work because it worked fine in dapper. For some weird reason, when I upgraded my system to Edgy, it wouldn't want to work and sometimes froze the system!

So, what fixed my problem? It was the kernel that came with the initial release of Edgy. Go to [www.kernel.org](www.kernel.org) and download and install the newest kernel, which I believe is 2.6.19.2. The default kernel that came with Edgy is 2.6.17.something. There are many posts regarding how to update the kernel, so refer to those and if you have a problem with the new kernel, you will always be able to come back to the old kernel unless you delete the option in grub.

After installing the new kernel, go back and follow the great many how-to's on enabling bcm4318 again. Hopefully you'll have success by then.

Good luck!

---

### Post by coady on 2007-01-19
@ fancyydk,
Thanks so much for posting your reply (you must have picked up the tone of fatal resignation in my previous comment). I will follow your advice and see how what happens.

Incidently, in your case, did you finally use the fwcutter method or the ndsiwrapper method?

Thanks again. This kind of mutual help and support is one of the reasons I switched to linux and the ubuntu community is one of the best! ;) 

coady

---

### Post by dsegarra on 2007-01-19
coady

I was able to setup a Broadcom4318 on a 386 platform using ndiswrapper. I wasnt able to set up the same card under x86 though. My card was a linksys WMP54GS. But yea I did noticed that the kernel that Edgy ships kind of sucks or totally.. The key for me was to disable the broadcom 43xx driver that edgy ships so it wouldnt load on startup.

```
sudo gedit /etc/modprobe.d/blacklist
blacklist bcm43xx
sudo rmmod bcm43xx
sudo ndiswrapper -i /location_of_your_wireless_driver/wmp54gs.inf
```

Then start it with

```
modprobe ndiswrapper
```


[URL="http://www.ubuntuforums.org/showthread.php?
t=285809&highlight=blacklist+broadcom+43xx"]http://www.ubuntuforums.org/showthread.php?t=285809&highlight=blacklist+broadcom+43xx[/URL]

Hope this helps

Dan

---

### Post by fancyydk on 2007-01-20
No problem at all. I myself got a lot of help from this forum and I wouldn't have been able to come all the way up to this point without all the help from other people.

I ended up using NDISwrapper. I tried the fwcutter method before I updated the kernel and it didn't work and I had been very frustrated at that moment. So after I updated the kernel, I just installed NDISwrapper, which I knew should work in any case. Had the NDISwrapper method not worked, I would've probably gone mad, but fortunately, it worked like a charm :). So up to this point, I've been using NDISwrapper. I will try the fwcutter method again when I reformat my computer and reinstall Ubuntu.

I'll be glad to help. Just let me know :)

---

### Post by fancyydk on 2007-01-20
oh yeah, just a warning here. When I used fwcutter and the built-in bcm43xx driver on the kernel that came with Edgy (2.6.17), it choked my laptop and froze the system at bootup and I had to reformat and reinstall Ubuntu. So you might want to blacklist bcm43xx as dsegarra said. But then I don't know if it will work on 2.6.19. Who knows? It might work seamlessly. So if you're brave enough, you might want to try it after upgrading the kernel ;) Let me know how it goes.

---


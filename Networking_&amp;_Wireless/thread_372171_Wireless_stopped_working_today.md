---
title: "Wireless stopped working today"
date: 2007-02-27
forum: Networking &amp; Wireless
---

### Post by ayasin on 2007-02-27
I have a serious problem.  Bear with me as I'm relatively new to linux, I'll post as much useful info as I can think of. 

I recently (last night) installed xen (2.6.17-6 kernel) via apt-get using a how-to here.  After that I haven't been able to get my wireless to work.  The light doesn't come on (although it does under windows so it's not a hardware issue) and I don't see eth1 at all if I type ifconfig.

Here is the output from lspci:
```

ou00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
	Subsystem: Dell Unknown device 01cd
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: dd000000-dfefffff
	Prefetchable memory behind bridge: 00000000c0000000-00000000cff00000
	Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
	Subsystem: Dell Unknown device 01cd
	Flags: bus master, fast devsel, latency 0, IRQ 20
	Memory at dfffc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0b, subordinate=0b, sec-latency=0
	Capabilities: <access denied>

00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0c, subordinate=0c, sec-latency=0
	Memory behind bridge: dcf00000-dcffffff
	Capabilities: <access denied>

00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0d, subordinate=0e, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: dcc00000-dcefffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000d0100000
	Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01) (prog-if 00 [UHCI])
	Subsystem: Dell Unknown device 01cd
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at bf80 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01) (prog-if 00 [UHCI])
	Subsystem: Dell Unknown device 01cd
	Flags: bus master, medium devsel, latency 0, IRQ 20
	I/O ports at bf60 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01) (prog-if 00 [UHCI])
	Subsystem: Dell Unknown device 01cd
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at bf40 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01) (prog-if 00 [UHCI])
	Subsystem: Dell Unknown device 01cd
	Flags: bus master, medium devsel, latency 0, IRQ 22
	I/O ports at bf20 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01) (prog-if 20 [EHCI])
	Subsystem: Dell Unknown device 01cd
	Flags: bus master, medium devsel, latency 0, IRQ 19
	Memory at ffa80000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=32
	Memory behind bridge: dcb00000-dcbfffff
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
	Subsystem: Dell Unknown device 01cd
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>

00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 01) (prog-if 80 [Master])
	Subsystem: Dell Unknown device 01cd
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 17
	I/O ports at <ignored>
	I/O ports at <ignored>
	I/O ports at <ignored>
	I/O ports at <ignored>
	I/O ports at bfa0 [size=16]
	Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
	Subsystem: Dell Unknown device 01cd
	Flags: medium devsel, IRQ 5
	I/O ports at 10c0 [size=32]

01:00.0 VGA compatible controller: nVidia Corporation GeForce Go 7900 GS (rev a1) (prog-if 00 [VGA])
	Subsystem: Dell Unknown device 019b
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at dd000000 (32-bit, non-prefetchable) [size=16M]
	Memory at c0000000 (64-bit, prefetchable) [size=256M]
	Memory at de000000 (64-bit, non-prefetchable) [size=16M]
	I/O ports at ef00 [size=128]
	[virtual] Expansion ROM at dfe00000 [disabled] [size=128K]
	Capabilities: <access denied>

03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
	Subsystem: Dell Unknown device 01cd
	Flags: fast devsel, IRQ 17
	Memory at dcbfe000 (32-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>

03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (prog-if 10 [OHCI])
	Subsystem: Dell Unknown device 01cd
	Flags: bus master, medium devsel, latency 64, IRQ 18
	Memory at dcbfd800 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>

03:01.1 Class 0805: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19) (prog-if 01)
	Subsystem: Dell Unknown device 01cd
	Flags: bus master, medium devsel, latency 64, IRQ 23
	Memory at dcbfd400 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

03:01.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
	Subsystem: Dell Unknown device 01cd
	Flags: bus master, medium devsel, latency 0, IRQ 9
	Memory at dcbfd500 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
	Subsystem: Dell Unknown device 01cd
	Flags: medium devsel, IRQ 9
	Memory at dcbfd600 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
	Subsystem: Dell Unknown device 01cd
	Flags: medium devsel, IRQ 9
	Memory at dcbfd700 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
	Subsystem: Intel Corporation Unknown device 1020
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at dcfff000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

```

Here is the output from lsmod:

```

Module                  Size  Used by
eth1394                21508  0 
binfmt_misc            13448  1 
rfcomm                 42260  6 
l2cap                  27136  5 rfcomm
cpufreq_userspace       5408  0 
cpufreq_stats           7744  0 
freq_table              6048  1 cpufreq_stats
cpufreq_powersave       2944  0 
cpufreq_ondemand        8876  0 
cpufreq_conservative     8712  0 
video                  17540  0 
tc1100_wmi              8324  0 
sbs                    16804  0 
sony_acpi               6412  0 
pcc_acpi               14080  0 
i2c_ec                  6272  1 sbs
hotkey                 11556  0 
ipv6                  272544  10 
dev_acpi               12292  0 
button                  7952  0 
battery                11652  0 
container               5632  0 
ac                      6788  0 
asus_acpi              17688  0 
af_packet              24584  2 
fuse                   43912  2 
sbp2                   25736  0 
parport_pc             37796  0 
lp                     12964  0 
parport                39752  2 parport_pc,lp
joydev                 11200  0 
tsdev                   9152  0 
usb_storage            75456  0 
sr_mod                 18212  0 
libusual               17040  1 usb_storage
hci_usb                18068  6 
sg                     37404  0 
ipw3945               124832  0 
cdrom                  38944  1 sr_mod
ieee80211              35272  1 ipw3945
ieee80211_crypt         7552  1 ieee80211
bluetooth              53476  15 rfcomm,l2cap,hci_usb
usbhid                 45408  0 
nvidia               6824052  32 
asix                   14080  0 
usbnet                 18568  1 asix
b44                    28940  0 
sdhci                  20108  0 
mmc_core               32776  1 sdhci
mii                     6912  2 asix,b44
snd_hda_intel          20372  1 
snd_hda_codec         164608  1 snd_hda_intel
snd_pcm_oss            47744  0 
i2c_core               23424  2 i2c_ec,nvidia
snd_mixer_oss          19584  1 snd_pcm_oss
snd_pcm                86532  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer              25988  1 snd_pcm
psmouse                41608  0 
serio_raw               8452  0 
pcspkr                  4352  0 
evdev                  11392  5 
intel_agp              26780  1 
agpgart                36296  2 nvidia,intel_agp
hw_random               7320  0 
shpchp                 41888  0 
pci_hotplug            32828  1 shpchp
snd                    58756  8 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              11232  1 snd
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
ext3                  142728  1 
jbd                    62228  1 ext3
ohci1394               37040  0 
ieee1394              306616  3 eth1394,sbp2,ohci1394
ide_generic             2432  0 
ehci_hcd               35080  0 
uhci_hcd               25608  0 
usbcore               136320  9 usb_storage,libusual,hci_usb,usbhid,asix,usbnet,ehci_hcd,uhci_hcd
sd_mod                 22656  4 
generic                 5764  0 
ata_piix               11780  3 
libata                 75020  1 ata_piix
scsi_mod              145160  6 sbp2,usb_storage,sr_mod,sg,sd_mod,libata
thermal                15624  0 
processor              31688  1 thermal
fan                     6020  0 
fbcon                  41504  0 
tileblit                3840  1 fbcon
font                    9344  1 fbcon
bitblit                 7168  1 fbcon
softcursor              3328  1 bitblit
vesafb                  9244  0 
cfbcopyarea             4992  1 vesafb
cfbimgblt               3968  1 vesafb
cfbfillrect             5248  1 vesafb
capability              5896  0 
commoncap               8704  1 capability

```

I manually added eth1394 via modprobe (mostly out of desperation) but still got nowhere.  I'm at a wall, I've searched for hours on the net and haven't been able to find an answer.  I'm hoping it's just some noob config thing I'm missing.  Anyone have any ideas?

Thanks in advance.

---

### Post by tgalati4 on 2007-02-27
Well from your post, it looks like you have an on-board Intel Pro wireless chipset.  Did you try searching the forum for Intel 3945ABG and see what module is supposed to be loaded.

When you find it, you can load it manually by:

sudo modprobe myintelwirelessdriverthatIfoundusingforumsearch

Then see if you get any response with:

ifconfig

and

iwconfig

Good luck!

---

### Post by ayasin on 2007-02-27
Thanks for your reply.  The driver for the wireless card I have is the ipw3945 driver.  It is already loaded (I added it to /etc/modules just to be sure).  Still no joy.

---

### Post by tgalati4 on 2007-02-28
You're right.  It is loaded and connected to the 802.11 sub drivers.  Did you do a google search to see if there is generic problem with the ipw3945 driver?

Perhaps you can blacklist it and use a windows driver with ndiswrapper.

Add to /etc/modprobe.d/blacklist

blacklist ipw3945

then

sudo ndiswrapper -i intelwirelessdriverthatIcopiedfromwindowsandputinmylocaldirectory.inf

Good luck.

---


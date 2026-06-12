---
title: "Toshiba Satellite S-video not working"
date: 2011-06-05
forum: New to Ubuntu
---

### Post by Bowman9709 on 2011-06-05
I am using ubuntu 10.10 I have a toshiba satellite A105-s2712 Im trying to get the s-video output to tv to work. I have tried the Monitors applaction but no good. Also i have tried Fn + F5 witch changes the screen i know this works because the vga out works. But all i get is a flicker every now and then. I know that it has an intel gpu but no luck finding any thing. The sooner i find this out the sooner the kids can watch there shows again.

---

### Post by ubudog on 2011-06-05
For more info, could you please type this in a terminal (Applications>Accessories>Terminal) and post the output here?  

```
lspci
```

---

### Post by woodmaster on 2011-06-05
same problem here, same laptop going s-video out to a sylvania flatscreen tv.  lspci gives:

```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
04:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
06:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
06:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
06:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
06:04.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller

```monitor app shows an unknown monitor for me...ubuntu 11.04, same with either classic or unity.  Fn+F5 flashes the video onto my tv, but then it goes away and back to the laptop screen

---

### Post by Bowman9709 on 2011-06-06
```
 00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 04)
01:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8036 PCI-E Fast Ethernet Controller (rev 10)
05:04.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
05:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
05:06.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
05:06.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
05:06.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD 
```

sry forgot to do that

---

### Post by ubudog on 2011-06-06
Hmm, all I can think of is running the dmesg command right after it flickers.  

```
dmesg
```

Post the output of that, right after the screen flickers.  It may give us some more info.

---

### Post by Bowman9709 on 2011-06-07
Ok since the last post i updated to 11.04 read somewhere that there were drivers but couldn't find them but now when i push Fn+F5 it switches to the resolution for same picture on all but no picture on the tv

This is what i got from dmesg```
[   17.765166] type=1400 audit(1307454392.611:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=520 comm="apparmor_parser"
[   17.766144] type=1400 audit(1307454392.611:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=520 comm="apparmor_parser"
[   17.766757] type=1400 audit(1307454392.611:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=520 comm="apparmor_parser"
[   17.767726] type=1400 audit(1307454392.611:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=519 comm="apparmor_parser"
[   17.768715] type=1400 audit(1307454392.615:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=519 comm="apparmor_parser"
[   17.769325] type=1400 audit(1307454392.615:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=519 comm="apparmor_parser"
[   17.770997] type=1400 audit(1307454392.615:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=638 comm="apparmor_parser"
[   17.771946] type=1400 audit(1307454392.615:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=638 comm="apparmor_parser"
[   17.772802] type=1400 audit(1307454392.619:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=638 comm="apparmor_parser"
[   20.520020] hda-intel: azx_get_response timeout, switching to polling mode: last cmd=0x000f0000
[   20.790776] hda_codec: ALC861: BIOS auto-probing.
[   23.223081] type=1400 audit(1307454398.067:11): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=843 comm="apparmor_parser"
[   23.226945] type=1400 audit(1307454398.071:12): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=844 comm="apparmor_parser"
[   23.227928] type=1400 audit(1307454398.071:13): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=844 comm="apparmor_parser"
[   23.228729] type=1400 audit(1307454398.075:14): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=844 comm="apparmor_parser"
[   23.581049] type=1400 audit(1307454398.427:15): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=845 comm="apparmor_parser"
[   23.596368] type=1400 audit(1307454398.443:16): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=845 comm="apparmor_parser"
[   23.610707] type=1400 audit(1307454398.455:17): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-thumbnailer" pid=845 comm="apparmor_parser"
[   23.719222] sky2 0000:01:00.0: eth0: enabling interface
[   23.730261] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   23.866650] type=1400 audit(1307454398.711:18): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=848 comm="apparmor_parser"
[   23.867792] type=1400 audit(1307454398.711:19): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=848 comm="apparmor_parser"
[   24.014024] type=1400 audit(1307454398.859:20): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=861 comm="apparmor_parser"
[   24.096904] ppdev: user-space parallel port driver
[   29.625933] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   34.608025] eth1: no IPv6 routers present
[   41.846287] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[  210.556681] lib80211_crypt: registered algorithm 'WEP'
[ 4973.420277] sky2 0000:01:00.0: eth0: disabling interface
[ 4975.012829] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[ 4977.174883] PM: Syncing filesystems ... done.
[ 4977.176201] PM: Preparing system for mem sleep
[ 4977.293753] Freezing user space processes ... (elapsed 0.01 seconds) done.
[ 4977.308127] Freezing remaining freezable tasks ... (elapsed 0.01 seconds) done.
[ 4977.324097] PM: Entering mem sleep
[ 4977.324117] Suspending console(s) (use no_console_suspend to debug)
[ 4977.324775] sd 0:0:0:0: [sda] Synchronizing SCSI cache
[ 4977.386236] i8042 kbd 00:07: wake-up capability enabled by ACPI
[ 4977.386749] ACPI handle has no context!
[ 4977.386761] sdhci-pci 0000:05:06.3: PCI INT C disabled
[ 4977.386768] ACPI handle has no context!
[ 4977.386836] ACPI handle has no context!
[ 4977.386844] tifm_7xx1 0000:05:06.2: PCI INT C disabled
[ 4977.386851] ACPI handle has no context!
[ 4977.386959] eth1: Going into suspend...
[ 4977.387069] ehci_hcd 0000:00:1d.7: PCI INT A disabled
[ 4977.387152] ipw2200 0000:05:04.0: PCI INT A disabled
[ 4977.387159] ACPI handle has no context!
[ 4977.387166] uhci_hcd 0000:00:1d.3: PCI INT D disabled
[ 4977.387181] uhci_hcd 0000:00:1d.2: PCI INT C disabled
[ 4977.387196] uhci_hcd 0000:00:1d.1: PCI INT B disabled
[ 4977.387209] uhci_hcd 0000:00:1d.0: PCI INT A disabled
[ 4977.388053] i915 0000:00:02.0: PCI INT A disabled
[ 4977.416462] sd 0:0:0:0: [sda] Stopping disk
[ 4977.592103] HDA Intel 0000:00:1b.0: PCI INT A disabled
[ 4977.608027] PM: suspend of drv:HDA Intel dev:0000:00:1b.0 complete after 220.796 msecs
[ 4977.859750] PM: suspend of drv:sd dev:0:0:0:0 complete after 534.978 msecs
[ 4977.859759] PM: suspend of drv:scsi dev:target0:0:0 complete after 534.862 msecs
[ 4977.859766] PM: suspend of drv:scsi dev:host0 complete after 473.110 msecs
[ 4977.859862] ata_piix 0000:00:1f.2: PCI INT B disabled
[ 4977.872027] PM: suspend of drv:ata_piix dev:0000:00:1f.2 complete after 485.026 msecs
[ 4977.872037] PM: suspend of drv: dev:pci0000:00 complete after 483.952 msecs
[ 4977.872044] PM: suspend of devices complete after 547.665 msecs
[ 4977.872047] PM: suspend devices took 0.548 seconds
[ 4978.028044] PM: late suspend of drv:sky2 dev:0000:01:00.0 complete after 155.543 msecs
[ 4978.044235] PM: late suspend of devices complete after 172.183 msecs
[ 4978.044675] ACPI: Preparing to enter system sleep state S3
[ 4978.067437] PM: Saving platform NVS memory
[ 4978.067467] Disabling non-boot CPUs ...
[ 4978.067467] Back to C!
[ 4978.067467] PM: Restoring platform NVS memory
[ 4978.067467] Force enabled HPET at resume
[ 4978.068238] ACPI: Waking up from system sleep state S3
[ 4978.102181] uhci_hcd 0000:00:1d.0: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
[ 4978.102207] uhci_hcd 0000:00:1d.1: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
[ 4978.102232] uhci_hcd 0000:00:1d.2: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
[ 4978.102257] uhci_hcd 0000:00:1d.3: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
[ 4978.102289] ehci_hcd 0000:00:1d.7: restoring config space at offset 0x1 (was 0x2900000, writing 0x2900002)
[ 4978.102369] ata_piix 0000:00:1f.2: restoring config space at offset 0x1 (was 0x2b80001, writing 0x2b00005)
[ 4978.156301] power_supply BAT1: parent PNP0C0A:00 should not be sleeping
[ 4978.256031] sky2 0000:01:00.0: BAR 0: set to [mem 0xcc000000-0xcc003fff 64bit] (PCI address [0xcc000000-0xcc003fff])
[ 4978.256039] sky2 0000:01:00.0: BAR 2: set to [io  0xc000-0xc0ff] (PCI address [0xc000-0xc0ff])
[ 4978.256064] sky2 0000:01:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
[ 4978.256087] sky2 0000:01:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x4)
[ 4978.256095] sky2 0000:01:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100007)
[ 4978.256118] PM: early resume of drv:sky2 dev:0000:01:00.0 complete after 153.737 msecs
[ 4978.256133] ipw2200 0000:05:04.0: restoring config space at offset 0xf (was 0x18030100, writing 0x1803010b)
[ 4978.256150] ipw2200 0000:05:04.0: restoring config space at offset 0x4 (was 0x0, writing 0xb800a000)
[ 4978.256156] ipw2200 0000:05:04.0: restoring config space at offset 0x3 (was 0x0, writing 0x8000)
[ 4978.256163] ipw2200 0000:05:04.0: restoring config space at offset 0x1 (was 0x2900000, writing 0x2900006)
[ 4978.256183] yenta_cardbus 0000:05:06.0: restoring config space at offset 0xf (was 0x34001ff, writing 0x5c001ff)
[ 4978.256189] yenta_cardbus 0000:05:06.0: restoring config space at offset 0xe (was 0x0, writing 0x84fc)
[ 4978.256195] yenta_cardbus 0000:05:06.0: restoring config space at offset 0xd (was 0x0, writing 0x8400)
[ 4978.256201] yenta_cardbus 0000:05:06.0: restoring config space at offset 0xc (was 0x0, writing 0x80fc)
[ 4978.256207] yenta_cardbus 0000:05:06.0: restoring config space at offset 0xb (was 0x0, writing 0x8000)
[ 4978.256213] yenta_cardbus 0000:05:06.0: restoring config space at offset 0xa (was 0x0, writing 0xbffff000)
[ 4978.256219] yenta_cardbus 0000:05:06.0: restoring config space at offset 0x9 (was 0x0, writing 0xbc000000)
[ 4978.256224] yenta_cardbus 0000:05:06.0: restoring config space at offset 0x8 (was 0x0, writing 0x8bfff000)
[ 4978.256230] yenta_cardbus 0000:05:06.0: restoring config space at offset 0x7 (was 0x0, writing 0x88000000)
[ 4978.256240] yenta_cardbus 0000:05:06.0: restoring config space at offset 0x3 (was 0x820010, writing 0x82a810)
[ 4978.256291] firewire_ohci 0000:05:06.1: restoring config space at offset 0x3 (was 0x800004, writing 0x808004)
[ 4978.256313] tifm_7xx1 0000:05:06.2: restoring config space at offset 0xf (was 0x40703ff, writing 0x407030b)
[ 4978.256330] tifm_7xx1 0000:05:06.2: restoring config space at offset 0x4 (was 0x0, writing 0xb8008000)
[ 4978.256336] tifm_7xx1 0000:05:06.2: restoring config space at offset 0x3 (was 0x800000, writing 0x808004)
[ 4978.256343] tifm_7xx1 0000:05:06.2: restoring config space at offset 0x1 (was 0x2100000, writing 0x2100006)
[ 4978.256362] sdhci-pci 0000:05:06.3: restoring config space at offset 0xf (was 0x40703ff, writing 0x407030b)
[ 4978.256380] sdhci-pci 0000:05:06.3: restoring config space at offset 0x4 (was 0x0, writing 0xb8009000)
[ 4978.256385] sdhci-pci 0000:05:06.3: restoring config space at offset 0x3 (was 0x800000, writing 0x808004)
[ 4978.256392] sdhci-pci 0000:05:06.3: restoring config space at offset 0x1 (was 0x2100000, writing 0x2100006)
[ 4978.256848] PM: early resume of devices complete after 154.938 msecs
[ 4978.260096] i915 0000:00:02.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[ 4978.260100] i915 0000:00:02.0: setting latency timer to 64
[ 4978.310578] HDA Intel 0000:00:1b.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[ 4978.310584] HDA Intel 0000:00:1b.0: setting latency timer to 64
[ 4978.310621] HDA Intel 0000:00:1b.0: irq 18 for MSI/MSI-X
[ 4978.310670] uhci_hcd 0000:00:1d.0: PCI INT A -> Link[LNKH] -> GSI 10 (level, low) -> IRQ 10
[ 4978.310676] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[ 4978.310698] usb usb2: root hub lost power or was reset
[ 4978.310712] uhci_hcd 0000:00:1d.1: PCI INT B -> Link[LNKD] -> GSI 10 (level, low) -> IRQ 10
[ 4978.310718] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[ 4978.310738] usb usb3: root hub lost power or was reset
[ 4978.310750] uhci_hcd 0000:00:1d.2: PCI INT C -> Link[LNKC] -> GSI 9 (level, low) -> IRQ 9
[ 4978.310755] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[ 4978.310776] usb usb4: root hub lost power or was reset
[ 4978.310787] uhci_hcd 0000:00:1d.3: PCI INT D -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[ 4978.310793] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[ 4978.310813] usb usb5: root hub lost power or was reset
[ 4978.310826] ehci_hcd 0000:00:1d.7: PCI INT A -> Link[LNKH] -> GSI 10 (level, low) -> IRQ 10
[ 4978.310832] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[ 4978.310873] pci 0000:00:1e.0: setting latency timer to 64
[ 4978.310887] ata_piix 0000:00:1f.2: PCI INT B -> Link[LNKD] -> GSI 10 (level, low) -> IRQ 10
[ 4978.310892] ata_piix 0000:00:1f.2: setting latency timer to 64
[ 4978.310948] eth1: Coming out of suspend...
[ 4978.310956] ipw2200 0000:05:04.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[ 4978.310983] tifm_7xx1 0000:05:06.2: PCI INT C -> Link[LNKG] -> GSI 6 (level, low) -> IRQ 6
[ 4978.311000] sdhci-pci 0000:05:06.3: PCI INT C -> Link[LNKG] -> GSI 6 (level, low) -> IRQ 6
[ 4978.324102] sd 0:0:0:0: [sda] Starting disk
[ 4978.396076] PM: resume of drv:i915 dev:0000:00:02.0 complete after 135.987 msecs
[ 4978.428029] PM: resume of drv:usb dev:usb2 complete after 116.965 msecs
[ 4978.428045] PM: resume of drv:usb dev:usb3 complete after 116.966 msecs
[ 4978.428054] PM: resume of drv:hub dev:2-0:1.0 complete after 116.985 msecs
[ 4978.428060] PM: resume of drv: dev:ep_00 complete after 116.985 msecs
[ 4978.428065] PM: resume of drv:hub dev:3-0:1.0 complete after 116.911 msecs
[ 4978.428071] PM: resume of drv: dev:ep_00 complete after 112.027 msecs
[ 4978.428076] PM: resume of drv: dev:ep_81 complete after 117.004 msecs
[ 4978.428081] PM: resume of drv: dev:ep_81 complete after 112.057 msecs
[ 4978.436026] PM: resume of drv:usb dev:usb4 complete after 119.964 msecs
[ 4978.436036] PM: resume of drv:hub dev:4-0:1.0 complete after 119.954 msecs
[ 4978.436041] PM: resume of drv: dev:ep_00 complete after 115.950 msecs
[ 4978.436046] PM: resume of drv: dev:ep_81 complete after 115.974 msecs
[ 4978.440027] PM: resume of drv:usb dev:usb5 complete after 119.918 msecs
[ 4978.440036] PM: resume of drv:hub dev:5-0:1.0 complete after 115.992 msecs
[ 4978.440042] PM: resume of drv: dev:ep_00 complete after 115.963 msecs
[ 4978.440047] PM: resume of drv: dev:ep_81 complete after 115.985 msecs
[ 4978.650443] PM: resume of drv:ac dev:ACPI0003:00 complete after 339.299 msecs
[ 4978.712361] firewire_core: skipped bus generations, destroying all nodes
[ 4978.760246] PM: resume of drv:battery dev:PNP0C0A:00 complete after 109.796 msecs
[ 4978.776466] ata2.00: ACPI cmd ef/03:0c:00:00:00:a0 (SET FEATURES) filtered out
[ 4978.776471] ata2.00: ACPI cmd ef/03:42:00:00:00:a0 (SET FEATURES) filtered out
[ 4978.792375] ata2.00: configured for UDMA/33
[ 4978.800123] i8042 kbd 00:07: wake-up capability disabled by ACPI
[ 4979.212047] firewire_core: rediscovered device fw0
[ 4980.556269] ata1.00: ACPI cmd ef/03:0c:00:00:00:a0 (SET FEATURES) filtered out
[ 4980.556273] ata1.00: ACPI cmd ef/03:45:00:00:00:a0 (SET FEATURES) filtered out
[ 4980.572523] ata1.00: configured for UDMA/100
[ 4980.587575] PM: resume of drv:sd dev:0:0:0:0 complete after 2263.474 msecs
[ 4980.587585] PM: resume of drv:scsi_device dev:0:0:0:0 complete after 2259.546 msecs
[ 4980.587591] PM: resume of drv:scsi_disk dev:0:0:0:0 complete after 1781.068 msecs
[ 4980.724061] PM: resume of drv:pcmcia_socket dev:pcmcia_socket0 complete after 136.411 msecs
[ 4980.724146] PM: resume of devices complete after 2464.121 msecs
[ 4980.724269] PM: resume devices took 2.468 seconds
[ 4980.724309] PM: Finishing wakeup.
[ 4980.724311] Restarting tasks ... done.
[ 4980.742734] video LNXVIDEO:01: Restoring backlight state
[ 4980.951121] sky2 0000:01:00.0: eth0: phy I/O error
[ 4980.951130] sky2 0000:01:00.0: eth0: phy I/O error
[ 4980.951134] sky2 0000:01:00.0: eth0: phy I/O error
[ 4980.951137] sky2 0000:01:00.0: eth0: phy I/O error
[ 4980.951141] sky2 0000:01:00.0: eth0: phy I/O error
[ 4980.951146] sky2 0000:01:00.0: eth0: phy I/O error
[ 4980.951150] sky2 0000:01:00.0: eth0: phy I/O error
[ 4980.951154] sky2 0000:01:00.0: eth0: phy I/O error
[ 4980.951158] sky2 0000:01:00.0: eth0: phy I/O error
[ 4980.951162] sky2 0000:01:00.0: eth0: phy I/O error
[ 4980.951165] sky2 0000:01:00.0: eth0: phy I/O error
[ 4980.951303] sky2 0000:01:00.0: eth0: enabling interface
[ 4980.951551] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 4980.953342] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 4982.161559] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[ 4982.479934] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[ 4993.136034] eth1: no IPv6 routers present
[ 6052.606498] psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 4
[ 6052.608517] psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 1
[ 6052.641876] psmouse.c: TouchPad at isa0060/serio1/input0 - driver resynched.
[10946.419915] sky2 0000:01:00.0: eth0: disabling interface
[10946.419939] sky2 0000:01:00.0: eth0: phy I/O error
[10947.767650] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[10948.645316] PM: Syncing filesystems ... done.
[10948.646679] PM: Preparing system for mem sleep
[10948.764487] Freezing user space processes ... (elapsed 0.01 seconds) done.
[10948.780094] Freezing remaining freezable tasks ... (elapsed 0.01 seconds) done.
[10948.796092] PM: Entering mem sleep
[10948.796111] Suspending console(s) (use no_console_suspend to debug)
[10948.796583] sd 0:0:0:0: [sda] Synchronizing SCSI cache
[10948.796707] sd 0:0:0:0: [sda] Stopping disk
[10948.856035] i8042 kbd 00:07: wake-up capability enabled by ACPI
[10948.856271] ACPI handle has no context!
[10948.856282] sdhci-pci 0000:05:06.3: PCI INT C disabled
[10948.856287] ACPI handle has no context!
[10948.856343] ACPI handle has no context!
[10948.856350] tifm_7xx1 0000:05:06.2: PCI INT C disabled
[10948.856355] ACPI handle has no context!
[10948.856442] eth1: Going into suspend...
[10948.856537] ehci_hcd 0000:00:1d.7: PCI INT A disabled
[10948.856550] uhci_hcd 0000:00:1d.3: PCI INT D disabled
[10948.856612] ipw2200 0000:05:04.0: PCI INT A disabled
[10948.856618] ACPI handle has no context!
[10948.856624] uhci_hcd 0000:00:1d.2: PCI INT C disabled
[10948.856637] uhci_hcd 0000:00:1d.1: PCI INT B disabled
[10948.856648] uhci_hcd 0000:00:1d.0: PCI INT A disabled
[10948.857451] i915 0000:00:02.0: PCI INT A disabled
[10948.960099] HDA Intel 0000:00:1b.0: PCI INT A disabled
[10948.976021] PM: suspend of drv:HDA Intel dev:0000:00:1b.0 complete after 119.354 msecs
[10949.243386] PM: suspend of drv:sd dev:0:0:0:0 complete after 446.806 msecs
[10949.243395] PM: suspend of drv:scsi dev:target0:0:0 complete after 446.634 msecs
[10949.243402] PM: suspend of drv:scsi dev:host0 complete after 387.694 msecs
[10949.243482] ata_piix 0000:00:1f.2: PCI INT B disabled
[10949.256021] PM: suspend of drv:ata_piix dev:0000:00:1f.2 complete after 399.543 msecs
[10949.256030] PM: suspend of drv: dev:pci0000:00 complete after 398.549 msecs
[10949.256036] PM: suspend of devices complete after 459.697 msecs
[10949.256039] PM: suspend devices took 0.460 seconds
[10949.412040] PM: late suspend of drv:sky2 dev:0000:01:00.0 complete after 155.678 msecs
[10949.428229] PM: late suspend of devices complete after 172.185 msecs
[10949.428496] ACPI: Preparing to enter system sleep state S3
[10949.451287] PM: Saving platform NVS memory
[10949.451317] Disabling non-boot CPUs ...
[10949.451317] Back to C!
[10949.451317] PM: Restoring platform NVS memory
[10949.451317] Force enabled HPET at resume
[10949.452083] ACPI: Waking up from system sleep state S3
[10949.486095] pcieport 0000:00:1c.0: restoring config space at offset 0x7 (was 0xd0c0, writing 0x2000d0c0)
[10949.486187] uhci_hcd 0000:00:1d.0: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
[10949.486213] uhci_hcd 0000:00:1d.1: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
[10949.486238] uhci_hcd 0000:00:1d.2: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
[10949.486262] uhci_hcd 0000:00:1d.3: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
[10949.486295] ehci_hcd 0000:00:1d.7: restoring config space at offset 0x1 (was 0x2900000, writing 0x2900002)
[10949.486375] ata_piix 0000:00:1f.2: restoring config space at offset 0x1 (was 0x2b80001, writing 0x22b00005)
[10949.540302] power_supply BAT1: parent PNP0C0A:00 should not be sleeping
[10949.640031] sky2 0000:01:00.0: BAR 0: set to [mem 0xcc000000-0xcc003fff 64bit] (PCI address [0xcc000000-0xcc003fff])
[10949.640038] sky2 0000:01:00.0: BAR 2: set to [io  0xc000-0xc0ff] (PCI address [0xc000-0xc0ff])
[10949.640078] sky2 0000:01:00.0: restoring config space at offset 0x6 (was 0xc001, writing 0x1)
[10949.640085] sky2 0000:01:00.0: restoring config space at offset 0x4 (was 0xcc000004, writing 0x4)
[10949.640095] sky2 0000:01:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x40100000)
[10949.640120] PM: early resume of drv:sky2 dev:0000:01:00.0 complete after 153.731 msecs
[10949.640134] ipw2200 0000:05:04.0: restoring config space at offset 0xf (was 0x18030100, writing 0x1803010b)
[10949.640152] ipw2200 0000:05:04.0: restoring config space at offset 0x4 (was 0x0, writing 0xb800a000)
[10949.640158] ipw2200 0000:05:04.0: restoring config space at offset 0x3 (was 0x0, writing 0x8000)
[10949.640165] ipw2200 0000:05:04.0: restoring config space at offset 0x1 (was 0x2900000, writing 0x2900006)
[10949.640185] yenta_cardbus 0000:05:06.0: restoring config space at offset 0xf (was 0x34001ff, writing 0x5c001ff)
[10949.640191] yenta_cardbus 0000:05:06.0: restoring config space at offset 0xe (was 0x0, writing 0x84fc)
[10949.640197] yenta_cardbus 0000:05:06.0: restoring config space at offset 0xd (was 0x0, writing 0x8400)
[10949.640203] yenta_cardbus 0000:05:06.0: restoring config space at offset 0xc (was 0x0, writing 0x80fc)
[10949.640209] yenta_cardbus 0000:05:06.0: restoring config space at offset 0xb (was 0x0, writing 0x8000)
[10949.640215] yenta_cardbus 0000:05:06.0: restoring config space at offset 0xa (was 0x0, writing 0xbffff000)
[10949.640221] yenta_cardbus 0000:05:06.0: restoring config space at offset 0x9 (was 0x0, writing 0xbc000000)
[10949.640227] yenta_cardbus 0000:05:06.0: restoring config space at offset 0x8 (was 0x0, writing 0x8bfff000)
[10949.640232] yenta_cardbus 0000:05:06.0: restoring config space at offset 0x7 (was 0x0, writing 0x88000000)
[10949.640242] yenta_cardbus 0000:05:06.0: restoring config space at offset 0x3 (was 0x820010, writing 0x82a810)
[10949.640293] firewire_ohci 0000:05:06.1: restoring config space at offset 0x3 (was 0x800004, writing 0x808004)
[10949.640315] tifm_7xx1 0000:05:06.2: restoring config space at offset 0xf (was 0x40703ff, writing 0x407030b)
[10949.640333] tifm_7xx1 0000:05:06.2: restoring config space at offset 0x4 (was 0x0, writing 0xb8008000)
[10949.640338] tifm_7xx1 0000:05:06.2: restoring config space at offset 0x3 (was 0x800000, writing 0x808004)
[10949.640345] tifm_7xx1 0000:05:06.2: restoring config space at offset 0x1 (was 0x2100000, writing 0x2100006)
[10949.640365] sdhci-pci 0000:05:06.3: restoring config space at offset 0xf (was 0x40703ff, writing 0x407030b)
[10949.640382] sdhci-pci 0000:05:06.3: restoring config space at offset 0x4 (was 0x0, writing 0xb8009000)
[10949.640388] sdhci-pci 0000:05:06.3: restoring config space at offset 0x3 (was 0x800000, writing 0x808004)
[10949.640395] sdhci-pci 0000:05:06.3: restoring config space at offset 0x1 (was 0x2100000, writing 0x2100006)
[10949.640853] PM: early resume of devices complete after 154.943 msecs
[10949.644115] i915 0000:00:02.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[10949.644120] i915 0000:00:02.0: setting latency timer to 64
[10949.700508] HDA Intel 0000:00:1b.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[10949.700514] HDA Intel 0000:00:1b.0: setting latency timer to 64
[10949.700552] HDA Intel 0000:00:1b.0: irq 18 for MSI/MSI-X
[10949.700603] uhci_hcd 0000:00:1d.0: PCI INT A -> Link[LNKH] -> GSI 10 (level, low) -> IRQ 10
[10949.700609] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[10949.700631] usb usb2: root hub lost power or was reset
[10949.700644] uhci_hcd 0000:00:1d.1: PCI INT B -> Link[LNKD] -> GSI 10 (level, low) -> IRQ 10
[10949.700650] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[10949.700670] usb usb3: root hub lost power or was reset
[10949.700683] uhci_hcd 0000:00:1d.2: PCI INT C -> Link[LNKC] -> GSI 9 (level, low) -> IRQ 9
[10949.700689] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[10949.700709] usb usb4: root hub lost power or was reset
[10949.700721] uhci_hcd 0000:00:1d.3: PCI INT D -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[10949.700726] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[10949.700746] usb usb5: root hub lost power or was reset
[10949.700760] ehci_hcd 0000:00:1d.7: PCI INT A -> Link[LNKH] -> GSI 10 (level, low) -> IRQ 10
[10949.700766] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[10949.700807] pci 0000:00:1e.0: setting latency timer to 64
[10949.700821] ata_piix 0000:00:1f.2: PCI INT B -> Link[LNKD] -> GSI 10 (level, low) -> IRQ 10
[10949.700826] ata_piix 0000:00:1f.2: setting latency timer to 64
[10949.700860] eth1: Coming out of suspend...
[10949.700868] ipw2200 0000:05:04.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[10949.700895] tifm_7xx1 0000:05:06.2: PCI INT C -> Link[LNKG] -> GSI 6 (level, low) -> IRQ 6
[10949.700911] sdhci-pci 0000:05:06.3: PCI INT C -> Link[LNKG] -> GSI 6 (level, low) -> IRQ 6
[10949.716066] sd 0:0:0:0: [sda] Starting disk
[10949.796075] PM: resume of drv:i915 dev:0000:00:02.0 complete after 151.968 msecs
[10949.820027] PM: resume of drv:usb dev:usb2 complete after 119.054 msecs
[10949.820043] PM: resume of drv:usb dev:usb3 complete after 119.054 msecs
[10949.820053] PM: resume of drv:hub dev:2-0:1.0 complete after 119.073 msecs
[10949.820059] PM: resume of drv: dev:ep_00 complete after 119.072 msecs
[10949.820064] PM: resume of drv:hub dev:3-0:1.0 complete after 118.997 msecs
[10949.820070] PM: resume of drv: dev:ep_00 complete after 116.007 msecs
[10949.820075] PM: resume of drv: dev:ep_81 complete after 119.092 msecs
[10949.820080] PM: resume of drv: dev:ep_81 complete after 116.036 msecs
[10949.824043] PM: resume of drv:usb dev:usb4 complete after 119.962 msecs
[10949.824052] PM: resume of drv:hub dev:4-0:1.0 complete after 116.021 msecs
[10949.824058] PM: resume of drv: dev:ep_00 complete after 115.991 msecs
[10949.824063] PM: resume of drv: dev:ep_81 complete after 116.014 msecs
[10949.832060] PM: resume of drv:usb dev:usb5 complete after 120.015 msecs
[10949.832070] PM: resume of drv:hub dev:5-0:1.0 complete after 120.004 msecs
[10949.832076] PM: resume of drv: dev:ep_00 complete after 116.033 msecs
[10949.832081] PM: resume of drv: dev:ep_81 complete after 119.998 msecs
[10950.045460] PM: resume of drv:ac dev:ACPI0003:00 complete after 344.403 msecs
[10950.107377] firewire_core: skipped bus generations, destroying all nodes
[10950.156243] PM: resume of drv:battery dev:PNP0C0A:00 complete after 110.776 msecs
[10950.172475] ata2.00: ACPI cmd ef/03:0c:00:00:00:a0 (SET FEATURES) filtered out
[10950.172480] ata2.00: ACPI cmd ef/03:42:00:00:00:a0 (SET FEATURES) filtered out
[10950.188359] ata2.00: configured for UDMA/33
[10950.196121] i8042 kbd 00:07: wake-up capability disabled by ACPI
[10950.604047] firewire_core: rediscovered device fw0
[10951.948173] ata1.00: ACPI cmd ef/03:0c:00:00:00:a0 (SET FEATURES) filtered out
[10951.948178] ata1.00: ACPI cmd ef/03:45:00:00:00:a0 (SET FEATURES) filtered out
[10951.964523] ata1.00: configured for UDMA/100
[10951.976840] PM: resume of drv:sd dev:0:0:0:0 complete after 2260.775 msecs
[10951.976850] PM: resume of drv:scsi_device dev:0:0:0:0 complete after 2260.743 msecs
[10951.976857] PM: resume of drv:scsi_disk dev:0:0:0:0 complete after 1777.364 msecs
[10952.116061] PM: resume of drv:pcmcia_socket dev:pcmcia_socket0 complete after 139.146 msecs
[10952.116143] PM: resume of devices complete after 2472.100 msecs
[10952.116270] PM: resume devices took 2.476 seconds
[10952.116309] PM: Finishing wakeup.
[10952.116311] Restarting tasks ... done.
[10952.187973] video LNXVIDEO:01: Restoring backlight state
[10952.268557] [drm:drm_mode_getfb] *ERROR* invalid framebuffer id
[10953.385730] sky2 0000:01:00.0: eth0: phy I/O error
[10953.385739] sky2 0000:01:00.0: eth0: phy I/O error
[10953.385744] sky2 0000:01:00.0: eth0: phy I/O error
[10953.385747] sky2 0000:01:00.0: eth0: phy I/O error
[10953.385752] sky2 0000:01:00.0: eth0: phy I/O error
[10953.385756] sky2 0000:01:00.0: eth0: phy I/O error
[10953.385760] sky2 0000:01:00.0: eth0: phy I/O error
[10953.385764] sky2 0000:01:00.0: eth0: phy I/O error
[10953.385768] sky2 0000:01:00.0: eth0: phy I/O error
[10953.385772] sky2 0000:01:00.0: eth0: phy I/O error
[10953.385776] sky2 0000:01:00.0: eth0: phy I/O error
[10953.385914] sky2 0000:01:00.0: eth0: enabling interface
[10953.386162] ADDRCONF(NETDEV_UP): eth0: link is not ready
[10953.387627] ADDRCONF(NETDEV_UP): eth1: link is not ready
[10954.035216] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[10954.397370] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[10964.248069] eth1: no IPv6 routers present
```

---

### Post by ubudog on 2011-06-07
Now that you've upgraded, try looking for drivers in 'Additional Drivers'.

In GNOME, it's under System>Administration>Additional Drivers.
In Unity, just search for it using the new app launcher.

---

### Post by Bowman9709 on 2011-06-11
The only driver the came of was Software Modem

---


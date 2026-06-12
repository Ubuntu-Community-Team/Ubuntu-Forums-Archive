---
title: "X-Fi installed but i cannot get it to be default"
date: 2009-01-06
forum: New to Ubuntu
---

### Post by Rrasyrogenees on 2009-01-06
i had another thread that i started about having sound problems... i thought that had solved my problem... it didn't.  i have an X-Fi Extreme Music sound card and it seems that everything (Rythymbox, at least) is working fine and the X-Fi installed fine but now there is still no sound.  what i noticed was that my X-Fi is not the default and i cannot find where to get it to do that... i have looked for precise instructions but most of those parts are very vague and i can't figure them out. i figure it is something simple but since i am still very very nOObish about ubuntu... i have to ask a lot.

---

### Post by Michael.Godawski on 2009-01-06
hi,

can you please run these commands in terminal and post the outputs here:

```
aplay -l
lspci -v | less
find /lib/modules/`uname -r` | grep snd
```

edit:
hmm this site says your card is unsupported:
[http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs](http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs)

or have I checked the wrong card, you can check on this site for yourself too.

---

### Post by Rrasyrogenees on 2009-01-06
i looked back at my install and tried again too, this is what it said...

rrasyrogenees@rrasyrogenees-desktop:~$ wget [http://ccftp.creative.com/manualdn/Drivers/AVP/10792/0x0343D29A/XFiDrv_Linux_Public_US_1.00.tar.gz](http://ccftp.creative.com/manualdn/Drivers/AVP/10792/0x0343D29A/XFiDrv_Linux_Public_US_1.00.tar.gz)
--2009-01-06 02:40:12--  [http://ccftp.creative.com/manualdn/Drivers/AVP/10792/0x0343D29A/XFiDrv_Linux_Public_US_1.00.tar.gz](http://ccftp.creative.com/manualdn/Drivers/AVP/10792/0x0343D29A/XFiDrv_Linux_Public_US_1.00.tar.gz)
Resolving ccftp.creative.com... 66.250.188.93
Connecting to ccftp.creative.com|66.250.188.93|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 70448 (69K) [application/x-gzip]
Saving to: `XFiDrv_Linux_Public_US_1.00.tar.gz.2'

100%[======================================>] 70,448       396K/s   in 0.2s    

2009-01-06 02:40:12 (396 KB/s) - `XFiDrv_Linux_Public_US_1.00.tar.gz.2' saved [70448/70448]

rrasyrogenees@rrasyrogenees-desktop:~$ tar -xf XFiDrv_Linux_Public_US_1.00.tar.gz
tar: XFiDrv_Linux_Public_US_1.00/ctmixer.c: Cannot open: File exists
tar: XFiDrv_Linux_Public_US_1.00/cthw20k1.c: Cannot open: File exists
tar: XFiDrv_Linux_Public_US_1.00/ct20k1reg.h: Cannot open: File exists
tar: XFiDrv_Linux_Public_US_1.00/ctsrc.h: Cannot open: File exists
tar: XFiDrv_Linux_Public_US_1.00/ctimap.h: Cannot open: File exists
tar: XFiDrv_Linux_Public_US_1.00/ctamixer.c: Cannot open: File exists
tar: XFiDrv_Linux_Public_US_1.00/ctamixer.h: Cannot open: File exists
tar: XFiDrv_Linux_Public_US_1.00/ctdaio.c: Cannot open: File exists
tar: XFiDrv_Linux_Public_US_1.00/ctatc.c: Cannot open: File exists
tar: XFiDrv_Linux_Public_US_1.00/ctsrc.c: Cannot open: File exists
tar: XFiDrv_Linux_Public_US_1.00/xfi.c: Cannot open: File exists
tar: XFiDrv_Linux_Public_US_1.00/ctutils.h: Cannot open: File exists
tar: XFiDrv_Linux_Public_US_1.00/cthw20k2.c: Cannot open: File exists
tar: XFiDrv_Linux_Public_US_1.00/ctresource.c: Cannot open: File exists
tar: XFiDrv_Linux_Public_US_1.00/ctresource.h: Cannot open: File exists
tar: XFiDrv_Linux_Public_US_1.00/ctatc.h: Cannot open: File exists
tar: XFiDrv_Linux_Public_US_1.00/README: Cannot open: File exists
tar: XFiDrv_Linux_Public_US_1.00/ct20k2reg.h: Cannot open: File exists
tar: XFiDrv_Linux_Public_US_1.00/ctvmem.c: Cannot open: File exists
tar: XFiDrv_Linux_Public_US_1.00/cthardware.h: Cannot open: File exists
tar: XFiDrv_Linux_Public_US_1.00/cthardware.c: Cannot open: File exists
tar: XFiDrv_Linux_Public_US_1.00/ctdrv.h: Cannot open: File exists
tar: XFiDrv_Linux_Public_US_1.00/ctpcm.h: Cannot open: File exists
tar: XFiDrv_Linux_Public_US_1.00/COPYING: Cannot open: File exists
tar: XFiDrv_Linux_Public_US_1.00/ctvmem.h: Cannot open: File exists
tar: XFiDrv_Linux_Public_US_1.00/ctpcm.c: Cannot open: File exists
tar: XFiDrv_Linux_Public_US_1.00/Disk.id: Cannot open: File exists
tar: XFiDrv_Linux_Public_US_1.00/Makefile: Cannot open: File exists
tar: XFiDrv_Linux_Public_US_1.00/ctmixer.h: Cannot open: File exists
tar: XFiDrv_Linux_Public_US_1.00/ctdaio.h: Cannot open: File exists
tar: XFiDrv_Linux_Public_US_1.00/ctimap.c: Cannot open: File exists
tar: XFiDrv_Linux_Public_US_1.00: Cannot utime: Operation not permitted
tar: Error exit delayed from previous errors
rrasyrogenees@rrasyrogenees-desktop:~$ 


Now for what you asked me to check...

rrasyrogenees@rrasyrogenees-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
rrasyrogenees@rrasyrogenees-desktop:~$ lspci -v | less
rrasyrogenees@rrasyrogenees-desktop:~$ 
00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
        Subsystem: Giga-byte Technology Device 5000
        Flags: bus master, 66MHz, fast devsel, latency 0
        Capabilities: <access denied>

00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
        Subsystem: Giga-byte Technology Device 0c11
        Flags: bus master, 66MHz, fast devsel, latency 0

00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
        Subsystem: Giga-byte Technology Device 0c11
        Flags: 66MHz, fast devsel, IRQ 10
        I/O ports at dc00 [size=32]
        I/O ports at 1c00 [size=64]
        I/O ports at 1c40 [size=64]
        Capabilities: <access denied>
        Kernel driver in use: nForce2_smbus
        Kernel modules: i2c-nforce2

00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2) (prog-if 10)
        Subsystem: Giga-byte Technology Device 5004
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
        Memory at fb001000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>
        Kernel driver in use: ohci_hcd
        Kernel modules: ohci-hcd

00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3) (prog-if 20)
        Subsystem: Giga-byte Technology Device 5004
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
        Memory at feb00000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>
        Kernel driver in use: ehci_hcd
        Kernel modules: ehci-hcd

00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev a2) (prog-if 8a [Master SecP PriP])
        Subsystem: Device f458:5002
        Flags: bus master, 66MHz, fast devsel, latency 0
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [siz:
e=8]
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
        I/O ports at f000 [size=16]
        Capabilities: <access denied>
        Kernel driver in use: pata_amd
        Kernel modules: pata_amd, ata_generic, pata_acpi

00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev a3) (prog-if 85 [Master SecO PriO])
        Subsystem: Giga-byte Technology Device b003
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
        I/O ports at 09f0 [size=8]
        I/O ports at 0bf0 [size=4]
        I/O ports at 0970 [size=8]
        I/O ports at 0b70 [size=4]
        I/O ports at c400 [size=16]
        Memory at fb004000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>
        Kernel driver in use: sata_nv
        Kernel modules: sata_nv, ata_generic, pata_acpi

00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev a3) 
(prog-if 85 [Master SecO PriO])
        Subsystem: Giga-byte Technology Device b003
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
        I/O ports at 09e0 [size=8]
        I/O ports at 0be0 [size=4]
        I/O ports at 0960 [size=8]
        I/O ports at 0b60 [size=4]
        I/O ports at d800 [size=16]
        Memory at fb000000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>
        Kernel driver in use: sata_nv
        Kernel modules: sata_nv, ata_generic, pata_acpi

00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2) (prog-if 01)
        Flags: bus master, 66MHz, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
        I/O behind bridge: 00009000-00009fff
        Memory behind bridge: f0000000-f7ffffff

00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
        Subsystem: Giga-byte Technology Device e000
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
        Memory at fb002000 (32-bit, non-prefetchable) [size=4K]
:        I/O ports at e000 [size=8]
        Capabilities: <access denied>
        Kernel driver in use: forcedeth
        Kernel modules: isp1760, forcedeth

00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        I/O behind bridge: 00006000-00006fff
        Capabilities: <access denied>
        Kernel driver in use: pcieport-driver
        Kernel modules: shpchp

00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        I/O behind bridge: 00008000-00008fff
        Capabilities: <access denied>
        Kernel driver in use: pcieport-driver
        Kernel modules: shpchp

00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
        Flags: bus master, fast devsel, latency 0
:        Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
        I/O behind bridge: 00007000-00007fff
        Capabilities: <access denied>
        Kernel driver in use: pcieport-driver
        Kernel modules: shpchp

00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
        I/O behind bridge: 0000a000-0000afff
        Memory behind bridge: f8000000-faffffff
        Prefetchable memory behind bridge: 00000000e0000000-00000000efffffff
        Capabilities: <access denied>
        Kernel driver in use: pcieport-driver
        Kernel modules: shpchp

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
        Flags: fast devsel
        Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
        Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
        Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
        Flags: fast devsel
        Kernel driver in use: k8temp
        Kernel modules: k8temp

01:08.0 Multimedia audio controller: Creative Labs SB X-Fi
        Subsystem: Creative Labs Device 0021
        Flags: bus master, medium devsel, latency 32, IRQ 11
        I/O ports at 9000 [size=32]
        Memory at f4000000 (64-bit, non-prefetchable) [size=2M]
        Memory at f0000000 (64-bit, non-prefetchable) [size=64M]
        Capabilities: <access denied>
        Kernel modules: ctxfi

05:00.0 VGA compatible controller: nVidia Corporation G71 [GeForce 7900 GT/GTO] (rev a1)
        Subsystem: Micro-Star International Co., Ltd. Device 0660
        Flags: bus master, fast devsel, latency 0, IRQ 18
        Memory at f8000000 (32-bit, non-prefetchable) [size=16M]
        Memory at e0000000 (64-bit, prefetchable) [size=256M]
        Memory at f9000000 (64-bit, non-prefetchable) [size=16M]
        I/O ports at a000 [size=128]
        [virtual] Expansion ROM at fa000000 [disabled] [size=128K]
        Capabilities: <access denied>
        Kernel driver in use: nvidia
        Kernel modules: nvidia, nvidiafb



rrasyrogenees@rrasyrogenees-desktop:~$ find /lib/modules/`uname -r` | grep snd
/lib/modules/2.6.27-11-generic/kernel/sound/synth/snd-util-mem.ko
/lib/modules/2.6.27-11-generic/kernel/sound/synth/emux/snd-emux-synth.ko
/lib/modules/2.6.27-11-generic/kernel/sound/soc/snd-soc-core.ko
/lib/modules/2.6.27-11-generic/kernel/sound/usb/snd-usb-lib.ko
/lib/modules/2.6.27-11-generic/kernel/sound/usb/snd-usb-audio.ko
/lib/modules/2.6.27-11-generic/kernel/sound/usb/usx2y/snd-usb-usx2y.ko
/lib/modules/2.6.27-11-generic/kernel/sound/usb/caiaq/snd-usb-caiaq.ko
/lib/modules/2.6.27-11-generic/kernel/sound/isa/sb/snd-sb16-dsp.ko
/lib/modules/2.6.27-11-generic/kernel/sound/isa/sb/snd-sb-common.ko
/lib/modules/2.6.27-11-generic/kernel/sound/drivers/snd-mts64.ko
/lib/modules/2.6.27-11-generic/kernel/sound/drivers/snd-virmidi.ko
/lib/modules/2.6.27-11-generic/kernel/sound/drivers/snd-serial-u16550.ko
/lib/modules/2.6.27-11-generic/kernel/sound/drivers/pcsp/snd-pcsp.ko
/lib/modules/2.6.27-11-generic/kernel/sound/drivers/mpu401/snd-mpu401-uart.ko
/lib/modules/2.6.27-11-generic/kernel/sound/drivers/mpu401/snd-mpu401.ko
/lib/modules/2.6.27-11-generic/kernel/sound/drivers/snd-dummy.ko
/lib/modules/2.6.27-11-generic/kernel/sound/drivers/snd-mtpav.ko
/lib/modules/2.6.27-11-generic/kernel/sound/drivers/vx/snd-vx-lib.ko
/lib/modules/2.6.27-11-generic/kernel/sound/drivers/snd-portman2x4.ko
/lib/modules/2.6.27-11-generic/kernel/sound/drivers/opl3/snd-opl3-lib.ko
/lib/modules/2.6.27-11-generic/kernel/sound/drivers/opl3/snd-opl3-synth.ko
/lib/modules/2.6.27-11-generic/kernel/sound/core/snd.ko
/lib/modules/2.6.27-11-generic/kernel/sound/core/snd-pcm.ko
/lib/modules/2.6.27-11-generic/kernel/sound/core/snd-timer.ko
/lib/modules/2.6.27-11-generic/kernel/sound/core/seq/snd-seq-dummy.ko
/lib/modules/2.6.27-11-generic/kernel/sound/core/seq/snd-seq-midi.ko
/lib/modules/2.6.27-11-generic/kernel/sound/core/seq/snd-seq-virmidi.ko
/lib/modules/2.6.27-11-generic/kernel/sound/core/seq/snd-seq.ko
/lib/modules/2.6.27-11-generic/kernel/sound/core/seq/snd-seq-midi-emul.ko
/lib/modules/2.6.27-11-generic/kernel/sound/core/seq/oss/snd-seq-oss.ko
/lib/modules/2.6.27-11-generic/kernel/sound/core/seq/snd-seq-device.ko
/lib/modules/2.6.27-11-generic/kernel/sound/core/seq/snd-seq-midi-event.ko
/lib/modules/2.6.27-11-generic/kernel/sound/core/snd-rawmidi.ko
/lib/modules/2.6.27-11-generic/kernel/sound/core/oss/snd-mixer-oss.ko
/lib/modules/2.6.27-11-generic/kernel/sound/core/oss/snd-pcm-oss.ko
/lib/modules/2.6.27-11-generic/kernel/sound/core/snd-hwdep.ko
/lib/modules/2.6.27-11-generic/kernel/sound/core/snd-page-alloc.ko
/lib/modules/2.6.27-11-generic/kernel/sound/i2c/other/snd-ak4114.ko
/lib/modules/2.6.27-11-generic/kernel/sound/i2c/other/snd-tea575x-tuner.ko
/lib/modules/2.6.27-11-generic/kernel/sound/i2c/other/snd-ak4117.ko
/lib/modules/2.6.27-11-generic/kernel/sound/i2c/other/snd-ak4xxx-adda.ko
/lib/modules/2.6.27-11-generic/kernel/sound/i2c/other/snd-pt2258.ko
/lib/modules/2.6.27-11-generic/kernel/sound/i2c/snd-i2c.ko
/lib/modules/2.6.27-11-generic/kernel/sound/i2c/snd-cs8427.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pcmcia/pdaudiocf/snd-pdaudiocf.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pcmcia/vx/snd-vxpocket.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/snd-via82xx-modem.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/ac97/snd-ac97-codec.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/hda/snd-hda-intel.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/snd-ens1370.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/snd-cmipci.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/riptide/snd-riptide.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/rme9652/snd-hdsp.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/rme9652/snd-rme9652.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/rme9652/snd-hdspm.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/ice1712/snd-ice1724.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/ice1712/snd-ice1712.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/ice1712/snd-ice17xx-ak4xxx.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/snd-atiixp.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/snd-azt3328.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/snd-sonicvibes.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/emu10k1/snd-emu10k1x.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/emu10k1/snd-emu10k1.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/emu10k1/snd-emu10k1-synth.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/snd-atiixp-modem.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/echoaudio/snd-indigoio.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/echoaudio/snd-indigodj.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/echoaudio/snd-gina20.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/echoaudio/snd-mia.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/echoaudio/snd-darla24.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/echoaudio/snd-darla20.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/echoaudio/snd-echo3g.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/echoaudio/snd-layla20.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/echoaudio/snd-gina24.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/echoaudio/snd-layla24.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/echoaudio/snd-mona.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/echoaudio/snd-indigo.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/snd-rme32.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/aw2/snd-aw2.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/snd-maestro3.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/snd-cs4281.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/snd-bt87x.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/snd-intel8x0m.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/vx222/snd-vx222.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/snd-als4000.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/snd-intel8x0.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/snd-es1968.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/ca0106/snd-ca0106.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/trident/snd-trident.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/cs46xx/snd-cs46xx.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/snd-ad1889.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/oxygen/snd-hifier.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/oxygen/snd-oxygen.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/oxygen/snd-virtuoso.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/oxygen/snd-oxygen-lib.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/snd-als300.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/ali5451/snd-ali5451.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/korg1212/snd-korg1212.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/ymfpci/snd-ymfpci.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/snd-ens1371.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/nm256/snd-nm256.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/snd-rme96.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/mixart/snd-mixart.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/snd-via82xx.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/snd-cs5530.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/snd-es1938.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/snd-fm801.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/au88x0/snd-au8820.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/au88x0/snd-au8810.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/au88x0/snd-au8830.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/pcxhr/snd-pcxhr.ko
/lib/modules/2.6.27-11-generic/kernel/ubuntu/misc/media/snd-bt-sco.ko
rrasyrogenees@rrasyrogenees-desktop:~$

---

### Post by Rrasyrogenees on 2009-01-06
oh... and this too...

rrasyrogenees@rrasyrogenees-desktop:~$ cd XFiDrv_Linux_Public_US_1.00
rrasyrogenees@rrasyrogenees-desktop:~/XFiDrv_Linux_Public_US_1.00$ sudo apt-get install build-essential linux-headers-`uname -r`
[sudo] password for rrasyrogenees: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
linux-headers-2.6.27-11-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
rrasyrogenees@rrasyrogenees-desktop:~/XFiDrv_Linux_Public_US_1.00$ make
make -C /lib/modules/2.6.27-11-generic/build M=/home/rrasyrogenees/XFiDrv_Linux_Public_US_1.00
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-11-generic'
  CC [M]  /home/rrasyrogenees/XFiDrv_Linux_Public_US_1.00/xfi.o
Assembler messages:
Fatal error: can't create /home/rrasyrogenees/XFiDrv_Linux_Public_US_1.00/.tmp_xfi.o: Permission denied
In file included from /home/rrasyrogenees/XFiDrv_Linux_Public_US_1.00/xfi.c:14:
include/sound/driver.h:1:2: warning: #warning "This file is deprecated"
In file included from /home/rrasyrogenees/XFiDrv_Linux_Public_US_1.00/ctatc.h:25,
                 from /home/rrasyrogenees/XFiDrv_Linux_Public_US_1.00/xfi.c:17:
include/sound/driver.h:1:2: warning: #warning "This file is deprecated"
make[2]: *** [/home/rrasyrogenees/XFiDrv_Linux_Public_US_1.00/xfi.o] Error 2
make[1]: *** [_module_/home/rrasyrogenees/XFiDrv_Linux_Public_US_1.00] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-11-generic'
make: *** [all] Error 2
rrasyrogenees@rrasyrogenees-desktop:~/XFiDrv_Linux_Public_US_1.00$ sudo make install
Copy module files...
Update module dependency relationships...
FATAL: Error inserting ctxfi (/lib/modules/2.6.27-11-generic/kernel/drivers/ssound/ctxfi.ko): Invalid module format
make: *** [install] Error 1
rrasyrogenees@rrasyrogenees-desktop:~/XFiDrv_Linux_Public_US_1.00$

---

### Post by Michael.Godawski on 2009-01-06
:D
use the code brackets the next time (#) so the output is more readable.

Perhaps you can try this to set your sound card as default:


[LIST]
[*][https://help.ubuntu.com/community/SoundTroubleshooting#Configuring%20default%20soundcards%20/%20stopping%20soundcards%20from%20switching](https://help.ubuntu.com/community/SoundTroubleshooting#Configuring%20default%20soundcards%20/%20stopping%20soundcards%20from%20switching)
[/LIST]

And it would not harm if you check the whole troubleshooting guide dealing with sound:


[LIST]
[*][https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)
[/LIST]

---

### Post by Rrasyrogenees on 2009-01-06
hey michael...

   how do i do this?  "use the code brackets the next time (#) so the output is more readable."  i am still very nOOb to ubuntu...:)

and i got this as well...
rrasyrogenees@rrasyrogenees-desktop:~$ cat /proc/asound/modules
 1 snd_usb_audio
rrasyrogenees@rrasyrogenees-desktop:~$ 

obviously no x-fi detected... i have it ok on xubuntu which i can boot to but i wanted it here... did i remove something that i needed to get it to be recognized?  i did have it working before but when i tried to do 'wine' and world of warcraft, that and the video went away... i have my video and sound programs working now but without sound...:confused: i also have not gotten my logitech camera to be recognized as well (for the microphone) but i haven't tried working on that yet because i need the sound to know if it is working or not.

umm... now that i checked... it seems that my dvd rom and my dvd r/w are not being recognized either... what the hell did i do to my os?#-o:-({|=

---


---
title: "[SOLVED] No sound"
date: 2008-12-13
forum: New to Ubuntu
---

### Post by cdmike2k8 on 2008-12-13
As the title says, I have no sound.  I do now know where to start diagnosing the issue.  It is an onboard card.  I know you need more info, but I don't know what you need.  Please let me know how I can help you help me. Thanks

---

### Post by Michael.Godawski on 2008-12-13
Making things short and painless:
have a look here

[LIST]
[*][https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)
[/LIST]
and then report back :p.

You may ask too.

---

### Post by cdmike2k8 on 2008-12-13
output of the commands in the troubleshooting section:
```
michael@michael-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
michael@michael-desktop:~$ find /lib/modules/`uname -r` | grep snd
/lib/modules/2.6.27-9-generic/kernel/ubuntu/misc/media/snd-bt-sco.ko
/lib/modules/2.6.27-9-generic/kernel/sound/isa/sb/snd-sb-common.ko
/lib/modules/2.6.27-9-generic/kernel/sound/isa/sb/snd-sb16-dsp.ko
/lib/modules/2.6.27-9-generic/kernel/sound/core/snd-timer.ko
/lib/modules/2.6.27-9-generic/kernel/sound/core/snd-pcm.ko
/lib/modules/2.6.27-9-generic/kernel/sound/core/seq/oss/snd-seq-oss.ko
/lib/modules/2.6.27-9-generic/kernel/sound/core/seq/snd-seq-device.ko
/lib/modules/2.6.27-9-generic/kernel/sound/core/seq/snd-seq-midi-emul.ko
/lib/modules/2.6.27-9-generic/kernel/sound/core/seq/snd-seq-midi-event.ko
/lib/modules/2.6.27-9-generic/kernel/sound/core/seq/snd-seq-midi.ko
/lib/modules/2.6.27-9-generic/kernel/sound/core/seq/snd-seq.ko
/lib/modules/2.6.27-9-generic/kernel/sound/core/seq/snd-seq-dummy.ko
/lib/modules/2.6.27-9-generic/kernel/sound/core/seq/snd-seq-virmidi.ko
/lib/modules/2.6.27-9-generic/kernel/sound/core/snd-hwdep.ko
/lib/modules/2.6.27-9-generic/kernel/sound/core/oss/snd-pcm-oss.ko
/lib/modules/2.6.27-9-generic/kernel/sound/core/oss/snd-mixer-oss.ko
/lib/modules/2.6.27-9-generic/kernel/sound/core/snd-rawmidi.ko
/lib/modules/2.6.27-9-generic/kernel/sound/core/snd-page-alloc.ko
/lib/modules/2.6.27-9-generic/kernel/sound/core/snd.ko
/lib/modules/2.6.27-9-generic/kernel/sound/drivers/snd-mts64.ko
/lib/modules/2.6.27-9-generic/kernel/sound/drivers/snd-serial-u16550.ko
/lib/modules/2.6.27-9-generic/kernel/sound/drivers/mpu401/snd-mpu401-uart.ko
/lib/modules/2.6.27-9-generic/kernel/sound/drivers/mpu401/snd-mpu401.ko
/lib/modules/2.6.27-9-generic/kernel/sound/drivers/opl3/snd-opl3-synth.ko
/lib/modules/2.6.27-9-generic/kernel/sound/drivers/opl3/snd-opl3-lib.ko
/lib/modules/2.6.27-9-generic/kernel/sound/drivers/pcsp/snd-pcsp.ko
/lib/modules/2.6.27-9-generic/kernel/sound/drivers/snd-virmidi.ko
/lib/modules/2.6.27-9-generic/kernel/sound/drivers/snd-portman2x4.ko
/lib/modules/2.6.27-9-generic/kernel/sound/drivers/snd-mtpav.ko
/lib/modules/2.6.27-9-generic/kernel/sound/drivers/snd-dummy.ko
/lib/modules/2.6.27-9-generic/kernel/sound/drivers/vx/snd-vx-lib.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/snd-sonicvibes.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/snd-ens1371.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/snd-es1968.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/vx222/snd-vx222.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/ice1712/snd-ice1712.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/ice1712/snd-ice17xx-ak4xxx.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/ice1712/snd-ice1724.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/trident/snd-trident.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/snd-atiixp.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/snd-rme32.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/snd-intel8x0m.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/echoaudio/snd-gina24.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/echoaudio/snd-indigo.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/echoaudio/snd-darla24.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/echoaudio/snd-gina20.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/echoaudio/snd-layla24.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/echoaudio/snd-darla20.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/echoaudio/snd-mia.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/echoaudio/snd-indigodj.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/echoaudio/snd-echo3g.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/echoaudio/snd-layla20.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/echoaudio/snd-indigoio.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/echoaudio/snd-mona.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/rme9652/snd-hdsp.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/rme9652/snd-rme9652.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/rme9652/snd-hdspm.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/ca0106/snd-ca0106.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/nm256/snd-nm256.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/snd-maestro3.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/snd-fm801.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/snd-ad1889.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/snd-azt3328.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/snd-via82xx.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/ac97/snd-ac97-codec.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/snd-via82xx-modem.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/snd-bt87x.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/hda/snd-hda-intel.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/snd-rme96.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/riptide/snd-riptide.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/snd-intel8x0.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/snd-es1938.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/ali5451/snd-ali5451.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/emu10k1/snd-emu10k1x.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/emu10k1/snd-emu10k1.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/emu10k1/snd-emu10k1-synth.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/snd-ens1370.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/snd-atiixp-modem.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/snd-cmipci.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/mixart/snd-mixart.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/snd-cs5530.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/oxygen/snd-oxygen-lib.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/oxygen/snd-hifier.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/oxygen/snd-virtuoso.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/oxygen/snd-oxygen.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/snd-als300.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/korg1212/snd-korg1212.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/au88x0/snd-au8820.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/au88x0/snd-au8830.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/au88x0/snd-au8810.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/ymfpci/snd-ymfpci.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/cs46xx/snd-cs46xx.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/aw2/snd-aw2.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/snd-als4000.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/pcxhr/snd-pcxhr.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/snd-cs4281.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pcmcia/pdaudiocf/snd-pdaudiocf.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pcmcia/vx/snd-vxpocket.ko
/lib/modules/2.6.27-9-generic/kernel/sound/synth/emux/snd-emux-synth.ko
/lib/modules/2.6.27-9-generic/kernel/sound/synth/snd-util-mem.ko
/lib/modules/2.6.27-9-generic/kernel/sound/soc/snd-soc-core.ko
/lib/modules/2.6.27-9-generic/kernel/sound/i2c/snd-i2c.ko
/lib/modules/2.6.27-9-generic/kernel/sound/i2c/snd-cs8427.ko
/lib/modules/2.6.27-9-generic/kernel/sound/i2c/other/snd-ak4114.ko
/lib/modules/2.6.27-9-generic/kernel/sound/i2c/other/snd-ak4xxx-adda.ko
/lib/modules/2.6.27-9-generic/kernel/sound/i2c/other/snd-tea575x-tuner.ko
/lib/modules/2.6.27-9-generic/kernel/sound/i2c/other/snd-pt2258.ko
/lib/modules/2.6.27-9-generic/kernel/sound/i2c/other/snd-ak4117.ko
/lib/modules/2.6.27-9-generic/kernel/sound/usb/caiaq/snd-usb-caiaq.ko
/lib/modules/2.6.27-9-generic/kernel/sound/usb/usx2y/snd-usb-usx2y.ko
/lib/modules/2.6.27-9-generic/kernel/sound/usb/snd-usb-audio.ko
/lib/modules/2.6.27-9-generic/kernel/sound/usb/snd-usb-lib.ko
michael@michael-desktop:~$ lspci -v | 
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 02)
        Subsystem: Micro-Star International Co., Ltd. Device 7514
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>
        Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation 4 Series Chipset PCI Express Root Port (rev 02)
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 0000b000-0000bfff
        Memory behind bridge: f4000000-f7dfffff
        Prefetchable memory behind bridge: 00000000a0000000-00000000bfffffff
        Capabilities: <access denied>
        Kernel driver in use: pcieport-driver
        Kernel modules: shpchp

00:1a.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
        Subsystem: Micro-Star International Co., Ltd. Device 7514
        Flags: bus master, medium devsel, latency 0, IRQ 16
        I/O ports at ac00 [size=32]
        Capabilities: <access denied>
Kernel driver in use: uhci_hcd
        Kernel modules: uhci-hcd

00:1a.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
        Subsystem: Micro-Star International Co., Ltd. Device 7514
        Flags: bus master, medium devsel, latency 0, IRQ 21
        I/O ports at a880 [size=32]
        Capabilities: <access denied>
        Kernel driver in use: uhci_hcd
        Kernel modules: uhci-hcd

00:1a.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
        Subsystem: Micro-Star International Co., Ltd. Device 7514
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at a800 [size=32]
        Capabilities: <access denied>
        Kernel driver in use: uhci_hcd
        Kernel modules: uhci-hcd

00:1a.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2 (prog-if 20)
        Subsystem: Micro-Star International Co., Ltd. Device 7514
        Flags: bus master, medium devsel, latency 0, IRQ 18
        Memory at f3fffc00 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>
        Kernel driver in use: ehci_hcd
        Kernel modules: ehci-hcd

00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
        Subsystem: Micro-Star International Co., Ltd. Device 7514
        Flags: bus master, fast devsel, latency 0, IRQ 22
        Memory at f3ff8000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 1
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        I/O behind bridge: 0000c000-0000cfff
        Memory behind bridge: f7e00000-f7efffff
        Capabilities: <access denied>
        Kernel driver in use: pcieport-driver
        Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 2
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        Capabilities: <access denied>
        Kernel driver in use: pcieport-driver
        Kernel modules: shpchp

00:1c.5 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 6
 Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
        I/O behind bridge: 0000d000-0000dfff
        Memory behind bridge: f7f00000-f7ffffff
        Prefetchable memory behind bridge: 00000000d7f00000-00000000d7ffffff
        Capabilities: <access denied>
        Kernel driver in use: pcieport-driver
        Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
        Subsystem: Micro-Star International Co., Ltd. Device 7514
        Flags: bus master, medium devsel, latency 0, IRQ 23
        I/O ports at a480 [size=32]
        Capabilities: <access denied>
        Kernel driver in use: uhci_hcd
        Kernel modules: uhci-hcd

00:1d.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
        Subsystem: Micro-Star International Co., Ltd. Device 7514
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at a400 [size=32]
        Capabilities: <access denied>
        Kernel driver in use: uhci_hcd
        Kernel modules: uhci-hcd

00:1d.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
        Subsystem: Micro-Star International Co., Ltd. Device 7514
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at a080 [size=32]
        Capabilities: <access denied>
        Kernel driver in use: uhci_hcd
        Kernel modules: uhci-hcd

00:1d.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1 (prog-if 20)
        Subsystem: Micro-Star International Co., Ltd. Device 7514
        Flags: bus master, medium devsel, latency 0, IRQ 23
        Memory at f3fff800 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>
        Kernel driver in use: ehci_hcd
        Kernel modules: ehci-hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90) (prog-if 01)
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=05, subordinate=06, sec-latency=32
        I/O behind bridge: 0000e000-0000efff
        Memory behind bridge: f8000000-febfffff
        Prefetchable memory behind bridge: 00000000d8000000-00000000dfffffff
        Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801JIB (ICH10) LPC Interface Controller
        Subsystem: Micro-Star International Co., Ltd. Device 7514
 Flags: bus master, medium devsel, latency 0
        Capabilities: <access denied>

00:1f.2 IDE interface: Intel Corporation 82801JI (ICH10 Family) 4 port SATA IDE Controller (prog-if 8f [Master SecP SecO PriP PriO])
        Subsystem: Micro-Star International Co., Ltd. Device 7514
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
        I/O ports at a000 [size=8]
        I/O ports at 9c00 [size=4]
        I/O ports at 9880 [size=8]
        I/O ports at 9800 [size=4]
        I/O ports at 9480 [size=16]
        I/O ports at 9400 [size=16]
        Capabilities: <access denied>
        Kernel driver in use: ata_piix
        Kernel modules: pata_acpi, ata_piix, ata_generic

00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
        Subsystem: Micro-Star International Co., Ltd. Device 7514
        Flags: medium devsel, IRQ 14
        Memory at f3fff400 (64-bit, non-prefetchable) [size=256]
        I/O ports at 0400 [size=32]
        Kernel modules: i2c-i801

00:1f.5 IDE interface: Intel Corporation 82801JI (ICH10 Family) 2 port SATA IDE Controller (prog-if 85 [Master SecO PriO])
        Subsystem: Micro-Star International Co., Ltd. Device 7514
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
        I/O ports at 9000 [size=8]
        I/O ports at 8c00 [size=4]
        I/O ports at 8880 [size=8]
        I/O ports at 8800 [size=4]
        I/O ports at 8480 [size=16]
        I/O ports at 8400 [size=16]
        Capabilities: <access denied>
        Kernel driver in use: ata_piix
        Kernel modules: pata_acpi, ata_piix, ata_generic

01:00.0 VGA compatible controller: nVidia Corporation GeForce 8800 GT (rev a2)
        Subsystem: Device 196e:053c
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at f6000000 (32-bit, non-prefetchable) [size=16M]
        Memory at a0000000 (64-bit, prefetchable) [size=512M]
        Memory at f4000000 (64-bit, non-prefetchable) [size=32M]
        I/O ports at bc00 [size=128]
        [virtual] Expansion ROM at f7000000 [disabled] [size=128K]
        Capabilities: <access denied>
        Kernel driver in use: nvidia
        Kernel modules: nvidiafb, nvidia

02:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 03) (prog-if 01)
        Subsystem: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller
        Flags: bus master, fast devsel, latency 0, IRQ 16
 Memory at f7efe000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: <access denied>
        Kernel driver in use: ahci
        Kernel modules: ahci

02:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 03) (prog-if 85 [Master SecO PriO])
        Subsystem: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller
        Flags: bus master, fast devsel, latency 0, IRQ 17
        I/O ports at cc00 [size=8]
        I/O ports at c880 [size=4]
        I/O ports at c800 [size=8]
        I/O ports at c480 [size=4]
        I/O ports at c400 [size=16]
        Capabilities: <access denied>
        Kernel driver in use: pata_jmicron
        Kernel modules: pata_acpi, pata_jmicron, ata_generic

04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
        Subsystem: Micro-Star International Co., Ltd. Device 514c
        Flags: bus master, fast devsel, latency 0, IRQ 2299
        I/O ports at d800 [size=256]
        Memory at d7fff000 (64-bit, prefetchable) [size=4K]
        Memory at d7fe0000 (64-bit, prefetchable) [size=64K]
        Expansion ROM at f7ff0000 [disabled] [size=64K]
        Capabilities: <access denied>
        Kernel driver in use: r8169
        Kernel modules: r8169

05:01.0 Ethernet controller: Atheros Communications Inc. AR5413 802.11abg NIC (rev 01)
        Subsystem: Lite-On Communications Inc Device 5001
        Flags: medium devsel, IRQ 20
        Memory at febf0000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>
        Kernel modules: ath_pci

05:02.0 Multimedia audio controller: Creative Labs SB X-Fi
        Subsystem: Creative Labs Device 0024
        Flags: bus master, medium devsel, latency 64, IRQ 11
        I/O ports at ec00 [size=32]
        Memory at fe800000 (64-bit, non-prefetchable) [size=2M]
        Memory at f8000000 (64-bit, non-prefetchable) [size=64M]
        Capabilities: <access denied>

05:03.0 PCI bridge: Hint Corp HB6 Universal PCI-PCI bridge (non-transparent mode) (rev 11)
        Flags: bus master, medium devsel, latency 64
        Bus: primary=05, secondary=06, subordinate=06, sec-latency=64
        Prefetchable memory behind bridge: d8000000-dfffffff
        Capabilities: <access denied>
        Kernel modules: shpchp

06:08.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
  Subsystem: Hauppauge computer works Inc. Device e807
        Flags: bus master, medium devsel, latency 64, IRQ 22
        Memory at dc000000 (32-bit, prefetchable) [size=64M]
        Capabilities: <access denied>
        Kernel driver in use: ivtv
        Kernel modules: ivtv

06:09.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
        Subsystem: Hauppauge computer works Inc. Device e817
        Flags: bus master, medium devsel, latency 64, IRQ 23
        Memory at d8000000 (32-bit, prefetchable) [size=64M]
        Capabilities: <access denied>
        Kernel driver in use: ivtv
        Kernel modules: ivtv

```
Probably the longest code line I have ever posted... It shows that I have an X-Fi card installed, but I don't want to try to get that working, I did a long time ago on a different install, and it was just a pain.  Onboard is enabled in BIOS, and used to work

---

### Post by cdmike2k8 on 2008-12-13
After reading everything on [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting) , running ```
udo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
``` and restarting, the issue went away.  Note to self: Be careful tinkering..

---


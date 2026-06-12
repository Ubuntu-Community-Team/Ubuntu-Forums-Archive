---
title: "Nikon Coolscan 4000ED Scanner"
date: 2010-10-16
forum: New to Ubuntu
---

### Post by chideock on 2010-10-16
Does anyone know how to get a SCSI connected Nikon Super Coolscan 4000 running on Ubuntu 10.10?

1) Install a scsi device
2) What gui app would I use.

Thanks
Tom

---

### Post by Hippytaff on 2010-10-17
You might need to identify and install the drivers I think you can find out by doing

```

lspci

```

with the scanner attached

---

### Post by chideock on 2010-10-17
ok I'll start there thanks

Tom

---

### Post by srs5694 on 2010-10-17
If you've got a SCSI host adapter, it's probably already supported. You should be able to verify that by turning on the scanner and doing:

```

cat /proc/scsi/scsi

```

One of the devices there should be the scanner. (You'll also probably see your disk devices; they're handled by Linux's SCSI subsystem, even if they're SATA or, in the case of Ubuntu, usually even PATA drives.)

As to software, for film scanning I prefer [VueScan.](http://www.hamrick.com) It's shareware (non-free), but it works better than other software I've tried. If you want open source software, look into [SANE](http://www.sane-project.org) and it's GUI front-ends.

---

### Post by chideock on 2010-10-17
Return from lspci
tom@Ubuntu:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133] (rev 03)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133 AGP]
00:04.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 40)
00:04.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:04.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 16)
00:04.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 16)
00:04.4 Bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 40)
00:0a.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
00:0b.0 Ethernet controller: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
00:0c.0 FireWire (IEEE 1394): NEC Corporation IEEE 1394 Host Controller (rev 01)
00:11.0 Mass storage controller: Promise Technology, Inc. PDC20265 (FastTrak100 Lite/Ultra100) (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Rage 128 SM/4x AGP 4x


So the machine sees the firewire card.

Return from "sane-find-scanner" is no scanners found.

I will try srs5694's command
Here it is
tom@Ubuntu:~$ cat /proc/scsi/scsi
Attached devices:
Host: scsi0 Channel: 00 Id: 00 Lun: 00
  Vendor: ATA      Model: WDC WD5000AAKB-0 Rev: 05.0
  Type:   Direct-Access                    ANSI  SCSI revision: 05
Host: scsi1 Channel: 00 Id: 00 Lun: 00
  Vendor: HL-DT-ST Model: DVDRAM GSA-4081B Rev: A104
  Type:   CD-ROM                           ANSI  SCSI revision: 05
Host: scsi1 Channel: 00 Id: 01 Lun: 00
  Vendor: SONY     Model: DVD-ROM DDU1621  Rev: S1.3
  Type:   CD-ROM                           ANSI  SCSI revision: 05

I tried "udevinfo -a -p /sys/class/scsi_generic/sg0 (and sg3). Return says command not found. (this is from another set of instructions I found)

Tom

---

### Post by chideock on 2010-10-17
Here is the lsmod
Module                  Size  Used by
r128                   35342  3 
drm                   168054  4 r128
binfmt_misc             6599  1 
snd_cmipci             30469  2 
gameport                9327  1 snd_cmipci
snd_pcm                71475  1 snd_cmipci
snd_page_alloc          7120  1 snd_pcm
snd_opl3_lib            8850  1 snd_cmipci
snd_hwdep               5040  1 snd_opl3_lib
snd_mpu401_uart         5661  1 snd_cmipci
snd_seq_midi            4588  0 
snd_rawmidi            17783  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
ppdev                   5556  0 
snd_timer              19067  3 snd_pcm,snd_opl3_lib,snd_seq
sbp2                   19332  0 
snd_seq_device          5744  4 snd_opl3_lib,snd_seq_midi,snd_rawmidi,snd_seq
ieee1394               81069  1 sbp2
psmouse                59033  0 
via_agp                 5322  1 
snd                    49006  13 snd_cmipci,snd_pcm,snd_opl3_lib,snd_hwdep,snd_mpu401_uart,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
parport_pc             26058  1 
serio_raw               4022  0 
soundcore                880  1 snd
via686a                11062  0 
i2c_viapro              5777  0 
agpgart                32011  2 drm,via_agp
shpchp                 29886  0 
lp                      7342  0 
parport                31492  3 ppdev,parport_pc,lp
firewire_ohci          21106  0 
firewire_core          46643  1 firewire_ohci
tulip                  46654  0 
floppy                 54311  0 
pata_via                7300  3 
pata_pdc202xx_old       3746  0 
crc_itu_t               1383  1 firewire_core

---

### Post by chideock on 2010-10-17
I now have the following - after a bios upgrade, a re-install of Ubuntu 10.10
tom@ubuntu:~$ sudo cat /proc/scsi/scsi
Attached devices:
Host: scsi0 Channel: 00 Id: 00 Lun: 00
  Vendor: ATA      Model: WDC WD5000AAKB-0 Rev: 05.0
  Type:   Direct-Access                    ANSI  SCSI revision: 05
Host: scsi1 Channel: 00 Id: 00 Lun: 00
  Vendor: HL-DT-ST Model: DVDRAM GSA-4081B Rev: A104
  Type:   CD-ROM                           ANSI  SCSI revision: 05
Host: scsi1 Channel: 00 Id: 01 Lun: 00
  Vendor: SONY     Model: DVD-ROM DDU1621  Rev: S1.3
  Type:   CD-ROM                           ANSI  SCSI revision: 05
Host: scsi4 Channel: 00 Id: 00 Lun: 00
  Vendor: Nikon    Model: LS-4000 ED       Rev: 1.10
  Type:   Scanner                          ANSI  SCSI revision: 02


tom@ubuntu:~$ sudo sane-find-scanner /dev/sg3

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

found SCSI scanner "Nikon LS-4000 ED 1.10" at /dev/sg3
  # Your SCSI scanner was detected. It may or may not be supported by SANE. Try
  # scanimage -L and read the backend's manpage.

  # No USB scanners found. If you expected something different, make sure that
  # you have loaded a kernel driver for your USB host controller and have setup
  # the USB system correctly. See man sane-usb for details.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.


I read the manpages for sane-scsi.5 and tried the scsi command but responce is no command found
I have uploaded lib-sane extras
The Sane pages show that my scanner is supported
My /usr/lib/sane directory has the coolscan packages

What do I do now?

Thanks
Tom

---

### Post by chideock on 2010-10-18
bump

---

### Post by chideock on 2010-10-18
I have found also that after a reboot the scanner does not show in cat /proc/scsi/scsi listing. Turning the scanner off then on and then the device shows in cat /proc/scsi/scsi.

How does one get the device to load automatically?

---

### Post by chideock on 2010-10-18
Well I got it working in xsane except it stops with an out of memory error. I'll have to work on that or anyone have a suggestion?

---


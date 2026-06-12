---
title: "Sound has quit - SB16"
date: 2009-02-16
forum: New to Ubuntu
---

### Post by farledagain on 2009-02-16
Hi, installed Intrepid in an older computer with a PCI SB16.  I initially had sound, but after the computer went into hibernation sound would no longer work.

Reinstalled Intrepid.  Sound did not initially work.  Ran alsamixer and found that volume was zero.  Adjusted volume, it worked.

Restarted computer today, no sound.  Checked alsamixer and other sound settings - everything looks okay.  Ran the following based on sticky posting in multimedia section:

colin@colin-desktop:~$ lspci

00:00.0 Host bridge: VIA Technologies, Inc. VT82C693A/694x [Apollo PRO133x] (rev c4)

00:01.0 PCI bridge: VIA Technologies, Inc. VT82C598/694x [Apollo MVP3/Pro133x AGP]

00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 40)

00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)

00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 16)

00:07.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 16)

00:07.4 Bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 40)

00:08.0 Communication controller: Conexant Systems, Inc. HCF 56k Data/Fax Modem (rev 08)

00:09.0 VGA compatible controller: ATI Technologies Inc 3D Rage Pro 215GP (rev 5c)

00:0a.0 Multimedia audio controller: Ensoniq 5880B [AudioPCI] (rev 02)

00:0c.0 Ethernet controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller


colin@colin-desktop:~$ lsusb

Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


colin@colin-desktop:~$ cat /proc/asound/cards

 0 [AudioPCI       ]: ENS1371 - Ensoniq AudioPCI

                      Ensoniq AudioPCI ENS1371 at 0xe800, irq 10


colin@colin-desktop:~$ cat /proc/asound/modules

 0 snd_ens1371


colin@colin-desktop:~$ aplay -l

**** List of PLAYBACK Hardware Devices ****

card 0: AudioPCI [Ensoniq AudioPCI], device 0: ES1371/1 [ES1371 DAC2/ADC]

  Subdevices: 1/1

  Subdevice #0: subdevice #0

card 0: AudioPCI [Ensoniq AudioPCI], device 1: ES1371/2 [ES1371 DAC1]

  Subdevices: 1/1

  Subdevice #0: subdevice #0


colin@colin-desktop:~$ arecord -l

**** List of CAPTURE Hardware Devices ****

card 0: AudioPCI [Ensoniq AudioPCI], device 0: ES1371/1 [ES1371 DAC2/ADC]

  Subdevices: 1/1

  Subdevice #0: subdevice #0


Any suggestions?

farledagain

---

### Post by farledagain on 2009-03-02
Sound started working again and has consistently worked since then.  Couldn't tell you why....

---


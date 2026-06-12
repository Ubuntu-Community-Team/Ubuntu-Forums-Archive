---
title: "no sound card found and no audio in 10.10 ubuntu"
date: 2011-04-15
forum: New to Ubuntu
---

### Post by gskumar31 on 2011-04-15
hi after following through number of posts i am adding this post .
I have installed with ubuntu 10.10 and getting sound crapy and so i nstalled alsa drivers,lib, utils of  1.0.24 version from alsa-project.org . 
After that I did nt find audio icon and output device and in system->preferences->sound    it is showing dummy output.

I tried with so many posts like changeing /adding alsa-base.conf file with intel-hda name 
but it did nt work.
Can you please tell me possible solution.

I will add here script so that you can see entire details of PC. 

!!################################
!!ALSA Information Script v 0.4.60
!!################################

!!Script ran on: Fri Apr 15 20:43:46 UTC 2011


!!Linux Distribution
!!------------------

Ubuntu 10.10 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 10.10"


!!DMI Information
!!---------------

Manufacturer:      TOSHIBA
Product Name:      Satellite A105
Product Version:   PSAA8U-1L502K


!!Kernel Information
!!------------------

Kernel release:    2.6.35-28-generic-pae
Operating System:  GNU/Linux
Architecture:      i686
Processor:         unknown
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     
Library version:    1.0.24.1
Utilities version:  1.0.24.2


!!Loaded ALSA modules
!!-------------------



!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes

ESound Daemon:
      Installed - Yes (/usr/bin/esd)
      Running - No


!!Soundcards recognised by ALSA
!!-----------------------------



!!PCI Soundcards installed in the system
!!--------------------------------------

00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
07:06.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!--------------------------------------------------------

00:1b.0 0403: 8086:27d8 (rev 02)
    Subsystem: 1179:ff10


!!Modprobe options (Sound related)
!!--------------------------------

snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-caiaq: index=-2
snd-usb-ua101: index=-2
snd-usb-us122l: index=-2
snd-usb-usx2y: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388
snd-pcsp: index=-2
snd-usb-audio: index=-2
snd-hda-intel: model=dallas position_fix=0


!!Loaded sound module options
!!--------------------------


!!ALSA Device nodes
!!-----------------



!!Aplay/Arecord output
!!------------

APLAY

aplay: device_list:240: no soundcards found...

ARECORD

arecord: device_list:240: no soundcards found...

!!Amixer output
!!-------------


!!Alsactl output
!!-------------

--startcollapse--
--endcollapse--


!!All Loaded Modules
!!------------------

Module
pppoe
pppox
nls_iso8859_1
nls_cp437
vfat
fat
binfmt_misc
parport_pc
ppdev
arc4
iwl3945
iwlcore
pcmcia
joydev
i915
drm_kms_helper
drm
intel_agp
mac80211
agpgart
i2c_algo_bit
lp
video
output
yenta_socket
pcmcia_rsrc
pcmcia_core
psmouse
cfg80211
parport
tifm_7xx1
tifm_core
serio_raw
usb_storage
e100
mii
firewire_ohci
sdhci_pci
sdhci
led_class
firewire_core
crc_itu_t


!!ALSA/HDA dmesg
!!------------------








Thanks in advance.

---

### Post by James Keating on 2011-10-28
I had the same problem, and for me the solution was surprisingly simple. The correct module was present, but turned off. I am using Lubuntu, which uses Alsa. 

From the command line, I ran alsamixer, pressed F6 to select sound card, and chose HDA Intel. Now sound works, even after rebooting.

Alsamixergui doesn't seem to have the ability to select the sound card. If you are using a different sound system, there should be some equivalent ability to turn on the master.

Before I found the solution, I went through the steps in the sticky Sound Problems Solutions Guide. Following that, I ran 

aplay -l

which told me I had
card 0: Intel [HDA Intel], device 0: ALC861 Analog [ALC861 Analog]

then

lspci -v

which told me
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
	Subsystem: Toshiba America Info Systems Toshiba Satellite A100-796 audio (Realtek ALC861)
	Flags: bus master, fast devsel, latency 0, IRQ 43
	Memory at f0b40000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

so I know I need to enable module snd-hda-intel

I tried
sudo modprobe snd-[tab]

but the card wasn't listed.

However, the search
slocate hda-intel

turned up 
/lib/modules/3.0.0-12-generic/kernel/sound/pci/hda/snd-hda-intel.ko

so I knew the module was present.

I thought I would have to add the line snd-hda-intel to /etc/modules and reboot. Perhaps that would work, but for me it's not necessary.

---


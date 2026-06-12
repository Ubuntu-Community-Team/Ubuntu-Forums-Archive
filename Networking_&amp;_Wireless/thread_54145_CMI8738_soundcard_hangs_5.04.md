---
title: "CMI8738 soundcard hangs 5.04"
date: 2005-08-03
forum: Networking &amp; Wireless
---

### Post by casperl on 2005-08-03
Hi all,

I have replaced the old soundcard (SB-pro that never worked) with a CMI8738 soundcard.  Upon playing a sound the system freezes solid, hdd led stays on, no response from kbd etc.  A .wav file would start playing (sound is audible) and the system then hangs.

I have booted up in single user mode and modprobe cmpci reports:
cmpci: version $Revision 6.82$ time etc 

In my absolute ignorance I have attempted:
sudo dpkg-reconfigure alsa-base
sudo dpkg-reconfigure alsa-oss
sudo dpkg-reconfigure alsa-utils

My best guess is that dormant drivers / settings are still present, unless either the PCI card is faulty or the card is totally incompatible with ubuntu.

What can I try?

TIA

---

### Post by casperl on 2005-08-04
Update #2

sudo lspci reports:
0000:00:00.0 Host bridge: VIA Technologies, Inc. VT82C693A/694x [Apollo PRO133x] (rev 44)
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT82C598/694x [Apollo MVP3/Pro133x AGP]
0000:00:07.0 ISA bridge: VIA Technologies, Inc. VT82C596 ISA [Mobile South] (rev 22)
0000:00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 10)
0000:00:07.3 Host bridge: VIA Technologies, Inc. VT82C596 Power Management (rev 30)
0000:00:0f.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:00:10.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
0000:00:13.0 USB Controller: OPTi Inc. 82C861 (rev 10)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV5 [RIVA TNT2/TNT2 Pro] (rev 15)

I have also checked that the following are true in the system BIOS:

Plug 'n Play OS is selected
All plug 'n play PCI slots
No ISA cards
Nothing selects IRQ 5 etc
Parallel port is set to IRQ7 E378 (default)
No reserved DMA / IRQ's 

Cannot trace any other conflict with H/ware

sudo modprobe cmpci reports:
cmpci: version $Revision 6.82$ time (system time)

A short .wav file < 2 secs can be played back
.wav files > 2 seconds freezes system

Have now removed sound card & replaced with SB card - with own set of problems though.

---

### Post by mr_stabby on 2005-08-04
psst - you're in the networking forum... Might be better off posting in the general hardware help forum.

---


---
title: "No Sound Card Detected"
date: 2009-05-14
forum: New to Ubuntu
---

### Post by Rog3236 on 2009-05-14
I attempted to upgrade my Alsa sound from version 1.0.18rc3 to the newer version which is 1.0.20. It didn't work and I started out with a working sound card with the only problem being I couldn't get the system to recognize a USB sound card adapter and someone suggested an upgrade might be helpful.

Well. Now I don't have anything. when I give a aplay -l command I get a device_list:217: no soundcards found...

As a Newbie I have no idea of how I can go about getting things working again. Any suggestions would be helpful.

---

### Post by spiderbatdad on 2009-05-14
Often the module is configured per card. For example, for intel:
```
./configure --with-cards=hda-intel

```or --with-cards=all
several things have to be done, generally, after rebuilding alsa, for example ```
sudo depmod -a
```Usually /etc/modprobe.d/alas-base.conf would also be edited to include an option like ```
options snd-hda-intel model=acer
```There are quite a number of options available. Then also a restart. Did you have a tutorial to follow?

---

### Post by Rog3236 on 2009-05-15
I have been following the procedures in the Ubuntu sound troubleshooting guide. one of the steps is to see if the card is installed and recognized when I do a lspci -v | less command I do get this result amongst many others. Yet a cat /proc/asound/version shows no card found

00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
        Subsystem: Dell Device 019d
        Flags: bus master, medium devsel, latency 0, IRQ 3
        I/O ports at ee00 [size=256]
        I/O ports at edc0 [size=64]
        Memory at feb7fa00 (32-bit, non-prefetchable) [size=512]
        Memory at feb7f900 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

---

### Post by spiderbatdad on 2009-05-15
```
cat /proc/asound/version
```this should only show you the alsa version. ```
cat /proc/asound/cards
```should show you detected sound cards.

lspci shows me this:```
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
        Subsystem: IBM Device 0508
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at 1c00 [size=256]
        I/O ports at 18c0 [size=64]
        Kernel driver in use: Intel ICH
        Kernel modules: snd-intel8x0

```some how, i think, the modlue isnt loaded. Try this:```
$ modprobe -r snd-hda-intel
  $ modprobe snd-hda-intel
```Also have you edited the alsa-base.conf for your model? Add this to the end of the file /etc/modprobe.d/alsa-base.conf:```
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
options snd-hda-intel model=dell
options snd-hda-intel enable_msi=1

```then reboot and check volume control options.

---

### Post by Rog3236 on 2009-05-16
Boy! Right from the giddyup with the first commands I get:

roger@rog3236-desktop:~$ modprobe -r snd-hda-intel
roger@rog3236-desktop:~$ modprobe snd-hda-intel
WARNING: Error inserting soundcore (/lib/modules/2.6.28-11-generic/kernel/sound/soundcore.ko): Operation not permitted
WARNING: Error inserting snd (/lib/modules/2.6.28-11-generic/kernel/sound/acore/snd.ko): Operation not permitted
WARNING: Error inserting snd_timer (/lib/modules/2.6.28-11-generic/kernel/sound/acore/snd-timer.ko): Operation not permitted
WARNING: Error inserting snd_pcm (/lib/modules/2.6.28-11-generic/kernel/sound/acore/snd-pcm.ko): Operation not permitted
WARNING: Error inserting snd_hwdep (/lib/modules/2.6.28-11-generic/kernel/sound/acore/snd-hwdep.ko): Operation not permitted
WARNING: Error inserting snd_hda_codec (/lib/modules/2.6.28-11-generic/kernel/sound/pci/hda/snd-hda-codec.ko): Operation not permitted
FATAL: Error inserting snd_hda_intel (/lib/modules/2.6.28-11-generic/kernel/sound/pci/hda/snd-hda-intel.ko): Operation not permitted
roger@rog3236-desktop:~$

---

### Post by Rog3236 on 2009-05-16
Still using the Ubuntu sound troubleshooting guide I attempted a couple of other commands with the following results:

roger@rog3236-desktop:~$ aplay -l
aplay: device_list:217: no soundcards found...
roger@rog3236-desktop:~$ sudo aptitude install linux-ubuntu-modules-`uname -r` linux-generic
[sudo] password for roger: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Couldn't find any package whose name or description matched "linux-ubuntu-modules-2.6.28-11-generic"
Couldn't find any package whose name or description matched "linux-ubuntu-modules-2.6.28-11-generic"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done

---

### Post by spiderbatdad on 2009-05-17
> **Rog3236 said:**
> Boy! Right from the giddyup with the first commands I get:

roger@rog3236-desktop:~$ modprobe -r snd-hda-intel
roger@rog3236-desktop:~$ modprobe snd-hda-intel
WARNING: Error inserting soundcore (/lib/modules/2.6.28-11-generic/kernel/sound/soundcore.ko): Operation not permitted
WARNING: Error inserting snd (/lib/modules/2.6.28-11-generic/kernel/sound/acore/snd.ko): Operation not permitted
WARNING: Error inserting snd_timer (/lib/modules/2.6.28-11-generic/kernel/sound/acore/snd-timer.ko): Operation not permitted
WARNING: Error inserting snd_pcm (/lib/modules/2.6.28-11-generic/kernel/sound/acore/snd-pcm.ko): Operation not permitted
WARNING: Error inserting snd_hwdep (/lib/modules/2.6.28-11-generic/kernel/sound/acore/snd-hwdep.ko): Operation not permitted
WARNING: Error inserting snd_hda_codec (/lib/modules/2.6.28-11-generic/kernel/sound/pci/hda/snd-hda-codec.ko): Operation not permitted
FATAL: Error inserting snd_hda_intel (/lib/modules/2.6.28-11-generic/kernel/sound/pci/hda/snd-hda-intel.ko): Operation not permitted
roger@rog3236-desktop:~$

Enable backports via System>>Aministration>>Software Sources.
```
roger@rog3236-desktop:~$ **sudo** modprobe -r snd-hda-intel
roger@rog3236-desktop:~$ **sudo** modprobe snd-hda-intel
```

---

### Post by Rog3236 on 2009-05-17
Unfortunately, receive the following when attempting to execute those commands:

roger@rog3236-desktop:~$ sudo modprobe -r snd-hda-intel
[sudo] password for roger: 
roger@rog3236-desktop:~$ sudo modprobe -r snd-hda-intel
roger@rog3236-desktop:~$ modprobe snd-hda-intel
WARNING: Error inserting soundcore (/lib/modules/2.6.28-11-generic/kernel/sound/soundcore.ko): Operation not permitted
WARNING: Error inserting snd (/lib/modules/2.6.28-11-generic/kernel/sound/acore/snd.ko): Operation not permitted
WARNING: Error inserting snd_timer (/lib/modules/2.6.28-11-generic/kernel/sound/acore/snd-timer.ko): Operation not permitted
WARNING: Error inserting snd_pcm (/lib/modules/2.6.28-11-generic/kernel/sound/acore/snd-pcm.ko): Operation not permitted
WARNING: Error inserting snd_hwdep (/lib/modules/2.6.28-11-generic/kernel/sound/acore/snd-hwdep.ko): Operation not permitted
WARNING: Error inserting snd_hda_codec (/lib/modules/2.6.28-11-generic/kernel/sound/pci/hda/snd-hda-codec.ko): Operation not permitted
FATAL: Error inserting snd_hda_intel (/lib/modules/2.6.28-11-generic/kernel/sound/pci/hda/snd-hda-intel.ko): Operation not permitted
roger@rog3236-desktop:~$ 

Can't understand this "operation not permitted" since I am the only user of the operating system.

---

### Post by Rog3236 on 2009-05-17
As a Newbie I don't understand what steps I should take after your suggestion:
 Enable backports via System>>Aministration>>Software Sources.
can't understand what I can do with those various windows that open up.

---

### Post by Rog3236 on 2009-05-21
After not having any success at all attempting to get my sound card recognized the latest update of Ubuntu 9.04 took care of my particular problem.

---


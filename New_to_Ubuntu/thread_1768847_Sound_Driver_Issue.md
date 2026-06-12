---
title: "Sound Driver Issue"
date: 2011-05-27
forum: New to Ubuntu
---

### Post by samyo on 2011-05-27
Hi all ;)
I recently installed Ubuntu 11.04. Everything was fine. When i tried to use a dial-up connection, I found that no modem-driver was installed. So i checked [www.linuxant.org]("http://www.linuxant.org") (after going through [www.linmodems.org]("http://www.linmodems.org")). Before installing the modem drivers, it was recommended that I should install Alsa-drivers-linuxant. I did that. But during the installation I got some error configuring the hsf and left is there (being a newbie :(). Thats it!
After restarting laptop, there is no sound. I tried uninstalling the Alsa-drivers-linuxant, but the speakers are still not working. I went through many posts and threads and lastly i followed [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting). I have posted whatever data I have regarding the trials.


1) Volume Turned Up,Speaker is not Muted, 
2) When I run "aplay /usr/share/sounds/alsa/Front_Center.wav", I hear no sound. No other User can play it either :( . The User is not in the Audio Group.

3)Results of (sudo aplay -l )
aplay: device_list:240: no soundcards found...

4) results of (find /lib/modules/`uname -r` | grep snd)
nothing :(

5)Results of (sudo apt-get install linux-ubuntu-modules-`uname -r` linux-generic)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-ubuntu-modules-2.6.38-8-generic
E: Couldn't find any package by regex 'linux-ubuntu-modules-2.6.38-8-generic'

6) Results of (lspci -v | less)
(I'm posting only the Audio Part)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
        Subsystem: Hewlett-Packard Company Device 30cd
        Flags: bus master, fast devsel, latency 0, IRQ 11
        Memory at f4500000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>


Please suggest some method to reinstall the sound driver. i dont want to reinstall Ubuntu coz I've updated it :D and hope it gets solved.
Waiting for responses :p

---

### Post by samyo on 2011-05-27
Result of ( bash alsa-info.sh --stdout )

cat: /proc/asound/version: No such file or directory
grep: /proc/asound/cards: No such file or directory
cat: /proc/asound/cards: No such file or directory
cat: /proc/asound/modules: No such file or directory
ls: cannot access /dev/snd/*: No such file or directory
grep: /proc/asound/cards: No such file or directory
/sbin/alsactl: save_state:1519: No soundcards found...
cat: /tmp/alsa-info.EcOZmOAwGR/alsactl.tmp: No such file or directory
upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.60
!!################################

!!Script ran on: Fri May 27 15:28:50 UTC 2011


!!Linux Distribution
!!------------------

Ubuntu 11.04 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 11.04"


!!DMI Information
!!---------------

Manufacturer:      Hewlett-Packard
Product Name:      HP Pavilion dv2700 Notebook PC
Product Version:   F.2E    


!!Kernel Information
!!------------------

Kernel release:    2.6.38-8-generic
Operating System:  GNU/Linux
Architecture:      i686
Processor:         i686
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

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!--------------------------------------------------------

00:1b.0 0403: 8086:284b (rev 03)
    Subsystem: 103c:30cd


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
usb_storage
uas
ppp_deflate
zlib_deflate
bsd_comp
ppp_async
crc_ccitt
rfcomm
sco
bnep
l2cap
btusb
bluetooth
binfmt_misc
parport_pc
ppdev
vesafb
nvidia
arc4
r852
sm_common
nand
nand_ids
nand_ecc
joydev
iwlagn
iwlcore
mtd
hp_wmi
mac80211
cfg80211
uvcvideo
videodev
psmouse
video
lp
parport
sparse_keymap
serio_raw
usbhid
hid
firewire_ohci
firewire_core
sdhci_pci
ahci
sky2
sdhci
crc_itu_t
libahci


!!ALSA/HDA dmesg
!!------------------

---

### Post by mylittletom on 2011-07-21
I have the same problems as yours !  I believe that  alsa-linuxant from   [www.linuxant.org]("http://www.linuxant.org/") is the culprit  which causes a big mess for ubuntu audio function. Even I followed instructions from [www.alsa-project.org]("http://www.alsa-project.org") to recompile  , it can't help. 

The only way  is  to discard all current system , reinstall from "ground zero".


updated for someone's still interested in this problem :  

I tried updating kernel 3.0 , then manually reinstall nvidia driver , and saw my sound driver restored . What a release to avoid reinstalling Ubuntu !

---


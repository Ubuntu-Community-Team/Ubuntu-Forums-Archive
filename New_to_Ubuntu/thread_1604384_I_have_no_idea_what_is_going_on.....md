---
title: "I have no idea what is going on...."
date: 2010-10-24
forum: New to Ubuntu
---

### Post by Amur756 on 2010-10-24
i just recently started using ubuntu for the last 2 weeks or so.  i have been an avid windows user my whole life, i hate mac's, and found this OS which seems to have the keys the perfect everything... except i dont know how to use it..

i have messed around a bit and now i feel im messing things up even worse.  i have a 2010 sony vaio VCP-ea290x and frickin love it.  it has an i5-540 processor and an independant graphics card but in not exactly 100% on its model, i do know its an ATI.

everything seems to be running smoothly but i have no sound.  i use to have them detected and after playing around for a couple days in the terminal, i now cannot detect my sound cards.  I think i have done some sort of system analysis and if anyone can take a look at it, point out what is good or bad about it, and if possible show me how to get my sound to work i would be soo soo thankful.  

he is my system:

[INDENT]!!################################
!!ALSA Information Script v 0.4.59
!!################################

!!Script ran on: Sun Oct 24 03:31:02 UTC 2010


!!Linux Distribution
!!------------------

Ubuntu 10.04.1 LTS \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 10.04.1 LTS"


!!DMI Information
!!---------------

Manufacturer:      Sony Corporation
Product Name:      VPCEA290X


!!Kernel Information
!!------------------

Kernel release:    2.6.32-25-generic
Operating System:  GNU/Linux
Architecture:      x86_64
Processor:         unknown
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.23
Library version:    1.0.23
Utilities version:  1.0.22


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

--- no soundcards ---


!!PCI Soundcards installed in the system
!!--------------------------------------

00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
01:00.1 Audio device: ATI Technologies Inc Manhattan HDMI Audio [Mobility Radeon HD 5000 Series]


!!Advanced information - PCI Vendor/Device/Susbsystem ID's
!!--------------------------------------------------------

00:1b.0 0403: 8086:3b56 (rev 05)
	Subsystem: 104d:9071
--
01:00.1 0403: 1002:aa68
	Subsystem: 104d:9071


!!Modprobe options (Sound related)
!!--------------------------------

snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-us122l: index=-2
snd-usb-usx2y: index=-2
snd-usb-caiaq: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388
snd-pcsp: index=-2


!!Loaded sound module options
!!--------------------------


!!ALSA Device nodes
!!-----------------

crw-rw----  1 root audio 116,  1 Oct 23 21:01 /dev/snd/seq
crw-rw----  1 root audio 116, 33 Oct 23 21:01 /dev/snd/timer


!!Aplay/Arecord output
!!------------

APLAY

aplay: device_list:223: no soundcards found...

ARECORD

arecord: device_list:223: no soundcards found...

!!Amixer output
!!-------------


!!Alsactl output
!!-------------

--startcollapse--
--endcollapse--


!!All Loaded Modules
!!------------------

Module
nls_utf8
udf
crc_itu_t
binfmt_misc
ppdev
ipmi_msghandler
nfsd
lockd
nfs_acl
auth_rpcgss
sunrpc
exportfs
dlm
configfs
snd_seq_dummy
snd_hwdep
snd_pcm_oss
snd_mixer_oss
snd_pcm
snd_seq_oss
snd_seq_midi
snd_rawmidi
snd_seq_midi_event
arc4
snd_seq
joydev
snd_timer
ath9k
mac80211
ath
sdhci_pci
snd_seq_device
cfg80211
uvcvideo
sdhci
fglrx
fbcon
tileblit
snd
font
lp
soundcore
bitblit
videodev
softcursor
psmouse
v4l1_compat
led_class
video
intel_agp
v4l2_compat_ioctl32
vga16fb
serio_raw
snd_page_alloc
vgastate
output
parport
sony_laptop
usbhid
hid
ahci
sky2


!!ALSA/HDA dmesg
!!------------------

[   23.450199] phy0: Atheros AR9285 MAC/BB Rev:2 AR5133 RF Rev:e0: mem=0xffffc900057a0000, irq=16
[   24.334692] snd_hda_codec: disagrees about version of symbol snd_ctl_add
[   24.334695] snd_hda_codec: Unknown symbol snd_ctl_add
[   24.334789] snd_hda_codec: disagrees about version of symbol snd_card_register
[   24.334790] snd_hda_codec: Unknown symbol snd_card_register
[   24.334851] snd_hda_codec: disagrees about version of symbol snd_card_proc_new
[   24.334852] snd_hda_codec: Unknown symbol snd_card_proc_new
[   24.334935] snd_hda_codec: disagrees about version of symbol snd_add_device_sysfs_file
[   24.334936] snd_hda_codec: Unknown symbol snd_add_device_sysfs_file
[   24.335031] snd_hda_codec: disagrees about version of symbol snd_ctl_remove
[   24.335033] snd_hda_codec: Unknown symbol snd_ctl_remove
[   24.335093] snd_hda_codec: disagrees about version of symbol snd_ctl_find_id
[   24.335095] snd_hda_codec: Unknown symbol snd_ctl_find_id
[   24.335180] snd_hda_codec: disagrees about version of symbol snd_ctl_new1
[   24.335182] snd_hda_codec: Unknown symbol snd_ctl_new1
[   24.335272] snd_hda_codec: disagrees about version of symbol snd_component_add
[   24.335273] snd_hda_codec: Unknown symbol snd_component_add
[   24.335335] snd_hda_codec: disagrees about version of symbol snd_ctl_make_virtual_master
[   24.335336] snd_hda_codec: Unknown symbol snd_ctl_make_virtual_master
[   24.335481] snd_hda_codec: disagrees about version of symbol snd_ctl_boolean_mono_info
[   24.335482] snd_hda_codec: Unknown symbol snd_ctl_boolean_mono_info
[   24.335608] snd_hda_codec: disagrees about version of symbol snd_hwdep_new
[   24.335610] snd_hda_codec: Unknown symbol snd_hwdep_new
[   24.335838] snd_hda_codec: disagrees about version of symbol _snd_ctl_add_slave
[   24.335839] snd_hda_codec: Unknown symbol _snd_ctl_add_slave
[   24.336165] snd_hda_codec: disagrees about version of symbol snd_pcm_hw_constraint_step
[   24.336166] snd_hda_codec: Unknown symbol snd_pcm_hw_constraint_step
[   24.394543] snd_hda_codec: disagrees about version of symbol snd_ctl_add
[   24.394545] snd_hda_codec: Unknown symbol snd_ctl_add
[   24.394640] snd_hda_codec: disagrees about version of symbol snd_card_register
[   24.394641] snd_hda_codec: Unknown symbol snd_card_register
[   24.394702] snd_hda_codec: disagrees about version of symbol snd_card_proc_new
[   24.394703] snd_hda_codec: Unknown symbol snd_card_proc_new
[   24.394786] snd_hda_codec: disagrees about version of symbol snd_add_device_sysfs_file
[   24.394787] snd_hda_codec: Unknown symbol snd_add_device_sysfs_file
[   24.394883] snd_hda_codec: disagrees about version of symbol snd_ctl_remove
[   24.394884] snd_hda_codec: Unknown symbol snd_ctl_remove
[   24.394945] snd_hda_codec: disagrees about version of symbol snd_ctl_find_id
[   24.394946] snd_hda_codec: Unknown symbol snd_ctl_find_id
[   24.395032] snd_hda_codec: disagrees about version of symbol snd_ctl_new1
[   24.395033] snd_hda_codec: Unknown symbol snd_ctl_new1
[   24.395123] snd_hda_codec: disagrees about version of symbol snd_component_add
[   24.395124] snd_hda_codec: Unknown symbol snd_component_add
[   24.395187] snd_hda_codec: disagrees about version of symbol snd_ctl_make_virtual_master
[   24.395188] snd_hda_codec: Unknown symbol snd_ctl_make_virtual_master
[   24.395333] snd_hda_codec: disagrees about version of symbol snd_ctl_boolean_mono_info
[   24.395335] snd_hda_codec: Unknown symbol snd_ctl_boolean_mono_info
[   24.395461] snd_hda_codec: disagrees about version of symbol snd_hwdep_new
[   24.395462] snd_hda_codec: Unknown symbol snd_hwdep_new
[   24.395691] snd_hda_codec: disagrees about version of symbol _snd_ctl_add_slave
[   24.395692] snd_hda_codec: Unknown symbol _snd_ctl_add_slave
[   24.396018] snd_hda_codec: disagrees about version of symbol snd_pcm_hw_constraint_step
[   24.396019] snd_hda_codec: Unknown symbol snd_pcm_hw_constraint_step
[   24.995319] cfg80211: World regulatory domain updated:

[/INDENT]please someone help me if you can!! im really really excited to start learning the ins and outs of this system and eventualy start programing in both linux/unix and Windows!

---

### Post by themusicalduck on 2010-10-24
I can't find much information about your laptop/chipset and Ubuntu on Google.

Have a look at this page - [https://wiki.ubuntu.com/DebuggingSoundProblems](https://wiki.ubuntu.com/DebuggingSoundProblems)

Also, if you are new to Ubuntu it might be worth looking at [www.ubuntu-manual.org](www.ubuntu-manual.org)

You could also try and load up an Ubuntu live CD session of Ubuntu 10.10 to see if the sound works in the latest version of Ubuntu.

edit: changed some wrong info

---

### Post by sgosnell on 2010-10-24
Are you sure Pulseaudio is set to use the soundcard you have?  Are you sure the volume is up?  Not muted?

---

### Post by garvinrick4 on 2010-10-24
When you have a long bit of a post you can highlight the whole thing and hit the # sign in the upper right of Message box and will put in a nice little box that will scrowl. Or you can put the [code] tags in yourself.

---

### Post by Amur756 on 2010-10-25
Thanks for the advice!  im going to look into the manual for sure soon.  i just wish i could figure out my sound an graphics cards.  its driving me insane!  i had my graphics working before and now everything has become choppy and no matter what driver i update or ATI catalyst i install i cant get it back =/.  is there a way to force ubuntu to find your devices?  i was at least able to see my sound card a week or so ago but they just wouldent work.  and i have a readon 5400 series independent graphics card if that helps anyone with a fix for me. 

Thanks for looking into it again!  I havent messed with forums all too much but i have to say the social support is great!  hope to put an end to this headache soon so if you have any ideas ill try anything!

P.s.  i also cut up my 500GB HD into about 3-4 sections.  about 250 for my NSFT windows 7 C:\ and 100GB or so for ubuntu.  leaving the other 150 scattered as healthy free space but i cant get them to reformat and extend to my other 2 primary drives...  i would love to be able to benifit from all of my HD so again if anyone has a solution im all ears!

---

### Post by ArgusVision on 2010-10-25
> **Amur756 said:**
> 
P.s.  i also cut up my 500GB HD into about 3-4 sections.  about 250 for my NSFT windows 7 C:\ and 100GB or so for ubuntu.  leaving the other 150 scattered as healthy free space but i cant get them to reformat and extend to my other 2 primary drives...  i would love to be able to benifit from all of my HD so again if anyone has a solution im all ears!

Toss in the Ubuntu live CD, open Gparted. Format the remaining 150 as NTFS (So both OS's can see it) and as an extended partition. If you give it a mount point /windows should work fine.

---


---
title: "Headphone jack help.."
date: 2010-12-26
forum: New to Ubuntu
---

### Post by promal_cotton on 2010-12-26
So I actually just got 10.10.  First time using Ubuntu.  I love it.. <3  I just can't seem to get the sound out of my headphone jack to work...  I have a USB headset that works just fine, but I have speakers that I want to use and they aren't USB...  I'm using a Laptop.  Gateway NV52.  64 bit system.  I tried looking for this else where but it only gave me ways to edit the file thats it /etc blah blah and I can't edit that file so yeah... :|  And if you can..  I don't know how to.  I can try and provide any information you guys need to help me fix this problem.  But like I said...  First time with Ubuntu.  Just got it 2 days ago even...

---

### Post by cherva on 2010-12-26
Can you open a terminal Applications->Accessories-> Terminal
And type these commands so we can find more about your problem (commands starting with sudo can ask for your accounts password):
```
sudo lshw -short | grep multimedia
```
```
cat /proc/asound/version
```
```
lsmod | grep snd
```
The next command will donwload a script witch will give us more info on ALSA ( the sound system ) After running it it will create a file in your home directory called alsa-info. Hit ENTER when you see the OK button.
```
wget -O alsa-info.sh http://alsa-project.org/alsa-info.sh && bash ./alsa-info.sh --with-configs --with-devices --no-upload --stdout
```
Now paste the results of all this commands...

---

### Post by promal_cotton on 2010-12-26
/0/100/1/5.1                 multimedia  RS780 Azalia controller
/0/100/14.2                  multimedia  SBx00 Azalia (Intel HDA)

That was for the first code

Advanced Linux Sound Architecture Driver Version 1.0.23.

Was the second code

And the third is a little long and didn't all fit...

[spoiler]		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 80'
		comment.dbmin -7400
		comment.dbmax 600
		iface MIXER
		name 'External Mic Volume'
		value.0 68
		value.1 68
	}
	control.4 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'External Mic Switch'
		value.0 true
		value.1 true
	}
	control.5 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 80'
		comment.dbmin -7400
		comment.dbmax 600
		iface MIXER
		name 'Docking Mic Volume'
		value.0 68
		value.1 68
	}
	control.6 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Docking Mic Switch'
		value.0 true
		value.1 true
	}
	control.7 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 74'
		comment.dbmin -7400
		comment.dbmax 0
		iface MIXER
		name 'Master Playback Volume'
		value.0 74
		value.1 74
	}
	control.8 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Master Playback Switch'
		value true
	}
	control.9 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Con Mask'
		value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.10 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Pro Mask'
		value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.11 {
		comment.access 'read write'
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Default'
		value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.12 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Switch'
		value true
	}
	control.13 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'IEC958 Default PCM Playback Switch'
		value true
	}
	control.14 {
		comment.access 'read write user'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 255'
		comment.tlv '0000000100000008ffffec1400000014'
		comment.dbmin -5100
		comment.dbmax 0
		iface MIXER
		name 'PCM Playback Volume'
		value.0 255
		value.1 255
	}
}
state.HDMI {
	control.1 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Con Mask'
		value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.2 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Pro Mask'
		value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.3 {
		comment.access 'read write'
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Default'
		value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.4 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Switch'
		value true
	}
}
state.Headset {
	control.1 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Mic Playback Switch'
		value false
	}
	control.2 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 464'
		comment.dbmin -4100
		comment.dbmax -1200
		iface MIXER
		name 'Mic Playback Volume'
		value 0
	}
	control.3 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Speaker Playback Switch'
		value true
	}
	control.4 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 44'
		comment.dbmin -4100
		comment.dbmax 300
		iface MIXER
		name 'Speaker Playback Volume'
		value.0 36
		value.1 36
	}
	control.5 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Mic Capture Switch'
		value true
	}
	control.6 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 13'
		comment.dbmin 1600
		comment.dbmax 2900
		iface MIXER
		name 'Mic Capture Volume'
		value 0
	}
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
qcaux
usbserial
cdc_acm
snd_usb_audio
snd_usbmidi_lib
cryptd
aes_x86_64
aes_generic
binfmt_misc
parport_pc
ppdev
arc4
snd_hda_codec_atihdmi
radeon
snd_hda_codec_conexant
snd_hda_intel
snd_hda_codec
snd_seq_midi
ath9k
snd_hwdep
snd_rawmidi
ath9k_common
snd_pcm
snd_seq_midi_event
ttm
ath9k_hw
ath
snd_seq
mac80211
drm_kms_helper
snd_timer
acer_wmi
snd_seq_device
uvcvideo
drm
snd
videodev
v4l1_compat
video
i2c_algo_bit
v4l2_compat_ioctl32
cfg80211
joydev
output
psmouse
edac_core
soundcore
serio_raw
k10temp
edac_mce_amd
snd_page_alloc
i2c_piix4
led_class
shpchp
lp
parport
usbhid
hid
ahci
tg3
libahci


!!Sysfs Files
!!-----------

/sys/class/sound/hwC0D0/init_pin_configs:
0x16 0x01214040
0x17 0x400001f0
0x18 0x01a19030
0x19 0x400001f0
0x1a 0x92170110
0x1b 0x400001f0
0x1c 0x214571f0
0x1d 0x97a70120

/sys/class/sound/hwC0D0/driver_pin_configs:

/sys/class/sound/hwC0D0/user_pin_configs:

/sys/class/sound/hwC0D0/init_verbs:

/sys/class/sound/hwC0D1/init_pin_configs:
0x73 0x016a10f0

/sys/class/sound/hwC0D1/driver_pin_configs:

/sys/class/sound/hwC0D1/user_pin_configs:

/sys/class/sound/hwC0D1/init_verbs:

/sys/class/sound/hwC1D0/init_pin_configs:
0x03 0x18560010

/sys/class/sound/hwC1D0/driver_pin_configs:

/sys/class/sound/hwC1D0/user_pin_configs:

/sys/class/sound/hwC1D0/init_verbs:


!!ALSA/HDA dmesg
!!------------------

[   13.290293] ath9k 0000:09:00.0: setting latency timer to 64
[   13.336572] HDA Intel 0000:00:14.2: power state changed by ACPI to D0
[   13.336650] HDA Intel 0000:00:14.2: power state changed by ACPI to D0
[   13.336705] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   13.579405] input: HDA ATI SB Mic as /devices/pci0000:00/0000:00:14.2/sound/card0/input10
[   13.579811] input: HDA ATI SB Mic as /devices/pci0000:00/0000:00:14.2/sound/card0/input11
[   13.580063] input: HDA ATI SB Headphone as /devices/pci0000:00/0000:00:14.2/sound/card0/input12
[   13.581236] HDA Intel 0000:01:05.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[   13.581313] HDA Intel 0000:01:05.1: setting latency timer to 64
[   13.637726] [drm] radeon defaulting to kernel modesetting.
--
[   13.871708] [drm] Connector 2:
[   13.871710] [drm]   HDMI-A
[   13.871712] [drm]   HPD1
--
[   17.201952] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   18.923730] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
[   21.108389] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
--
[19627.870084] ehci_hcd 0000:00:13.2: PCI INT B disabled
[19627.960082] HDA Intel 0000:01:05.1: PCI INT B disabled
[19627.960113] ACPI handle has no context!
[19627.980025] PM: suspend of drv:HDA Intel dev:0000:01:05.1 complete after 121.145 msecs
[19628.185574] PM: suspend of drv:sd dev:0:0:0:0 complete after 392.770 msecs
--
[19629.062547] PM: suspend of drv:pci dev:0000:00:01.0 complete after 1203.078 msecs
[19630.990011] hda-intel: azx_get_response timeout, switching to polling mode: last cmd=0x00170503
[19632.000009] hda_intel: azx_get_response timeout, switching to single_cmd mode: last cmd=0x00170503
[19632.110119] HDA Intel 0000:00:14.2: PCI INT A disabled
[19632.130131] HDA Intel 0000:00:14.2: power state changed by ACPI to D3
[19632.130171] PM: suspend of drv:HDA Intel dev:0000:00:14.2 complete after 4271.013 msecs
[19632.130193] PM: suspend of drv: dev:pci0000:00 complete after 4270.611 msecs
--
[19633.962612] ehci_hcd 0000:00:13.2: restoring config space at offset 0x1 (was 0x2b00000, writing 0x2b00013)
[19633.962693] HDA Intel 0000:00:14.2: restoring config space at offset 0xf (was 0x10a, writing 0xa)
[19633.962723] HDA Intel 0000:00:14.2: restoring config space at offset 0x1 (was 0x4100006, writing 0x4100002)
[19633.962793] pci 0000:00:14.4: restoring config space at offset 0x9 (was 0x0, writing 0xfff0)
--
[19633.962822] pci 0000:00:14.4: restoring config space at offset 0x1 (was 0x2a00000, writing 0x2a00004)
[19633.963007] HDA Intel 0000:01:05.1: restoring config space at offset 0x4 (was 0x0, writing 0xcfdec000)
[19633.963012] HDA Intel 0000:01:05.1: restoring config space at offset 0x3 (was 0x800000, writing 0x800008)
[19633.963018] HDA Intel 0000:01:05.1: restoring config space at offset 0x1 (was 0x100000, writing 0x100003)
[19633.963194] tg3 0000:03:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x8)
--
[19633.964709] radeon 0000:01:05.0: setting latency timer to 64
[19633.965119] HDA Intel 0000:00:14.2: power state changed by ACPI to D0
[19633.965195] HDA Intel 0000:00:14.2: power state changed by ACPI to D0
[19633.965422] HDA Intel 0000:00:14.2: power state changed by ACPI to D0
[19633.965461] HDA Intel 0000:00:14.2: power state changed by ACPI to D0
[19633.965469] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[19633.965508] HDA Intel 0000:01:05.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[19633.965514] HDA Intel 0000:01:05.1: setting latency timer to 64
[19633.965539] ath9k 0000:09:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
--
[20724.190067] wlan0: no IPv6 routers present
[21735.853523] hda-intel: spurious response 0x20001:0x1, last cmd=0x10270503
[21735.853534] hda-intel: spurious response 0x102:0x1, last cmd=0x10270503
[21735.853540] hda-intel: spurious response 0x700004:0x1, last cmd=0x10270503
[21735.853545] hda-intel: spurious response 0xf00000:0x1, last cmd=0x10270503
[21735.853549] hda-intel: spurious response 0x100100:0x1, last cmd=0x10270503
[21735.853554] hda-intel: spurious response 0x0:0x1, last cmd=0x10270503
[21735.853559] hda-intel: spurious response 0x400100:0x1, last cmd=0x10270503
[21735.853563] hda-intel: spurious response 0x16a10f0:0x1, last cmd=0x10270503
[21735.853568] hda-intel: spurious response 0x60:0x1, last cmd=0x10270503
[21735.853573] hda-intel: spurious response 0x10250093:0x1, last cmd=0x10270503
[21735.853577] hda-intel: spurious response 0x0:0x1, last cmd=0x10270503
[21735.853582] hda-intel: spurious response 0x0:0x1, last cmd=0x10270503
[21735.853589] hda-intel: spurious response 0x0:0x0, last cmd=0x1424011
[21735.853594] hda-intel: spurious response 0x0:0x0, last cmd=0x1424011
[21735.853598] hda-intel: spurious response 0x0:0x0, last cmd=0x1424011
[21735.853602] hda-intel: spurious response 0x0:0x0, last cmd=0x1424011
[21735.853607] hda-intel: spurious response 0x0:0x0, last cmd=0x1424011
[21735.853611] hda-intel: spurious response 0x0:0x0, last cmd=0x1424011
[21735.853615] hda-intel: spurious response 0x0:0x0, last cmd=0x1424011
[21735.853620] hda-intel: spurious response 0x0:0x0, last cmd=0x1424011
[21735.853624] hda-intel: spurious response 0x0:0x0, last cmd=0x1424011
[21735.853629] hda-intel: spurious response 0x0:0x0, last cmd=0x1424011
[21735.853633] hda-intel: spurious response 0x0:0x0, last cmd=0x1424011
[21735.853637] hda-intel: spurious response 0x0:0x0, last cmd=0x1424011
[21735.853642] hda-intel: spurious response 0x0:0x0, last cmd=0x1424011
[21735.853646] hda-intel: spurious response 0x0:0x0, last cmd=0x1424011
[21735.853651] hda-intel: spurious response 0x0:0x0, last cmd=0x1424011
[21735.853655] hda-intel: spurious response 0x0:0x0, last cmd=0x1424011
[21735.853659] hda-intel: spurious response 0x0:0x0, last cmd=0x1424011
[21735.853664] hda-intel: spurious response 0x0:0x0, last cmd=0x1424011
[21735.853668] hda-intel: spurious response 0x0:0x0, last cmd=0x1424011
[21735.853673] hda-intel: spurious response 0x0:0x0, last cmd=0x1424011
[21735.853677] hda-intel: spurious response 0x0:0x0, last cmd=0x1424011
[21735.853681] hda-intel: spurious response 0x0:0x0, last cmd=0x1424011
[21735.853686] hda-intel: spurious response 0x0:0x0, last cmd=0x1424011
[21735.853690] hda-intel: spurious response 0x0:0x0, last cmd=0x1424011
[21735.853694] hda-intel: spurious response 0x0:0x0, last cmd=0x1424011
[21735.853699] hda-intel: spurious response 0x0:0x0, last cmd=0x1424011
[21735.853703] hda-intel: spurious response 0x0:0x0, last cmd=0x1424011
[21735.853708] hda-intel: spurious response 0x0:0x0, last cmd=0x1424011
[21735.853712] hda-intel: spurious response 0x0:0x0, last cmd=0x1424011
[21735.853716] hda-intel: spurious response 0x0:0x0, last cmd=0x1424011
[21735.853721] hda-intel: spurious response 0x0:0x0, last cmd=0x1424011
[21735.853725] hda-intel: spurious response 0x0:0x0, last cmd=0x1424011
[21735.853730] hda-intel: spurious response 0x0:0x0, last cmd=0x1424011
[21735.853734] hda-intel: spurious response 0x0:0x0, last cmd=0x1424011
[21735.853738] hda-intel: spurious response 0x0:0x0, last cmd=0x1424011
[21735.853743] hda-intel: spurious response 0x0:0x0, last cmd=0x1424011
[21735.853747] hda-intel: spurious response 0x0:0x0, last cmd=0x1424011
[21735.853752] hda-intel: spurious response 0x0:0x0, last cmd=0x1424011
[21735.853756] hda-intel: spurious response 0x0:0x0, last cmd=0x1424011
[21735.853760] hda-intel: spurious response 0x0:0x0, last cmd=0x1424011
[21735.853765] hda-intel: spurious response 0x0:0x0, last cmd=0x1424011
[21735.853769] hda-intel: spurious response 0x0:0x0, last cmd=0x1424011
[21735.853774] hda-intel: spurious response 0x0:0x0, last cmd=0x1424011
[21735.853778] hda-intel: spurious response 0x0:0x0, last cmd=0x1424011
[21735.853782] hda-intel: spurious response 0x0:0x0, last cmd=0x1424011
[21735.853787] hda-intel: spurious response 0x0:0x0, last cmd=0x1424011
[21735.853791] hda-intel: spurious response 0x0:0x0, last cmd=0x1424011
[21735.853796] hda-intel: spurious response 0x0:0x0, last cmd=0x1424011
[21735.853800] hda-intel: spurious response 0x0:0x0, last cmd=0x1424011
[21735.853804] hda-intel: spurious response 0x0:0x0, last cmd=0x1424011
[21735.853809] hda-intel: spurious response 0x0:0x0, last cmd=0x1424011
[21735.853813] hda-intel: spurious response 0x0:0x0, last cmd=0x1424011
[21735.853817] hda-intel: spurious response 0x0:0x0, last cmd=0x1424011
[21735.853822] hda-intel: spurious response 0x0:0x0, last cmd=0x1424011
[21735.853826] hda-intel: spurious response 0x0:0x0, last cmd=0x1424011
[21735.853831] hda-intel: spurious response 0x0:0x0, last cmd=0x1424011
[21735.853835] hda-intel: spurious response 0x0:0x0, last cmd=0x1424011
[21735.853839] hda-intel: spurious response 0x0:0x0, last cmd=0x1424011
[21735.853844] hda-intel: spurious response 0x0:0x0, last cmd=0x1424011
[21735.853848] hda-intel: spurious response 0x0:0x0, last cmd=0x1424011
[21735.853853] hda-intel: spurious response 0x0:0x0, last cmd=0x1424011
[21735.853857] hda-intel: spurious response 0x0:0x0, last cmd=0x1424011
[21735.853861] hda-intel: spurious response 0x0:0x0, last cmd=0x1424011
[21735.853866] hda-intel: spurious response 0x0:0x0, last cmd=0x1424011
[21735.853870] hda-intel: spurious response 0x0:0x0, last cmd=0x1424011
[21735.853874] hda-intel: spurious response 0x0:0x0, last cmd=0x1424011
[21735.853879] hda-intel: spurious response 0x0:0x0, last cmd=0x1424011
[21735.853883] hda-intel: spurious response 0x0:0x0, last cmd=0x1424011
[21735.853888] hda-intel: spurious response 0x0:0x0, last cmd=0x1424011
[21735.853892] hda-intel: spurious response 0x0:0x0, last cmd=0x1424011
[21735.853896] hda-intel: spurious response 0x0:0x0, last cmd=0x1424011
[21735.853901] hda-intel: spurious response 0x0:0x0, last cmd=0x1424011
[21735.853905] hda-intel: spurious response 0x0:0x0, last cmd=0x1424011
[21735.853910] hda-intel: spurious response 0x0:0x0, last cmd=0x1424011


mv: cannot stat `/tmp/alsa-info.zPLuCreFzb/alsa-info.txt': No such file or directory
[/spoiler]

^^I really hope the spoiler works on this site..  Lol.

EDIT:  No it doesn't..  Sorry.
And you said some screen would pop up and I should download something and press Enter or whatever.  Well that never happened...  Lol.

---

### Post by cherva on 2010-12-27
To get all the info we can add the output to a file .. try:
```
wget -O alsa-info.sh http://alsa-project.org/alsa-info.sh && bash ./alsa-info.sh --with-configs --with-devices --no-upload --stdout ~/Desktop/alsa_into_output
``` This will create a text file named alsa_info_output on your desktop. Paste the text here ...

---

### Post by woodpush on 2010-12-27
This worked for me

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

Its not hard to follow. The command to edit the text file is
sudo nano /etc/modprobe.d/alsa-base.

---

### Post by promal_cotton on 2010-12-27
> **woodpush said:**
> This worked for me

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

Its not hard to follow. The command to edit the text file is
sudo nano /etc/modprobe.d/alsa-base.

Hmm..  The file doesn't have my sound card in it... :|

---

### Post by idi0tf0wl on 2010-12-27
What channels do you see when you run ```
alsamixer
``` in the terminal? Any muted channels? ('mm' underneath the "fader"). If so, use your arrow keys to highlight that channel and press M to unmute it, then esc to exit and log out and back in. If this is indeed the case, fixing your issue will be deathly simple.

Cheers!

---

### Post by sandyd on 2010-12-27
just missing your audio chipset post output of
```

aplay -l
```

---

### Post by promal_cotton on 2010-12-27
> **idi0tf0wl said:**
> What channels do you see when you run ```
alsamixer
``` in the terminal? Any muted channels? ('mm' underneath the "fader"). If so, use your arrow keys to highlight that channel and press M to unmute it, then esc to exit and log out and back in. If this is indeed the case, fixing your issue will be deathly simple.

Cheers!

I don't see any 'mm' under anything.  Everything looked fine..  I think..  Lol.

> **sandyd said:**
> just missing your audio chipset post output of
```

aplay -l
```

^^I honestly have no idea what you're talking about...  Lol.  I JUST got Ubuntu like 3 days ago now.  I only heard about it like one other time and that was quite a long time ago...



And no multi-quote? :'(

---

### Post by audiomick on 2010-12-27
> **promal_cotton said:**
> I don't see any 'mm' under anything.  Everything looked fine..  I think..  Lol.



^^I honestly have no idea what you're talking about...  Lol.  I JUST got Ubuntu like 3 days ago now.  I only heard about it like one other time and that was quite a long time ago...



And no multi-quote? :'(
Both of these are suggesting you run a command in the terminal and post the output here, or report what the output was.

You can open a terminal in
Applications> accessories> terminal

I think it is accessories. My system speaks German... ;)

When you have a terminal open, type (or copy and paste) the command in and press enter.

In the terminal, you need to do shift + ctrl + c to copy, shift + ctrl + v to paste.

if the command produces a lot of output which you want to post here, use the "code" button. It is the one that looks like this: #


Multiple quote is the button to the right of quote.

---

### Post by promal_cotton on 2010-12-27
> **audiomick said:**
> Both of these are suggesting you run a command in the terminal and post the output here, or report what the output was.

You can open a terminal in
Applications> accessories> terminal

I think it is accessories. My system speaks German... ;)

When you have a terminal open, type (or copy and paste) the command in and press enter.

In the terminal, you need to do shift + ctrl + c to copy, shift + ctrl + v to paste.

if the command produces a lot of output which you want to post here, use the "code" button. It is the one that looks like this: #


Multiple quote is the button to the right of quote.

Well my damn sir.  That helps a lot.  Haha.
Thanks.

EDIT:

> **sandyd said:**
> just missing your audio chipset post output of
```

aplay -l
```


```
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Headset [Logitech USB Headset], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

---

### Post by sandyd on 2010-12-28
> **promal_cotton said:**
> Well my damn sir.  That helps a lot.  Haha.
Thanks.

EDIT:




```
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Headset [Logitech USB Headset], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

You need to add the stack for your codec.
check out [http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)

---

### Post by sandyd on 2010-12-28
> **promal_cotton said:**
> So I actually just got 10.10.  First time using Ubuntu.  I love it.. <3  I just can't seem to get the sound out of my headphone jack to work...  I have a USB headset that works just fine, but I have speakers that I want to use and they aren't USB...  I'm using a Laptop.  Gateway NV52.  64 bit system.  I tried looking for this else where but it only gave me ways to edit the file thats it /etc blah blah and I can't edit that file so yeah... :|  And if you can..  I don't know how to.  I can try and provide any information you guys need to help me fix this problem.  But like I said...  First time with Ubuntu.  Just got it 2 days ago even...

and you might as well do this too, or youll scream when you want sound over HDMI.

[http://crunchbanglinux.org/forums/topic/2310/hdmi-ati-hda-sound-how-i-got-hdmi-sound-working-in/](http://crunchbanglinux.org/forums/topic/2310/hdmi-ati-hda-sound-how-i-got-hdmi-sound-working-in/)

---

### Post by promal_cotton on 2010-12-29
Alright.  I'll give those a try right now.  Thanks guys. :)

---


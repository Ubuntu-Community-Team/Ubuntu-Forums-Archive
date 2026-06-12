---
title: "wireless usb connection"
date: 2014-08-23
forum: Networking &amp; Wireless
---

### Post by bill_2 on 2014-08-23
I just installed "ubuntu-14.04.1-desktop-amd64" and it does not recognize my BELKIN N450 DB/N60 DUAL BAND WI-FI USB ADAPTER. 
I tried to install drivers from the disk but they are only for Windows. I have Windows VISTA HOME sharing the computer and the USB adapter works fine when logged into Windows. 

Any help finding the correct drivers would be greatly appreciated. 

Thanks
Bill

---

### Post by praseodym on 2014-08-24
Please open a terminal and show the outputs of these commands:
```

lsusb
lsmod
iwconfig
rfkill list
cat /etc/resolv.conf
```
Does LAN work?

---

### Post by bill_2 on 2014-08-25
below are the outputs for the codes you listed. 

This is a desktop computer. I am trying to run ubunu side by side with Windows Vista Home Premium, which connects via cable modem using the 
[COLOR=#000000]BELKIN N450 DB/N60 DUAL BAND WI-FI USB ADAPTER. 

I did get connection in Ubunu via tethering with my cell phone and USB cable it came with. 

Thanks for the quick response

Bill


[/COLOR]bill@Bill-B:~$ lsusb
Bus 001 Device 006: ID 0bda:0111 Realtek Semiconductor Corp. RTS5111 Card Reader Controller
Bus 001 Device 005: ID 050d:110a Belkin Components
Bus 001 Device 004: ID 04e8:6860 Samsung Electronics Co., Ltd GT-I9100 Phone [Galaxy S II], GT-I9300 Phone [Galaxy S III], GT-P7500 [Galaxy Tab 10.1]
Bus 001 Device 003: ID 14cd:6600 Super Top USB 2.0 IDE DEVICE
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 045e:0745 Microsoft Corp. Nano Transceiver v1.0 for Bluetooth
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
bill@Bill-B:~$


______________________________________________________________________________________________________________________________________________
 
bill@Bill-B:~$ lsmod
Module                  Size  Used by
bnep                   19624  2
rfcomm                 69160  0
bluetooth             391196  10 bnep,rfcomm
cx18_alsa              13730  1
mxl5005s               54281  1
s5h1409                18550  1
tuner_simple           22368  1
tuner_types            24636  1 tuner_simple
cs5345                 13014  1
tda9887                13906  1
tda8290                22428  0
tuner                  27308  2
joydev                 17381  0
snd_hda_codec_realtek    61438  1
coretemp               13435  0
serio_raw              13462  0
cx18                  131667  1 cx18_alsa
videobuf_vmalloc       13589  1 cx18
tveeprom               21216  1 cx18
cx2341x                28230  1 cx18
snd_hda_intel          52355  3
snd_hda_codec         192906  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102099  3 cx18_alsa,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
dvb_core              121659  1 cx18
snd_seq_midi           13324  0
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30144  1 snd_seq_midi
v4l2_common            15681  4 cx18,cx2341x,tuner,cs5345
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
lpc_ich                21080  0
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29482  2 snd_pcm,snd_seq
videobuf_core          26023  2 cx18,videobuf_vmalloc
videodev              134688  5 cx18,cx2341x,tuner,cs5345,v4l2_common
snd                    69238  19 snd_hda_codec_realtek,cx18_alsa,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
i915                  783805  3
mac_hid                13205  0
video                  19476  1 i915
drm_kms_helper         53081  1 i915
drm                   303102  4 i915,drm_kms_helper
i2c_algo_bit           13413  2 cx18,i915
soundcore              12680  1 snd
parport_pc             32701  0
ppdev                  17671  0
lp                     17759  0
parport                42348  3 lp,ppdev,parport_pc
hid_generic            12548  0
usbhid                 52570  0
hid                   106148  2 hid_generic,usbhid
usb_storage            62209  3
psmouse               106678  0
firewire_ohci          40409  0
firewire_core          68769  1 firewire_ohci
e100                   40819  0
mii                    13934  1 e100
crc_itu_t              12707  1 firewire_core
ahci                   25819  1
libahci                32560  1 ahci
bill@Bill-B:~$
 
 
 
 ________________________________________________________________________________________
 
 
 
bill@Bill-B:~$ iwconfig
eth0      no wireless extensions.
 
lo        no wireless extensions.
 
__________________________________________________________________________________________ 
 
bill@Bill-B:~$ rfkill list
bill@Bill-B:~$
 
 ___________________________________________________________________________________________
 
bill@Bill-B:~$ cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
bill@Bill-B:~$

---

### Post by varunendra on 2014-08-25
[s]The required driver for this adapter should have been included in 14.04.1.[/s]
EDIT: Evidently, I am wrong about above, the required driver doesn't exist in kernel versions upto 3.15 (haven't compiled 3.16, so can't say about that).

So it seems you have to compile the driver from github, as described in this post : [http://ubuntuforums.org/showpost.php?p=12799964](http://ubuntuforums.org/showpost.php?p=12799964)

If it fails to compile, please post back the entire output of the terminal to let us see the error. If everything goes fine, you should have a working wifi.

---

### Post by Malcolm_Gaissert on 2014-08-25
Had the same problem. Win 8.1 worked with the USB adapter. But would not work with the Ubuntu distro 13.10. Then it finally dawned on me. The problem was that Ubuntu was actually blocking the original WiFi device that was still in the laptop and therefore not allowing the USB device to function.

What to do? I turned off the computer turned it over, found the door that the internal wifi device was behind and carefully removed it. Remove the screws first then when the device lifts up gently remove the antenna wires. If at some time you wish to replace the device with a new one make note of where the wires were attached.

Powered up the laptop and I have had WiFi since the moment I filled in the correct info. (I have a D-Link DWA140 attached to its short USB cord.)

Good luck

---


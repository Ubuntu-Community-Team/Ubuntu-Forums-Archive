---
title: "Help new wifi not working"
date: 2016-12-26
forum: Networking &amp; Wireless
---

### Post by jack2723 on 2016-12-26
I have an Archer T1U that I just purchased and it is showing in the network manager but it is not actually downloading anything, for me. I got this new device because my old device, an Arlink 101 ceased working after a recent update. I am running 14.04, 32 bit. Attached is that text file that another thread told me to run that maybe shows the trained eye what is wrong here (I think that I successfully attached that file, but I don't see any way to verify that I succeeded, so please let me know if I did not succeed). Thanks for any help.

---

### Post by wildmanne39 on 2016-12-26
Please post the output of:
```
modinfo rt73usb
```
using code tags.
Thanks

---

### Post by jack2723 on 2016-12-26
```

filename:       /lib/modules/3.13.0-106-generic/kernel/drivers/net/wireless/rt2x00/rt73usb.ko
license:        GPL
firmware:       rt73.bin
description:    Ralink RT73 USB Wireless LAN driver.
version:        2.3.0
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
srcversion:     66CCBB24DCA72AAD23E9588
alias:          usb:v0586p3415d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CDEp001Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v7167p3840d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019pAB50d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019pAB01d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0471p200Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v6933p5001d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0769p31F3d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p9712d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p90ACd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p002Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0027d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0024d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1740p7100d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04E8p4471d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v18E8p6238d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v18E8p6229d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v18E8p6196d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0812p3101d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp2671d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp2573d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04BBp093Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B75p7318d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DB0pA874d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DB0pA861d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DB0p6874d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DB0p6877d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DB0p4600d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13B1p0028d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13B1p0023d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13B1p0020d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v06F8pE020d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v06F8pE010d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v06F8pE002d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1472p0009d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1044p800Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1044p8008d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v15A9p0004d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1740p3701d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v7392p7618d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v7392p7318d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07D1p3C07d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07D1p3C06d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07D1p3C04d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07D1p3C03d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07AAp002Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v14B2p3C22d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1371p9032d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1371p9022d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v178Dp02BEd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0411p0137d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0411p0119d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0411p0116d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0411p00F4d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0411p00E6d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0411p00D9d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0411p00D8d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v08DDp0120d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1631pC019d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp905Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp905Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp705Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp7050d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B05p1724d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B05p1723d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1690p0722d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v18C5p0002d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0EB0p9021d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp9021d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v14B2p3C10d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07B8pB21Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07B8pB21Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07B8pB21Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07B8pB21Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07B8pB21Bd*dc*dsc*dp*ic*isc*ip*in*
depends:        rt2x00lib,rt2x00usb,crc-itu-t
intree:         Y
vermagic:       3.13.0-106-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        35:8F:00:51:4A:EE:9D:E6:96:BC:B1:FE:CF:E9:98:39:A5:C6:78:20
sig_hashalgo:   sha512
parm:           nohwcrypt:Disable hardware encryption. (bool)

```

---

### Post by wildmanne39 on 2016-12-26
I was almost positive that the driver loaded does not drive your device, from what I have seen no one has that device working but we will give it a shot.

Did you compile a driver for the new device because you say it shows in network manager if so will you please post a link to it.

Please do:
```
modinfo  mt7610u
lsmod
```
post the output using code tags.

I did not look close enough the first time to see that you were running 14.04 the newer version will be more likely to work with this device.

---

### Post by jack2723 on 2016-12-26
I did some stuff, sorry to say.  I think what I did is on this page [http://askubuntu.com/questions/791780/need-tp-link-archer-t1u-driver-for-ubuntu-16-04/819231#819231](http://askubuntu.com/questions/791780/need-tp-link-archer-t1u-driver-for-ubuntu-16-04/819231#819231).  And, that code was 
sudo add-apt-repository ppa:hanipouspilot/rtlwifi
sudo apt update
sudo apt install mt7610u-dkms

Before I did that (I think that's the code I used), I could not even see the T1U. I was trying some stuff over the last few days. Hope I didn't make things worse.

---

### Post by wildmanne39 on 2016-12-26
Please do:
```
echo "blacklist rt73usb" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
your signal strength is 30, anything below 50 and ubuntu will not connect or it will be very slow. How far from the router are you?  Is there walls or floors between the router and the computer?

Please provide the output of the two commands in my previous post.

---

### Post by jack2723 on 2016-12-26
Here's what I get:  blacklist rt73usb
Before, when I go that other code, my wifi may not have been on.  I use my smart phone as a hot spot.  It was on and connected to the T1U for this last bit of code, if that matters.  Should I run that earlier code, again, for you?  Thanks so much for your time and advice.

---

### Post by wildmanne39 on 2016-12-26
Please post the out put from the wireless script and the following commands:
```
modinfo  mt7610u
lsmod
```
Thanks

---

### Post by jack2723 on 2016-12-26
modinfo  mt7610u
```
modinfo: ERROR: Module mt7610u not found.
lsmod
Module                  Size  Used by
mt7610u_sta           835092  0 
pci_stub               12550  1 
vboxpci                22896  0 
vboxnetadp             25636  0 
vboxnetflt             27291  0 
vboxdrv               300383  3 vboxnetadp,vboxnetflt,vboxpci
bnep                   18895  2 
rfcomm                 53664  0 
bluetooth             342208  10 bnep,rfcomm
arc4                   12536  0 
rt73usb                26890  0 
rt2x00usb              20041  1 rt73usb
rt2x00lib              48886  2 rt73usb,rt2x00usb
mac80211              554291  2 rt2x00lib,rt2x00usb
cfg80211              417586  3 mac80211,rt2x00lib,mt7610u_sta
gpio_ich               13229  0 
crc_itu_t              12627  1 rt73usb
snd_hda_codec_via      23156  1 
snd_hda_intel          42858  3 
snd_hda_codec         168250  2 snd_hda_codec_via,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
i915                  710018  4 
snd_pcm                85501  2 snd_hda_codec,snd_hda_intel
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
coretemp               13195  0 
snd_rawmidi            25543  1 snd_seq_midi
video                  18903  1 i915
snd_seq                55431  2 snd_seq_midi_event,snd_seq_midi
kvm_intel             132651  0 
drm_kms_helper         48868  1 i915
kvm                   388316  1 kvm_intel
drm                   244037  5 i915,drm_kms_helper
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              28569  2 snd_pcm,snd_seq
i2c_algo_bit           13197  1 i915
snd                    60939  16 snd_hwdep,snd_timer,snd_hda_codec_via,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
soundcore              12600  1 snd
serio_raw              13230  0 
shpchp                 32128  0 
lpc_ich                16864  0 
parport_pc             31981  0 
ppdev                  17391  0 
asus_atk0110           18201  0 
mac_hid                13037  0 
lp                     13299  0 
parport                40836  3 lp,ppdev,parport_pc
psmouse                95439  0 
pata_acpi              12886  0 
r8169                  61562  0 
mii                    13654  1 r8169
```

---

### Post by wildmanne39 on 2016-12-26
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

I am going to take a break until morning, maybe someone else will step in.

---

### Post by wildmanne39 on 2016-12-27
Please post the content of /etc/modprobe.d/blacklist.conf by doing:
```
cat /etc/modprobe.d/blacklist.conf
```
using code tags.
Thanks

---

### Post by jack2723 on 2016-12-27
```
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
blacklist rt73usb


```

See next post to see results with wifi being on.

With wifi on:
```
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
blacklist rt73usb
jack@jack-System-Product-Name:~$ cat /etc/modprobe.d/blacklist.conf
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
blacklist rt73usb
jack@jack-System-Product-Name:~$ cat /etc/modprobe.d/blacklist.conf
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
blacklist rt73usb
jack@jack-System-Product-Name:~$ clear

jack@jack-System-Product-Name:~$ cat /etc/modprobe.d/blacklist.conf
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
blacklist rt73usb
jack@jack-System-Product-Name:~$ clear

jack@jack-System-Product-Name:~$ cat /etc/modprobe.d/blacklist.conf
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
blacklist rt73usb
```

---

### Post by wildmanne39 on 2016-12-27
Please post the output of:
```
modinfo mt7610u_sta
```
Strange but the  rt73usb module is still loading even though it is blacklisted, Let's try blacklisting the other modules that go with the rt73usb, after you have posted the results of the command above so we make sure the driver you are using do not need any of the other modules that are loaded.

---

### Post by jack2723 on 2016-12-27
```
filename:       /lib/modules/3.13.0-106-generic/updates/dkms/mt7610u_sta.ko
version:        3.0.0.2
license:        GPL
description:    RT2870 Wireless Lan Linux Driver
author:         Paul Lin <paul_lin@ralinktech.com>
license:        GPL
srcversion:     75BC5DA09129BFDB11A12A5
alias:          usb:v0E8Dp7650d*dc*dsc*dp*icFFisc02ipFFin*
alias:          usb:v0E8Dp7630d*dc*dsc*dp*icFFisc02ipFFin*
alias:          usb:v20F4p806Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019pAB31d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v293Cp5702d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v057Cp8502d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04BBp0951d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07B8p7610d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0586p3425d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3D02d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0075d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B05p17DBd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B05p17D1d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2357p0105d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp760Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp761Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v7392pB711d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v7392pA711d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13B1p003Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0E8Dp7610d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp7610d*dc*dsc*dp*ic*isc*ip*in*
depends:        cfg80211
vermagic:       3.13.0-106-generic SMP mod_unload modversions 686 
parm:           mac:wireless mac addr (charp)
parm:           debug:log verbosity level (0: off, 1: error only [default], 2: warnings, 3: trace, 4: info, 5: loud) (long)


```

---

### Post by wildmanne39 on 2016-12-27
Let's blacklist the other uneeded modules.
```
echo "blacklist rt2x00usb" | sudo tee -a /etc/modprobe.d/blacklist.conf
echo "blacklist rt2x00lib" | sudo tee -a /etc/modprobe.d/blacklist.conf
echo "blacklist mac80211" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Reboot then run and post the wireless script please.

---

### Post by jack2723 on 2016-12-27
OK, I echo'd those commands. I rebooted. And, now, I have to ask you what exactly is the "wireless script" that I need to run?

---

### Post by wildmanne39 on 2016-12-27
Hi, please click on the wireless script in my signature, follow the directions for running it and posting the results back here using code tags.

---

### Post by jack2723 on 2016-12-27
```

########## wireless info START ##########

Report from: 27 Dec 2016 19:58 PST -0800

Booted last: 27 Dec 2016 19:35 PST -0800

Script from: 08 Jul 2016 02:16 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.5 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.13.0-106-generic #153-Ubuntu SMP Tue Dec 6 15:45:13 UTC 2016 i686 i686 i686 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 03)
    Subsystem: ASUSTeK Computer Inc. M4A785TD Motherboard [1043:83a3]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 001 Device 002: ID 2357:0105  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

cfg80211              417586  1 mt7610u_sta

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF1]>  
          inet addr:192.168.1.64  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'eth0' [IF1]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5756 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6373 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3219608 (3.2 MB)  TX bytes:892588 (892.5 KB)

ra0       Link encap:Ethernet  HWaddr <MAC 'ra0' [IF2]>  
          inet6 addr: fe80::<IP6 'ra0' [IF2]>/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:416 errors:0 dropped:0 overruns:0 frame:0
          TX packets:207 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:70909 (70.9 KB)  TX bytes:31257 (31.2 KB)

##### iwconfig ##########################

lo        no wireless extensions.

eth0      no wireless extensions.

ra0       Ralink STA  ESSID:"11n-AP"  Nickname:"MT7610U_STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1
search gateway.pace.com

##### network managers ##################

Installed:

    NetworkManager

Running:

root       923     1  0 19:35 ?        00:00:01 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: ra0 ------------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            usb
  State:             disconnected
  Default:           no
  HW Address:        <MAC 'ra0' [IF2]>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF1]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.64
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254

    DNS:             192.168.1.254

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

no-auto-default=<MAC 'eth0' [IF1]>,

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/Network Not Found]] (600 root)
[connection] id=Network Not Found | type=802-11-wireless
[802-11-wireless] ssid=Network Not Found | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/lily's pad]] (600 root)
[connection] id=lily's pad | type=802-11-wireless
[802-11-wireless] ssid=lily's pad | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Tribute_1622]] (600 root)
[connection] id=Tribute_1622 | type=802-11-wireless
[802-11-wireless] ssid=Tribute_1622 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/PACE304]] (600 root)
[connection] id=PACE304 | type=802-11-wireless
[802-11-wireless] ssid=PACE304 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Wi-Fi connection 1]] (600 root)
[connection] id=Disneyland | type=802-11-wireless | permissions=user:jack:; | autoconnect=false
[802-11-wireless] ssid=PACE304 | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/9P72L]] (600 root)
[connection] id=9P72L | type=802-11-wireless
[802-11-wireless] ssid=9P72L | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/FiOS-IQDBR]] (600 root)
[connection] id=FiOS-IQDBR | type=802-11-wireless
[802-11-wireless] ssid=FiOS-IQDBR | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/gil]] (600 root)
[connection] id=gil | type=802-11-wireless
[802-11-wireless] ssid=gil | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/beachhouse]] (600 root)
[connection] id=beachhouse | type=802-11-wireless
[802-11-wireless] ssid=beachhouse | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/2.4 Number 3]] (600 root)
[connection] id=2.4 Number 3 | type=802-11-wireless
[802-11-wireless] ssid=2.4 Number 3 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/2WIRE978]] (600 root)
[connection] id=2WIRE978 | type=802-11-wireless
[802-11-wireless] ssid=2WIRE978 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Tribute_1622 1]] (600 root)
[connection] id=Tribute_1622 1 | type=802-11-wireless
[802-11-wireless] ssid=Tribute_1622
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: America/Los_Angeles (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

lo        no frequency information.

eth0      no frequency information.

ra0       27 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 14 : 2.484 GHz
          Channel 36 : 5.18 GHz
          Channel 38 : 5.19 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 46 : 5.23 GHz
          Channel 48 : 5.24 GHz
          Channel 149 : 5.745 GHz
          Channel 151 : 2.412 GHz
          Channel 153 : 5.765 GHz
          Channel 157 : 5.785 GHz
          Channel 159 : 2.412 GHz
          Channel 161 : 5.805 GHz
          Channel 165 : 5.825 GHz
          Current Frequency=2.412 GHz (Channel 1)

##### iwlist scan #######################

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

Channel occupancy:

      2   APs on   Frequency:5.745 GHz (Channel 149)

ra0       Scan completed :
          Cell 01 - Address: <MAC '5.0 Number 3' [AC1]>
                    Protocol:802.11a/n
                    ESSID:"5.0 Number 3"
                    Mode:Managed
                    Frequency:5.745 GHz (Channel 149)
                    Quality=34/100  Signal level=-76 dBm  Noise level=-85 dBm
                    Encryption key:on
                    Bit Rates:120 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'Reeser5-5G' [AC2]>
                    Protocol:802.11a/n
                    ESSID:"Reeser5-5G"
                    Mode:Managed
                    Frequency:5.745 GHz (Channel 149)
                    Quality=34/100  Signal level=-76 dBm  Noise level=-71 dBm
                    Encryption key:on
                    Bit Rates:120 Mb/s
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[cfg80211]
filename:       /lib/modules/3.13.0-106-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     0055529745EF9A8A3E57FC3
depends:        
intree:         Y
vermagic:       3.13.0-106-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        35:8F:00:51:4A:EE:9D:E6:96:BC:B1:FE:CF:E9:98:39:A5:C6:78:20
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

lp

##### modprobe options ##################

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac
blacklist rt73usb
blacklist rt2x00usb
blacklist rt2x00usb
blacklist rt2x00lib
blacklist mac80211

[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.1/0000:01:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF1]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# USB device 0x:0x (rt73usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[  203.304798] r8169 0000:02:00.0 eth0: link up

########## wireless info END ############


```

---

### Post by wildmanne39 on 2016-12-27
Your signal strength and link quality is is 10 that is very low. Your wifi connection is on 1 but the AP's are on 149.

I recommend setting them both to 1 then remove all connections in network manager, run the following command.
```
sudo rm /etc/udev/rules.d/70-persistent-net.rules
```
Reboot and let network manger find your connection.

---

### Post by wildmanne39 on 2016-12-27
After the connections are found unplug your wired connection and let the wireless try to connect.

---

### Post by jack2723 on 2016-12-28
My phone, which is my wifi hotspot is showing my computer address and my computer is showing the connection name.  So, they can see each other. But, nothing is downloading. What about that?

---

### Post by wildmanne39 on 2016-12-28
What is your computer network name? did you make the changes and reboot, with the exception of the AP's? you have to have your wired connection unplugged for your wifi to connect. Run the wireless script again since you made the changes by running the following command:
```
./wireless-info
```
and post the results here.

---

### Post by jack2723 on 2016-12-28
I'm sorry, I can't figure out what you mean by "AP." (It's probably too obvious, [laugh])  Yes, my wifi will not connect unless I disconnect my LAN. When I do disconect my LAN, my wifi does communicate with my computer, but won't download. The name of my wifi connection is: Tribute_1622  And, here is what I get when I run that "./wireless-infp" code.
```

########## wireless info START ##########

Report from: 28 Dec 2016 10:14 PST -0800

Booted last: 28 Dec 2016 09:33 PST -0800

Script from: 08 Jul 2016 02:16 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.5 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.13.0-106-generic #153-Ubuntu SMP Tue Dec 6 15:45:13 UTC 2016 i686 i686 i686 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 03)
    Subsystem: ASUSTeK Computer Inc. M4A785TD Motherboard [1043:83a3]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 001 Device 006: ID 2357:0105  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

1: phy1: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

cfg80211              417586  1 mt7610u_sta

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF1]>  
          inet addr:192.168.1.64  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'eth0' [IF1]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9304 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10144 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6197250 (6.1 MB)  TX bytes:1621919 (1.6 MB)

ra0       Link encap:Ethernet  HWaddr <MAC 'ra0' [IF2]>  
          inet6 addr: fe80::<IP6 'ra0' [IF2]>/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:12213 errors:0 dropped:0 overruns:0 frame:0
          TX packets:567 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3199622 (3.1 MB)  TX bytes:53172 (53.1 KB)

##### iwconfig ##########################

lo        no wireless extensions.

eth0      no wireless extensions.

ra0       Ralink STA  ESSID:"11n-AP"  Nickname:"MT7610U_STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1
search gateway.pace.com

##### network managers ##################

Installed:

    NetworkManager

Running:

root       927     1  0 09:33 ?        00:00:01 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: ra0 ------------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            usb
  State:             disconnected
  Default:           no
  HW Address:        <MAC 'ra0' [IF2]>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    Reeser5-5G:      Infra, <MAC 'Reeser5-5G' [AC1]>, Freq 5180 MHz, Rate 54 Mb/s, Strength 0 WPA2
    5.0 Number 3:    Infra, <MAC '5.0 Number 3' [AC2]>, Freq 5745 MHz, Rate 54 Mb/s, Strength 0 WPA WPA2
    Gil's Testing 5ghz: Infra, <MAC 'Gil's Testing 5ghz' [AC3]>, Freq 5240 MHz, Rate 54 Mb/s, Strength 0 WPA WPA2

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF1]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.64
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254

    DNS:             192.168.1.254

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

no-auto-default=<MAC 'eth0' [IF1]>,

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/Network Not Found]] (600 root)
[connection] id=Network Not Found | type=802-11-wireless
[802-11-wireless] ssid=Network Not Found | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/lily's pad]] (600 root)
[connection] id=lily's pad | type=802-11-wireless
[802-11-wireless] ssid=lily's pad | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Tribute_1622]] (600 root)
[connection] id=Tribute_1622 | type=802-11-wireless
[802-11-wireless] ssid=Tribute_1622 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/PACE304]] (600 root)
[connection] id=PACE304 | type=802-11-wireless
[802-11-wireless] ssid=PACE304 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Wi-Fi connection 1]] (600 root)
[connection] id=Disneyland | type=802-11-wireless | permissions=user:jack:; | autoconnect=false
[802-11-wireless] ssid=PACE304 | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/9P72L]] (600 root)
[connection] id=9P72L | type=802-11-wireless
[802-11-wireless] ssid=9P72L | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/FiOS-IQDBR]] (600 root)
[connection] id=FiOS-IQDBR | type=802-11-wireless
[802-11-wireless] ssid=FiOS-IQDBR | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/gil]] (600 root)
[connection] id=gil | type=802-11-wireless
[802-11-wireless] ssid=gil | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/beachhouse]] (600 root)
[connection] id=beachhouse | type=802-11-wireless
[802-11-wireless] ssid=beachhouse | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/2.4 Number 3]] (600 root)
[connection] id=2.4 Number 3 | type=802-11-wireless
[802-11-wireless] ssid=2.4 Number 3 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/2WIRE978]] (600 root)
[connection] id=2WIRE978 | type=802-11-wireless
[802-11-wireless] ssid=2WIRE978 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Tribute_1622 1]] (600 root)
[connection] id=Tribute_1622 1 | type=802-11-wireless
[802-11-wireless] ssid=Tribute_1622
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: America/Los_Angeles (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

lo        no frequency information.

eth0      no frequency information.

ra0       27 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 14 : 2.484 GHz
          Channel 36 : 5.18 GHz
          Channel 38 : 5.19 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 46 : 5.23 GHz
          Channel 48 : 5.24 GHz
          Channel 149 : 5.745 GHz
          Channel 151 : 2.412 GHz
          Channel 153 : 5.765 GHz
          Channel 157 : 5.785 GHz
          Channel 159 : 2.412 GHz
          Channel 161 : 5.805 GHz
          Channel 165 : 5.825 GHz
          Current Frequency=2.412 GHz (Channel 1)

##### iwlist scan #######################

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:5.18 GHz (Channel 36)
      1   APs on   Frequency:5.24 GHz (Channel 48)
      1   APs on   Frequency:5.745 GHz (Channel 149)

ra0       Scan completed :
          Cell 01 - Address: <MAC 'Reeser5-5G' [AC1]>
                    Protocol:802.11a/n
                    ESSID:"Reeser5-5G"
                    Mode:Managed
                    Frequency:5.18 GHz (Channel 36)
                    Quality=13/100  Signal level=-85 dBm  Noise level=-87 dBm
                    Encryption key:on
                    Bit Rates:120 Mb/s
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC '5.0 Number 3' [AC2]>
                    Protocol:802.11a/n
                    ESSID:"5.0 Number 3"
                    Mode:Managed
                    Frequency:5.745 GHz (Channel 149)
                    Quality=39/100  Signal level=-74 dBm  Noise level=-83 dBm
                    Encryption key:on
                    Bit Rates:120 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'Gil's Testing 5ghz' [AC3]>
                    Protocol:802.11a/n
                    ESSID:"Gil's Testing 5ghz"
                    Mode:Managed
                    Frequency:5.24 GHz (Channel 48)
                    Quality=0/100  Signal level=-91 dBm  Noise level=-86 dBm
                    Encryption key:on
                    Bit Rates:120 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

##### module infos ######################

[cfg80211]
filename:       /lib/modules/3.13.0-106-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     0055529745EF9A8A3E57FC3
depends:        
intree:         Y
vermagic:       3.13.0-106-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        35:8F:00:51:4A:EE:9D:E6:96:BC:B1:FE:CF:E9:98:39:A5:C6:78:20
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

lp

##### modprobe options ##################

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac
blacklist rt73usb
blacklist rt2x00usb
blacklist rt2x00usb
blacklist rt2x00lib
blacklist mac80211

[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF1]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

##### dmesg #############################

########## wireless info END ############


```

---

### Post by wildmanne39 on 2016-12-28
This is the AP's that I am talking about. 
> Channel occupancy:

      1   APs on   Frequency:5.18 GHz (Channel 36)
      1   APs on   Frequency:5.24 GHz (Channel 48)
      1   APs on   Frequency:5.745 GHz (Channel 149)


Your network is not even listed how far away are you from it? 

This is an Asus computer correct? If it is it probably has two antennas and with a newer driver by using a driver parameter the one being used can be switched to the other antenna which is almost always needed. 

I really recommend upgrading to 16.10 and installing the newest driver that is out instead of missing with an old version since your the driver is just now starting to get better.

---

### Post by jack2723 on 2016-12-28
OK, I'm learning a lot, now. My ASUS mobo has its own LAN? I checked. Yes, it does. OK. Thanks for that Info.
So, install 16.10, 64 bit, and use that LAN. That should show up in the "software update" place like normal, then.  And, I can just tick a box.  I'm going to try that.  Thanks so much for your help! 
BTW, here' that output again, and this time I made sure to generate the file with my computer in definite touch with my wifi. This is just for your Info., if you desire to see it. The wifi is showing.
```

########## wireless info START ##########

Report from: 28 Dec 2016 16:35 PST -0800

Booted last: 28 Dec 2016 16:31 PST -0800

Script from: 08 Jul 2016 02:16 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.5 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.13.0-106-generic #153-Ubuntu SMP Tue Dec 6 15:45:13 UTC 2016 i686 i686 i686 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 03)
    Subsystem: ASUSTeK Computer Inc. M4A785TD Motherboard [1043:83a3]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 001 Device 002: ID 2357:0105  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

cfg80211              417586  1 mt7610u_sta

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF1]>  
          inet6 addr: fe80::<IP6 'eth0' [IF1]>/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:769 errors:0 dropped:0 overruns:0 frame:0
          TX packets:912 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:366687 (366.6 KB)  TX bytes:103297 (103.2 KB)

ra0       Link encap:Ethernet  HWaddr <MAC 'ra0' [IF2]>  
          inet addr:192.168.43.95  Bcast:192.168.43.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'ra0' [IF2]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2594 errors:0 dropped:0 overruns:0 frame:0
          TX packets:416 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:650325 (650.3 KB)  TX bytes:51647 (51.6 KB)

##### iwconfig ##########################

lo        no wireless extensions.

eth0      no wireless extensions.

ra0       Ralink STA  ESSID:"Tribute_1622"  Nickname:"MT7610U_STA"
          Mode:Managed  Frequency=2.412 GHz  Access Point: <MAC 'Tribute_1622' [AC5]>   
          Bit Rate=13 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=80/100  Signal level:-81 dBm  Noise level:-81 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.43.1    0.0.0.0         UG    0      0        0 ra0
192.168.43.0    0.0.0.0         255.255.255.0   U     9      0        0 ra0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       922     1  0 16:31 ?        00:00:00 NetworkManager
root      2886   922  0 16:35 ?        00:00:00 sh -c /sbin/resolvconf -a NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: ra0  [Tribute_1622 1] ------------------------------------------------
  Type:              802.11 WiFi
  Driver:            usb
  State:             connected
  Default:           yes
  HW Address:        <MAC 'ra0' [IF2]>

  Capabilities:
    Speed:           13 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    Reeser5-5G:      Infra, <MAC 'Reeser5-5G' [AC1]>, Freq 5180 MHz, Rate 54 Mb/s, Strength 0 WPA2
    Gil's Testing 5ghz: Infra, <MAC 'Gil's Testing 5ghz' [AC4]>, Freq 5240 MHz, Rate 54 Mb/s, Strength 0 WPA WPA2
    5.0 Number 3:    Infra, <MAC '5.0 Number 3' [AC3]>, Freq 5745 MHz, Rate 54 Mb/s, Strength 0 WPA WPA2
    *Tribute_1622:   Infra, <MAC 'Tribute_1622' [AC5]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 30 WPA2

  IPv4 Settings:
    Address:         192.168.43.95
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.43.1

    DNS:             192.168.43.1

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth0' [IF1]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         off

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

no-auto-default=<MAC 'eth0' [IF1]>,

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/Network Not Found]] (600 root)
[connection] id=Network Not Found | type=802-11-wireless
[802-11-wireless] ssid=Network Not Found | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/lily's pad]] (600 root)
[connection] id=lily's pad | type=802-11-wireless
[802-11-wireless] ssid=lily's pad | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Tribute_1622]] (600 root)
[connection] id=Tribute_1622 | type=802-11-wireless
[802-11-wireless] ssid=Tribute_1622 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/PACE304]] (600 root)
[connection] id=PACE304 | type=802-11-wireless
[802-11-wireless] ssid=PACE304 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Wi-Fi connection 1]] (600 root)
[connection] id=Disneyland | type=802-11-wireless | permissions=user:jack:; | autoconnect=false
[802-11-wireless] ssid=PACE304 | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/9P72L]] (600 root)
[connection] id=9P72L | type=802-11-wireless
[802-11-wireless] ssid=9P72L | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/FiOS-IQDBR]] (600 root)
[connection] id=FiOS-IQDBR | type=802-11-wireless
[802-11-wireless] ssid=FiOS-IQDBR | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/gil]] (600 root)
[connection] id=gil | type=802-11-wireless
[802-11-wireless] ssid=gil | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/beachhouse]] (600 root)
[connection] id=beachhouse | type=802-11-wireless
[802-11-wireless] ssid=beachhouse | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/2.4 Number 3]] (600 root)
[connection] id=2.4 Number 3 | type=802-11-wireless
[802-11-wireless] ssid=2.4 Number 3 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/2WIRE978]] (600 root)
[connection] id=2WIRE978 | type=802-11-wireless
[802-11-wireless] ssid=2WIRE978 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Tribute_1622 1]] (600 root)
[connection] id=Tribute_1622 1 | type=802-11-wireless
[802-11-wireless] ssid=Tribute_1622
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: America/Los_Angeles (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

lo        no frequency information.

eth0      no frequency information.

ra0       27 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 14 : 2.484 GHz
          Channel 36 : 5.18 GHz
          Channel 38 : 5.19 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 46 : 5.23 GHz
          Channel 48 : 5.24 GHz
          Channel 149 : 5.745 GHz
          Channel 151 : 2.412 GHz
          Channel 153 : 5.765 GHz
          Channel 157 : 5.785 GHz
          Channel 159 : 2.412 GHz
          Channel 161 : 5.805 GHz
          Channel 165 : 5.825 GHz
          Current Frequency=2.412 GHz (Channel 1)

##### iwlist scan #######################

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:5.18 GHz (Channel 36)
      2   APs on   Frequency:5.24 GHz (Channel 48)
      1   APs on   Frequency:5.745 GHz (Channel 149)

ra0       Scan completed :
          Cell 01 - Address: <MAC 'Reeser5-5G' [AC1]>
                    Protocol:802.11a/n
                    ESSID:"Reeser5-5G"
                    Mode:Managed
                    Frequency:5.18 GHz (Channel 36)
                    Quality=5/100  Signal level=-88 dBm  Noise level=-91 dBm
                    Encryption key:on
                    Bit Rates:120 Mb/s
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC '' [AC2]>
                    Protocol:802.11a/n
                    ESSID:""
                    Mode:Managed
                    Frequency:5.24 GHz (Channel 48)
                    Quality=5/100  Signal level=-88 dBm  Noise level=-97 dBm
                    Encryption key:on
                    Bit Rates:57.5 Mb/s
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC '5.0 Number 3' [AC3]>
                    Protocol:802.11a/n
                    ESSID:"5.0 Number 3"
                    Mode:Managed
                    Frequency:5.745 GHz (Channel 149)
                    Quality=34/100  Signal level=-76 dBm  Noise level=-85 dBm
                    Encryption key:on
                    Bit Rates:120 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'Gil's Testing 5ghz' [AC4]>
                    Protocol:802.11a/n
                    ESSID:"Gil's Testing 5ghz"
                    Mode:Managed
                    Frequency:5.24 GHz (Channel 48)
                    Quality=0/100  Signal level=-90 dBm  Noise level=-85 dBm
                    Encryption key:on
                    Bit Rates:120 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'Tribute_1622' [AC5]>
                    Protocol:802.11b/g/n
                    ESSID:"Tribute_1622"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality=23/100  Signal level=-81 dBm  Noise level=-76 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[cfg80211]
filename:       /lib/modules/3.13.0-106-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     0055529745EF9A8A3E57FC3
depends:        
intree:         Y
vermagic:       3.13.0-106-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        35:8F:00:51:4A:EE:9D:E6:96:BC:B1:FE:CF:E9:98:39:A5:C6:78:20
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

lp

##### modprobe options ##################

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac
blacklist rt73usb
blacklist rt2x00usb
blacklist rt2x00usb
blacklist rt2x00lib
blacklist mac80211

[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF1]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

##### dmesg #############################

########## wireless info END ############


```

---

### Post by wildmanne39 on 2016-12-28
If by lan you mean ethernet port yes it does, but it is using the wrong driver so it will be very slow, the wifi is now showing connected but signal strength is at 30 and that is still low, are you next to your hotspot? 

Can you ping the following:
```
ping -c3 www.google.com
```

There is some information that looks strange but I have not worked with this device before, your wifi connection is not showing up in udev rules just the etho one. Go into network manager at the top of the page and make sure your wifi and networking is enabled.

Do:
```
sudo dpkg-reconfigure resolvconf
```

Check the settings in network manager for your wifi set IPV6 to ignore and the dns server to 8.8.8.8,8.8.4.4 and the comma is important.

If that does not do it then proceed with a fresh install of 16.10, if you have radeon graphics you may have display issues.

---


---
title: "Wifi weak signal with realtek d723"
date: 2020-05-08
forum: Networking &amp; Wireless
---

### Post by andresgaibor on 2020-05-08
I am new to Linux, I installed the drivers for the graphics card (Realtek d723), it works, but I am literally sitting next to the router and I have a -78dBm signal, I don't know what to do, I have already seen in a lot of forums but nothing solves my trouble. I don't know what information you need, if you need anything let me know

---

### Post by jeremy31 on 2020-05-08
What site did you get the driver from?

---

### Post by andresgaibor on 2020-05-08
[B]I used this
[/B]
```

git clone -b extended --single-branch [https://github.com/lwfinger/rtlwifi_new.git](https://github.com/lwfinger/rtlwifi_new.git)
sudo dkms add rtlwifi_new
sudo dkms install rtlwifi-new/0.6

```

---

### Post by jeremy31 on 2020-05-08
Did you set the ant_sel parameter?  Most of the time it works best if set to 2

---

### Post by andresgaibor on 2020-05-08
Yes, but it doesn't work for me

```

sudo modprobe rtl8723be ant_sel=(1/2)

```

---

### Post by jeremy31 on 2020-05-08
Post results from terminal for ```
grep [[:alnum:]] /etc/modprobe.d/*
```

---

### Post by andresgaibor on 2020-05-08
```

/etc/modprobe.d/50-rtl8723be.conf:options rtl8723be ant_sel=1
/etc/modprobe.d/alsa-base.conf:# autoloader aliases
/etc/modprobe.d/alsa-base.conf:install sound-slot-0 /sbin/modprobe snd-card-0
/etc/modprobe.d/alsa-base.conf:install sound-slot-1 /sbin/modprobe snd-card-1
/etc/modprobe.d/alsa-base.conf:install sound-slot-2 /sbin/modprobe snd-card-2
/etc/modprobe.d/alsa-base.conf:install sound-slot-3 /sbin/modprobe snd-card-3
/etc/modprobe.d/alsa-base.conf:install sound-slot-4 /sbin/modprobe snd-card-4
/etc/modprobe.d/alsa-base.conf:install sound-slot-5 /sbin/modprobe snd-card-5
/etc/modprobe.d/alsa-base.conf:install sound-slot-6 /sbin/modprobe snd-card-6
/etc/modprobe.d/alsa-base.conf:install sound-slot-7 /sbin/modprobe snd-card-7
/etc/modprobe.d/alsa-base.conf:# Cause optional modules to be loaded above generic modules
/etc/modprobe.d/alsa-base.conf:install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
/etc/modprobe.d/alsa-base.conf:# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
/etc/modprobe.d/alsa-base.conf:install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
/etc/modprobe.d/alsa-base.conf:install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
/etc/modprobe.d/alsa-base.conf:install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
/etc/modprobe.d/alsa-base.conf:install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
/etc/modprobe.d/alsa-base.conf:# Cause optional modules to be loaded above sound card driver modules
/etc/modprobe.d/alsa-base.conf:install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
/etc/modprobe.d/alsa-base.conf:install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }
/etc/modprobe.d/alsa-base.conf:# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
/etc/modprobe.d/alsa-base.conf:install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
/etc/modprobe.d/alsa-base.conf:# Prevent abnormal drivers from grabbing index 0
/etc/modprobe.d/alsa-base.conf:options bt87x index=-2
/etc/modprobe.d/alsa-base.conf:options cx88_alsa index=-2
/etc/modprobe.d/alsa-base.conf:options saa7134-alsa index=-2
/etc/modprobe.d/alsa-base.conf:options snd-atiixp-modem index=-2
/etc/modprobe.d/alsa-base.conf:options snd-intel8x0m index=-2
/etc/modprobe.d/alsa-base.conf:options snd-via82xx-modem index=-2
/etc/modprobe.d/alsa-base.conf:options snd-usb-audio index=-2
/etc/modprobe.d/alsa-base.conf:options snd-usb-caiaq index=-2
/etc/modprobe.d/alsa-base.conf:options snd-usb-ua101 index=-2
/etc/modprobe.d/alsa-base.conf:options snd-usb-us122l index=-2
/etc/modprobe.d/alsa-base.conf:options snd-usb-usx2y index=-2
/etc/modprobe.d/alsa-base.conf:# Ubuntu #62691, enable MPU for snd-cmipci
/etc/modprobe.d/alsa-base.conf:options snd-cmipci mpu_port=0x330 fm_port=0x388
/etc/modprobe.d/alsa-base.conf:# Keep snd-pcsp from being loaded as first soundcard
/etc/modprobe.d/alsa-base.conf:options snd-pcsp index=-2
/etc/modprobe.d/alsa-base.conf:# Keep snd-usb-audio from beeing loaded as first soundcard
/etc/modprobe.d/alsa-base.conf:options snd-usb-audio index=-2
/etc/modprobe.d/amd64-microcode-blacklist.conf:# The microcode module attempts to apply a microcode update when
/etc/modprobe.d/amd64-microcode-blacklist.conf:# it autoloads.  This is not always safe, so we block it by default.
/etc/modprobe.d/amd64-microcode-blacklist.conf:blacklist microcode
/etc/modprobe.d/blacklist-ath_pci.conf:# For some Atheros 5K RF MACs, the madwifi driver loads buts fails to
/etc/modprobe.d/blacklist-ath_pci.conf:# correctly initialize the hardware, leaving it in a state from
/etc/modprobe.d/blacklist-ath_pci.conf:# which ath5k cannot recover. To prevent this condition, stop
/etc/modprobe.d/blacklist-ath_pci.conf:# madwifi from loading by default. Use Jockey to select one driver
/etc/modprobe.d/blacklist-ath_pci.conf:# or the other. (Ubuntu: #315056, #323830)
/etc/modprobe.d/blacklist-ath_pci.conf:blacklist ath_pci
/etc/modprobe.d/blacklist.conf:# This file lists those modules which we don't want to be loaded by
/etc/modprobe.d/blacklist.conf:# alias expansion, usually so some other driver will be loaded for the
/etc/modprobe.d/blacklist.conf:# device instead.
/etc/modprobe.d/blacklist.conf:# evbug is a debug tool that should be loaded explicitly
/etc/modprobe.d/blacklist.conf:blacklist evbug
/etc/modprobe.d/blacklist.conf:# these drivers are very simple, the HID drivers are usually preferred
/etc/modprobe.d/blacklist.conf:blacklist usbmouse
/etc/modprobe.d/blacklist.conf:blacklist usbkbd
/etc/modprobe.d/blacklist.conf:# replaced by e100
/etc/modprobe.d/blacklist.conf:blacklist eepro100
/etc/modprobe.d/blacklist.conf:# replaced by tulip
/etc/modprobe.d/blacklist.conf:blacklist de4x5
/etc/modprobe.d/blacklist.conf:# causes no end of confusion by creating unexpected network interfaces
/etc/modprobe.d/blacklist.conf:blacklist eth1394
/etc/modprobe.d/blacklist.conf:# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
/etc/modprobe.d/blacklist.conf:# hardware on its own (Ubuntu bug #2011, #6810)
/etc/modprobe.d/blacklist.conf:blacklist snd_intel8x0m
/etc/modprobe.d/blacklist.conf:# Conflicts with dvb driver (which is better for handling this device)
/etc/modprobe.d/blacklist.conf:blacklist snd_aw2
/etc/modprobe.d/blacklist.conf:# Causes trackpads to stop working on Lenovo 11e 2nd gen (Ubuntu: #1802135)
/etc/modprobe.d/blacklist.conf:# and Lenovo x240 to hang on boot (Ubuntu: #1802689)
/etc/modprobe.d/blacklist.conf:blacklist i2c_i801
/etc/modprobe.d/blacklist.conf:# replaced by p54pci
/etc/modprobe.d/blacklist.conf:blacklist prism54
/etc/modprobe.d/blacklist.conf:# replaced by b43 and ssb.
/etc/modprobe.d/blacklist.conf:blacklist bcm43xx
/etc/modprobe.d/blacklist.conf:# most apps now use garmin usb driver directly (Ubuntu: #114565)
/etc/modprobe.d/blacklist.conf:blacklist garmin_gps
/etc/modprobe.d/blacklist.conf:# replaced by asus-laptop (Ubuntu: #184721)
/etc/modprobe.d/blacklist.conf:blacklist asus_acpi
/etc/modprobe.d/blacklist.conf:# low-quality, just noise when being used for sound playback, causes
/etc/modprobe.d/blacklist.conf:# hangs at desktop session start (Ubuntu: #246969)
/etc/modprobe.d/blacklist.conf:blacklist snd_pcsp
/etc/modprobe.d/blacklist.conf:# ugly and loud noise, getting on everyone's nerves; this should be done by a
/etc/modprobe.d/blacklist.conf:# nice pulseaudio bing (Ubuntu: #77010)
/etc/modprobe.d/blacklist.conf:blacklist pcspkr
/etc/modprobe.d/blacklist.conf:# EDAC driver for amd76x clashes with the agp driver preventing the aperture
/etc/modprobe.d/blacklist.conf:# from being initialised (Ubuntu: #297750). Blacklist so that the driver
/etc/modprobe.d/blacklist.conf:# continues to build and is installable for the few cases where its
/etc/modprobe.d/blacklist.conf:# really needed.
/etc/modprobe.d/blacklist.conf:blacklist amd76x_edac
/etc/modprobe.d/blacklist-firewire.conf:# Select the legacy firewire stack over the new CONFIG_FIREWIRE one.
/etc/modprobe.d/blacklist-firewire.conf:blacklist ohci1394
/etc/modprobe.d/blacklist-firewire.conf:blacklist sbp2
/etc/modprobe.d/blacklist-firewire.conf:blacklist dv1394
/etc/modprobe.d/blacklist-firewire.conf:blacklist raw1394
/etc/modprobe.d/blacklist-firewire.conf:blacklist video1394
/etc/modprobe.d/blacklist-firewire.conf:#blacklist firewire-ohci
/etc/modprobe.d/blacklist-firewire.conf:#blacklist firewire-sbp2
/etc/modprobe.d/blacklist-framebuffer.conf:# Framebuffer drivers are generally buggy and poorly-supported, and cause
/etc/modprobe.d/blacklist-framebuffer.conf:# suspend failures, kernel panics and general mayhem.  For this reason we
/etc/modprobe.d/blacklist-framebuffer.conf:# never load them automatically.
/etc/modprobe.d/blacklist-framebuffer.conf:blacklist aty128fb
/etc/modprobe.d/blacklist-framebuffer.conf:blacklist atyfb
/etc/modprobe.d/blacklist-framebuffer.conf:blacklist bochs-drm
/etc/modprobe.d/blacklist-framebuffer.conf:blacklist radeonfb
/etc/modprobe.d/blacklist-framebuffer.conf:blacklist cirrusfb
/etc/modprobe.d/blacklist-framebuffer.conf:blacklist cyber2000fb
/etc/modprobe.d/blacklist-framebuffer.conf:blacklist cyblafb
/etc/modprobe.d/blacklist-framebuffer.conf:blacklist gx1fb
/etc/modprobe.d/blacklist-framebuffer.conf:blacklist hgafb
/etc/modprobe.d/blacklist-framebuffer.conf:blacklist i810fb
/etc/modprobe.d/blacklist-framebuffer.conf:blacklist intelfb
/etc/modprobe.d/blacklist-framebuffer.conf:blacklist kyrofb
/etc/modprobe.d/blacklist-framebuffer.conf:blacklist lxfb
/etc/modprobe.d/blacklist-framebuffer.conf:blacklist matroxfb_base
/etc/modprobe.d/blacklist-framebuffer.conf:blacklist neofb
/etc/modprobe.d/blacklist-framebuffer.conf:blacklist nvidiafb
/etc/modprobe.d/blacklist-framebuffer.conf:blacklist pm2fb
/etc/modprobe.d/blacklist-framebuffer.conf:blacklist rivafb
/etc/modprobe.d/blacklist-framebuffer.conf:blacklist s1d13xxxfb
/etc/modprobe.d/blacklist-framebuffer.conf:blacklist savagefb
/etc/modprobe.d/blacklist-framebuffer.conf:blacklist sisfb
/etc/modprobe.d/blacklist-framebuffer.conf:blacklist sstfb
/etc/modprobe.d/blacklist-framebuffer.conf:blacklist tdfxfb
/etc/modprobe.d/blacklist-framebuffer.conf:blacklist tridentfb
/etc/modprobe.d/blacklist-framebuffer.conf:#blacklist vesafb
/etc/modprobe.d/blacklist-framebuffer.conf:blacklist vfb
/etc/modprobe.d/blacklist-framebuffer.conf:blacklist viafb
/etc/modprobe.d/blacklist-framebuffer.conf:blacklist vt8623fb
/etc/modprobe.d/blacklist-framebuffer.conf:blacklist udlfb
/etc/modprobe.d/blacklist-modem.conf:# Uncomment these entries in order to blacklist unwanted modem drivers
/etc/modprobe.d/blacklist-modem.conf:# blacklist snd-atiixp-modem
/etc/modprobe.d/blacklist-modem.conf:# blacklist snd-intel8x0m
/etc/modprobe.d/blacklist-modem.conf:# blacklist snd-via82xx-modem
/etc/modprobe.d/blacklist-oss.conf:blacklist ac97
/etc/modprobe.d/blacklist-oss.conf:blacklist ac97_codec
/etc/modprobe.d/blacklist-oss.conf:blacklist ac97_plugin_ad1980
/etc/modprobe.d/blacklist-oss.conf:blacklist ad1848
/etc/modprobe.d/blacklist-oss.conf:blacklist ad1889
/etc/modprobe.d/blacklist-oss.conf:blacklist adlib_card
/etc/modprobe.d/blacklist-oss.conf:blacklist aedsp16
/etc/modprobe.d/blacklist-oss.conf:blacklist ali5455
/etc/modprobe.d/blacklist-oss.conf:blacklist btaudio
/etc/modprobe.d/blacklist-oss.conf:blacklist cmpci
/etc/modprobe.d/blacklist-oss.conf:blacklist cs4232
/etc/modprobe.d/blacklist-oss.conf:blacklist cs4281
/etc/modprobe.d/blacklist-oss.conf:blacklist cs461x
/etc/modprobe.d/blacklist-oss.conf:blacklist cs46xx
/etc/modprobe.d/blacklist-oss.conf:blacklist emu10k1
/etc/modprobe.d/blacklist-oss.conf:blacklist es1370
/etc/modprobe.d/blacklist-oss.conf:blacklist es1371
/etc/modprobe.d/blacklist-oss.conf:blacklist esssolo1
/etc/modprobe.d/blacklist-oss.conf:blacklist forte
/etc/modprobe.d/blacklist-oss.conf:blacklist gus
/etc/modprobe.d/blacklist-oss.conf:blacklist i810_audio
/etc/modprobe.d/blacklist-oss.conf:blacklist kahlua
/etc/modprobe.d/blacklist-oss.conf:blacklist mad16
/etc/modprobe.d/blacklist-oss.conf:blacklist maestro
/etc/modprobe.d/blacklist-oss.conf:blacklist maestro3
/etc/modprobe.d/blacklist-oss.conf:blacklist maui
/etc/modprobe.d/blacklist-oss.conf:blacklist mpu401
/etc/modprobe.d/blacklist-oss.conf:blacklist nm256_audio
/etc/modprobe.d/blacklist-oss.conf:blacklist opl3
/etc/modprobe.d/blacklist-oss.conf:blacklist opl3sa
/etc/modprobe.d/blacklist-oss.conf:blacklist opl3sa2
/etc/modprobe.d/blacklist-oss.conf:blacklist pas2
/etc/modprobe.d/blacklist-oss.conf:blacklist pss
/etc/modprobe.d/blacklist-oss.conf:blacklist rme96xx
/etc/modprobe.d/blacklist-oss.conf:blacklist sb
/etc/modprobe.d/blacklist-oss.conf:blacklist sb_lib
/etc/modprobe.d/blacklist-oss.conf:blacklist sgalaxy
/etc/modprobe.d/blacklist-oss.conf:blacklist sonicvibes
/etc/modprobe.d/blacklist-oss.conf:blacklist sound
/etc/modprobe.d/blacklist-oss.conf:blacklist sscape
/etc/modprobe.d/blacklist-oss.conf:blacklist trident
/etc/modprobe.d/blacklist-oss.conf:blacklist trix
/etc/modprobe.d/blacklist-oss.conf:blacklist uart401
/etc/modprobe.d/blacklist-oss.conf:blacklist uart6850
/etc/modprobe.d/blacklist-oss.conf:blacklist via82cxxx_audio
/etc/modprobe.d/blacklist-oss.conf:blacklist v_midi
/etc/modprobe.d/blacklist-oss.conf:blacklist wavefront
/etc/modprobe.d/blacklist-oss.conf:blacklist ymfpci
/etc/modprobe.d/blacklist-oss.conf:blacklist ac97_plugin_wm97xx
/etc/modprobe.d/blacklist-oss.conf:blacklist ad1816
/etc/modprobe.d/blacklist-oss.conf:blacklist audio
/etc/modprobe.d/blacklist-oss.conf:blacklist awe_wave
/etc/modprobe.d/blacklist-oss.conf:blacklist dmasound_core
/etc/modprobe.d/blacklist-oss.conf:blacklist dmasound_pmac
/etc/modprobe.d/blacklist-oss.conf:blacklist harmony
/etc/modprobe.d/blacklist-oss.conf:blacklist sequencer
/etc/modprobe.d/blacklist-oss.conf:blacklist soundcard
/etc/modprobe.d/blacklist-oss.conf:blacklist usb-midi
/etc/modprobe.d/blacklist-radeon.conf:blacklist radeon
/etc/modprobe.d/blacklist-rare-network.conf:# Many less commonly used network protocols have recently had various
/etc/modprobe.d/blacklist-rare-network.conf:# security flaws discovered. In an effort to reduce the scope of future
/etc/modprobe.d/blacklist-rare-network.conf:# vulnerability exploitations, they are being blacklisted here so that
/etc/modprobe.d/blacklist-rare-network.conf:# unprivileged users cannot use them by default. System owners can still
/etc/modprobe.d/blacklist-rare-network.conf:# either modify this file, or specifically modprobe any needed protocols.
/etc/modprobe.d/blacklist-rare-network.conf:# ax25
/etc/modprobe.d/blacklist-rare-network.conf:alias net-pf-3 off
/etc/modprobe.d/blacklist-rare-network.conf:# netrom
/etc/modprobe.d/blacklist-rare-network.conf:alias net-pf-6 off
/etc/modprobe.d/blacklist-rare-network.conf:# x25
/etc/modprobe.d/blacklist-rare-network.conf:alias net-pf-9 off
/etc/modprobe.d/blacklist-rare-network.conf:# rose
/etc/modprobe.d/blacklist-rare-network.conf:alias net-pf-11 off
/etc/modprobe.d/blacklist-rare-network.conf:# decnet
/etc/modprobe.d/blacklist-rare-network.conf:alias net-pf-12 off
/etc/modprobe.d/blacklist-rare-network.conf:# econet
/etc/modprobe.d/blacklist-rare-network.conf:alias net-pf-19 off
/etc/modprobe.d/blacklist-rare-network.conf:# rds
/etc/modprobe.d/blacklist-rare-network.conf:alias net-pf-21 off
/etc/modprobe.d/blacklist-rare-network.conf:# af_802154
/etc/modprobe.d/blacklist-rare-network.conf:alias net-pf-36 off
/etc/modprobe.d/blacklist-watchdog.conf:# Watchdog drivers should not be loaded automatically, but only if a
/etc/modprobe.d/blacklist-watchdog.conf:# watchdog daemon is installed.
/etc/modprobe.d/blacklist-watchdog.conf:blacklist acquirewdt
/etc/modprobe.d/blacklist-watchdog.conf:blacklist advantechwdt
/etc/modprobe.d/blacklist-watchdog.conf:blacklist alim1535_wdt
/etc/modprobe.d/blacklist-watchdog.conf:blacklist alim7101_wdt
/etc/modprobe.d/blacklist-watchdog.conf:blacklist booke_wdt
/etc/modprobe.d/blacklist-watchdog.conf:blacklist cpu5wdt
/etc/modprobe.d/blacklist-watchdog.conf:blacklist eurotechwdt
/etc/modprobe.d/blacklist-watchdog.conf:blacklist i6300esb
/etc/modprobe.d/blacklist-watchdog.conf:blacklist i8xx_tco
/etc/modprobe.d/blacklist-watchdog.conf:blacklist ib700wdt
/etc/modprobe.d/blacklist-watchdog.conf:blacklist ibmasr
/etc/modprobe.d/blacklist-watchdog.conf:blacklist indydog
/etc/modprobe.d/blacklist-watchdog.conf:blacklist iTCO_wdt
/etc/modprobe.d/blacklist-watchdog.conf:blacklist it8712f_wdt
/etc/modprobe.d/blacklist-watchdog.conf:blacklist it87_wdt
/etc/modprobe.d/blacklist-watchdog.conf:blacklist ixp2000_wdt
/etc/modprobe.d/blacklist-watchdog.conf:blacklist ixp4xx_wdt
/etc/modprobe.d/blacklist-watchdog.conf:blacklist machzwd
/etc/modprobe.d/blacklist-watchdog.conf:blacklist mixcomwd
/etc/modprobe.d/blacklist-watchdog.conf:blacklist mpc8xx_wdt
/etc/modprobe.d/blacklist-watchdog.conf:blacklist mpcore_wdt
/etc/modprobe.d/blacklist-watchdog.conf:blacklist mv64x60_wdt
/etc/modprobe.d/blacklist-watchdog.conf:blacklist pc87413_wdt
/etc/modprobe.d/blacklist-watchdog.conf:blacklist pcwd
/etc/modprobe.d/blacklist-watchdog.conf:blacklist pcwd_pci
/etc/modprobe.d/blacklist-watchdog.conf:blacklist pcwd_usb
/etc/modprobe.d/blacklist-watchdog.conf:blacklist s3c2410_wdt
/etc/modprobe.d/blacklist-watchdog.conf:blacklist sa1100_wdt
/etc/modprobe.d/blacklist-watchdog.conf:blacklist sbc60xxwdt
/etc/modprobe.d/blacklist-watchdog.conf:blacklist sbc7240_wdt
/etc/modprobe.d/blacklist-watchdog.conf:blacklist sb8360
/etc/modprobe.d/blacklist-watchdog.conf:blacklist sc1200wdt
/etc/modprobe.d/blacklist-watchdog.conf:blacklist sc520_wdt
/etc/modprobe.d/blacklist-watchdog.conf:blacklist sch311_wdt
/etc/modprobe.d/blacklist-watchdog.conf:blacklist scx200_wdt
/etc/modprobe.d/blacklist-watchdog.conf:blacklist shwdt
/etc/modprobe.d/blacklist-watchdog.conf:blacklist smsc37b787_wdt
/etc/modprobe.d/blacklist-watchdog.conf:blacklist softdog
/etc/modprobe.d/blacklist-watchdog.conf:blacklist twl4030_wdt
/etc/modprobe.d/blacklist-watchdog.conf:blacklist w83627hf_wdt
/etc/modprobe.d/blacklist-watchdog.conf:blacklist w83697hf_wdt
/etc/modprobe.d/blacklist-watchdog.conf:blacklist w83697ug_wdt
/etc/modprobe.d/blacklist-watchdog.conf:blacklist w83877f_wdt
/etc/modprobe.d/blacklist-watchdog.conf:blacklist w83977f_wdt
/etc/modprobe.d/blacklist-watchdog.conf:blacklist wafer5823wdt
/etc/modprobe.d/blacklist-watchdog.conf:blacklist wdt
/etc/modprobe.d/blacklist-watchdog.conf:blacklist wdt_pci
/etc/modprobe.d/blacklist-watchdog.conf:blacklist wm8350_wdt
/etc/modprobe.d/dkms.conf:# modprobe information used for DKMS modules
/etc/modprobe.d/dkms.conf:# This is a stub file, should be edited when needed,
/etc/modprobe.d/dkms.conf:# used by default by DKMS.
/etc/modprobe.d/intel-microcode-blacklist.conf:# The microcode module attempts to apply a microcode update when
/etc/modprobe.d/intel-microcode-blacklist.conf:# it autoloads.  This is not always safe, so we block it by default.
/etc/modprobe.d/intel-microcode-blacklist.conf:blacklist microcode
/etc/modprobe.d/iwlwifi.conf:# /etc/modprobe.d/iwlwifi.conf
/etc/modprobe.d/iwlwifi.conf:# iwlwifi will dyamically load either iwldvm or iwlmvm depending on the
/etc/modprobe.d/iwlwifi.conf:# microcode file installed on the system.  When removing iwlwifi, first
/etc/modprobe.d/iwlwifi.conf:# remove the iwl?vm module and then iwlwifi.
/etc/modprobe.d/iwlwifi.conf:remove iwlwifi \
/etc/modprobe.d/iwlwifi.conf:(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
/etc/modprobe.d/iwlwifi.conf:&& /sbin/modprobe -r mac80211
/etc/modprobe.d/rtl8723-ant-sel.conf:options rtl8723be ant_sel=1
/etc/modprobe.d/rtl8723be-ant.conf:options rtl8723be ant_sel=2
/etc/modprobe.d/vmwgfx-fbdev.conf:options vmwgfx enable_fbdev=1


```

---

### Post by jeremy31 on 2020-05-08
Ok, do this and reboot
```
echo "options rtl8723de ant_sel=2" | sudo tee /etc/modprobe.d/50-rtl8723be.conf
```

---

### Post by andresgaibor on 2020-05-08
It worked, thank you very much

---

### Post by bwakkie on 2020-05-15
For reference you can read up about it in an arch linux post: [https://bbs.archlinux.org/viewtopic.php?id=208472]("https://bbs.archlinux.org/viewtopic.php?id=208472")

I stumbled on this post after I already followed the arch wiki. It turned out I had to use the second antena. These where my steps:

# As the article is somewhat Arch Linux specific I had to do tiny adaptations for ubuntu 20.04

# edit / create the following file:
/etc/modprobe.d/rtl8723be.conf
==============================
options rtl8723be fwlps=N ips=N swlps=N swenc=Y disable_watchdog=1

git clone [https://github.com/lwfinger/rtlwifi_new.git](https://github.com/lwfinger/rtlwifi_new.git)
cd rtlwifi_new
#git checkout rock.new_btcoex --> this isn't working so checkout the following as stated in the error message:
git checkout origin/extended -b extended

make clean && make
sudo make install

# sudo mkinitcpio -p linux
# ubuntu version to update initramfs:
update-initramfs -u

 
 # After every kernel update:
 cd rtlwifi_new
 # Clean previous builds
 make clean
 # Update git repository
 git pull
 # Compile
 make clean && make
 # Install
 sudo make install
 # Update initramfs
 update-initramfs -u
 
 
 #Test which antenna works best for you:
 sudo rmmod rtl8723be
 sudo modprobe rtl8723be ant_sel=1
 sudo iwlist wlan0 scan
 sudo rmmod rtl8723be
 sudo modprobe rtl8723be ant_sel=2
 sudo iwlist wlan0 scan
 
 # then
 /etc/modprobe.d/rtl8723be.conf
 ==============================
 options rtl8723be fwlps=N ips=N swlps=N swenc=Y disable_watchdog=1 ant_sel=X

---


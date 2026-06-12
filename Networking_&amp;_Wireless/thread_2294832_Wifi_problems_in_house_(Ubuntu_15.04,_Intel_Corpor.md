---
title: "Wifi problems in house (Ubuntu 15.04, Intel Corporation Centrino Wireless-N 2230)"
date: 2015-09-13
forum: Networking &amp; Wireless
---

### Post by hein5 on 2015-09-13
Hello!

I have a problem with the wireless internet in my house. In other places (uni, friends houses etc) it works well. Basically the problem is that it drops when I start using the internet more 'intensely', like playing an internet game + trying to use the browser. and it will not work after that. Also, when I connect a bluetooth mouse that seems to kill the internet also. Earlier today I could not even connect at all, or extremely slowely. After searching the web on my phone (which works fine, btw, in the same house) it seemed other people with lenovo laptop had some success with resetting their BIOS to default settings so I did this as well. This helped a bit as I was now able to connect after rebooting but then I was faced with the problem I just mentioned.
I attached the output of the wireless script.

---

### Post by tgalati4 on 2015-09-13
OK, let's look at your switches:

```
modinfo iwlwifi
```

You will find the following parameters that can be set:

> parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (defualt: 0 dB) (int)
parm:           wd_disable:Disable stuck queue watchdog timer 0=system default, 1=disable, 2=enable (default: 0) (int)
parm:           nvm_file:NVM file name (charp)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)


The key is to figure out the correct settings to work well for both your home wifi and everywhere else.

Many wifi chipsets have bluetooth built-in.  And because bluetooth is 2.4 GHz (same as Wireless G Band) they tend to share the same antenna.  Which means when you have bluetooth turned on, the chipset will chop up the signal and multiplex it--switching rapidly between bluetooth transmission and wireless G transmission.  As you can imagine, this can totally destroy some wireless connections.

So for all troubleshooting from now one, keep bluetooth turned off.  Turn it off in BIOS if you have a switch.

What are your current switches?

```
sudo modprobe -c iwlwifi
```

I missed it from the wifi troubleshooting report:

> [iwlwifi]
11n_disable: 0
amsdu_size_8K: 0
antenna_coupling: 0
bt_coex_active: Y
fw_monitor: N
fw_restart: Y
led_mode: 0
nvm_file: (null)
power_level: 0
power_save: N
swcrypto: 0
uapsd_disable: Y
wd_disable: 1


I have no idea what the "magic" settings are to make your wifi to work.  You will have to do some more research.

I do know that one of the first things to do is to shut off Wireless N.  Change one parameter at a time.  Keep good notes.

Oh, and welcome to the forums!

---

### Post by hein5 on 2015-09-14
Thanks for your help!
This is the output (up until 'end of configuration files') of sudo modprobe -c iwlwifi:

```

blacklist ath_pci
blacklist ohci1394
blacklist sbp2
blacklist dv1394
blacklist raw1394
blacklist video1394
blacklist aty128fb
blacklist atyfb
blacklist bochs_drm
blacklist radeonfb
blacklist cirrusfb
blacklist cyber2000fb
blacklist cyblafb
blacklist gx1fb
blacklist hgafb
blacklist i810fb
blacklist intelfb
blacklist kyrofb
blacklist lxfb
blacklist matroxfb_base
blacklist neofb
blacklist nvidiafb
blacklist pm2fb
blacklist rivafb
blacklist s1d13xxxfb
blacklist savagefb
blacklist sisfb
blacklist sstfb
blacklist tdfxfb
blacklist tridentfb
blacklist vfb
blacklist viafb
blacklist vt8623fb
blacklist udlfb
blacklist ac97
blacklist ac97_codec
blacklist ac97_plugin_ad1980
blacklist ad1848
blacklist ad1889
blacklist adlib_card
blacklist aedsp16
blacklist ali5455
blacklist btaudio
blacklist cmpci
blacklist cs4232
blacklist cs4281
blacklist cs461x
blacklist cs46xx
blacklist emu10k1
blacklist es1370
blacklist es1371
blacklist esssolo1
blacklist forte
blacklist gus
blacklist i810_audio
blacklist kahlua
blacklist mad16
blacklist maestro
blacklist maestro3
blacklist maui
blacklist mpu401
blacklist nm256_audio
blacklist opl3
blacklist opl3sa
blacklist opl3sa2
blacklist pas2
blacklist pss
blacklist rme96xx
blacklist sb
blacklist sb_lib
blacklist sgalaxy
blacklist sonicvibes
blacklist sound
blacklist sscape
blacklist trident
blacklist trix
blacklist uart401
blacklist uart6850
blacklist via82cxxx_audio
blacklist v_midi
blacklist wavefront
blacklist ymfpci
blacklist ac97_plugin_wm97xx
blacklist ad1816
blacklist audio
blacklist awe_wave
blacklist dmasound_core
blacklist dmasound_pmac
blacklist harmony
blacklist sequencer
blacklist soundcard
blacklist usb_midi
blacklist acquirewdt
blacklist advantechwdt
blacklist alim1535_wdt
blacklist alim7101_wdt
blacklist booke_wdt
blacklist cpu5wdt
blacklist eurotechwdt
blacklist i6300esb
blacklist i8xx_tco
blacklist ib700wdt
blacklist ibmasr
blacklist indydog
blacklist iTCO_wdt
blacklist it8712f_wdt
blacklist it87_wdt
blacklist ixp2000_wdt
blacklist ixp4xx_wdt
blacklist machzwd
blacklist mixcomwd
blacklist mpc8xx_wdt
blacklist mpcore_wdt
blacklist mv64x60_wdt
blacklist pc87413_wdt
blacklist pcwd
blacklist pcwd_pci
blacklist pcwd_usb
blacklist s3c2410_wdt
blacklist sa1100_wdt
blacklist sbc60xxwdt
blacklist sbc7240_wdt
blacklist sb8360
blacklist sc1200wdt
blacklist sc520_wdt
blacklist sch311_wdt
blacklist scx200_wdt
blacklist shwdt
blacklist smsc37b787_wdt
blacklist softdog
blacklist twl4030_wdt
blacklist w83627hf_wdt
blacklist w83697hf_wdt
blacklist w83697ug_wdt
blacklist w83877f_wdt
blacklist w83977f_wdt
blacklist wafer5823wdt
blacklist wdt
blacklist wdt_pci
blacklist wm8350_wdt
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
blacklist snd_mixer_oss
blacklist snd_pcm_oss
blacklist acquirewdt
blacklist advantechwdt
blacklist alim1535_wdt
blacklist alim7101_wdt
blacklist cpu5wdt
blacklist da9052_wdt
blacklist da9055_wdt
blacklist da9063_wdt
blacklist dw_wdt
blacklist eurotechwdt
blacklist f71808e_wdt
blacklist hpwdt
blacklist i6300esb
blacklist iTCO_vendor_support
blacklist iTCO_wdt
blacklist ib700wdt
blacklist ibmasr
blacklist ie6xx_wdt
blacklist it8712f_wdt
blacklist it87_wdt
blacklist kempld_wdt
blacklist machzwd
blacklist mena21_wdt
blacklist menf21bmc_wdt
blacklist nv_tco
blacklist of_xilinx_wdt
blacklist pc87413_wdt
blacklist pcwd_pci
blacklist pcwd_usb
blacklist retu_wdt
blacklist rn5t618_wdt
blacklist sbc60xxwdt
blacklist sbc_epx_c3
blacklist sbc_fitpc2_wdt
blacklist sc1200wdt
blacklist sch311x_wdt
blacklist smsc37b787_wdt
blacklist softdog
blacklist sp5100_tco
blacklist twl4030_wdt
blacklist via_wdt
blacklist w83627hf_wdt
blacklist w83877f_wdt
blacklist w83977f_wdt
blacklist wafer5823wdt
blacklist wdt_pci
blacklist wm831x_wdt
blacklist wm8350_wdt
blacklist xen_wdt
blacklist snd_mixer_oss
blacklist snd_pcm_oss
blacklist acquirewdt
blacklist advantechwdt
blacklist alim1535_wdt
blacklist alim7101_wdt
blacklist cpu5wdt
blacklist da9052_wdt
blacklist da9055_wdt
blacklist da9063_wdt
blacklist dw_wdt
blacklist eurotechwdt
blacklist f71808e_wdt
blacklist hpwdt
blacklist i6300esb
blacklist iTCO_vendor_support
blacklist iTCO_wdt
blacklist ib700wdt
blacklist ibmasr
blacklist ie6xx_wdt
blacklist it8712f_wdt
blacklist it87_wdt
blacklist kempld_wdt
blacklist machzwd
blacklist mena21_wdt
blacklist menf21bmc_wdt
blacklist nv_tco
blacklist of_xilinx_wdt
blacklist pc87413_wdt
blacklist pcwd_pci
blacklist pcwd_usb
blacklist retu_wdt
blacklist rn5t618_wdt
blacklist sbc60xxwdt
blacklist sbc_epx_c3
blacklist sbc_fitpc2_wdt
blacklist sc1200wdt
blacklist sch311x_wdt
blacklist smsc37b787_wdt
blacklist softdog
blacklist sp5100_tco
blacklist twl4030_wdt
blacklist via_wdt
blacklist w83627hf_wdt
blacklist w83877f_wdt
blacklist w83977f_wdt
blacklist wafer5823wdt
blacklist wdt_pci
blacklist wm831x_wdt
blacklist wm8350_wdt
blacklist xen_wdt
blacklist snd_mixer_oss
blacklist snd_pcm_oss
blacklist acquirewdt
blacklist advantechwdt
blacklist alim1535_wdt
blacklist alim7101_wdt
blacklist cpu5wdt
blacklist da9052_wdt
blacklist da9055_wdt
blacklist da9063_wdt
blacklist dw_wdt
blacklist eurotechwdt
blacklist f71808e_wdt
blacklist hpwdt
blacklist i6300esb
blacklist iTCO_vendor_support
blacklist iTCO_wdt
blacklist ib700wdt
blacklist ibmasr
blacklist ie6xx_wdt
blacklist it8712f_wdt
blacklist it87_wdt
blacklist kempld_wdt
blacklist machzwd
blacklist mena21_wdt
blacklist menf21bmc_wdt
blacklist nv_tco
blacklist of_xilinx_wdt
blacklist pc87413_wdt
blacklist pcwd_pci
blacklist pcwd_usb
blacklist retu_wdt
blacklist rn5t618_wdt
blacklist sbc60xxwdt
blacklist sbc_epx_c3
blacklist sbc_fitpc2_wdt
blacklist sc1200wdt
blacklist sch311x_wdt
blacklist smsc37b787_wdt
blacklist softdog
blacklist sp5100_tco
blacklist twl4030_wdt
blacklist via_wdt
blacklist w83627hf_wdt
blacklist w83877f_wdt
blacklist w83977f_wdt
blacklist wafer5823wdt
blacklist wdt_pci
blacklist wm831x_wdt
blacklist wm8350_wdt
blacklist xen_wdt
blacklist snd_mixer_oss
blacklist snd_pcm_oss
blacklist acquirewdt
blacklist advantechwdt
blacklist alim1535_wdt
blacklist alim7101_wdt
blacklist cpu5wdt
blacklist da9052_wdt
blacklist da9055_wdt
blacklist da9063_wdt
blacklist dw_wdt
blacklist eurotechwdt
blacklist f71808e_wdt
blacklist hpwdt
blacklist i6300esb
blacklist iTCO_vendor_support
blacklist iTCO_wdt
blacklist ib700wdt
blacklist ibmasr
blacklist ie6xx_wdt
blacklist it8712f_wdt
blacklist it87_wdt
blacklist kempld_wdt
blacklist machzwd
blacklist mena21_wdt
blacklist menf21bmc_wdt
blacklist nv_tco
blacklist of_xilinx_wdt
blacklist pc87413_wdt
blacklist pcwd_pci
blacklist pcwd_usb
blacklist retu_wdt
blacklist rn5t618_wdt
blacklist sbc60xxwdt
blacklist sbc_epx_c3
blacklist sbc_fitpc2_wdt
blacklist sc1200wdt
blacklist sch311x_wdt
blacklist smsc37b787_wdt
blacklist softdog
blacklist sp5100_tco
blacklist twl4030_wdt
blacklist via_wdt
blacklist w83627hf_wdt
blacklist w83877f_wdt
blacklist w83977f_wdt
blacklist wafer5823wdt
blacklist wdt_pci
blacklist wm831x_wdt
blacklist wm8350_wdt
blacklist xen_wdt
blacklist snd_mixer_oss
blacklist snd_pcm_oss
blacklist acquirewdt
blacklist advantechwdt
blacklist alim1535_wdt
blacklist alim7101_wdt
blacklist cpu5wdt
blacklist da9052_wdt
blacklist da9055_wdt
blacklist da9063_wdt
blacklist dw_wdt
blacklist eurotechwdt
blacklist f71808e_wdt
blacklist hpwdt
blacklist i6300esb
blacklist iTCO_vendor_support
blacklist iTCO_wdt
blacklist ib700wdt
blacklist ibmasr
blacklist ie6xx_wdt
blacklist it8712f_wdt
blacklist it87_wdt
blacklist kempld_wdt
blacklist machzwd
blacklist mena21_wdt
blacklist menf21bmc_wdt
blacklist nv_tco
blacklist of_xilinx_wdt
blacklist pc87413_wdt
blacklist pcwd_pci
blacklist pcwd_usb
blacklist retu_wdt
blacklist rn5t618_wdt
blacklist sbc60xxwdt
blacklist sbc_epx_c3
blacklist sbc_fitpc2_wdt
blacklist sc1200wdt
blacklist sch311x_wdt
blacklist smsc37b787_wdt
blacklist softdog
blacklist sp5100_tco
blacklist twl4030_wdt
blacklist via_wdt
blacklist w83627hf_wdt
blacklist w83877f_wdt
blacklist w83977f_wdt
blacklist wafer5823wdt
blacklist wdt_pci
blacklist wm831x_wdt
blacklist wm8350_wdt
blacklist xen_wdt
blacklist snd_mixer_oss
blacklist snd_pcm_oss
blacklist acquirewdt
blacklist advantechwdt
blacklist alim1535_wdt
blacklist alim7101_wdt
blacklist cpu5wdt
blacklist da9052_wdt
blacklist da9055_wdt
blacklist da9063_wdt
blacklist dw_wdt
blacklist eurotechwdt
blacklist f71808e_wdt
blacklist hpwdt
blacklist i6300esb
blacklist iTCO_vendor_support
blacklist iTCO_wdt
blacklist ib700wdt
blacklist ibmasr
blacklist ie6xx_wdt
blacklist it8712f_wdt
blacklist it87_wdt
blacklist kempld_wdt
blacklist machzwd
blacklist mena21_wdt
blacklist menf21bmc_wdt
blacklist nv_tco
blacklist of_xilinx_wdt
blacklist pc87413_wdt
blacklist pcwd_pci
blacklist pcwd_usb
blacklist retu_wdt
blacklist rn5t618_wdt
blacklist sbc60xxwdt
blacklist sbc_epx_c3
blacklist sbc_fitpc2_wdt
blacklist sc1200wdt
blacklist sch311x_wdt
blacklist smsc37b787_wdt
blacklist softdog
blacklist sp5100_tco
blacklist twl4030_wdt
blacklist via_wdt
blacklist w83627hf_wdt
blacklist w83877f_wdt
blacklist w83977f_wdt
blacklist wafer5823wdt
blacklist wdt_pci
blacklist wm831x_wdt
blacklist wm8350_wdt
blacklist xen_wdt
blacklist snd_mixer_oss
blacklist snd_pcm_oss
blacklist acquirewdt
blacklist advantechwdt
blacklist alim1535_wdt
blacklist alim7101_wdt
blacklist cpu5wdt
blacklist da9052_wdt
blacklist da9055_wdt
blacklist da9063_wdt
blacklist dw_wdt
blacklist eurotechwdt
blacklist f71808e_wdt
blacklist hpwdt
blacklist i6300esb
blacklist iTCO_vendor_support
blacklist iTCO_wdt
blacklist ib700wdt
blacklist ibmasr
blacklist ie6xx_wdt
blacklist it8712f_wdt
blacklist it87_wdt
blacklist kempld_wdt
blacklist machzwd
blacklist mena21_wdt
blacklist menf21bmc_wdt
blacklist nv_tco
blacklist of_xilinx_wdt
blacklist pc87413_wdt
blacklist pcwd_pci
blacklist pcwd_usb
blacklist retu_wdt
blacklist rn5t618_wdt
blacklist sbc60xxwdt
blacklist sbc_epx_c3
blacklist sbc_fitpc2_wdt
blacklist sc1200wdt
blacklist sch311x_wdt
blacklist smsc37b787_wdt
blacklist softdog
blacklist sp5100_tco
blacklist twl4030_wdt
blacklist via_wdt
blacklist w83627hf_wdt
blacklist w83877f_wdt
blacklist w83977f_wdt
blacklist wafer5823wdt
blacklist wdt_pci
blacklist wm831x_wdt
blacklist wm8350_wdt
blacklist xen_wdt
blacklist arkfb
blacklist aty128fb
blacklist atyfb
blacklist radeonfb
blacklist cirrusfb
blacklist cyber2000fb
blacklist kyrofb
blacklist matroxfb_base
blacklist mb862xxfb
blacklist neofb
blacklist pm2fb
blacklist pm3fb
blacklist s3fb
blacklist savagefb
blacklist sisfb
blacklist tdfxfb
blacklist tridentfb
blacklist vt8623fb
install sound_slot_0 /sbin/modprobe snd-card-0
install sound_slot_1 /sbin/modprobe snd-card-1
install sound_slot_2 /sbin/modprobe snd-card-2
install sound_slot_3 /sbin/modprobe snd-card-3
install sound_slot_4 /sbin/modprobe snd-card-4
install sound_slot_5 /sbin/modprobe snd-card-5
install sound_slot_6 /sbin/modprobe snd-card-6
install sound_slot_7 /sbin/modprobe snd-card-7
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
install snd_pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd_mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd_seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
install snd_rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
install snd_emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd_via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
remove iwlwifi (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) && /sbin/modprobe -r mac80211
alias net_pf_3 off
alias net_pf_6 off
alias net_pf_9 off
alias net_pf_11 off
alias net_pf_12 off
alias net_pf_19 off
alias net_pf_21 off
alias net_pf_36 off
alias wlan0 ndiswrapper
options bt87x index=-2
options cx88_alsa index=-2
options saa7134_alsa index=-2
options snd_atiixp_modem index=-2
options snd_intel8x0m index=-2
options snd_via82xx_modem index=-2
options snd_usb_audio index=-2
options snd_usb_caiaq index=-2
options snd_usb_ua101 index=-2
options snd_usb_us122l index=-2
options snd_usb_usx2y index=-2
options snd_cmipci mpu_port=0x330 fm_port=0x388
options snd_pcsp index=-2
options snd_usb_audio index=-2
options iwlwifi 11n_disable=0 amsdu_size_8K=0 bt_coex_active=N 
options vmwgfx enable_fbdev=1
options vt handoff=7
softdep mlx4_core post: mlx4_en
softdep sctp_probe pre: sctp

```

I have tried various iwlwifi options and seem to get the best result from the following (/etc/modprobe.d/iwlwifi.conf)
```
# /etc/modprobe.d/iwlwifi.conf# iwlwifi will dyamically load either iwldvm or iwlmvm depending on the
# microcode file installed on the system.  When removing iwlwifi, first
# remove the iwl?vm module and then iwlwifi.
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211
options iwlwifi 11n_disable=1
options iwlwifi wd_disable=1
options iwlwifi bt_coex_active=1 
options iwlwifi uapsd_disable=1
```

Not sure what the first lines of code there do, I did not touch them. (at least don't remember doing so).

I switched off my bluetooth in the BIOS and that did improve the stability and speed of my connection quite a bit, however not quite enough to stream HD youtube videos, for instance. However, good enough to post on this forum, for instance.
Do you think buying a seperate USB wireless adapter would be a good idea?

edit: also, right now, my wifi status is showing as 'device not ready', although my connection is working fine.

---

### Post by tgalati4 on 2015-09-14
This option should be set to 0:  options iwlwifi bt_coex_active=1  (1 means allow bluetooth and wifi at the same time--even though you have it turned off in BIOS).

You can't stream HD video using Wireless G.  Not enough bandwidth.  You need N and you need low interference from your neighbors.  Try using a cable and see if you can stream the same videos.  It could be a bandwidth issue.  If your videos can stream OK using an ethernet cable, then there is at least a chance to get wifi to work.  If your video stutters with a cable, then nothing will help your wireless bandwidth--it will always be the same or lower than your ethernet cable bandwidth.

Read the reviews on your wireless router's Wireless N capability.  Some are better than others.  It's possible that your wireless card using the Intel driver does not work well with your router.

---

### Post by RobertoRecordo on 2015-09-14
I recently got tired of my poor wi-fi performance at home and downloaded [WiFi Analyser]("http://wirelessmscresearch.blogspot.com/2012/09/wifi-analyser.html") by Kevin Yuan to my Kindle Fire .
I discovered
[LIST=1]
[*]My router was on the same channel as all the neighbours. I changed my router settings and got away from the competition. 
[*]I have dead spots in my home due to a fireplace and chimney on an interior wall 
[*]With the meter and the "Geiger counter" sound on, I was able to aim my router to substantially improve my service. 
[/LIST]


Hope it helps.

-Rob

---

### Post by tgalati4 on 2015-09-14
Yes, WiFi Analyzer is available for Android phones, a helpful tool.  Use 5 GHz band if your wireless card supports it and you are not too far from your access point.  5 GHz can't go as far at 2.4 GHz; the signal strength drops off faster.  Any metal between you and your AP will also cut down your signal.

---

### Post by hein5 on 2015-09-21
I tried changing channel on my router settings, but that did not seem to make a real difference.

What did help were the following commands:

```

sudo rmmod iwldvm
sudo modprobe iwldvm

```

After doing this, my wifi works flawlessly right now. Again it is not the signal which should be the problem, it must be some sort of (intel?) driver issue. My phone + apple TV have perfectly working wifi. I will try and see if this method gives me a consistent result.

---

### Post by tgalati4 on 2015-09-21
Sometimes reloading the wireless module will reset the card or reload the card's firmware, both of which can help with wonky wifi performance.  If it happens frequently, then perhaps your wifi card needs reseating or the antenna connection needs reseating.  Sometimes the antenna wears out--it's a thin wire that runs through the screen hinge.  How old is this laptop?

---

### Post by hein5 on 2015-09-21
It's about 1,5 years old - not old I would say. I will look into reseating and see if that helps.

---


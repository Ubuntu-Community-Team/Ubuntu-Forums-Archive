---
title: "Needing help with setting up wireless in ubuntu 11.04 64bit"
date: 2011-07-24
forum: New to Ubuntu
---

### Post by zelfaldor on 2011-07-24
I have just installed Ubuntu 11.04 64bit and it went fairly smooth, except for the fact of my wireless card was not working. My card is a Belkin F5D7000 version 4000. I have followed the instructions here: [http://ubuntuforums.org/showthread.php?t=1298275](http://ubuntuforums.org/showthread.php?t=1298275) and here: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)
to no avail. I am getting an error with the Network Connection manager in the top right corner stating that the device is not ready, that the firmware is missing. As a precaution after one set of direction did not work, I just went and did a Re-install of the os to ensure everything was back to the original settings. So my question is this, please help me get my wireless card working in Ubuntu as it does work in Windows just fine. any and all help is appreciated.

I have used ubuntu off and on several times in the past, with a wired connection. this is my First time trying a wireless connection, as I have no choice at this time about it.

---

### Post by bigpayne69 on 2011-07-24
If you can get a wired connection, you possibly just need to install updates.

---

### Post by wildmanne39 on 2011-07-24
Hi, run these commands in a terminal
```
lspci -nn | grep 0280
```
```
lsmod
```
```
iwconfig
```
```
rfkill list All
```
and post the outcome  here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by zelfaldor on 2011-07-25
results from lspci -nn | grep 0280
```
01:07.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02) 
```

results from lsmod
```
lsmod 
Module                  Size  Used by 
rtl8187                60982  0  
eeprom_93cx6           12725  1 rtl8187 
binfmt_misc            17565  1  
saa7134_alsa           18551  1  
rc_msi_tvanywhere_plus    12538  0  
ir_kbd_i2c             13272  0  
snd_intel8x0           38272  2  
snd_ac97_codec        134270  1 snd_intel8x0 
ir_lirc_codec          12898  0  
lirc_dev               19232  1 ir_lirc_codec 
ir_sony_decoder        12549  0  
ac97_bus               12730  1 snd_ac97_codec 
snd_pcm                96625  3 saa7134_alsa,snd_intel8x0,snd_ac97_codec 
ir_jvc_decoder         12546  0  
tda827x                18179  1  
snd_seq_midi           13324  0  
ir_rc6_decoder         12546  0  
tda8290                22627  1  
snd_rawmidi            30486  1 snd_seq_midi 
ir_rc5_decoder         12546  0  
tuner                  27386  1  
ir_nec_decoder         12546  0  
snd_seq_midi_event     14899  1 snd_seq_midi 
arc4                   12529  2  
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event 
nouveau               682322  2  
b43                   318638  0  
snd_timer              29602  2 snd_pcm,snd_seq 
saa7134               177094  1 saa7134_alsa 
ttm                    76664  1 nouveau 
rc_core                26918  10 rc_msi_tvanywhere_plus,ir_kbd_i2c,ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,saa7134 
drm_kms_helper         42136  1 nouveau 
v4l2_common            17647  2 tuner,saa7134 
drm                   227495  4 nouveau,ttm,drm_kms_helper 
videodev               82052  3 tuner,saa7134,v4l2_common 
i2c_algo_bit           13400  1 nouveau 
ppdev                  17113  0  
v4l2_compat_ioctl32    17078  1 videodev 
parport_pc             36959  1  
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq 
video                  19438  1 nouveau 
i2c_nforce2            13058  0  
mac80211              294370  2 rtl8187,b43 
psmouse                73535  0  
edac_core              53845  0  
videobuf_dma_sg        19307  2 saa7134_alsa,saa7134 
edac_mce_amd           23464  0  
lp                     17825  0  
parport                46458  3 ppdev,parport_pc,lp 
videobuf_core          26135  2 saa7134,videobuf_dma_sg 
tveeprom               21249  1 saa7134 
serio_raw              13166  0  
joydev                 17606  0  
snd                    67382  14 saa7134_alsa,snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
soundcore              12680  1 snd 
cfg80211              178528  3 rtl8187,b43,mac80211 
snd_page_alloc         18529  2 snd_intel8x0,snd_pcm 
k8temp                 13016  0  
usbhid                 46956  0  
hid                    91020  1 usbhid 
usb_storage            53538  0  
uas                    17996  0  
ssb                    51945  1 b43 
sata_nv                32054  0  
pata_amd               14130  2  
forcedeth              63555  0 
```

results of iwconfig
```
lo        no wireless extensions. 
 
eth0      no wireless extensions. 
 
wlan0     IEEE 802.11bg  ESSID:off/any   
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm    
          Retry  long limit:7   RTS thr:off   Fragment thr:off 
          Power Management:off 
```

and finally results of rfkill list all 
```
0: phy0: Wireless LAN 
    Soft blocked: no 
    Hard blocked: no 
```

---

### Post by linuxman94 on 2011-07-25
You must have a wired connection for this to work.

```
sudo apt-get install b43-fwcutter firmware-b43-installer
```

Once doing that, you can activate the drivers in the additional drivers utility.  Just search drivers in unity, or if you are using classic, system -> administration menu

Check this out if you don't have internet:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20No%20Internet%20access]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20No%20Internet%20access")

---

### Post by wildmanne39 on 2011-07-25
Hi, you also have this driver rtl8187 conflicting with the broadcom drivers you have installed we need to black list it. Copy this into a terminal
```
gksu gedit /etc/modprobe.d/blacklist.conf
```
and add blacklist rtl8187 and that will stop it from being loaded then save and exit. Then restart you system and see if your wireless works if not post back here, if it does mark the thread solved.

I made a mistake and corrected it.
Thank you

---

### Post by linuxman94 on 2011-07-29
If you comment out rtl8187 with a # sign it will cause it not to be backlisted.  You should just add the line "rtl8187" without quotes of course.

---


---
title: "compaq cq60 headphone jack not working"
date: 2011-04-20
forum: New to Ubuntu
---

### Post by josephmills on 2011-04-20
Hi there my headphone jack will not play any thing out of it here is some info 
[b]
File /etc/modprobe.d/alsa-base.conf
[/b]
```

 autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

 Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modpro$
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbi$
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { $
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbi$
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OP

 Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS &$
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS &$

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbi$
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-caiaq index=-2
options snd-usb-ua101 index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388

```

Here is 
[b]
cat /proc/asound/card0/codec#* | grep Codec
[/b]
```

Codec: Conexant CX20561 (Hermosa)
Codec: Nvidia MCP77/78 HDMI

```
if you want anymore info just ask thans you so much for your time 
joseph

---

### Post by mörgæs on 2011-04-20
I guess searching in this forum will help you better:
[http://ubuntuforums.org/forumdisplay.php?f=334](http://ubuntuforums.org/forumdisplay.php?f=334)

---


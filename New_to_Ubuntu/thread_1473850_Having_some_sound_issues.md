---
title: "Having some sound issues"
date: 2010-05-05
forum: New to Ubuntu
---

### Post by guitardennison on 2010-05-05
_**My setup:**_

hp dv7t quad
4 gb ram 
500 gb hd 
1 gb graphics card
half windows 7
half Ubuntu
dual boot

_**Problem:**_ 
  
  When I power off or restart Ubuntu the speakers kind of crackle and make a static noise.  Followed by the usual sub woofer pop.  I believe that I need a kernel install, but I have not heard of this specific problem.

Any ideas?

---

### Post by madjr on 2010-05-05
new kernel ?

maybe there's something here for you:
[http://ubuntuguide.org/wiki/Ubuntu:Lucid](http://ubuntuguide.org/wiki/Ubuntu:Lucid)

or try lowering your volume

---

### Post by lidex on 2010-05-05
Not a kubuntu user myself but I'm guessing similarities with gnome. Try this in a terminal and post the output:
```
cat /etc/modprobe.d/alsa-base.conf
```

---

### Post by guitardennison on 2010-05-06
> **lidex said:**
> Not a kubuntu user myself but I'm guessing similarities with gnome. Try this in a terminal and post the output:
```
cat /etc/modprobe.d/alsa-base.conf
```
sorry, wrong tag im running ubuntu 10.04 and there are the results

# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2

options snd-hda-intel model=hp-dv5
options snd-hda-intel enable_msi=1

---

### Post by guitardennison on 2010-05-07
bump.....still not working

---

### Post by cuberts on 2010-05-07
> **guitardennison said:**
> _**My setup:**_

hp dv7t quad
4 gb ram 
500 gb hd 
1 gb graphics card
half windows 7
half Ubuntu
dual boot

_**Problem:**_ 
  
  When I power off or restart Ubuntu the speakers kind of crackle and make a static noise.  Followed by the usual sub woofer pop.  I believe that I need a kernel install, but I have not heard of this specific problem.

Any ideas?I was having the same problem on Ubuntu, but ttshivers fixed my problem. It turned out that my speakers were plugged into the digital port. :)

---

### Post by guitardennison on 2010-05-09
> **cuberts said:**
> I was having the same problem on Ubuntu, but ttshivers fixed my problem. It turned out that my speakers were plugged into the digital port. :)

ttshivers? im not quite familiar with that term.  

Could it be that my volume is just set too high?

---


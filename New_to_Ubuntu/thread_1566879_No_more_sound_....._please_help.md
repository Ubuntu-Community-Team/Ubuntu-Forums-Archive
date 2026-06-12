---
title: "No more sound ..... please help"
date: 2010-09-03
forum: New to Ubuntu
---

### Post by tahitiwibble on 2010-09-03
I don't know why but I can no longer get eany sound out of my 10.04. I upgraded to the new Skype beta version and since then nothing works sound-wise ....... can anyone please help to diagnose the problem?

Many, many thanks in advance. :)

---

### Post by _0R10N on 2010-09-03
What exactly have you tried so far?. Did you look into your alsa-mixer configuration for some muted value.

---

### Post by tahitiwibble on 2010-09-03
Ooops, sorry ........... a false alarm I think, my headset seems to be shot.

Thanks for the offer of help though very much.

---

### Post by tahitiwibble on 2010-09-13
Well I bought a brand new Logitech USB headset and the same thing happens as with the old set ...... even with volume up as high as it'll go I only have the **slightest** sound output in the headset.

Could anyone suggest where to start? :)

---

### Post by sandyd on 2010-09-13
> **tahitiwibble said:**
> Well I bought a brand new Logitech USB headset and the same thing happens as with the old set ...... even with volume up as high as it'll go I only have the **slightest** sound output in the headset.

Could anyone suggest where to start? :)
run
```

alsamixer
```
in a terminal and make sure all the outputs are at their highest position

---

### Post by ezhik on 2010-09-13
It may be problem with ALSA. Try this [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

---

### Post by tahitiwibble on 2010-09-13
Hi sandyd, thanks for chipping in. I have everything where adjustments are possible set at 100% but no change ...... 

This is what it looks like 

[IMG]http://i221.photobucket.com/albums/dd79/wibble_01/Screenshot-daddad-desktop-1.png[/IMG]

---

### Post by tahitiwibble on 2010-09-13
> **ezhik said:**
> It may be problem with ALSA. Try this [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

Hi ezhik, I got to here with the howto article and don't have a clue what to do now :(

```
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
```

---

### Post by Yumi on 2010-09-14
Also have no sound but found the following solution:

Open terminal and type:
$ **pactl load-module module-detect**

then open alsamixer
adjust the soundlevel.

Thats all. It does no harm, but I have to do it every day when I switch on the system.

Michael

---

### Post by tahitiwibble on 2010-09-14
No sound anywhere any more ..... zilch ](*,)

Reinstall the whole OS ??

---

### Post by ezhik on 2010-09-14
tahitiwibble,
what does that code mean? I had problems with sound as well and specifying codec manually worked for me. But I have not seen any code like that. 
 
> **tahitiwibble said:**
> Hi ezhik, I got to here with the howto article and don't have a clue what to do now :(
 
```
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
```

---

### Post by tahitiwibble on 2010-09-14
ezkik, sorry, maybe I shouldn't have called it code. In fact it was the result in terminal to "sudo nano /etc/modprobe.d/alsa-base.conf"

and this is my sound card info

"ALC662/663/272
==============
  3stack-dig    3-stack (2-channel) with SPDIF
  3stack-6ch     3-stack (6-channel)
  3stack-6ch-dig 3-stack (6-channel) with SPDIF
  6stack-dig     6-stack with SPDIF
  lenovo-101e     Lenovo laptop
  eeepc-p701    ASUS Eeepc P701
  eeepc-ep20    ASUS Eeepc EP20
  ecs        ECS/Foxconn mobo
  m51va        ASUS M51VA
  g71v        ASUS G71V
  h13        ASUS H13
  g50v        ASUS G50V
  asus-mode1    ASUS
  asus-mode2    ASUS
  asus-mode3    ASUS
  asus-mode4    ASUS
  asus-mode5    ASUS
  asus-mode6    ASUS
  dell        Dell with ALC272
  dell-zm1    Dell ZM1 with ALC272
  samsung-nc10    Samsung NC10 mini notebook
  auto        auto-config reading BIOS (default)"

so according to the link you gave me, you think I should just add "options snd-hda-intel model=auto" to the end of that same .conf file?

---

### Post by tahitiwibble on 2010-09-14
ezhik, thanks for your message. I have found out what's going wrong .... more or less.

After messing around with alsamixer in terminal I eventually hit the F6 key and found my headset to be considered a sound card. It turns out that every time I shut the computer down the volume setting for the headset speaker goes to zero. This morning I boot up, go to terminal>alsamixer>F6>Logitech USB Headset, turn the volume up and bingo.

So if anyone can suggest why alsamixer started reducing, and is not holding the headset volume setting, this would be a great help :)

---


---
title: "no sound with two soundcards"
date: 2010-11-05
forum: New to Ubuntu
---

### Post by Sonic Reducer on 2010-11-05
i have two soundcards on my desktop, an onboard intel ICH6 and an creative audigy (which is the one i want to use with some analog 2.1 speakers)

when i look in /preferences/sound and change the default card to the audigy and test the speakers it doesn't work, i had this problem waaay back in the day (i think on ubuntu 6.06 lol) and i think i fixed it by blacklisting the onboard audio so ubuntu doesn't see it and then the other card worked.

i looked up a few commands to run in terminal for info:

```
**-desktop:~$ sudo lsmod | grep snd**
snd_emu10k1_synth       5136  0 
snd_emux_synth         29012  1 snd_emu10k1_synth
snd_seq_virmidi         4193  1 snd_emux_synth
snd_seq_midi_emul       5547  1 snd_emux_synth
snd_emu10k1           131818  2 snd_emu10k1_synth
snd_intel8x0           25632  0 
snd_ac97_codec         99227  2 snd_emu10k1,snd_intel8x0
snd_util_mem            3118  2 snd_emux_synth,snd_emu10k1
ac97_bus                1014  1 snd_ac97_codec
snd_pcm                71475  3 snd_emu10k1,snd_intel8x0,snd_ac97_codec
snd_hwdep               5040  2 snd_emux_synth,snd_emu10k1
snd_seq_midi            4588  0 
snd_rawmidi            17783  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
snd_seq_midi_event      6047  2 snd_seq_virmidi,snd_seq_midi
snd_seq                47174  5 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_midi,snd_seq_midi_event
snd_timer              19067  3 snd_emu10k1,snd_pcm,snd_seq
snd_seq_device          5744  5 snd_emu10k1_synth,snd_emu10k1,snd_seq_midi,snd_rawmidi,snd_seq
snd                    49006  13 snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_intel8x0,snd_ac97_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
snd_page_alloc          7120  3 snd_emu10k1,snd_intel8x0,snd_pcm
soundcore                880  1 snd
**-desktop:~$ lspci | grep -i audio**
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
03:01.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
```

---

### Post by cek on 2010-11-05
Can you disable the on board card in the BIOS settings?  That's usually the easiest way.

Pulse audio (and alsa for that matter) seem to have trouble picking a reliable default card -- between reboots it seems to arbitrarily pick which card will be default.  This can be mitigated, but the easiest approach if you really only need to use one card is to disable the on-board card in the BIOS.

---

### Post by tkoco on 2010-11-05
I agree that disabling one of the cards is one possibility. If you have to have both cards functional, look at ```
/etc/modprobe.d/alsa-base.conf
```
At the end of the file, you can list the unwanted card with an index of -2 which will prevent the card from being selected at boot-up time.

Hope that helps.

> **Sonic Reducer said:**
> i have two soundcards on my desktop, an onboard intel ICH6 and an creative audigy (which is the one i want to use with some analog 2.1 speakers)

when i look in /preferences/sound and change the default card to the audigy and test the speakers it doesn't work, i had this problem waaay back in the day (i think on ubuntu 6.06 lol) and i think i fixed it by blacklisting the onboard audio so ubuntu doesn't see it and then the other card worked.

i looked up a few commands to run in terminal for info:

```
**-desktop:~$ sudo lsmod | grep snd**
snd_emu10k1_synth       5136  0 
snd_emux_synth         29012  1 snd_emu10k1_synth
snd_seq_virmidi         4193  1 snd_emux_synth
snd_seq_midi_emul       5547  1 snd_emux_synth
snd_emu10k1           131818  2 snd_emu10k1_synth
snd_intel8x0           25632  0 
snd_ac97_codec         99227  2 snd_emu10k1,snd_intel8x0
snd_util_mem            3118  2 snd_emux_synth,snd_emu10k1
ac97_bus                1014  1 snd_ac97_codec
snd_pcm                71475  3 snd_emu10k1,snd_intel8x0,snd_ac97_codec
snd_hwdep               5040  2 snd_emux_synth,snd_emu10k1
snd_seq_midi            4588  0 
snd_rawmidi            17783  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
snd_seq_midi_event      6047  2 snd_seq_virmidi,snd_seq_midi
snd_seq                47174  5 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_midi,snd_seq_midi_event
snd_timer              19067  3 snd_emu10k1,snd_pcm,snd_seq
snd_seq_device          5744  5 snd_emu10k1_synth,snd_emu10k1,snd_seq_midi,snd_rawmidi,snd_seq
snd                    49006  13 snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_intel8x0,snd_ac97_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
snd_page_alloc          7120  3 snd_emu10k1,snd_intel8x0,snd_pcm
soundcore                880  1 snd
**-desktop:~$ lspci | grep -i audio**
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
03:01.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
```

---

### Post by Sonic Reducer on 2010-11-09
> **tkoco said:**
> I agree that disabling one of the cards is one possibility. If you have to have both cards functional, look at ```
/etc/modprobe.d/alsa-base.conf
```
At the end of the file, you can list the unwanted card with an index of -2 which will prevent the card from being selected at boot-up time.

so i would add this to the end of **alsa-base.conf**?
```
options snd_intel8x0 index=-2
```

if i disable the "snd_intel" will it disable everything, or should i add others too?

i'm almost sure i cannot disable the onboard audio in my BIOS, but before i do any file editing i'm going to reboot and poke around in the BIOS to make sure

.:**EDIT**:. there was an option for disabling the onboard audio in the BIOS, i disabled it but it hasn't made a difference. unless you count "now theres only one card listed in sound preferences" as a difference (still doesnt work though). i have ruled out any hardware problems, because i can boot into windows 7 and audio works beautifully

here's my **alsa-base.conf** (i haven't changed anything yet)
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
options snd-usb-caiaq index=-2
options snd-usb-ua101 index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2
```

---


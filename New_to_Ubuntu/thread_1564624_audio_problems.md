---
title: "audio problems"
date: 2010-08-30
forum: New to Ubuntu
---

### Post by ornothaloapq on 2010-08-30
i have a netbook running ubuntu 10.04 and for some reason when i plug in my headphones and try to listen it  just sounds extremely staticesque. is this a hardware problem or a software problem that could maybe be helped?

---

### Post by jtarin on 2010-08-30
Enter this command in a terminal and post the output ```
cat /etc/modprobe.d/alsa-base.conf
```

---

### Post by ornothaloapq on 2010-08-30
this is what came up from that line of code  " cat /etc/modprobe.d/alsa-base.conf # autoloader aliases install sound-slot-0 /sbin/modprobe snd-card-0 install sound-slot-1 /sbin/modprobe snd-card-1 install sound-slot-2 /sbin/modprobe snd-card-2 install sound-slot-3 /sbin/modprobe snd-card-3 install sound-slot-4 /sbin/modprobe snd-card-4 install sound-slot-5 /sbin/modprobe snd-card-5 install sound-slot-6 /sbin/modprobe snd-card-6 install sound-slot-7 /sbin/modprobe snd-card-7  # Cause optional modules to be loaded above generic modules install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; } # # Workaround at bug #499695 (reverted in Ubuntu see LP #319505) install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; } install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; } install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; } # install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; } # Cause optional modules to be loaded above sound card driver modules install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; } install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }  # Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway) install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; } # Prevent abnormal drivers from grabbing index 0 options bt87x index=-2 options cx88_alsa index=-2 options saa7134-alsa index=-2 options snd-atiixp-modem index=-2 options snd-intel8x0m index=-2 options snd-via82xx-modem index=-2 options snd-usb-audio index=-2 options snd-usb-us122l index=-2 options snd-usb-usx2y index=-2 options snd-usb-caiaq index=-2 # Ubuntu #62691, enable MPU for snd-cmipci options snd-cmipci mpu_port=0x330 fm_port=0x388 # Keep snd-pcsp from being loaded as first soundcard options snd-pcsp index=-2

---

### Post by jtarin on 2010-08-30
Edit your post and wrap it in [code] tags. It's almost unreadable the way you have it.I need to see it as you see it.

---

### Post by ornothaloapq on 2010-08-30
sorry ill try again.   [cat /etc/modprobe.d/alsa-base.conf # autoloader aliases install sound-slot-0 /sbin/modprobe snd-card-0 install sound-slot-1 /sbin/modprobe snd-card-1 install sound-slot-2 /sbin/modprobe snd-card-2 install sound-slot-3 /sbin/modprobe snd-card-3 install sound-slot-4 /sbin/modprobe snd-card-4 install sound-slot-5 /sbin/modprobe snd-card-5 install sound-slot-6 /sbin/modprobe snd-card-6 install sound-slot-7 /sbin/modprobe snd-card-7 # Cause optional modules to be loaded above generic modules install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; } # # Workaround at bug #499695 (reverted in Ubuntu see LP #319505) install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS &&  { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; } install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; } install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; } # install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; } # Cause optional modules to be loaded above sound card driver modules install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; } install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; } # Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway) install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; } # Prevent abnormal drivers from grabbing index 0 options bt87x index=-2 options cx88_alsa index=-2 options saa7134-alsa index=-2 options snd-atiixp-modem index=-2 options snd-intel8x0m index=-2 options snd-via82xx-modem index=-2 options snd-usb-audio index=-2 options snd-usb-us122l index=-2 options snd-usb-usx2y index=-2 options snd-usb-caiaq index=-2 # Ubuntu #62691, enable MPU for snd-cmipci options snd-cmipci mpu_port=0x330 fm_port=0x388 # Keep snd-pcsp from being loaded as first soundcard options snd-pcsp index=-2 ]

---

### Post by ornothaloapq on 2010-08-30
hang on still need to find out what code tags are

---

### Post by ornothaloapq on 2010-08-30
here i go again  ```
 cat /etc/modprobe.d/alsa-base.conf # autoloader aliases install sound-slot-0 /sbin/modprobe snd-card-0 install sound-slot-1 /sbin/modprobe snd-card-1 install sound-slot-2 /sbin/modprobe snd-card-2 install sound-slot-3 /sbin/modprobe snd-card-3 install sound-slot-4 /sbin/modprobe snd-card-4 install sound-slot-5 /sbin/modprobe snd-card-5 install sound-slot-6 /sbin/modprobe snd-card-6 install sound-slot-7 /sbin/modprobe snd-card-7  # Cause optional modules to be loaded above generic modules install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; } # # Workaround at bug #499695 (reverted in Ubuntu see LP #319505) install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; } install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; } install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; } # install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; } # Cause optional modules to be loaded above sound card driver modules install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; } install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }  # Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway) install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; } # Prevent abnormal drivers from grabbing index 0 options bt87x index=-2 options cx88_alsa index=-2 options saa7134-alsa index=-2 options snd-atiixp-modem index=-2 options snd-intel8x0m index=-2 options snd-via82xx-modem index=-2 options snd-usb-audio index=-2 options snd-usb-us122l index=-2 options snd-usb-usx2y index=-2 options snd-usb-caiaq index=-2 # Ubuntu #62691, enable MPU for snd-cmipci options snd-cmipci mpu_port=0x330 fm_port=0x388 # Keep snd-pcsp from being loaded as first soundcard options snd-pcsp index=-2  
```

---

### Post by ornothaloapq on 2010-08-30
is that readable or should i try something else? thanks for your help with the inital command anyhow.

---

### Post by jtarin on 2010-08-31
Don't make an additional post...edit what you have posted already. Here's what mine looks like....when I copy from the terminal and paste between "#" code tags.```
cat /etc/modprobe.d/alsa-base.conf 
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

### Post by jtarin on 2010-08-31
Make you terminal not so wide on your desktop. 
Lets pretend I can read that and its OK. enter the command ```
lsmod
``` in the terminal and post the output as it is viewed by you in the terminal.

---

### Post by jtarin on 2010-08-31
Now the command ```
lspci
``` and post.

---

### Post by jtarin on 2010-08-31
Are you running Compiz? (Desktop Effects)

---

### Post by ornothaloapq on 2010-08-31
ok here is the lsmod code  ```
 # Module                  Size  Used by xt_limit                1382  8  xt_tcpudp               2011  10  nls_iso8859_1           3249  1  nls_cp437               4919  1  vfat                    8933  1  fat                    47767  1 vfat ipt_LOG                 4542  8  ipt_MASQUERADE          1407  0  xt_DSCP                 1677  0  ipt_REJECT              1928  1  nf_conntrack_irc        3332  0  nf_conntrack_ftp        5381  0  xt_state                1098  6  binfmt_misc             6587  1  ppdev                   5259  0  snd_hda_codec_realtek   203310  1  snd_hda_intel          21941  1  snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel snd_hwdep               5412  1 snd_hda_codec iptable_nat             4414  0  joydev                  8708  0  snd_pcm_oss            35308  0  nf_nat                 15735  2 ipt_MASQUERADE,iptable_nat snd_mixer_oss          13746  1 snd_pcm_oss nf_conntrack_ipv4      10672  9 iptable_nat,nf_nat snd_pcm                70662  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss nf_conntrack           61583  7 ipt_MASQUERADE,nf_conntrack_irc,nf_conntrack_ftp,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4 nf_defrag_ipv4          1073  1 nf_conntrack_ipv4 iptable_mangle          2771  0  snd_seq_dummy           1338  0  fbcon                  35102  71  tileblit                2031  1 fbcon font                    7557  1 fbcon snd_seq_oss            26726  0  bitblit                 4707  1 fbcon softcursor              1189  1 bitblit arc4                    1153  2  iptable_filter          2271  1  snd_seq_midi            4557  0  vga16fb                11385  0  vgastate                8961  1 vga16fb ip_tables               9991  3 iptable_nat,iptable_mangle,iptable_filter snd_rawmidi            19056  1 snd_seq_midi x_tables               14299  9 xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,xt_DSCP,ipt_REJECT,xt_state,iptable_nat,ip_tables snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event snd_timer              19098  2 snd_pcm,snd_seq snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq ath5k                 121792  0  snd                    54148  14 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device i915                  285076  3  mac80211              205146  1 ath5k ath                     7611  1 ath5k uvcvideo               56990  0  drm_kms_helper         29297  1 i915 psmouse                63245  0  soundcore               6620  1 snd videodev               34361  1 uvcvideo drm                   162409  4 i915,drm_kms_helper serio_raw               3978  0  cfg80211              126517  3 ath5k,mac80211,ath v4l1_compat            13251  2 uvcvideo,videodev led_class               2864  1 ath5k snd_page_alloc          7076  2 snd_hda_intel,snd_pcm intel_agp              24119  2 i915 atl1c                  28083  0  agpgart                31724  2 drm,intel_agp i2c_algo_bit            5028  1 i915 video                  17375  1 i915 output                  1871  1 video lp                      7028  0  parport                32635  2 ppdev,lp ahci                   32200  2  usb_storage            39425  1  # 
```

---

### Post by jtarin on 2010-08-31
Do you have your terminal set to a wide width? Here is my lsmod with the terminal set to half the height and half the width of my monitor.Can you edit your post above until it looks as mine does...please?```
Module                  Size  Used by
xt_TCPMSS               2931  1 
xt_tcpmss               1197  1 
xt_tcpudp               2011  1 
iptable_mangle          2771  1 
ip_tables               9991  1 iptable_mangle
x_tables               14299  4 xt_TCPMSS,xt_tcpmss,xt_tcpudp,ip_tables
pppoe                   8943  2 
pppox                   2074  1 pppoe
binfmt_misc             6587  1 
snd_hda_codec_realtek   203168  1 
fbcon                  35102  72 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
snd_hda_intel          21877  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
i915                  282354  3 
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ppdev                   5259  0 
drm_kms_helper         29297  1 i915
usb_storage            39425  3 
snd                    54148  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm                   162471  4 i915,drm_kms_helper
parport_pc             25962  1 
psmouse                63245  0 
serio_raw               3978  0 
intel_agp              24177  2 i915
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
i2c_algo_bit            5028  1 i915
video                  17375  1 i915
output                  1871  1 video
agpgart                31724  2 drm,intel_agp
lp                      7028  0 
parport                32635  3 ppdev,parport_pc,lp
r8169                  33884  0 
mii                     4381  1 r8169

```

---

### Post by ornothaloapq on 2010-08-31
lsmod  ```
 # Module                  Size  Used by xt_limit                1382  8  xt_tcpudp               2011  10  ipt_LOG                 4542  8  ipt_MASQUERADE          1407  0  xt_DSCP                 1677  0  ipt_REJECT              1928  1  nf_conntrack_irc        3332  0  nf_conntrack_ftp        5381  0  xt_state                1098  6  nls_iso8859_1           3249  1  nls_cp437               4919  1  vfat                    8933  1  fat                    47767  1 vfat binfmt_misc             6587  1  ppdev                   5259  0  snd_hda_codec_realtek   203310  1  iptable_nat             4414  0  nf_nat                 15735  2 ipt_MASQUERADE,iptable_nat nf_conntrack_ipv4      10672  9 iptable_nat,nf_nat fbcon                  35102  71  tileblit                2031  1 fbcon font                    7557  1 fbcon bitblit                 4707  1 fbcon softcursor              1189  1 bitblit vga16fb                11385  0  vgastate                8961  1 vga16fb nf_conntrack           61583  7 ipt_MASQUERADE,nf_conntrack_irc,nf_conntrack_ftp,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4 nf_defrag_ipv4          1073  1 nf_conntrack_ipv4 iptable_mangle          2771  0  iptable_filter          2271  1  ip_tables               9991  3 iptable_nat,iptable_mangle,iptable_filter arc4                    1153  2  joydev                  8708  0  snd_hda_intel          21941  1  x_tables               14299  9 xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,xt_DSCP,ipt_REJECT,xt_state,iptable_nat,ip_tables snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel snd_hwdep               5412  1 snd_hda_codec snd_pcm_oss            35308  0  snd_mixer_oss          13746  1 snd_pcm_oss snd_pcm                70662  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss snd_seq_dummy           1338  0  snd_seq_oss            26726  0  snd_seq_midi            4557  0  snd_rawmidi            19056  1 snd_seq_midi snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event snd_timer              19098  2 snd_pcm,snd_seq ath5k                 121792  0  snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq i915                  285076  3  uvcvideo               56990  0  mac80211              205146  1 ath5k ath                     7611  1 ath5k drm_kms_helper         29297  1 i915 snd                    54148  14 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device cfg80211              126517  3 ath5k,mac80211,ath drm                   162409  4 i915,drm_kms_helper videodev               34361  1 uvcvideo v4l1_compat            13251  2 uvcvideo,videodev psmouse                63245  0  serio_raw               3978  0  atl1c                  28083  0  led_class               2864  1 ath5k soundcore               6620  1 snd snd_page_alloc          7076  2 snd_hda_intel,snd_pcm intel_agp              24119  2 i915 agpgart                31724  2 drm,intel_agp i2c_algo_bit            5028  1 i915 video                  17375  1 i915 output                  1871  1 video lp                      7028  0  parport                32635  2 ppdev,lp ahci                   32200  2  usb_storage            39425  1    
```

---

### Post by ornothaloapq on 2010-08-31
my terminal height was already like the dimensions you said  the second lsmod post is the same as the first, i posted it by mistake. when i paste it into this message window it looks good, and yet when i submit reply it makes it ultra skinny.

---

### Post by jtarin on 2010-08-31
> **ornothaloapq said:**
> my terminal height was already like the dimensions you said  the second lsmod post is the same as the first, i posted it by mistake. when i paste it into this message window it looks good, and yet when i submit reply it makes it ultra skinny.
When I ask you to edit a post it means go back to the post I am reffering to and click on the edit button. When the dialog opens look at the bottom and if there is an advanced tab....click it. It will take you to another dialog window where you can edit/post whatever....it has additionla features. Before posting do a preview to see if your satisfied with how it looks...if yes hit submit. Now I want you to edit your last post with code in it. Remove everying and then post the results from the terminal of ```
lsmod |grep snd 
```
Don't repost the same mistaken post.....just reedit if its not satisfactory.Remember to use Go Advanced and preview.

---


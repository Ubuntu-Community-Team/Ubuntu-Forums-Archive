---
title: "How do I create a suspend Log?"
date: 2011-04-19
forum: New to Ubuntu
---

### Post by Zanderist on 2011-04-19
I want to see what commands my laptop runs while it suspends in ubuntu so I can troubleshoot why I can't resume from suspend.

This didn't work for me;
> 
SUSPEND_MODULES="xhci-hcd"


[http://ubuntuforums.org/showthread.php?t=1614891&page=2](http://ubuntuforums.org/showthread.php?t=1614891&page=2)

I have a Hp pavilion dv6.

---

### Post by mikewhatever on 2011-04-22
There is a suspend log - /var/log/pm-suspend.log.

---

### Post by Zanderist on 2011-04-23
```
Sat Apr 23 00:52:46 EDT 2011: performing suspend
Allocated buffer at 0x11000 (base is 0x0)
ES: 0x1100 EBX: 0x0000
``````
Sun Apr  3 07:28:49 EDT 2011: performing suspend
Allocated buffer at 0x11000 (base is 0x0)
ES: 0x1100 EBX: 0x0000
Initial commandline parameters: 

``````
Tue Apr 19 14:41:03 EDT 2011: performing suspend
Allocated buffer at 0x11000 (base is 0x0)
ES: 0x1100 EBX: 0x0000
Initial commandline parameters: 
Tue Apr 19 14:45:38 EDT 2011: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux ubuntu 2.6.35-28-generic #50-Ubuntu SMP Fri Mar 18 18:42:20 UTC 2011 x86_64 GNU/Linux
Module                  Size  Used by
nls_iso8859_1           4657  2 
nls_cp437               6375  2 
vfat                   10954  2 
fat                    56244  1 vfat
binfmt_misc             7984  1 
parport_pc             30086  0 
ppdev                   6804  0 
snd_hda_codec_atihdmi     3079  1 
snd_hda_codec_idt      64699  1 
uvcvideo               62379  0 
videodev               49359  1 uvcvideo
arc4                    1497  2 
v4l1_compat            15519  2 uvcvideo,videodev
v4l2_compat_ioctl32    12614  1 videodev
snd_seq_midi            5932  0 
snd_hda_intel          26147  3 
snd_rawmidi            22207  1 snd_seq_midi
snd_hda_codec         100951  3 snd_hda_codec_atihdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep               6660  1 snd_hda_codec
snd_seq_midi_event      7291  1 snd_seq_midi
ath9k                 101858  0 
snd_pcm                89104  3 snd_hda_intel,snd_hda_codec
snd_seq                57512  2 snd_seq_midi,snd_seq_midi_event
joydev                 11395  0 
ath9k_common            6874  1 ath9k
ath9k_hw              314731  2 ath9k,ath9k_common
ath                    10413  2 ath9k,ath9k_hw
snd_timer              23850  2 snd_pcm,snd_seq
mac80211              267099  2 ath9k,ath9k_common
snd_seq_device          6912  3 snd_seq_midi,snd_rawmidi,snd_seq
hp_wmi                  6467  0 
cfg80211              170485  4 ath9k,ath9k_common,ath,mac80211
snd                    64181  14 snd_hda_codec_idt,snd_rawmidi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_seq,snd_timer,snd_seq_device
psmouse                62080  0 
edac_core              46822  0 
hp_accel               14304  0 
lis3lv02d              10384  1 hp_accel
input_polldev           4527  1 lis3lv02d
shpchp                 34910  0 
serio_raw               4910  0 
i2c_piix4              10047  0 
k10temp                 3535  0 
edac_mce_amd            9387  0 
led_class               3393  2 ath9k,hp_accel
soundcore               1240  1 snd
snd_page_alloc          8588  2 snd_hda_intel,snd_pcm
lp                     10201  0 
parport                37032  3 parport_pc,ppdev,lp
uvesafb                25058  1 
usbhid                 42030  0 
hid                    84710  1 usbhid
usb_storage            50436  2 
radeon                909939  2 
ttm                    68212  1 radeon
drm_kms_helper         32836  1 radeon
drm                   206198  5 radeon,ttm,drm_kms_helper
video                  22176  0 
output                  2527  1 video
i2c_algo_bit            6208  1 radeon
r8169                  42254  0 
mii                     5261  1 r8169
ahci                   22210  3 
libahci                26148  1 ahci
             total       used       free     shared    buffers     cached
Mem:       3794884    1011004    2783880          0     114488     296220
-/+ buffers/cache:     600296    3194588
Swap:      4358140          0    4358140

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/44bluetooth-known-quirk suspend suspend:

/usr/lib/pm-utils/sleep.d/44bluetooth-known-quirk suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/45bluetooth-service suspend suspend:

/usr/lib/pm-utils/sleep.d/45bluetooth-service suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:

/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...method return sender=:1.3 -> dest=:1.62 reply_serial=2
Done.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/70action_wpa suspend suspend:

/usr/lib/pm-utils/sleep.d/70action_wpa suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
Unloading kernel module xhci-hcd...Done.

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Using last known working set of quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
```

---


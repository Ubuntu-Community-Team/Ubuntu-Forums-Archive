---
title: "A mode like Windows XP's &quot;Stand By&quot;?"
date: 2010-07-04
forum: New to Ubuntu
---

### Post by juggleclown on 2010-07-04
Hello. I've been using Ubuntu on and off for a long time. With each release, I find less and less problems (back in 2008, I had to spend weeks just to discover how to get it to display correctly on my Thinkpad, but Lucid works perfectly on it, and it even works out of the box with my wifi USB adapter).

But, nevermind that. This question pertains to the desktop computer I'm using now. I've learned a good amount since 2008, much more familiar with the terminal commands (I was already very familiar with ms-dos command lines, using them for batch files and mass-renaming, so it didn't take too much learning, especially after I discovered 'man'), but, you know, to be frank, it's no secret that I'm a dense, knuckle-headed moron.

Well, in Windows XP, whenever I'm not using my computer for a few minutes, instead of shutting it down I like to click "stand by". My computer's fans come to a halt, and it's in a state where, according to my kill-a-watt, it goes from running at 130+ watts to a mere 40.

In the power menu for Ubuntu, I notice there's a "suspend" command. I expected this to do something similar. Well, the wattage dies down for a split second, almost like stand by, but the screen turns back on immediately and shows the password screen. I tried installing hibernate through apt-get, which was even less what I wanted. It displays a bunch of messages, like it's backing something up, restarts the computer, spends more time than usual trying to load whatever it was trying to save, and loads up Ubuntu like it normally would. I would've expected a hibernate function to load up whatever was running at the time, but I guess not. >_>


So, is there an option like the "Stand By" in Windows XP? I like putting it into a powersave mode for when I step away, rather than shutting it down every time, or letting it waste electricity for no good reason. I'll admit, I can't move away from XP entirely. I have both XP and Ubuntu on here, because I like to play computer games a lot, and Wine doesn't quite fill that niche satisfactorily. However, being able to go into "stand by" in Ubuntu would be another great reason not to boot into XP. ;)

---

### Post by J V on 2010-07-04
That would be suspend... perhaps you can check the logs (In administration) to see why it isn't working... As for hibernate, it does work as expected, but it's very slow on ubuntu, not worth it.

---

### Post by juggleclown on 2010-07-05
To be honest, I have no idea what I'm looking for in the logs. I checked pm-suspend.log, and this is what it says:


```
Initial commandline parameters: 
Thu Jul  1 22:36:39 MST 2010: Running hooks for suspend.
/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:success.
/usr/lib/pm-utils/sleep.d/00logging suspend suspend:Linux grant-desktop 2.6.32-23-generic-pae #37-Ubuntu SMP Fri Jun 11 09:26:55 UTC 2010 i686 GNU/Linux
Module                  Size  Used by
nls_iso8859_1           3249  1 
nls_cp437               4919  1 
vfat                    8933  1 
fat                    47767  1 vfat
binfmt_misc             6587  1 
ppdev                   5259  0 
snd_intel8x0           25588  2 
snd_ac97_codec        100646  1 snd_intel8x0
ac97_bus                1002  1 snd_ac97_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70886  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
w83627hf               21388  0 
hwmon_vid               2298  1 w83627hf
fbcon                  35102  71 
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
nvidia               9962496  38 
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
tileblit                2031  1 fbcon
snd_timer              19098  2 snd_pcm,snd_seq
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
vga16fb                11385  1 
vgastate                8961  1 vga16fb
snd                    54148  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                63245  0 
soundcore               6620  1 snd
intel_agp              24415  1 
snd_page_alloc          7172  2 snd_intel8x0,snd_pcm
shpchp                 28884  0 
serio_raw               3978  0 
joydev                  8708  0 
lp                      7028  0 
agpgart                31788  2 nvidia,intel_agp
parport                32635  2 ppdev,lp
hid_pl                  2427  0 
ff_memless              4093  1 hid_pl
usbhid                 36174  1 hid_pl
hid                    67032  2 hid_pl,usbhid
e100                   28563  0 
mii                     4381  1 e100
usb_storage            39457  1 
floppy                 53080  0 
             total       used       free     shared    buffers     cached
Mem:       2060508     524396    1536112          0      57304     216824
-/+ buffers/cache:     250268    1810240
Swap:            0          0          0
success.
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend:success.
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:success.
/etc/pm/sleep.d/10_grub-common suspend suspend:success.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:success.
/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:success.
/usr/lib/pm-utils/sleep.d/75modules suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/90clock suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:success.
/usr/lib/pm-utils/sleep.d/95anacron suspend suspend:stop: Unknown instance: 
success.
/usr/lib/pm-utils/sleep.d/95led suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/95packagekit suspend suspend:success.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:success.
/usr/lib/pm-utils/sleep.d/99video suspend suspend:kernel.acpi_video_flags = 0
success.
/etc/pm/sleep.d/action_wpa suspend suspend:success.
Thu Jul  1 22:36:41 MST 2010: performing suspend
Thu Jul  1 22:36:51 MST 2010: Awake.
Thu Jul  1 22:36:51 MST 2010: Running hooks for resume
/etc/pm/sleep.d/action_wpa resume suspend:success.
/usr/lib/pm-utils/sleep.d/99video resume suspend:success.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:success.
/usr/lib/pm-utils/sleep.d/95packagekit resume suspend:method return sender=:1.56 -> dest=:1.55 reply_serial=2
success.
/usr/lib/pm-utils/sleep.d/95led resume suspend:not applicable.
/usr/lib/pm-utils/sleep.d/95anacron resume suspend:success.
/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:success.
/usr/lib/pm-utils/sleep.d/90clock resume suspend:not applicable.
/usr/lib/pm-utils/sleep.d/75modules resume suspend:success.
/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:success.
/usr/lib/pm-utils/sleep.d/49bluetooth resume suspend:not applicable.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:success.
/etc/pm/sleep.d/10_grub-common resume suspend:success.
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend:success.
/usr/lib/pm-utils/sleep.d/00powersave resume suspend:success.
/usr/lib/pm-utils/sleep.d/00logging resume suspend:success.
/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:success.
Thu Jul  1 22:36:52 MST 2010: Finished.
Initial commandline parameters: 
Thu Jul  1 23:48:54 MST 2010: Running hooks for suspend.
/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:success.
/usr/lib/pm-utils/sleep.d/00logging suspend suspend:Linux grant-desktop 2.6.32-23-generic-pae #37-Ubuntu SMP Fri Jun 11 09:26:55 UTC 2010 i686 GNU/Linux
Module                  Size  Used by
nls_iso8859_1           3249  1 
nls_cp437               4919  1 
vfat                    8933  1 
fat                    47767  1 vfat
binfmt_misc             6587  1 
ppdev                   5259  0 
snd_intel8x0           25588  2 
snd_ac97_codec        100646  1 snd_intel8x0
ac97_bus                1002  1 snd_ac97_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70886  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
w83627hf               21388  0 
hwmon_vid               2298  1 w83627hf
fbcon                  35102  71 
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
nvidia               9962496  42 
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
tileblit                2031  1 fbcon
snd_timer              19098  2 snd_pcm,snd_seq
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
vga16fb                11385  1 
vgastate                8961  1 vga16fb
snd                    54148  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                63245  0 
soundcore               6620  1 snd
intel_agp              24415  1 
snd_page_alloc          7172  2 snd_intel8x0,snd_pcm
shpchp                 28884  0 
serio_raw               3978  0 
joydev                  8708  0 
lp                      7028  0 
agpgart                31788  2 nvidia,intel_agp
parport                32635  2 ppdev,lp
hid_pl                  2427  0 
ff_memless              4093  1 hid_pl
usbhid                 36174  1 hid_pl
hid                    67032  2 hid_pl,usbhid
e100                   28563  0 
mii                     4381  1 e100
usb_storage            39457  1 
floppy                 53080  0 
             total       used       free     shared    buffers     cached
Mem:       2060508     775972    1284536          0      63072     336376
-/+ buffers/cache:     376524    1683984
Swap:            0          0          0
success.
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend:success.
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:success.
/etc/pm/sleep.d/10_grub-common suspend suspend:success.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:success.
/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:success.
/usr/lib/pm-utils/sleep.d/75modules suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/90clock suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:success.
/usr/lib/pm-utils/sleep.d/95anacron suspend suspend:stop: Unknown instance: 
success.
/usr/lib/pm-utils/sleep.d/95led suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/95packagekit suspend suspend:success.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:success.
/usr/lib/pm-utils/sleep.d/99video suspend suspend:kernel.acpi_video_flags = 0
success.
/etc/pm/sleep.d/action_wpa suspend suspend:success.
Thu Jul  1 23:48:55 MST 2010: performing suspend
Thu Jul  1 23:49:05 MST 2010: Awake.
Thu Jul  1 23:49:05 MST 2010: Running hooks for resume
/etc/pm/sleep.d/action_wpa resume suspend:success.
/usr/lib/pm-utils/sleep.d/99video resume suspend:success.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:success.
/usr/lib/pm-utils/sleep.d/95packagekit resume suspend:method return sender=:1.78 -> dest=:1.77 reply_serial=2
success.
/usr/lib/pm-utils/sleep.d/95led resume suspend:not applicable.
/usr/lib/pm-utils/sleep.d/95anacron resume suspend:success.
/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:success.
/usr/lib/pm-utils/sleep.d/90clock resume suspend:not applicable.
/usr/lib/pm-utils/sleep.d/75modules resume suspend:success.
/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:success.
/usr/lib/pm-utils/sleep.d/49bluetooth resume suspend:not applicable.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:success.
/etc/pm/sleep.d/10_grub-common resume suspend:success.
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend:success.
/usr/lib/pm-utils/sleep.d/00powersave resume suspend:success.
/usr/lib/pm-utils/sleep.d/00logging resume suspend:success.
/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:success.
Thu Jul  1 23:49:07 MST 2010: Finished.
Initial commandline parameters: 
Fri Jul  2 00:08:16 MST 2010: Running hooks for suspend.
/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:success.
/usr/lib/pm-utils/sleep.d/00logging suspend suspend:Linux grant-desktop 2.6.32-23-generic-pae #37-Ubuntu SMP Fri Jun 11 09:26:55 UTC 2010 i686 GNU/Linux
Module                  Size  Used by
nls_iso8859_1           3249  1 
nls_cp437               4919  1 
vfat                    8933  1 
fat                    47767  1 vfat
binfmt_misc             6587  1 
ppdev                   5259  0 
snd_intel8x0           25588  2 
snd_ac97_codec        100646  1 snd_intel8x0
ac97_bus                1002  1 snd_ac97_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70886  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
w83627hf               21388  0 
hwmon_vid               2298  1 w83627hf
fbcon                  35102  71 
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
nvidia               9962496  42 
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
tileblit                2031  1 fbcon
snd_timer              19098  2 snd_pcm,snd_seq
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
vga16fb                11385  1 
vgastate                8961  1 vga16fb
snd                    54148  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                63245  0 
soundcore               6620  1 snd
intel_agp              24415  1 
snd_page_alloc          7172  2 snd_intel8x0,snd_pcm
shpchp                 28884  0 
serio_raw               3978  0 
joydev                  8708  0 
lp                      7028  0 
agpgart                31788  2 nvidia,intel_agp
parport                32635  2 ppdev,lp
hid_pl                  2427  0 
ff_memless              4093  1 hid_pl
usbhid                 36174  1 hid_pl
hid                    67032  2 hid_pl,usbhid
e100                   28563  0 
mii                     4381  1 e100
usb_storage            39457  1 
floppy                 53080  0 
             total       used       free     shared    buffers     cached
Mem:       2060508     783236    1277272          0      63564     336888
-/+ buffers/cache:     382784    1677724
Swap:            0          0          0
success.
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend:success.
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:success.
/etc/pm/sleep.d/10_grub-common suspend suspend:success.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:success.
/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:success.
/usr/lib/pm-utils/sleep.d/75modules suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/90clock suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:success.
/usr/lib/pm-utils/sleep.d/95anacron suspend suspend:success.
/usr/lib/pm-utils/sleep.d/95led suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/95packagekit suspend suspend:success.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:success.
/usr/lib/pm-utils/sleep.d/99video suspend suspend:kernel.acpi_video_flags = 0
success.
/etc/pm/sleep.d/action_wpa suspend suspend:success.
Fri Jul  2 00:08:17 MST 2010: performing suspend
Fri Jul  2 00:08:27 MST 2010: Awake.
Fri Jul  2 00:08:27 MST 2010: Running hooks for resume
/etc/pm/sleep.d/action_wpa resume suspend:success.
/usr/lib/pm-utils/sleep.d/99video resume suspend:success.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:success.
/usr/lib/pm-utils/sleep.d/95packagekit resume suspend:method return sender=:1.98 -> dest=:1.97 reply_serial=2
success.
/usr/lib/pm-utils/sleep.d/95led resume suspend:not applicable.
/usr/lib/pm-utils/sleep.d/95anacron resume suspend:success.
/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:success.
/usr/lib/pm-utils/sleep.d/90clock resume suspend:not applicable.
/usr/lib/pm-utils/sleep.d/75modules resume suspend:success.
/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:success.
/usr/lib/pm-utils/sleep.d/49bluetooth resume suspend:not applicable.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:success.
/etc/pm/sleep.d/10_grub-common resume suspend:success.
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend:success.
/usr/lib/pm-utils/sleep.d/00powersave resume suspend:success.
/usr/lib/pm-utils/sleep.d/00logging resume suspend:success.
/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:success.
Fri Jul  2 00:08:29 MST 2010: Finished.
Initial commandline parameters: 
Sun Jul  4 11:50:49 MST 2010: Running hooks for suspend.
/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:success.
/usr/lib/pm-utils/sleep.d/00logging suspend suspend:Linux grant-desktop 2.6.32-23-generic-pae #37-Ubuntu SMP Fri Jun 11 09:26:55 UTC 2010 i686 GNU/Linux
Module                  Size  Used by
nls_utf8                1069  0 
isofs                  29250  0 
btrfs                 458938  0 
zlib_deflate           19568  1 btrfs
crc32c                  2519  1 
libcrc32c                875  1 btrfs
ufs                    72774  0 
qnx4                    6484  0 
hfsplus                70800  0 
hfs                    40754  0 
minix                  25197  0 
ntfs                   94919  0 
vfat                    8933  0 
msdos                   6392  0 
fat                    47767  2 vfat,msdos
jfs                   172682  0 
xfs                   515324  0 
exportfs                3437  1 xfs
reiserfs              225539  0 
binfmt_misc             6587  1 
ppdev                   5259  0 
vboxnetadp              6390  0 
vboxnetflt             12740  0 
vboxdrv               169169  2 vboxnetadp,vboxnetflt
snd_intel8x0           25588  3 
snd_ac97_codec        100646  1 snd_intel8x0
ac97_bus                1002  1 snd_ac97_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70886  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
w83627hf               21388  0 
hwmon_vid               2298  1 w83627hf
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
snd                    54148  15 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
nvidia               9962496  38 
vga16fb                11385  1 
vgastate                8961  1 vga16fb
intel_agp              24415  1 
psmouse                63245  0 
soundcore               6620  1 snd
joydev                  8708  0 
serio_raw               3978  0 
lp                      7028  0 
snd_page_alloc          7172  2 snd_intel8x0,snd_pcm
shpchp                 28884  0 
agpgart                31788  2 nvidia,intel_agp
parport                32635  2 ppdev,lp
hid_pl                  2427  0 
ff_memless              4093  1 hid_pl
usbhid                 36174  1 hid_pl
hid                    67032  2 hid_pl,usbhid
floppy                 53080  0 
e100                   28563  0 
mii                     4381  1 e100
             total       used       free     shared    buffers     cached
Mem:       2060508    1625868     434640          0     104828    1109844
-/+ buffers/cache:     411196    1649312
Swap:            0          0          0
success.
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend:success.
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:success.
/etc/pm/sleep.d/10_grub-common suspend suspend:success.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:success.
/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:success.
/usr/lib/pm-utils/sleep.d/75modules suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/90clock suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:success.
/usr/lib/pm-utils/sleep.d/95anacron suspend suspend:stop: Unknown instance: 
success.
/usr/lib/pm-utils/sleep.d/95led suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/95packagekit suspend suspend:success.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:success.
/usr/lib/pm-utils/sleep.d/99video suspend suspend:kernel.acpi_video_flags = 0
success.
/etc/pm/sleep.d/action_wpa suspend suspend:success.
Sun Jul  4 11:50:52 MST 2010: performing suspend
Sun Jul  4 11:51:03 MST 2010: Awake.
Sun Jul  4 11:51:03 MST 2010: Running hooks for resume
/etc/pm/sleep.d/action_wpa resume suspend:success.
/usr/lib/pm-utils/sleep.d/99video resume suspend:success.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:success.
/usr/lib/pm-utils/sleep.d/95packagekit resume suspend:method return sender=:1.65 -> dest=:1.64 reply_serial=2
success.
/usr/lib/pm-utils/sleep.d/95led resume suspend:not applicable.
/usr/lib/pm-utils/sleep.d/95anacron resume suspend:success.
/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:success.
/usr/lib/pm-utils/sleep.d/90clock resume suspend:not applicable.
/usr/lib/pm-utils/sleep.d/75modules resume suspend:success.
/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:success.
/usr/lib/pm-utils/sleep.d/49bluetooth resume suspend:not applicable.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:success.
/etc/pm/sleep.d/10_grub-common resume suspend:success.
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend:success.
/usr/lib/pm-utils/sleep.d/00powersave resume suspend:success.
/usr/lib/pm-utils/sleep.d/00logging resume suspend:success.
/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:success.
Sun Jul  4 11:51:05 MST 2010: Finished.
Initial commandline parameters: 
Mon Jul  5 09:28:11 MST 2010: Running hooks for suspend.
/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:success.
/usr/lib/pm-utils/sleep.d/00logging suspend suspend:Linux grant-desktop 2.6.32-23-generic-pae #37-Ubuntu SMP Fri Jun 11 09:26:55 UTC 2010 i686 GNU/Linux
Module                  Size  Used by
binfmt_misc             6587  1 
ppdev                   5259  0 
vboxnetadp              6390  0 
vboxnetflt             12740  0 
vboxdrv               169169  2 vboxnetadp,vboxnetflt
snd_intel8x0           25588  2 
snd_ac97_codec        100646  1 snd_intel8x0
ac97_bus                1002  1 snd_ac97_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70886  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
joydev                  8708  0 
w83627hf               21388  0 
hwmon_vid               2298  1 w83627hf
nvidia               9962496  38 
snd                    54148  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                63245  0 
serio_raw               3978  0 
intel_agp              24415  1 
soundcore               6620  1 snd
snd_page_alloc          7172  2 snd_intel8x0,snd_pcm
vga16fb                11385  1 
vgastate                8961  1 vga16fb
agpgart                31788  2 nvidia,intel_agp
shpchp                 28884  0 
lp                      7028  0 
parport                32635  2 ppdev,lp
hid_pl                  2427  0 
ff_memless              4093  1 hid_pl
usbhid                 36174  1 hid_pl
hid                    67032  2 hid_pl,usbhid
e100                   28563  0 
floppy                 53080  0 
mii                     4381  1 e100
             total       used       free     shared    buffers     cached
Mem:       2060508     618988    1441520          0      60272     239604
-/+ buffers/cache:     319112    1741396
Swap:            0          0          0
success.
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend:success.
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:success.
/etc/pm/sleep.d/10_grub-common suspend suspend:success.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:success.
/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:success.
/usr/lib/pm-utils/sleep.d/75modules suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/90clock suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:success.
/usr/lib/pm-utils/sleep.d/95anacron suspend suspend:success.
/usr/lib/pm-utils/sleep.d/95led suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/95packagekit suspend suspend:success.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:success.
/usr/lib/pm-utils/sleep.d/99video suspend suspend:kernel.acpi_video_flags = 0
success.
/etc/pm/sleep.d/action_wpa suspend suspend:success.
Mon Jul  5 09:28:15 MST 2010: performing suspend
Mon Jul  5 09:28:27 MST 2010: Awake.
Mon Jul  5 09:28:27 MST 2010: Running hooks for resume
/etc/pm/sleep.d/action_wpa resume suspend:success.
/usr/lib/pm-utils/sleep.d/99video resume suspend:success.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:success.
/usr/lib/pm-utils/sleep.d/95packagekit resume suspend:method return sender=:1.56 -> dest=:1.55 reply_serial=2
success.
/usr/lib/pm-utils/sleep.d/95led resume suspend:not applicable.
/usr/lib/pm-utils/sleep.d/95anacron resume suspend:success.
/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:success.
/usr/lib/pm-utils/sleep.d/90clock resume suspend:not applicable.
/usr/lib/pm-utils/sleep.d/75modules resume suspend:success.
/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:success.
/usr/lib/pm-utils/sleep.d/49bluetooth resume suspend:not applicable.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:success.
/etc/pm/sleep.d/10_grub-common resume suspend:success.
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend:success.
/usr/lib/pm-utils/sleep.d/00powersave resume suspend:success.
/usr/lib/pm-utils/sleep.d/00logging resume suspend:success.
/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:success.
Mon Jul  5 09:28:29 MST 2010: Finished.
```


The only thing of interest I can see without understanding any of this is the part that says:

```
Mon Jul  5 09:28:15 MST 2010: performing suspend
Mon Jul  5 09:28:27 MST 2010: Awake.
```


I didn't press anything, I didn't move the mouse. It just turns black, the light on the monitor turns orange (meaning there's no output), I don't hear the fans turn off or anything, and the screen immediately turns back on and shows the password screen.

I found it suspicious that a "suspend" feature would just take you to the password screen. I guess it's not supposed to do this after all, huh?



I remember in Windows XP, I had a problem just like this. I would put it into standby, and in a minute it'd just go back to the desktop again. Most of the information I found on the matter suggested people to go into their bios and disable 'wake on lan'. However, my bios has no such feature. Eventually, I was told of an option, that at this point I don't even remember anymore, as some sort of setting in Windows that disabled 'wake on lan', which allows the system to go into stand by and stay like that until I press a key or click the mouse.

Well, that's all I really know. Hopefully you guys can figure out more from that. If you need hardware information, I can get that too. On that note, I've never been entirely sure what the best way of gathering all my hardware information in Ubuntu, much less any other distro, is. Sorry.

---


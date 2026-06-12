---
title: "installing Sabrent Philips7130 PCI TV Tuner/Video capture card in 10.04"
date: 2010-05-13
forum: New to Ubuntu
---

### Post by pdlethbridge on 2010-05-13
How does one get to enjoy TV on his computer if the card won't install in 10.04?
I have used the following method with success in 9.04 but it didn't work with 9.10 either.
The instructions were in this post.
[http://ubuntuforums.org/showthread.php?t=927234&highlight=sabrent+video+card](http://ubuntuforums.org/showthread.php?t=927234&highlight=sabrent+video+card)

sudo nano /etc/modprobe.d/saa7134        hit enter
next you will be asked for your password enter and press the enter key.

now in the nano editor, type the following lines pressing enter at the end of each one.

alias chr-major-81 videodev       enter
alias chr-major-81-0 saa7134      enter
options saa7134 card=42 tuner=43 oss=1       enter

now press the control key (ctrl) and the "x" key at the same time
you will be asked if you want to save file: saa7134 
say yes by pressing "y" key on the keyboard.
reboot and it will work

---

### Post by ukripper on 2010-05-13
plug in the card and in terminal run below commands then post output here.
```
dmesg | tail
```

```
ls -al /dev/vid*
```

```
lsmod
```

```
tail -n 100 /var/log/messages
```

---

### Post by pdlethbridge on 2010-05-13
sorry, new 10.04 cd wouldn't install at all. I had tried the upgrade method and it wouldn't work then. I had expected to try and get it working on a fresh install of 10.04, but it constantly gave me an error 5. Must be a bad cd, as I was able to reinstall 9.04 without problems

---

### Post by pdlethbridge on 2010-05-14
I managed to install 10.04 by putting it on ext 4, not my usual ext 2. I don't know why that worked, but it did! I also tried to change the kernel, but that was a waste of time. I'll do a reinstall tomorrow and try to give you that info. thanks, Paul

---

### Post by pdlethbridge on 2010-05-15
here is what you asked for, I just reinstalled 10.04 but did not add this
sudo nano /etc/modprobe.d/saa7134        hit enter
next you will be asked for your password enter and press the enter key.

now in the nano editor, type the following lines pressing enter at the end of each one.

alias chr-major-81 videodev       enter
alias chr-major-81-0 saa7134      enter
options saa7134 card=42 tuner=43 oss=1       enter

now press the control key (ctrl) and the "x" key at the same time
you will be asked if you want to save file: saa7134 
say yes by pressing "y" key on the keyboard.


pdleth@pdleth-desktop:~$ dmesg | tail
[ 3020.974239] SGI XFS Quota Management subsystem
[ 3021.013388] JFS: nTxBlock = 8018, nTxLock = 64149
[ 3021.096422] NTFS driver 2.1.29 [Flags: R/O MODULE].
[ 3021.147268] QNX4 filesystem 0.2.3 registered.
[ 3021.235111] Btrfs loaded
[ 3076.489889] type=1505 audit(1273900258.470:15):  operation="profile_replace" pid=8573 name="/usr/lib/cups/backend/cups-pdf"
[ 3076.490647] type=1505 audit(1273900258.470:16):  operation="profile_replace" pid=8573 name="/usr/sbin/cupsd"
[ 3107.169616] type=1505 audit(1273900289.150:17):  operation="profile_replace" pid=8691 name="/usr/bin/evince"
[ 3107.172233] type=1505 audit(1273900289.154:18):  operation="profile_replace" pid=8691 name="/usr/bin/evince-previewer"
[ 3107.174235] type=1505 audit(1273900289.154:19):  operation="profile_replace" pid=8691 name="/usr/bin/evince-thumbnailer"
pdleth@pdleth-desktop:~$ ls -al /dev/vid*
crw-rw----+ 1 root video 81, 0 2010-05-15 02:02 /dev/video0
pdleth@pdleth-desktop:~$ lsmod
Module                  Size  Used by
btrfs                 458906  0 
zlib_deflate           19568  1 btrfs
crc32c                  2519  1 
libcrc32c                875  1 btrfs
ufs                    72774  0 
qnx4                    6484  0 
hfsplus                70800  0 
hfs                    40754  0 
minix                  25197  0 
ntfs                   94791  0 
msdos                   6392  0 
jfs                   172650  0 
xfs                   513904  0 
exportfs                3437  1 xfs
reiserfs              225633  0 
nls_iso8859_1           3249  1 
nls_cp437               4919  1 
vfat                    8901  1 
fat                    47767  2 msdos,vfat
binfmt_misc             6587  1 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
snd_intel8x0           25588  2 
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
snd_ac97_codec        100646  1 snd_intel8x0
ac97_bus                1002  1 snd_ac97_codec
vga16fb                11385  0 
vgastate                8961  1 vga16fb
saa7134_alsa           10380  0 
snd_seq_dummy           1338  0 
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_seq_oss            26726  0 
snd_pcm                70662  4 snd_intel8x0,snd_ac97_codec,saa7134_alsa,snd_pcm_oss
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
saa7134               143391  1 saa7134_alsa
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
ir_common              38875  1 saa7134
nouveau               467048  2 
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
v4l2_common            15431  1 saa7134
videodev               34361  2 saa7134,v4l2_common
ttm                    49943  1 nouveau
v4l1_compat            13251  1 videodev
snd                    54148  15 snd_intel8x0,snd_ac97_codec,saa7134_alsa,snd_pcm_oss,snd_mixer_oss,snd_seq_oss,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
videobuf_dma_sg        10782  2 saa7134_alsa,saa7134
drm_kms_helper         29297  1 nouveau
intel_agp              24177  1 
soundcore               6620  1 snd
videobuf_core          16356  2 saa7134,videobuf_dma_sg
tveeprom               11102  1 saa7134
drm                   162471  4 nouveau,ttm,drm_kms_helper
i2c_algo_bit            5028  1 nouveau
agpgart                31724  3 ttm,intel_agp,drm
snd_page_alloc          7076  2 snd_intel8x0,snd_pcm
shpchp                 28820  0 
ppdev                   5259  0 
psmouse                63245  0 
serio_raw               3978  0 
parport_pc             25962  1 
lp                      7028  0 
parport                32635  3 ppdev,parport_pc,lp
floppy                 53016  0 
r8169                  33884  0 
mii                     4381  1 r8169
pdleth@pdleth-desktop:~$ tail -n 100 /var/log/messages
May 15 00:19:51 pdleth-desktop kernel: [    9.962426] r8169: eth0: link up
May 15 00:19:51 pdleth-desktop kernel: [    9.965822] type=1505 audit(1273897191.946:14):  operation="profile_load" pid=933 name="/usr/sbin/tcpdump"
May 15 00:19:58 pdleth-desktop kernel: [   16.650515] [drm] nouveau 0000:01:00.0: Allocating FIFO number 1
May 15 00:19:58 pdleth-desktop kernel: [   16.652389] [drm] nouveau 0000:01:00.0: nouveau_channel_alloc: initialised FIFO 1
May 15 00:20:08 pdleth-desktop pulseaudio[1291]: ratelimit.c: 3 events suppressed
May 15 00:20:15 pdleth-desktop pulseaudio[1291]: ratelimit.c: 7 events suppressed
May 15 00:23:37 pdleth-desktop kernel: [  235.530121] nvidia: module license 'NVIDIA' taints kernel.
May 15 00:23:37 pdleth-desktop kernel: [  235.530128] Disabling lock debugging due to kernel taint
May 15 00:23:38 pdleth-desktop kernel: [  236.220175] NVRM: The NVIDIA probe routine was not called for 1 device(s).
May 15 00:23:38 pdleth-desktop kernel: [  236.220183] NVRM: This can occur when a driver such as rivafb, nvidiafb or
May 15 00:23:38 pdleth-desktop kernel: [  236.220187] NVRM: rivatv was loaded and obtained ownership of the NVIDIA
May 15 00:23:38 pdleth-desktop kernel: [  236.220190] NVRM: device(s).
May 15 00:23:38 pdleth-desktop kernel: [  236.220196] NVRM: Try unloading the rivafb, nvidiafb or rivatv kernel module
May 15 00:23:38 pdleth-desktop kernel: [  236.220198] NVRM: (and/or reconfigure your kernel without rivafb/nvidiafb
May 15 00:23:38 pdleth-desktop kernel: [  236.220200] NVRM: support), then try loading the NVIDIA kernel module again.
May 15 00:23:38 pdleth-desktop kernel: [  236.220205] NVRM: No NVIDIA graphics adapter probed!
May 15 01:10:02 pdleth-desktop kernel: [ 3020.970108] SGI XFS with ACLs, security attributes, realtime, large block/inode numbers, no debug enabled
May 15 01:10:02 pdleth-desktop kernel: [ 3020.974239] SGI XFS Quota Management subsystem
May 15 01:10:02 pdleth-desktop kernel: [ 3021.013388] JFS: nTxBlock = 8018, nTxLock = 64149
May 15 01:10:03 pdleth-desktop kernel: [ 3021.096422] NTFS driver 2.1.29 [Flags: R/O MODULE].
May 15 01:10:03 pdleth-desktop kernel: [ 3021.147268] QNX4 filesystem 0.2.3 registered.
May 15 01:10:03 pdleth-desktop kernel: [ 3021.235111] Btrfs loaded
May 15 01:10:03 pdleth-desktop os-prober: debug: running /usr/lib/os-probes/mounted/10freedos on mounted /dev/sda2
May 15 01:10:03 pdleth-desktop 10freedos: debug: /dev/sda2 is not a FAT partition: exiting
May 15 01:10:03 pdleth-desktop os-prober: debug: running /usr/lib/os-probes/mounted/10qnx on mounted /dev/sda2
May 15 01:10:03 pdleth-desktop 10qnx: debug: /dev/sda2 is not a QNX4 partition: exiting
May 15 01:10:03 pdleth-desktop os-prober: debug: running /usr/lib/os-probes/mounted/20macosx on mounted /dev/sda2
May 15 01:10:03 pdleth-desktop macosx-prober: debug: /dev/sda2 is not an HFS+ partition: exiting
May 15 01:10:03 pdleth-desktop os-prober: debug: running /usr/lib/os-probes/mounted/20microsoft on mounted /dev/sda2
May 15 01:10:03 pdleth-desktop 20microsoft: debug: /dev/sda2 is not a MS partition: exiting
May 15 01:10:03 pdleth-desktop os-prober: debug: running /usr/lib/os-probes/mounted/30utility on mounted /dev/sda2
May 15 01:10:03 pdleth-desktop 30utility: debug: /dev/sda2 is not a FAT partition: exiting
May 15 01:10:03 pdleth-desktop os-prober: debug: running /usr/lib/os-probes/mounted/40lsb on mounted /dev/sda2
May 15 01:10:03 pdleth-desktop os-prober: debug: running /usr/lib/os-probes/mounted/70hurd on mounted /dev/sda2
May 15 01:10:03 pdleth-desktop os-prober: debug: running /usr/lib/os-probes/mounted/80minix on mounted /dev/sda2
May 15 01:10:03 pdleth-desktop os-prober: debug: running /usr/lib/os-probes/mounted/90linux-distro on mounted /dev/sda2
May 15 01:10:03 pdleth-desktop os-prober: debug: running /usr/lib/os-probes/mounted/90solaris on mounted /dev/sda2
May 15 01:10:03 pdleth-desktop os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda3
May 15 01:10:03 pdleth-desktop 50mounted-tests: debug: /dev/sda3 type not recognised; skipping
May 15 01:10:03 pdleth-desktop os-prober: debug: os detected by /usr/lib/os-probes/50mounted-tests
May 15 01:10:03 pdleth-desktop os-prober: debug: running /usr/lib/os-probes/mounted/10freedos on mounted /dev/sda4
May 15 01:10:03 pdleth-desktop 10freedos: debug: /dev/sda4 is a FAT32 partition
May 15 01:10:03 pdleth-desktop os-prober: debug: running /usr/lib/os-probes/mounted/10qnx on mounted /dev/sda4
May 15 01:10:03 pdleth-desktop 10qnx: debug: /dev/sda4 is not a QNX4 partition: exiting
May 15 01:10:03 pdleth-desktop os-prober: debug: running /usr/lib/os-probes/mounted/20macosx on mounted /dev/sda4
May 15 01:10:03 pdleth-desktop macosx-prober: debug: /dev/sda4 is not an HFS+ partition: exiting
May 15 01:10:03 pdleth-desktop os-prober: debug: running /usr/lib/os-probes/mounted/20microsoft on mounted /dev/sda4
May 15 01:10:03 pdleth-desktop 20microsoft: debug: /dev/sda4 is a FAT32 partition
May 15 01:10:03 pdleth-desktop os-prober: debug: running /usr/lib/os-probes/mounted/30utility on mounted /dev/sda4
May 15 01:10:03 pdleth-desktop 30utility: debug: /dev/sda4 is a FAT32 partition
May 15 01:10:03 pdleth-desktop os-prober: debug: running /usr/lib/os-probes/mounted/40lsb on mounted /dev/sda4
May 15 01:10:03 pdleth-desktop os-prober: debug: running /usr/lib/os-probes/mounted/70hurd on mounted /dev/sda4
May 15 01:10:03 pdleth-desktop os-prober: debug: running /usr/lib/os-probes/mounted/80minix on mounted /dev/sda4
May 15 01:10:03 pdleth-desktop os-prober: debug: running /usr/lib/os-probes/mounted/90linux-distro on mounted /dev/sda4
May 15 01:10:03 pdleth-desktop os-prober: debug: running /usr/lib/os-probes/mounted/90solaris on mounted /dev/sda4
May 15 01:10:03 pdleth-desktop os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda5
May 15 01:10:03 pdleth-desktop 50mounted-tests: debug: /dev/sda5 is a swap partition; skipping
May 15 01:10:03 pdleth-desktop os-prober: debug: os detected by /usr/lib/os-probes/50mounted-tests
May 15 01:10:04 pdleth-desktop dkms_autoinstaller: nvidia-173 (173.14.22): Installing module on kernel 2.6.32-22-generic.
May 15 01:10:58 pdleth-desktop kernel: [ 3076.489889] type=1505 audit(1273900258.470:15):  operation="profile_replace" pid=8573 name="/usr/lib/cups/backend/cups-pdf"
May 15 01:10:58 pdleth-desktop kernel: [ 3076.490647] type=1505 audit(1273900258.470:16):  operation="profile_replace" pid=8573 name="/usr/sbin/cupsd"
May 15 01:11:29 pdleth-desktop kernel: [ 3107.169616] type=1505 audit(1273900289.150:17):  operation="profile_replace" pid=8691 name="/usr/bin/evince"
May 15 01:11:29 pdleth-desktop kernel: [ 3107.172233] type=1505 audit(1273900289.154:18):  operation="profile_replace" pid=8691 name="/usr/bin/evince-previewer"
May 15 01:11:29 pdleth-desktop kernel: [ 3107.174235] type=1505 audit(1273900289.154:19):  operation="profile_replace" pid=8691 name="/usr/bin/evince-thumbnailer"
May 15 01:11:54 pdleth-desktop os-prober: debug: running /usr/lib/os-probes/mounted/10freedos on mounted /dev/sda2
May 15 01:11:54 pdleth-desktop 10freedos: debug: /dev/sda2 is not a FAT partition: exiting
May 15 01:11:54 pdleth-desktop os-prober: debug: running /usr/lib/os-probes/mounted/10qnx on mounted /dev/sda2
May 15 01:11:54 pdleth-desktop 10qnx: debug: /dev/sda2 is not a QNX4 partition: exiting
May 15 01:11:54 pdleth-desktop os-prober: debug: running /usr/lib/os-probes/mounted/20macosx on mounted /dev/sda2
May 15 01:11:54 pdleth-desktop macosx-prober: debug: /dev/sda2 is not an HFS+ partition: exiting
May 15 01:11:54 pdleth-desktop os-prober: debug: running /usr/lib/os-probes/mounted/20microsoft on mounted /dev/sda2
May 15 01:11:54 pdleth-desktop 20microsoft: debug: /dev/sda2 is not a MS partition: exiting
May 15 01:11:54 pdleth-desktop os-prober: debug: running /usr/lib/os-probes/mounted/30utility on mounted /dev/sda2
May 15 01:11:54 pdleth-desktop 30utility: debug: /dev/sda2 is not a FAT partition: exiting
May 15 01:11:54 pdleth-desktop os-prober: debug: running /usr/lib/os-probes/mounted/40lsb on mounted /dev/sda2
May 15 01:11:54 pdleth-desktop os-prober: debug: running /usr/lib/os-probes/mounted/70hurd on mounted /dev/sda2
May 15 01:11:54 pdleth-desktop os-prober: debug: running /usr/lib/os-probes/mounted/80minix on mounted /dev/sda2
May 15 01:11:54 pdleth-desktop os-prober: debug: running /usr/lib/os-probes/mounted/90linux-distro on mounted /dev/sda2
May 15 01:11:54 pdleth-desktop os-prober: debug: running /usr/lib/os-probes/mounted/90solaris on mounted /dev/sda2
May 15 01:11:54 pdleth-desktop os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda3
May 15 01:11:54 pdleth-desktop 50mounted-tests: debug: /dev/sda3 type not recognised; skipping
May 15 01:11:54 pdleth-desktop os-prober: debug: os detected by /usr/lib/os-probes/50mounted-tests
May 15 01:11:54 pdleth-desktop os-prober: debug: running /usr/lib/os-probes/mounted/10freedos on mounted /dev/sda4
May 15 01:11:55 pdleth-desktop 10freedos: debug: /dev/sda4 is a FAT32 partition
May 15 01:11:55 pdleth-desktop os-prober: debug: running /usr/lib/os-probes/mounted/10qnx on mounted /dev/sda4
May 15 01:11:55 pdleth-desktop 10qnx: debug: /dev/sda4 is not a QNX4 partition: exiting
May 15 01:11:55 pdleth-desktop os-prober: debug: running /usr/lib/os-probes/mounted/20macosx on mounted /dev/sda4
May 15 01:11:55 pdleth-desktop macosx-prober: debug: /dev/sda4 is not an HFS+ partition: exiting
May 15 01:11:55 pdleth-desktop os-prober: debug: running /usr/lib/os-probes/mounted/20microsoft on mounted /dev/sda4
May 15 01:11:55 pdleth-desktop 20microsoft: debug: /dev/sda4 is a FAT32 partition
May 15 01:11:55 pdleth-desktop os-prober: debug: running /usr/lib/os-probes/mounted/30utility on mounted /dev/sda4
May 15 01:11:55 pdleth-desktop 30utility: debug: /dev/sda4 is a FAT32 partition
May 15 01:11:55 pdleth-desktop os-prober: debug: running /usr/lib/os-probes/mounted/40lsb on mounted /dev/sda4
May 15 01:11:55 pdleth-desktop os-prober: debug: running /usr/lib/os-probes/mounted/70hurd on mounted /dev/sda4
May 15 01:11:55 pdleth-desktop os-prober: debug: running /usr/lib/os-probes/mounted/80minix on mounted /dev/sda4
May 15 01:11:55 pdleth-desktop os-prober: debug: running /usr/lib/os-probes/mounted/90linux-distro on mounted /dev/sda4
May 15 01:11:55 pdleth-desktop os-prober: debug: running /usr/lib/os-probes/mounted/90solaris on mounted /dev/sda4
May 15 01:11:55 pdleth-desktop os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda5
May 15 01:11:55 pdleth-desktop 50mounted-tests: debug: /dev/sda5 is a swap partition; skipping
May 15 01:11:55 pdleth-desktop os-prober: debug: os detected by /usr/lib/os-probes/50mounted-tests
pdleth@pdleth-desktop:~$

---

### Post by pdlethbridge on 2010-05-15
bump

---

### Post by Mze on 2010-05-15
[SAA7130 TV tuner card under Linux. How To.]("http://sites.google.com/site/jobinau2/saa7130basedtvtunercardunderlinux")

---

### Post by pdlethbridge on 2010-05-15
I think that might be over my head.

---

### Post by pdlethbridge on 2010-05-15
This is the code after I tried that small code install
pdleth@pdleth-desktop:~$ dmesg | tail
[   15.040231] type=1505 audit(1273933847.022:10):  operation="profile_load" pid=696 name="/usr/bin/evince-previewer"
[   15.065266] type=1505 audit(1273933847.046:11):  operation="profile_load" pid=696 name="/usr/bin/evince-thumbnailer"
[   16.327430] agpgart-intel 0000:00:00.0: AGP 3.0 bridge
[   16.327481] agpgart-intel 0000:00:00.0: putting AGP V3 device into 8x mode
[   16.327566] nvidia 0000:01:00.0: putting AGP V3 device into 8x mode
[   25.812024] eth0: no IPv6 routers present
[   53.672357] end_request: I/O error, dev fd0, sector 0
[   65.849594] end_request: I/O error, dev fd0, sector 0
[   70.843565] __ratelimit: 9 callbacks suppressed
[   70.843576] tvtime[1345]: segfault at 6b0 ip 0804d824 sp bfec0bcc error 4 in tvtime[8048000+76000]
pdleth@pdleth-desktop:~$ ls -al /dev/vid*
ls: cannot access /dev/vid*: No such file or directory
pdleth@pdleth-desktop:~$ lsmod
Module                  Size  Used by
binfmt_misc             6587  1 
snd_intel8x0           25588  2 
snd_ac97_codec        100646  1 snd_intel8x0
ac97_bus                1002  1 snd_ac97_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ir_common              38875  0 
v4l2_common            15431  0 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
ppdev                   5259  0 
snd                    54148  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
videodev               34361  1 v4l2_common
v4l1_compat            13251  1 videodev
videobuf_dma_sg        10782  0 
nvidia               7087672  24 
vga16fb                11385  1 
soundcore               6620  1 snd
parport_pc             25962  1 
vgastate                8961  1 vga16fb
videobuf_core          16356  1 videobuf_dma_sg
tveeprom               11102  0 
psmouse                63245  0 
serio_raw               3978  0 
snd_page_alloc          7076  2 snd_intel8x0,snd_pcm
intel_agp              24177  1 
agpgart                31724  2 nvidia,intel_agp
shpchp                 28820  0 
lp                      7028  0 
parport                32635  3 ppdev,parport_pc,lp
r8169                  33884  0 
floppy                 53016  0 
mii                     4381  1 r8169
pdleth@pdleth-desktop:~$ tail -n 100 /var/log/messages
May 15 10:30:46 pdleth-desktop kernel: [    0.512755] device-mapper: uevent: version 1.0.3
May 15 10:30:46 pdleth-desktop kernel: [    0.513045] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
May 15 10:30:46 pdleth-desktop kernel: [    0.513174] device-mapper: multipath: version 1.1.0 loaded
May 15 10:30:46 pdleth-desktop kernel: [    0.513180] device-mapper: multipath round-robin: version 1.0.0 loaded
May 15 10:30:46 pdleth-desktop kernel: [    0.513389] EISA: Probing bus 0 at eisa.0
May 15 10:30:46 pdleth-desktop kernel: [    0.513436] EISA: Detected 0 cards.
May 15 10:30:46 pdleth-desktop kernel: [    0.513581] cpuidle: using governor ladder
May 15 10:30:46 pdleth-desktop kernel: [    0.513586] cpuidle: using governor menu
May 15 10:30:46 pdleth-desktop kernel: [    0.514555] TCP cubic registered
May 15 10:30:46 pdleth-desktop kernel: [    0.514804] NET: Registered protocol family 10
May 15 10:30:46 pdleth-desktop kernel: [    0.515807] lo: Disabled Privacy Extensions
May 15 10:30:46 pdleth-desktop kernel: [    0.516534] NET: Registered protocol family 17
May 15 10:30:46 pdleth-desktop kernel: [    0.516631] Using IPI No-Shortcut mode
May 15 10:30:46 pdleth-desktop kernel: [    0.516821] registered taskstats version 1
May 15 10:30:46 pdleth-desktop kernel: [    0.517152]   Magic number: 10:83:536
May 15 10:30:46 pdleth-desktop kernel: [    0.517179] bdi 1:14: hash matches
May 15 10:30:46 pdleth-desktop kernel: [    0.517271] rtc_cmos 00:04: setting system clock to 2010-05-15 14:30:32 UTC (1273933832)
May 15 10:30:46 pdleth-desktop kernel: [    0.517277] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
May 15 10:30:46 pdleth-desktop kernel: [    0.517280] EDD information not available.
May 15 10:30:46 pdleth-desktop kernel: [    0.530309] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
May 15 10:30:46 pdleth-desktop kernel: [    0.610711] ata1.00: ATAPI: LITE-ON DVDRW SOHW-1693S, KS04, max UDMA/66
May 15 10:30:46 pdleth-desktop kernel: [    0.610772] ata1.01: ATAPI: Hewlett-Packard CD-Writer Plus 9500b, 1.04, max MWDMA2
May 15 10:30:46 pdleth-desktop kernel: [    0.623713] ata1.00: configured for UDMA/66
May 15 10:30:46 pdleth-desktop kernel: [    0.639751] ata1.01: configured for MWDMA2
May 15 10:30:46 pdleth-desktop kernel: [    0.659692] ata4.00: ATA-7: WDC WD800JD-55MUA1, 10.01E01, max UDMA/133
May 15 10:30:46 pdleth-desktop kernel: [    0.659697] ata4.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 0/32)
May 15 10:30:46 pdleth-desktop kernel: [    0.667272] isapnp: No Plug & Play device found
May 15 10:30:46 pdleth-desktop kernel: [    0.667795] ata4.00: configured for UDMA/133
May 15 10:30:46 pdleth-desktop kernel: [    0.668332] scsi 0:0:0:0: CD-ROM            LITE-ON  DVDRW SOHW-1693S KS04 PQ: 0 ANSI: 5
May 15 10:30:46 pdleth-desktop kernel: [    0.672408] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
May 15 10:30:46 pdleth-desktop kernel: [    0.672413] Uniform CD-ROM driver Revision: 3.20
May 15 10:30:46 pdleth-desktop kernel: [    0.672676] sr 0:0:0:0: Attached scsi generic sg0 type 5
May 15 10:30:46 pdleth-desktop kernel: [    0.676319] scsi 0:0:1:0: CD-ROM            HP       CD-Writer+ 9500b 1.04 PQ: 0 ANSI: 5
May 15 10:30:46 pdleth-desktop kernel: [    0.682095] sr1: scsi3-mmc drive: 24x/32x writer cd/rw xa/form2 cdda tray
May 15 10:30:46 pdleth-desktop kernel: [    0.682318] sr 0:0:1:0: Attached scsi generic sg1 type 5
May 15 10:30:46 pdleth-desktop kernel: [    0.682511] scsi 3:0:0:0: Direct-Access     ATA      WDC WD800JD-55MU 10.0 PQ: 0 ANSI: 5
May 15 10:30:46 pdleth-desktop kernel: [    0.682724] sd 3:0:0:0: [sda] 156301488 512-byte logical blocks: (80.0 GB/74.5 GiB)
May 15 10:30:46 pdleth-desktop kernel: [    0.682752] sd 3:0:0:0: Attached scsi generic sg2 type 0
May 15 10:30:46 pdleth-desktop kernel: [    0.682846] sd 3:0:0:0: [sda] Write Protect is off
May 15 10:30:46 pdleth-desktop kernel: [    0.682908] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May 15 10:30:46 pdleth-desktop kernel: [    0.683149]  sda: sda1 sda2 sda3 < sda5 > sda4
May 15 10:30:46 pdleth-desktop kernel: [    0.732136] sd 3:0:0:0: [sda] Attached SCSI disk
May 15 10:30:46 pdleth-desktop kernel: [    0.732159] Freeing unused kernel memory: 656k freed
May 15 10:30:46 pdleth-desktop kernel: [    0.733134] Write protecting the kernel text: 4676k
May 15 10:30:46 pdleth-desktop kernel: [    0.733215] Write protecting the kernel read-only data: 1840k
May 15 10:30:46 pdleth-desktop kernel: [    0.767585] udev: starting version 151
May 15 10:30:46 pdleth-desktop kernel: [    1.042766] Floppy drive(s): fd0 is 1.44M
May 15 10:30:46 pdleth-desktop kernel: [    1.055433] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
May 15 10:30:46 pdleth-desktop kernel: [    1.055495] r8169 0000:02:06.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
May 15 10:30:46 pdleth-desktop kernel: [    1.055541] r8169 0000:02:06.0: no PCI Express capability
May 15 10:30:46 pdleth-desktop kernel: [    1.057053] eth0: RTL8110s at 0xf806ab00, 00:13:d3:64:9e:a7, XID 04000000 IRQ 20
May 15 10:30:46 pdleth-desktop kernel: [    1.063876] FDC 0 is a post-1991 82077
May 15 10:30:46 pdleth-desktop kernel: [    1.139557] usb 5-1: new full speed USB device using uhci_hcd and address 2
May 15 10:30:46 pdleth-desktop kernel: [    1.318046] usb 5-1: configuration #1 chosen from 1 choice
May 15 10:30:46 pdleth-desktop kernel: [    1.539702] EXT4-fs (sda1): mounted filesystem with ordered data mode
May 15 10:30:46 pdleth-desktop kernel: [    9.666154] udev: starting version 151
May 15 10:30:46 pdleth-desktop kernel: [    9.676161] Adding 2867560k swap on /dev/sda5.  Priority:-1 extents:1 across:2867560k 
May 15 10:30:46 pdleth-desktop kernel: [    9.834003] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
May 15 10:30:46 pdleth-desktop kernel: [    9.933925] Linux agpgart interface v0.103
May 15 10:30:46 pdleth-desktop kernel: [    9.983787] lp: driver loaded but no devices found
May 15 10:30:46 pdleth-desktop kernel: [    9.996870] intel_rng: FWH not detected
May 15 10:30:46 pdleth-desktop kernel: [   10.041137] agpgart-intel 0000:00:00.0: Intel 865 Chipset
May 15 10:30:46 pdleth-desktop kernel: [   10.044719] agpgart-intel 0000:00:00.0: AGP aperture is 64M @ 0xf8000000
May 15 10:30:46 pdleth-desktop kernel: [   10.115352] parport_pc 00:0c: reported by Plug and Play ACPI
May 15 10:30:46 pdleth-desktop kernel: [   10.115464] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
May 15 10:30:46 pdleth-desktop kernel: [   10.208435] lp0: using parport0 (interrupt-driven).
May 15 10:30:46 pdleth-desktop kernel: [   10.221352] vga16fb: mapped to 0xc00a0000
May 15 10:30:46 pdleth-desktop kernel: [   10.221537] fb0: VGA16 VGA frame buffer device
May 15 10:30:46 pdleth-desktop kernel: [   10.403728] nvidia: module license 'NVIDIA' taints kernel.
May 15 10:30:46 pdleth-desktop kernel: [   10.403737] Disabling lock debugging due to kernel taint
May 15 10:30:46 pdleth-desktop kernel: [   10.846768] input: ImPS/2 Logitech Wheel Mouse as /devices/platform/i8042/serio1/input/input4
May 15 10:30:46 pdleth-desktop kernel: [   10.961277] Linux video capture interface: v2.00
May 15 10:30:46 pdleth-desktop kernel: [   10.968843] ppdev: user-space parallel port driver
May 15 10:30:46 pdleth-desktop kernel: [   11.204468] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
May 15 10:30:46 pdleth-desktop kernel: [   11.208040] NVRM: loading NVIDIA UNIX x86 Kernel Module  173.14.22  Sun Nov  8 20:26:31 PST 2009
May 15 10:30:46 pdleth-desktop kernel: [   11.453388] Console: switching to colour frame buffer device 80x30
May 15 10:30:46 pdleth-desktop kernel: [   11.499166] type=1505 audit(1273933843.478:2):  operation="profile_load" pid=521 name="/sbin/dhclient3"
May 15 10:30:46 pdleth-desktop kernel: [   11.500006] type=1505 audit(1273933843.478:3):  operation="profile_load" pid=521 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
May 15 10:30:46 pdleth-desktop kernel: [   11.500413] type=1505 audit(1273933843.482:4):  operation="profile_load" pid=521 name="/usr/lib/connman/scripts/dhclient-script"
May 15 10:30:46 pdleth-desktop kernel: [   11.655527] Intel ICH 0000:00:1f.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
May 15 10:30:46 pdleth-desktop kernel: [   11.977041] intel8x0_measure_ac97_clock: measured 54198 usecs (2612 samples)
May 15 10:30:46 pdleth-desktop kernel: [   11.977050] intel8x0: clocking to 48000
May 15 10:30:46 pdleth-desktop kernel: [   13.878783] kjournald starting.  Commit interval 5 seconds
May 15 10:30:46 pdleth-desktop kernel: [   13.881479] EXT3 FS on sda2, internal journal
May 15 10:30:46 pdleth-desktop kernel: [   13.881496] EXT3-fs: mounted filesystem with ordered data mode.
May 15 10:30:46 pdleth-desktop kernel: [   14.964289] r8169: eth0: link up
May 15 10:30:46 pdleth-desktop kernel: [   14.976251] type=1505 audit(1273933846.958:5):  operation="profile_load" pid=693 name="/usr/share/gdm/guest-session/Xsession"
May 15 10:30:46 pdleth-desktop kernel: [   14.986025] type=1505 audit(1273933846.966:6):  operation="profile_replace" pid=694 name="/sbin/dhclient3"
May 15 10:30:46 pdleth-desktop kernel: [   14.986829] type=1505 audit(1273933846.966:7):  operation="profile_replace" pid=694 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
May 15 10:30:46 pdleth-desktop kernel: [   14.987273] type=1505 audit(1273933846.966:8):  operation="profile_replace" pid=694 name="/usr/lib/connman/scripts/dhclient-script"
May 15 10:30:46 pdleth-desktop kernel: [   15.009619] type=1505 audit(1273933846.990:9):  operation="profile_load" pid=696 name="/usr/bin/evince"
May 15 10:30:47 pdleth-desktop kernel: [   15.040231] type=1505 audit(1273933847.022:10):  operation="profile_load" pid=696 name="/usr/bin/evince-previewer"
May 15 10:30:47 pdleth-desktop kernel: [   15.065266] type=1505 audit(1273933847.046:11):  operation="profile_load" pid=696 name="/usr/bin/evince-thumbnailer"
May 15 10:30:48 pdleth-desktop kernel: [   16.327430] agpgart-intel 0000:00:00.0: AGP 3.0 bridge
May 15 10:30:48 pdleth-desktop kernel: [   16.327481] agpgart-intel 0000:00:00.0: putting AGP V3 device into 8x mode
May 15 10:30:48 pdleth-desktop kernel: [   16.327566] nvidia 0000:01:00.0: putting AGP V3 device into 8x mode
May 15 10:30:56 pdleth-desktop pulseaudio[1037]: ratelimit.c: 3 events suppressed
May 15 10:31:23 pdleth-desktop pulseaudio[1261]: ratelimit.c: 2 events suppressed
May 15 10:31:43 pdleth-desktop kernel: [   70.843565] __ratelimit: 9 callbacks suppressed
May 15 10:31:43 pdleth-desktop kernel: [   70.843576] tvtime[1345]: segfault at 6b0 ip 0804d824 sp bfec0bcc error 4 in tvtime[8048000+76000]
pdleth@pdleth-desktop:~$

---

### Post by buster3 on 2010-06-06
Got news for you! NO GO!!

---


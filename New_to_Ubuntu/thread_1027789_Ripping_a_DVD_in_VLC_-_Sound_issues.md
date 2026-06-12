---
title: "Ripping a DVD in VLC - Sound issues"
date: 2009-01-01
forum: New to Ubuntu
---

### Post by transmition on 2009-01-01
I am attempting to rip a DVD in VLC. Here is my procedure:

1. Insert DVD and open VLC
2. Click Media --> Convert / Save
3. Click the Disk tab
4. Change the title to 1
5. Click Save
6. Click the file checkbox and type out the name of my movie with a .mpg suffix.
7. Select MPEG-TS as the encapsulation method
8. Click the Video tab, click the video checkbox, and choose h264 as the video codec
9. Set the bitrate to 2048 kb/s.
10. Click the Audio tab, click the audio checkbox, and choose mp3 as the audio codec.
11. Set the bitrate to 256 kb/s.
12. Click Save.

This results in vlc quickly closing. The output from the terminal is as follows:
```

libdvdnav: Language 'en' not found, using '&#65533;&#65533;' instead
libdvdnav: Menu Languages available: &#65533;&#65533; 
libdvdnav: Language 'en' not found, using '&#65533;&#65533;' instead
libdvdnav: Menu Languages available: &#65533;&#65533; 
libdvdnav: Language 'en' not found, using '&#65533;&#65533;' instead
libdvdnav: Menu Languages available: &#65533;&#65533; 
x264 [info]: using cpu capabilities: MMX MMXEXT SSE SSE2 SSE3 SSSE3 Cache64 
x264 [info]: using SAR=32/27
x264 [info]: using cpu capabilities: MMX MMXEXT SSE SSE2 SSE3 SSSE3 Cache64 
libdvdnav: Suspected RCE Region Protection!!!
[00000456] a52 packetizer: A/52 channels:6 samplerate:48000 bitrate:384000
[00000410] main stream out error: Failed to create audio filter2
[00000410] main stream out error: Failed to create audio filter2
[00000489] a52 packetizer: A/52 channels:6 samplerate:48000 bitrate:384000
[00000410] main stream out error: Failed to create audio filter2
[00000410] main stream out error: Failed to create audio filter2
[00000490] a52 decoder: A/52 channels:6 samplerate:48000 bitrate:384000
*** glibc detected *** vlc: malloc(): memory corruption: 0x0a9185b8 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7cfd116]
/lib/tls/i686/cmov/libc.so.6(__libc_malloc+0x95)[0xb7cfe865]
/usr/lib/libvlccore.so.0(__stats_TimerStart+0x215)[0xb7e79eb5]
======= Memory map: ========
08048000-0804a000 r-xp 00000000 08:03 395742     /usr/bin/vlc
0804a000-0804b000 r--p 00001000 08:03 395742     /usr/bin/vlc
0804b000-0804c000 rw-p 00002000 08:03 395742     /usr/bin/vlc
09bc8000-0a9ff000 rw-p 09bc8000 00:00 0          [heap]
ab3bb000-ab43a000 rw-p ab3bb000 00:00 0 
ab43a000-ab453000 r-xp 00000000 08:03 418359     /usr/lib/libdca.so.0.0.0
ab453000-ab454000 r--p 00018000 08:03 418359     /usr/lib/libdca.so.0.0.0
ab454000-ab461000 rw-p 00019000 08:03 418359     /usr/lib/libdca.so.0.0.0
ab4bf000-ab563000 r-xp 00000000 08:03 417869     /usr/lib/libxvidcore.so.4.1
ab563000-ab564000 rw-p 000a3000 08:03 417869     /usr/lib/libxvidcore.so.4.1
ab564000-ab5d7000 rw-p ab564000 00:00 0 
ab5d7000-ab619000 r-xp 00000000 08:03 417875     /usr/lib/libmp3lame.so.0.0.0
ab619000-ab61a000 r--p 00042000 08:03 417875     /usr/lib/libmp3lame.so.0.0.0
ab61a000-ab61c000 rw-p 00043000 08:03 417875     /usr/lib/libmp3lame.so.0.0.0
ab61c000-ab64c000 rw-p ab61c000 00:00 0 
ab64c000-abaa2000 r-xp 00000000 08:03 787704     /usr/lib/i686/cmov/libavcodec.so.51.50.0
abaa2000-abaa3000 r--p 00455000 08:03 787704     /usr/lib/i686/cmov/libavcodec.so.51.50.0
abaa3000-abaa9000 rw-p 00456000 08:03 787704     /usr/lib/i686/cmov/libavcodec.so.51.50.0
abaa9000-abd5c000 rw-p abaa9000 00:00 0 
abd5c000-abd5d000 ---p abd5c000 00:00 0 
abd5d000-ac55d000 rwxp abd5d000 00:00 0 
ac55d000-ac719000 rw-p ac55d000 00:00 0 
ac719000-ac71a000 ---p ac719000 00:00 0 
ac71a000-acf1a000 rwxp ac71a000 00:00 0 
acf1a000-ad155000 rw-p acf1a000 00:00 0 
ad155000-ad156000 ---p ad155000 00:00 0 
ad156000-ad956000 rwxp ad156000 00:00 0 
ad956000-ae6b2000 rw-p ad956000 00:00 0 
ae6ba000-ae6d0000 r-xp 00000000 08:03 34402      /usr/lib/libmad.so.0.2.1
ae6d0000-ae6d1000 r--p 00015000 08:03 34402      /usr/lib/libmad.so.0.2.1
ae6d1000-ae6d2000 rw-p 00016000 08:03 34402      /usr/lib/libmad.so.0.2.1
ae6d9000-ae6dd000 r-xp 00000000 08:03 395797     /usr/lib/vlc/audio_filter/libaudio_format_plugin.so
ae6dd000-ae6de000 r--p 00004000 08:03 395797     /usr/lib/vlc/audio_filter/libaudio_format_plugin.so
ae6de000-ae6df000 rw-p 00005000 08:03 395797     /usr/lib/vlc/audio_filter/libaudio_format_plugin.so
ae6df000-ae6e2000 r-xp 00000000 08:03 395782     /usr/lib/vlc/audio_filter/libmono_plugin.so
ae6e2000-ae6e3000 r--p 00002000 08:03 395782     /usr/lib/vlc/audio_filter/libmono_plugin.so
ae6e3000-ae6e4000 rw-p 00003000 08:03 395782     /usr/lib/vlc/audio_filter/libmono_plugin.so
ae6e4000-ae6e6000 r-xp 00000000 08:03 395793     /usr/lib/vlc/audio_filter/liblinear_resampler_plugin.so
ae6e6000-ae6e7000 r--p 00001000 08:03 395793     /usr/lib/vlc/audio_filter/liblinear_resampler_plugin.so
ae6e7000-ae6e8000 rw-p 00002000 08:03 395793     /usr/lib/vlc/audio_filter/liblinear_resampler_plugin.so
ae6e8000-ae723000 r-xp 00000000 08:03 34394      /usr/lib/libfaad.so.0.0.0
ae723000-ae724000 ---p 0003b000 08:03 34394      /usr/lib/libfaad.so.0.0.0
ae724000-ae725000 r--p 0003b000 08:03 34394      /usr/lib/libfaad.so.0.0.0
ae725000-ae728000 rw-p 0003c000 08:03 34394      /usr/lib/libfaad.so.0.0.0
ae728000-ae963000 rw-p ae728000 00:00 0 
ae963000-ae965000 r-xp 00000000 08:03 395783     /usr/lib/vlc/audio_filter/libsimple_channel_mixer_plugin.so
ae965000-ae966000 r--p 00001000 08:03 395783     /usr/lib/vlc/audio_filter/libsimple_channel_mixer_plugin.so
ae966000-ae967000 rw-p 00002000 08:03 395783     /usr/lib/vlc/audio_filter/libsimple_channel_mixer_plugin.so
ae967000-ae973000 r-xp 00000000 08:03 34325      /usr/lib/libgsm.so.1.0.12
ae973000-ae974000 rw-p 0000b000 08:03 34325      /usr/lib/libgsm.so.1.0.12
ae974000-ae982000 r-xp 00000000 08:03 39243      /usr/lib/libfaac.so.0.0.0
ae982000-ae983000 r--p 0000d000 08:03 39243      /usr/lib/libfaac.so.0.0.0
ae983000-ae986000 rw-p 0000e000 08:03 39243      /usr/lib/libfaac.so.0.0.0
ae986000-ae98f000 r-xp 00000000 08:03 34322      /usr/lib/liba52-0.7.4.so
ae98f000-ae990000 rw-p 00008000 08:03 34322      /usr/lib/liba52-0.7.4.so
ae990000-ae991000 rw-p ae990000 00:00 0 
ae991000-ae99c000 r-xp 00000000 08:03 49414      /usr/lib/i686/cmov/libavutil.so.49.6.0
ae99c000-ae99d000 r--p 0000a000 08:03 49414      /usr/lib/i686/cmov/libavutil.so.49.6.0
ae99d000-ae99e000 rw-p 0000b000 08:03 49414      /usr/lib/i686/cmov/libavutil.so.49.6.0
ae99e000-ae9a1000 rw-p ae99e000 00:00 0 
ae9a2000-ae9a8000 r-xp 00000000 08:03 395792     /usr/lib/vlc/audio_filter/libbandlimited_resampler_plugin.so
ae9a8000-ae9a9000 r--p 00005000 08:03 395792     /usr/lib/vlc/audio_filter/libbandlimited_resampler_plugin.so
ae9a9000-ae9aa000 rw-p 00006000 08:03 395792     /usr/lib/vlc/audio_filter/libbandlimited_resampler_plugin.so
ae9aa000-ae9ac000 r-xp 00000000 08:03 395789     /usr/lib/vlc/audio_filter/libdtstofloat32_plugin.so
ae9ac000-ae9ad000 r--p 00001000 08:03 395789     /usr/lib/vlc/audio_filter/libdtstofloat32_plugin.so
ae9ad000-ae9ae000 rw-p 00002000 08:03 395789     /usr/lib/vlc/audio_filter/libdtstofloat32_plugin.so
ae9ae000-ae9b0000 r-xp 00000000 08:03 395785     /usr/lib/vlc/audio_filter/liba52tofloat32_plugin.so
ae9b0000-ae9b1000 r--p 00001000 08:03 395785     /usr/lib/vlc/audio_filter/liba52tofloat32_plugin.so
ae9b1000-ae9b2000 rw-p 00002000 08:03 395785     /usr/lib/vlc/audio_filter/liba52tofloat32_plugin.so
ae9b2000-ae9b5000 r-xp 00000000 08:03 395791     /usr/lib/vlc/audio_filter/libmpgatofixed32_plugin.so
ae9b5000-ae9b6000 r--p 00002000 08:03 395791     /usr/lib/vlc/audio_filter/libmpgatofixed32_plugin.so
ae9b6000-ae9b7000 rw-p 00003000 08:03 395791     /usr/lib/vlc/audio_filter/libmpgatofixed32_plugin.so
ae9b7000-ae9c6000 r-xp 00000000 08:03 395814     /usr/lib/vlc/codec/libavcodec_plugin.so
ae9c6000-ae9c9000 r--p 0000f000 08:03 395814     /usr/lib/vlc/codec/libavcodec_plugin.so
ae9c9000-ae9ca000 rw-p 00012000 08:03 395814     /usr/lib/vlc/codec/libavcodec_plugin.so
ae9ca000-ae9cf000 r-xp 00000000 08:03 395813     /usr/lib/vlc/codec/libaraw_plugin.so
ae9cf000-ae9d0000 r--p 00004000 08:03 395813     /usr/lib/vlc/codec/libaraw_plugin.so
ae9d0000-ae9d1000 rw-p 00005000 08:03 395813     /usr/lib/vlc/codec/libaraw_plugin.so
ae9d1000-ae9d7000 r-xp 00000000 08:03 395934     /usr/lib/vlc/packetizer/libpacketizer_mpeg4audio_plugin.so
ae9d7000-ae9d8000 r--p 00005000 08:03 395934     /usr/lib/vlc/packetizer/libpacketizer_mpeg4audio_plugin.so
ae9d8000-ae9d9000 rw-p 00006000 08:03 395934     /usr/lib/vlc/packetizer/libpacketizer_mpeg4audio_plugin.so
ae9d9000-aec14000 rw-p ae9d9000 00:00 0 
aec14000-aec97000 r-xp 00000000 08:03 34566      /usr/lib/libx264.so.59
aec97000-aec98000 rw-p 00082000 08:03 34566      /usr/lib/libx264.so.59
aec98000-aedc5000 rw-p aec98000 00:00 0 
aedc5000-aede1000 r-xp 00000000 08:03 49419      /usr/local/lib/libmpeg2.so.0.1.0
aede1000-aede2000 r--p 0001b000 08:03 49419      /usr/local/lib/libmpeg2.so.0.1.0
aede2000-aede3000 rw-p 0001c000 08:03 49419      /usr/local/lib/libmpeg2.so.0.1.0
aede3000-aede5000 rw-p aede3000 00:00 0 
aede7000-aede9000 r-xp 00000000 08:03 395811     /usr/lib/vlc/codec/liba52_plugin.so
aede9000-aedea000 r--p 00001000 08:03 395811     /usr/lib/vlc/codec/liba52_plugin.so
aedea000-aedeb000 rw-p 00002000 08:03 395811     /usr/lib/vlc/codec/liba52_plugin.so
aedeb000-aedf4000 r-xp 00000000 08:03 395935     /usr/lib/vlc/packetizer/libpacketizer_h264_plugin.so
aedf4000-aedf5000 r--p 00008000 08:03 395935     /usr/lib/vlc/packetizer/libpacketizer_h264_plugin.so
aedf5000-aedf6000 rw-p 00009000 08:03 395935     /usr/lib/vlc/packetizer/libpacketizer_h264_plugin.so
aedf6000-aedf9000 r-xp 00000000 08:03 395936     /usr/lib/vlc/packetizer/libpacketizer_vc1_plugin.so
aedf9000-aedfa000 r--p 00002000 08:03 395936     /usr/lib/vlc/packetizer/libpacketizer_vc1_plugin.so
aedfa000-aedfb000 rw-p 00003000 08:03 395936     /usr/lib/vlc/packetizer/libpacketizer_vc1_plugin.so
aedfb000-aee50000 r-xp 00000000 08:03 37560      /usr/lib/liboil-0.3.so.0.3.0
aee50000-aee51000 r--p 00054000 08:03 37560      /usr/lib/liboil-0.3.so.0.3.0
aee51000-aee68000 rw-p 00055000 08:03 37560      /usr/lib/liboil-0.3.so.0.3.0
aee68000-aee6a000 rw-p aee68000 00:00 0 
aee6a000-aeed7000 r-xp 00000000 08:03 40123      /usr/lib/libschroedinger-1.0.so.0.1.0
aeedAborted

```

When running without the sound checkbox ticked, VLC stays open and proceeds to encode my movie perfectly, except without sound.

How can I fix this?

---

### Post by %hMa@?b&lt;C on 2009-01-01
two programs for ripping DVDs that I have found very good were handbrake and k9copy
hanbrake for xvid conversion and k9copy for dvd5

---

### Post by transmition on 2009-01-01
Thanks for the reply, and I suppose this solves the ultimate problem, being that I want to encode one of my DVD's, but it is not the solution as to why VLC is not working properly.

---

### Post by ken22 on 2009-01-01
Do you have the ubuntu-restricted packages installed allowing use of mp3?

---

### Post by transmition on 2009-01-01
In addition, here are the outputs of

MPEG Audio:

```

x264 [info]: using cpu capabilities: MMX MMXEXT SSE SSE2 SSE3 SSSE3 Cache64 
x264 [info]: using SAR=32/27
x264 [info]: using cpu capabilities: MMX MMXEXT SSE SSE2 SSE3 SSSE3 Cache64 
libdvdnav: Suspected RCE Region Protection!!!
[00000456] a52 packetizer: A/52 channels:6 samplerate:48000 bitrate:384000
[00000410] main stream out error: Failed to create audio filter2
[00000410] main stream out error: Failed to create audio filter2
[00000489] a52 packetizer: A/52 channels:6 samplerate:48000 bitrate:384000
[00000410] main stream out error: Failed to create audio filter2
[00000410] main stream out error: Failed to create audio filter2
[00000490] a52 decoder: A/52 channels:6 samplerate:48000 bitrate:384000
*** glibc detected *** vlc: malloc(): memory corruption: 0x08ea6728 ***
Segmentation fault

```

A52/AC-3:
```

[00000456] a52 packetizer: A/52 channels:6 samplerate:48000 bitrate:384000
[00000410] main stream out error: Failed to create audio filter2
[00000410] main stream out error: Failed to create audio filter2
[00000489] a52 packetizer: A/52 channels:6 samplerate:48000 bitrate:384000
[00000410] main stream out error: Failed to create audio filter2
[00000410] main stream out error: Failed to create audio filter2
[00000490] a52 decoder: A/52 channels:6 samplerate:48000 bitrate:384000
*** glibc detected *** vlc: malloc(): memory corruption: 0x0a318258 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7df6116]
/lib/tls/i686/cmov/libc.so.6(__libc_malloc+0x95)[0xb7df7865]
/lib/tls/i686/cmov/libc.so.6(__strdup+0x30)[0xb7dfb000]
/usr/lib/libvlccore.so.0(__stats_TimerStart+0x197)[0xb7f72e37]
======= Memory map: ========
08048000-0804a000 r-xp 00000000 08:03 395742     /usr/bin/vlc
0804a000-0804b000 r--p 00001000 08:03 395742     /usr/bin/vlc
0804b000-0804c000 rw-p 00002000 08:03 395742     /usr/bin/vlc
09df3000-0a398000 rw-p 09df3000 00:00 0          [heap]
aac15000-aac94000 rw-p aac15000 00:00 0 
aac94000-aad38000 r-xp 00000000 08:03 417869     /usr/lib/libxvidcore.so.4.1
aad38000-aad39000 rw-p 000a3000 08:03 417869     /usr/lib/libxvidcore.so.4.1
aad39000-aadac000 rw-p aad39000 00:00 0 
aadac000-ab202000 r-xp 00000000 08:03 787704     /usr/lib/i686/cmov/libavcodec.so.51.50.0
ab202000-ab203000 r--p 00455000 08:03 787704     /usr/lib/i686/cmov/libavcodec.so.51.50.0
ab203000-ab209000 rw-p 00456000 08:03 787704     /usr/lib/i686/cmov/libavcodec.so.51.50.0
ab209000-ab300000 rw-p ab209000 00:00 0 
ab300000-ab3f7000 rw-p ab300000 00:00 0 
ab3f7000-ab400000 ---p ab3f7000 00:00 0 
ab45f000-ab4a1000 r-xp 00000000 08:03 417875     /usr/lib/libmp3lame.so.0.0.0
ab4a1000-ab4a2000 r--p 00042000 08:03 417875     /usr/lib/libmp3lame.so.0.0.0
ab4a2000-ab4a4000 rw-p 00043000 08:03 417875     /usr/lib/libmp3lame.so.0.0.0
ab4a4000-ab690000 rw-p ab4a4000 00:00 0 
ab690000-ab691000 ---p ab690000 00:00 0 
ab691000-abe91000 rwxp ab691000 00:00 0 
abe91000-abf00000 rw-p abe91000 00:00 0 
abf00000-abfe9000 rw-p abf00000 00:00 0 
abfe9000-ac000000 ---p abfe9000 00:00 0 
ac054000-ac0c3000 rw-p ac054000 00:00 0 
ac0c3000-ac0c4000 ---p ac0c3000 00:00 0 
ac0c4000-ac8c4000 rwxp ac0c4000 00:00 0 
ac8c4000-acaff000 rw-p ac8c4000 00:00 0 
acaff000-acb00000 ---p acaff000 00:00 0 
acb00000-ad300000 rwxp acb00000 00:00 0 
ad300000-ad3f9000 rw-p ad300000 00:00 0 
ad3f9000-ad400000 ---p ad3f9000 00:00 0 
ad414000-ad800000 rw-p ad414000 00:00 0 
ad800000-ad8f5000 rw-p ad800000 00:00 0 
ad8f5000-ad900000 ---p ad8f5000 00:00 0 
ad906000-ad91f000 r-xp 00000000 08:03 418359     /usr/lib/libdca.so.0.0.0
ad91f000-ad920000 r--p 00018000 08:03 418359     /usr/lib/libdca.so.0.0.0
ad920000-ad92d000 rw-p 00019000 08:03 418359     /usr/lib/libdca.so.0.0.0
ad92d000-adb00000 rw-p ad92d000 00:00 0 
adb00000-adbf5000 rw-p adb00000 00:00 0 
adbf5000-adc00000 ---p adbf5000 00:00 0 
adc07000-adc1d000 r-xp 00000000 08:03 34402      /usr/lib/libmad.so.0.2.1
adc1d000-adc1e000 r--p 00015000 08:03 34402      /usr/lib/libmad.so.0.2.1
adc1e000-adc1f000 rw-p 00016000 08:03 34402      /usr/lib/libmad.so.0.2.1
adc1f000-ae200000 rw-p adc1f000 00:00 0 
ae200000-ae2f3000 rw-p ae200000 00:00 0 
ae2f3000-ae300000 ---p ae2f3000 00:00 0 
ae30f000-ae34a000 r-xp 00000000 08:03 34394      /usr/lib/libfaad.so.0.0.0
ae34a000-ae34b000 ---p 0003b000 08:03 34394      /usr/lib/libfaad.so.0.0.0
ae34b000-ae34c000 r--p 0003b000 08:03 34394      /usr/lib/libfaad.so.0.0.0
ae34c000-ae34f000 rw-p 0003c000 08:03 34394      /usr/lib/libfaad.so.0.0.0
ae34f000-ae50b000 rw-p ae34f000 00:00 0 
ae512000-ae600000 rw-p ae512000 00:00 0 
ae600000-ae6e8000 rw-p ae600000 00:00 0 
ae6e8000-ae700000 ---p ae6e8000 00:00 0 
ae71f000-ae723000 r-xp 00000000 08:03 395797     /usr/lib/vlc/audio_filter/libaudio_format_plugin.so
ae723000-ae724000 r--p 00004000 08:03 395797     /usr/lib/vlc/audio_filter/libaudio_format_plugin.so
ae724000-ae725000 rw-p 00005000 08:03 395797     /usr/lib/vlc/audio_filter/libaudio_format_plugin.so
ae725000-ae731000 r-xp 00000000 08:03 34325      /usr/lib/libgsm.so.1.0.12
ae731000-ae732000 rw-p 0000b000 08:03 34325      /usr/lib/libgsm.so.1.0.12
ae732000-ae740000 r-xp 00000000 08:03 39243      /usr/lib/libfaac.so.0.0.0
ae740000-ae741000 r--p 0000d000 08:03 39243      /usr/lib/libfaac.so.0.0.0
ae741000-ae744000 rw-p 0000e000 08:03 39243      /usr/lib/libfaac.so.0.0.0
ae744000-ae74d000 r-xp 00000000 08:03 34322      /usr/lib/liba52-0.7.4.so
ae74d000-ae74e000 rw-p 00008000 08:03 34322      /usr/lib/liba52-0.7.4.so
ae74e000-ae90b000 rw-p ae74e000 00:00 0 
ae90d000-ae910000 r-xp 00000000 08:03 395782     /usr/lib/vlc/audio_filter/libmono_plugin.so
ae910000-ae911000 r--p 00002000 08:03 395782     /usr/lib/vlc/audio_filter/libmono_plugin.so
ae911000-ae912000 rw-p 00003000 08:03 395782     /usr/lib/vlc/audio_filter/libmono_plugin.so
ae912000-aea00000 rw-p ae912000 00:00 0 
aea00000-aeae7000 rw-p aea00000 00:00 0 
aeae7000-aeb00000 ---p aeae7000 00:00 0 
aeb00000-aeb02000 r-xp 00000000 08:03 395793     /usr/lib/vlc/audio_filter/liblinear_resampler_plugin.so
aeb02000-aeb03000 r--p 00001000 08:03 395793     /usr/lib/vlc/audio_filter/liblinear_resampler_plugin.so
aeb03000-aeb04000 rw-p 00002000 08:03 395793     /usr/lib/vlc/audio_filter/liblinear_resampler_plugin.so
aeb04000-aeb06000 r-xp 00000000 08:03 395783     /usr/lib/vlc/audio_filter/libsimple_channel_mixer_plugin.so
aeb06000-aeb07000 r--p 00001000 08:03 395783     /usr/lib/vlc/audio_filter/libsimple_channel_mixer_plugin.so
aeb07000-aeb08000 rw-p 00002000 08:03 395783     /usr/lib/vlc/audio_filter/libsimple_channel_mixer_plugin.so
aeb08000-aeb13000 r-xp 00000000 08:03 49414      /usr/lib/i686/cmov/libavutil.so.49.6.0
aeb13000-aeb14000 r--p 0000a000 08:03 49414      /usr/lib/i686/cmov/libavutil.so.49.6.0
aeb14000-aeb15000 rw-p 0000b000 08:03 49414      /usr/lib/i686/cmov/libavutil.so.49.6.0
aeb15000-aeb18000 rw-p aeb15000 00:00 0 
aeb19000-aeb1f000 r-xp 00000000 08:03 395792     /usr/lib/vlc/audio_filter/libbandlimited_resampler_plugin.so
aeb1f000-aeb20000 r--p 00005000 08:03 395792     /usr/lib/vlc/audio_filter/libbandlimited_resampler_plugin.so
aeb20000-aeb21000 rw-p 00006000 08:03 395792     /usr/lib/vlc/audio_filter/libbandlimited_resampler_plugin.so
aeb21000-aeb23000 r-xp 00000000 08:03 395789     /usr/lib/vlc/audio_filter/libdtstofloat32_plugin.so
aeb23000-aeb24000 r--p 00001000 08:03 395789     /usr/lib/vlc/audio_filter/libdtstofloat32_plugin.so
aeb24000-aeb25000 rw-p 00002000 08:03 395789     /usr/lib/vlc/audio_filter/libdtstofloat32_plugin.so
aeb25000-aeb27000 r-xp 00000000 08:03 395785     /usr/lib/vlc/audio_filter/liba52tofloat32_plugin.so
aeb27000-aeb28000 r--p 00001000 08:03 395785     /usr/lib/vlc/audio_filter/liba52tofloat32_plugin.so
aeb28000-aeb29000 rw-p 00002000 08:03 395785     /usr/lib/vlc/audio_filter/liba52tofloat32_plugin.so
aeb29000-aeb2c000 r-xp 00000000 08:03 395791     /usr/lib/vlc/audio_filter/libmpgatofixed32_plugin.so
aeb2c000-aeb2d000 r--p 00002000 08:03 395791     /usr/lib/vlc/audio_filter/libmpgatofixed32_plugin.so
aeb2d000-aeb2e000 rw-p 00003000 08:03 395791     /usr/lib/vlc/audio_filter/libmpgatofixed32_plugin.so
aeb2e000-aeb3d000 r-xp 00000000 08:03 395814     /usr/lib/vlc/codec/libavcodec_plugin.so
aeb3d000-aeb40000 r--p 0000f000 08:03 395814     /usr/lib/vlc/codec/libavcodec_plugin.so
aeb40000-aeb41000 rw-p 00012000 08:03 395814     /usr/lib/vlc/codec/libavcodec_plugin.so
aeb41000-aeb46000 r-xp 00000000 08:03 395813     /usr/lib/vlc/codec/libaraw_plugin.so
aeb46000-aeb47000 r--p 00004000 08:03 395813     /usr/lib/vlc/codec/libaraw_plugin.so
aeb47000-aeb48000 rw-p 00005000 08:03 395813     /usr/lib/vlc/codec/libaraw_plugin.so
aeb48000-aeb4e000 r-xp 00000000 08:03 395934     /usr/lib/vlc/packetizer/libpacketizer_mpeg4audio_plugin.so
aeb4e000-aeb4f000 r--p 00005000 08:03 395934     /usr/lib/vlc/packetizer/liAborted

```

WAV:
```

[00000456] a52 packetizer: A/52 channels:6 samplerate:48000 bitrate:384000
[00000410] main stream out error: Failed to create audio filter2
[00000410] main stream out error: Failed to create audio filter2
[00000419] main mux error: cannot add this stream
[00000456] main packetizer error: cannot create packetizer output (a52 )
[00000486] a52 packetizer: A/52 channels:6 samplerate:48000 bitrate:384000
[00000410] main stream out error: Failed to create audio filter2
[00000410] main stream out error: Failed to create audio filter2
[00000419] main mux error: cannot add this stream
[00000486] main packetizer error: cannot create packetizer output (a52 )

```

Etc.

---

### Post by transmition on 2009-01-01
> 
Do you have the ubuntu-restricted packages installed allowing use of mp3? 


Yes.

---


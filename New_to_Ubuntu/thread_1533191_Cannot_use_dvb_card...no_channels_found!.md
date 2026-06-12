---
title: "Cannot use dvb card...no channels found!"
date: 2010-07-17
forum: New to Ubuntu
---

### Post by sad_iq on 2010-07-17
Hi. I just bought my first dvb card and I would like to use it in Ubuntu, unfortunately when I scan for channels I find nothing. The card is recognized by Ubuntu, but all I get are errors when scanning:

```
sadiq@jigsaw:~$ lsb_release -d
Description:	Ubuntu 10.04.1 LTS
sadiq@jigsaw:~$ uname -a
Linux jigsaw 2.6.32-24-generic #38-Ubuntu SMP Mon Jul 5 09:22:14 UTC 2010 i686 GNU/Linux

```
```
sadiq@jigsaw:~$ lspci | grep Multimedia
04:00.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
04:00.2 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
```
```
sadiq@jigsaw:~$ lsmod
Module                  Size  Used by
sha256_generic         11191  2 
aes_i586                7268  290 
aes_generic            26863  1 aes_i586
dm_crypt               11331  1 
binfmt_misc             6587  1 
ppdev                   5259  0 
dvb_pll                 9085  1 
cx22702                 5032  1 
cx88_dvb               19413  0 
cx88_vp3054_i2c         1808  1 cx88_dvb
videobuf_dvb            5175  1 cx88_dvb
dvb_core               86142  2 cx88_dvb,videobuf_dvb
snd_hda_codec_realtek   203310  1 
snd_hda_intel          21941  4 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
cx8800                 27188  0 
cx8802                 12841  1 cx88_dvb
cx88xx                 72596  3 cx88_dvb,cx8800,cx8802
snd_timer              19098  2 snd_pcm,snd_seq
fbcon                  35102  72 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
ir_common              38875  1 cx88xx
v4l2_common            15431  2 cx8800,cx88xx
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
rt2870sta             461811  1 
softcursor              1189  1 bitblit
snd                    54148  19 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_algo_bit            5028  2 cx88_vp3054_i2c,cx88xx
videodev               34361  3 cx8800,cx88xx,v4l2_common
v4l1_compat            13251  1 videodev
tveeprom               11102  1 cx88xx
btcx_risc               3624  3 cx8800,cx8802,cx88xx
videobuf_dma_sg        10782  4 cx88_dvb,cx8800,cx8802,cx88xx
videobuf_core          16356  5 videobuf_dvb,cx8800,cx8802,cx88xx,videobuf_dma_sg
nvidia               9961216  38 
vga16fb                11385  1 
vgastate                8961  1 vga16fb
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
lp                      7028  0 
parport                32635  2 ppdev,lp
vesafb                  3542  0 
usbhid                 36110  0 
hid                    67032  1 usbhid
ohci1394               26950  0 
intel_agp              24119  0 
r8169                  34076  0 
mii                     4381  1 r8169
agpgart                31724  2 nvidia,intel_agp
ahci                   32200  2 
ieee1394               81181  1 ohci1394

```

_Kaffeine_ shows me I have signal but all I get after scanning is : **kaffeine(1964) DvbDevice::frontendEvent: tuning failed**
 _w_scan_ just gives me this:
 ```
sadiq@jigsaw:~$ w_scan -t3 -c ES -F channels.conf
w_scan version 20091230 (compiled for DVB API 5.1)
using settings for SPAIN
DVB aerial
DVB-T Europe
frontend_type DVB-T, channellist 4
output format vdr-1.6
Info: using DVB adapter auto detection.
	/dev/dvb/adapter0/frontend0 -> DVB-T "Conexant CX22702 DVB-T": good :-)
Using DVB-T frontend (adapter /dev/dvb/adapter0/frontend0)
-_-_-_-_ Getting frontend capabilities-_-_-_-_ 
Using DVB API 5.1
frontend Conexant CX22702 DVB-T supports
INVERSION_AUTO
QAM_AUTO
TRANSMISSION_MODE_AUTO
GUARD_INTERVAL_AUTO
HIERARCHY_AUTO
FEC_AUTO
-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_ 
Scanning 7MHz frequencies...
177500: (time: 00:00) 
184500: (time: 00:03) 
191500: (time: 00:05) 
198500: (time: 00:08) 
205500: (time: 00:10) 
212500: (time: 00:13) 
219500: (time: 00:15) 
226500: (time: 00:18) 
Scanning 8MHz frequencies...
474000: (time: 00:21) 
482000: (time: 00:23) 
490000: (time: 00:26) 
498000: (time: 00:28) 
506000: (time: 00:31) 
514000: (time: 00:33) 
522000: (time: 00:36) 
530000: (time: 00:38) 
538000: (time: 00:41) 
546000: (time: 00:43) 
554000: (time: 00:46) 
562000: (time: 00:48) 
570000: (time: 00:51) 
578000: (time: 00:53) 
586000: (time: 00:56) 
594000: (time: 00:58) 
602000: (time: 01:01) 
610000: (time: 01:03) 
618000: (time: 01:06) 
626000: (time: 01:08) 
634000: (time: 01:11) 
642000: (time: 01:13) 
650000: (time: 01:16) 
658000: (time: 01:18) 
666000: (time: 01:21) 
674000: (time: 01:23) 
682000: (time: 01:26) 
690000: (time: 01:28) 
698000: (time: 01:31) 
706000: (time: 01:33) 
714000: (time: 01:36) 
722000: (time: 01:38) 
730000: (time: 01:41) 
738000: (time: 01:44) 
746000: (time: 01:46) 
754000: (time: 01:49) 
762000: (time: 01:51) 
770000: (time: 01:54) 
778000: (time: 01:56) 
786000: (time: 01:59) 
794000: (time: 02:01) 
802000: (time: 02:04) 
810000: (time: 02:06) 
818000: (time: 02:09) 
826000: (time: 02:11) 
834000: (time: 02:14) 
842000: (time: 02:16) 
850000: (time: 02:19) 
858000: (time: 02:21) 

ERROR: Sorry - i couldn't get any working frequency/transponder
 Nothing to scan!!

```
_me-tv_:
 ```
sadiq@jigsaw:~$ me-tv
Me TV 1.3.1
07/17/2010 20:44:19: Device: 'Conexant CX22702 DVB-T' (DVB-T) at "/dev/dvb/adapter0/frontend0"
07/17/2010 20:44:30: Frontend::tune_to(618000000)
07/17/2010 20:44:30: Waiting for signal lock ...
07/17/2010 20:44:32: Frontend::tune_to(706000000)
07/17/2010 20:44:32: Waiting for signal lock ...
07/17/2010 20:44:33: Frontend::tune_to(770000000)
07/17/2010 20:44:33: Waiting for signal lock ...
07/17/2010 20:44:35: Frontend::tune_to(810000000)
07/17/2010 20:44:35: Waiting for signal lock ...
07/17/2010 20:44:37: Frontend::tune_to(834000000)
07/17/2010 20:44:37: Waiting for signal lock ...
07/17/2010 20:44:38: Frontend::tune_to(842000000)
07/17/2010 20:44:38: Waiting for signal lock ...
07/17/2010 20:44:40: Frontend::tune_to(850000000)
07/17/2010 20:44:40: Waiting for signal lock ...
07/17/2010 20:44:41: Frontend::tune_to(858000000)
07/17/2010 20:44:41: Waiting for signal lock ...
```

Is there anything I can do to get this baby working?
Google-ing for things wasn't really helpful...there is a bug about kaffeine not being able to scan DVB-S channels, but it's not my case, and I believe I have to scan for DVB-T (not that I researched about what that means...I guess Satellite vs Terrestrial channels...not really sure).

---

### Post by sad_iq on 2010-07-18
Anyone? Anything? I'm clueless :(

---

### Post by bance on 2010-07-18
you could try searching V4L (video for linux), search for your card, it would seem it is supported. but you 'll be able to find what you need (drivers/firmware) to get it working

[http://www.linuxtv.org/wiki/index.php/Main_Page](http://www.linuxtv.org/wiki/index.php/Main_Page)

HTH, steve

---

### Post by sad_iq on 2010-07-18
> **bance said:**
> you could try searching V4L (video for linux), search for your card, it would seem it is supported. but you 'll be able to find what you need (drivers/firmware) to get it working

[http://www.linuxtv.org/wiki/index.php/Main_Page](http://www.linuxtv.org/wiki/index.php/Main_Page)

HTH, steve

Did that...no luck with that :(
The same thing happens when I scan for channels.

---

### Post by dave01945 on 2011-08-18
this may be abit obvious but do you know if your aerial is getting a signal has it been used before

---


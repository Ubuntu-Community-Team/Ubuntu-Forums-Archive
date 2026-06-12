---
title: "ffmpeg unsupported codec prob"
date: 2009-04-19
forum: New to Ubuntu
---

### Post by loobyloo on 2009-04-19
Hi there
I'm trying to get an mp3 from an flv using ffmpeg.  I get the following error.


cliff@cliff-laptop:~$ ffmpeg -i /home/cliff/Desktop/Sweden-Malena-La_Voix.flv -ac 2 -ar 44100 -ab 320 /home/cliff/Desktop/audio.mp3
FFmpeg version SVN-r18532, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: 
  libavutil     50. 3. 0 / 50. 3. 0
  libavcodec    52.25. 0 / 52.25. 0
  libavformat   52.32. 0 / 52.32. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libswscale     0. 7. 1 /  0. 7. 1
  built on Apr 16 2009 16:10:36, gcc: 4.3.2
[flv @ 0xa836b00]skipping flv packet: type 18, size 294, flags 0

Seems stream 0 codec frame rate differs from container frame rate: 50.00 (50/1) -> 25.00 (25/1)
Input #0, flv, from '/home/cliff/Desktop/Sweden-Malena-La_Voix.flv':
  Duration: 00:03:07.61, start: 0.000000, bitrate: N/A
    Stream #0.0: Video: h264, yuv420p, 320x240 [PAR 1:1 DAR 4:3], 25 tbr, 1k tbn, 50 tbc
    Stream #0.1: Audio: aac, 22050 Hz, stereo, s16
WARNING: The bitrate parameter is set too low. It takes bits/s as argument, not kbits/s
Output #0, mp3, to '/home/cliff/Desktop/audio.mp3':
    Stream #0.0: Audio: 0x0000, 44100 Hz, stereo, s16, 0 kb/s
Stream mapping:
  Stream #0.1 -> #0.0
Unsupported codec for output stream #0.0
--------

In another thread here someone recommended installing the libaveccodec 51 unstripped, which I have done, but the problem persists.  Does anyone know how I can solve this?

Many thanks

---

### Post by Didius Falco on 2009-04-19
> **loobyloo said:**
> Hi there
I'm trying to get an mp3 from an flv using ffmpeg.  I get the following error.


cliff@cliff-laptop:~$ ffmpeg -i /home/cliff/Desktop/Sweden-Malena-La_Voix.flv -ac 2 -ar 44100 -ab 320 /home/cliff/Desktop/audio.mp3

    Stream #0.1: Audio: aac, 22050 Hz, stereo, s16
WARNING: The bitrate parameter is set too low. It takes bits/s as argument, not kbits/s
Output #0, mp3, to '/home/cliff/Desktop/audio.mp3':
    Stream #0.0: Audio: 0x0000, 44100 Hz, stereo, s16, 0 kb/s
Stream mapping:
  Stream #0.1 -> #0.0
Unsupported codec for output stream #0.0

Many thanks

I just took a quick look at the documentation for ffmpeg, and it looks to me like your command needs a slight tweak. I think if you put a "k" in the bitrate (-ab 320 should be -ab320**k**), it will work: 

f```
ffmpeg -i /home/cliff/Desktop/Sweden-Malena-La_Voix.flv -ac 2 -ar 44100 -ab 320k /home/cliff/Desktop/audio.mp3
```Give it a go and see if it works. Here is a link to the documentation I looked over:

[http://ffmpeg.mplayerhq.hu/ffmpeg-doc.html](http://ffmpeg.mplayerhq.hu/ffmpeg-doc.html)

I hope this helps...

---

### Post by loobyloo on 2009-04-19
Thanks - I changed the bitrate but still get the same error.

Another puzzling thing is that mp3 is listed when I do a -formats on ffmpeg.

---

### Post by Didius Falco on 2009-04-19
I found another thread with a solution that worked for someone else. Try this:

```
ffmpeg -i /home/cliff/Desktop/Sweden-Malena-La_Voix.flv  -acodec copy /home/cliff/Desktop/audio.mp3

```

---

### Post by loobyloo on 2009-04-19
Hi thanks - that at least converts the file but then Movie Player says "Could not determine type of stream."

I might give up to be honest!  The world won't stop turning if I can't save this year's Swedish Eurovision song to my HD.

---

### Post by Didius Falco on 2009-04-19
I didn't even have ffmpeg installed, but I installed it and tried it out and it worked fine. I'm listening to the mp3 right now in Rhythmbox. Just loaded it in Movie Player too...are you sure you have all the codecs for Movie Player?

On Edit: here is a website with instructions on how to get the codecs:

[http://www.ubuntugeek.com/install-mplayer-and-multimedia-codecs-libdvdcss2w32codecsw64codecs-in-ubuntu-810-intrepid-ibex.html](http://www.ubuntugeek.com/install-mplayer-and-multimedia-codecs-libdvdcss2w32codecsw64codecs-in-ubuntu-810-intrepid-ibex.html)

---

### Post by loobyloo on 2009-04-19
Really? That's odd. All my other mp3s work in both of those.

---

### Post by Didius Falco on 2009-04-19
is that flv on youtube? I'll download and try it out, just out of curiosity.

I'm learning as much as you are, maybe more. <G>

---

### Post by loobyloo on 2009-04-19
Yes, I saved the flv using the extension Mozilla extension UnPlug [https://addons.mozilla.org/en-US/firefox/addon/2254](https://addons.mozilla.org/en-US/firefox/addon/2254)

The (rather dire) song I'm trying to capture is at 
[http://www.youtube.com/watch?v=cnHr69JuiEk&feature=PlayList&p=29B0CA95AE3FF862&index=0&playnext=1](http://www.youtube.com/watch?v=cnHr69JuiEk&feature=PlayList&p=29B0CA95AE3FF862&index=0&playnext=1)

I do apologise in advance for the crimes against taste which this singer commits.

I downloaded MPlayer but it said I already had the most up to date version installed.  When I go to open the file it says LAVF_header av_find_stream_info() failed.  Which dfoesn't mean a huge amount :)

---

### Post by Didius Falco on 2009-04-19
> **loobyloo said:**
> Yes, I saved the flv using the extension Mozilla extension UnPlug

I do apologise in advance for the crimes against taste which this singer commits.

I downloaded MPlayer but it said I already had the most up to date version installed.  When I go to open the file it says LAVF_header av_find_stream_info() failed.  Which doesn't mean a huge amount :)

I googled that error, and it mostly seems to be caused by .avi and .flv files, not .mp3's.

Do you have the lame codec installed? It's in the multiverse repo. You can install it from the CLI by running:

```
sudo aptitude install lame
```

I downloaded that flv (I use DownloadHelper) and converted it and it's working in Movie Player, VLC and Rhythmbox.

I'm a little stumped if the lame codec doesn't help...

BTW, I laughed out loud at the "apology". <G>

You won't catch any flack from me, though. I'm originally from the land that spawned Vanilla Ice, so I'll just keep my stones in my own little glass house. ;)

---

### Post by loobyloo on 2009-04-19
Yes, I've got the latest lame.

It's a puzzle, but it's a nice day and I'm going for a walk before I get obssessed about this :)

---

### Post by cotcot on 2009-04-19
Try to install ffmpeg like [[COLOR="Red"]this[/COLOR]]("http://ubuntuforums.org/showthread.php?t=786095"). Ffmpeg from the repos does not have all codecs included because of license issues. The compiled version from the link is ok on that.

---

### Post by loobyloo on 2009-04-19
Thanks, that's very kind of you, but it's too much.  It's not a crucial element to have ffmpeg running on my computer.

---

### Post by FakeOutdoorsman on 2009-04-19
Did you compile FFmpeg yourself?  "SVN-r18532" seems way too recent for a repository FFmpeg.  Here's a command that should work for SVN FFmpeg and will convert your source audio to mp3:
```
ffmpeg -i /home/cliff/Desktop/Sweden-Malena-La_Voix.flv -acodec libmp3lame -ab 192k /home/cliff/Desktop/audio.mp3
```

Didius Falco's suggestion (post 4) didn't work because your source video contains aac audio and that command is trying to force aac into a mp3 container.  The command would work perfectly if the source audio is also mp3.

You also don't need the **lame** package for FFmpeg to encode to mp3.  This is done through libmp3lame which is part of the **libavcodec-unstripped-51** package (for users of the repository FFmpeg), or **libmp3lame-dev** for those who want to compile FFmpeg themselves.  More details:

[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

---

### Post by loobyloo on 2009-04-19
> **FakeOutdoorsman said:**
> Did you compile FFmpeg yourself?  "SVN-r18532" seems way too recent for a repository FFmpeg.  Here's a command that should work for SVN FFmpeg and will convert your source audio to mp3:
```
ffmpeg -i /home/cliff/Desktop/Sweden-Malena-La_Voix.flv -acodec libmp3lame -ab 192k /home/cliff/Desktop/audio.mp3
```

Didius Falco's suggestion (post 4) didn't work because your source video contains aac audio and that command is trying to force aac into a mp3 container.  The command would work perfectly if the source audio is also mp3.

You also don't need the **lame** package for FFmpeg to encode to mp3.  This is done through libmp3lame which is part of the **libavcodec-unstripped-51** package (for users of the repository FFmpeg), or **libmp3lame-dev** for those who want to compile FFmpeg themselves.  More details:

[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

Thank you...I tried that and it came back with

cliff@cliff-laptop:~$ ffmpeg -i /home/cliff/Desktop/Sweden-Malena-La_Voix.flv -acodec libmp3lame -ab 192k /home/cliff/Desktop/audio.mp3
FFmpeg version SVN-r18532, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: 
  libavutil     50. 3. 0 / 50. 3. 0
  libavcodec    52.25. 0 / 52.25. 0
  libavformat   52.32. 0 / 52.32. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libswscale     0. 7. 1 /  0. 7. 1
  built on Apr 16 2009 16:10:36, gcc: 4.3.2
[flv @ 0x8b77b00]skipping flv packet: type 18, size 294, flags 0

Seems stream 0 codec frame rate differs from container frame rate: 50.00 (50/1) -> 25.00 (25/1)
Input #0, flv, from '/home/cliff/Desktop/Sweden-Malena-La_Voix.flv':
  Duration: 00:03:07.61, start: 0.000000, bitrate: N/A
    Stream #0.0: Video: h264, yuv420p, 320x240 [PAR 1:1 DAR 4:3], 25 tbr, 1k tbn, 50 tbc
    Stream #0.1: Audio: aac, 22050 Hz, stereo, s16
Unknown encoder 'libmp3lame'

-------
So in the light of what you said, I checked if I had libavcodec-unstripped-51 or [b]libmp3lame-dev and I've got both.

---

### Post by FakeOutdoorsman on 2009-04-19
Where did you get this FFmpeg from?  There is nothing listed under "configuration", so encoding with libmp3lame has not been enabled.  This looks like a non-repository FFmpeg.

---

### Post by loobyloo on 2009-04-19
I think it was from [http://www.ffmpeg.org/download.html#release](http://www.ffmpeg.org/download.html#release)
I don't know what an SVM is, but that's what I've got.

I look in Synamptic and it said I had ffmpeg, but from some of check update, which probably indicates an update of the "wrong" version that you mentioned.

So I reinstalled it from [https://wiki.ubuntu.com/ffmpeg](https://wiki.ubuntu.com/ffmpeg) using the "Unstripped build of FFmpeg for Ubuntu 8.10 Intrepid". When I tried it again it came back with nothing under configuration and "unknown encoder libmp3lame.

What would be the best place to get ffmpeg from?

---

### Post by FakeOutdoorsman on 2009-04-19
Your computer is still using FFmpeg SVN, but it has not been configured to use any external encoders such as libmp3lame.  If you installed it with checkinstall you can uninstall it via Synaptic, apt-get, or aptitude.  If you simply installed it with "make install", navigate to your ffmpeg directory and then run:
```
sudo make uninstall
```
Now you can install FFmpeg from the repository:
```
sudo apt-get install ffmpeg
```

---

### Post by loobyloo on 2009-04-19
Thanks - it *was* from checkinstall.

I uninstalled it and reinstalled it from the repository.

I tried converting trhe file again and it came up with

Seems stream 0 codec frame rate differs from container frame rate: 1000.00 (1000/1) -> 25.00 (25/1)
Input #0, flv, from '/home/cliff/Desktop/Sweden-Malena-La_Voix.flv':
  Duration: 00:03:07.1, start: 0.000000, bitrate: N/A
    Stream #0.0: Video: 0x0007, 25.00 tb(r)
    Stream #0.1: Audio: 0x000a, 44100 Hz, stereo
Output #0, mp3, to '/home/cliff/Desktop/audio.mp3':
    Stream #0.0: Audio: libmp3lame, 44100 Hz, stereo, 192 kb/s
Stream mapping:
  Stream #0.1 -> #0.0
Unsupported codec (id=0) for input stream #0.1
-----------
So I went to Synaptic and checked for libavcodec-unstripped-51, which was there.

Oh, dear...it's a good job I've got a bottle of red wine about a foot away!

Thanks for all your help so far. I don't know why I'm getting so obssessed about this damn thing.

---

### Post by FakeOutdoorsman on 2009-04-20
Give the full output of:
```
ffmpeg -formats
```
and:
```
dpkg --get-selections | grep libavcodec
```

---

### Post by loobyloo on 2009-04-20
> **FakeOutdoorsman said:**
> Give the full output of:
```
ffmpeg -formats
```
and:
```
dpkg --get-selections | grep libavcodec
```


Hi again - here we go:  

cliff@cliff-laptop:~$ ffmpeg -formats
FFmpeg version r11872+debian_3:0.svn20080206-12ubuntu3.1, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-x11grab --prefix=/usr --enable-libgsm --enable-libtheora --enable-libvorbis --enable-pthreads --disable-strip --enable-libfaad --enable-libfaadbin --enable-liba52 --enable-liba52bin --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil version: 49.6.0
  libavcodec version: 51.50.0
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Mar 13 2009 17:48:10, gcc: 4.3.2
File formats:
  E 3g2             3gp2 format
  E 3gp             3gp format
 D  4xm             4X Technologies format
 D  MTV             MTV format
 DE RoQ             Id RoQ format
 D  aac             ADTS AAC
 DE ac3             raw ac3
  E adts            ADTS AAC
 DE aiff            Audio IFF
 DE alaw            pcm A law format
 DE amr             3gpp amr file format
 D  apc             CRYO APC format
 D  ape             Monkey's Audio
 DE asf             asf format
  E asf_stream      asf format
 DE au              SUN AU Format
 DE avi             avi format
  E avm2            Flash 9 (AVM2) format
 D  avs             avs format
 D  bethsoftvid     Bethesda Softworks 'Daggerfall' VID format
 D  c93             Interplay C93
  E crc             crc testing format
 D  daud            D-Cinema audio format
 D  dsicin          Delphine Software International CIN format
 D  dts             raw dts
 DE dv              DV video format
 D  dv1394          dv1394 A/V grab
  E dvd             MPEG2 PS format (DVD VOB)
 D  dxa             dxa
 D  ea              Electronic Arts Multimedia Format
 D  ea_cdata        Electronic Arts cdata
 DE ffm             ffm format
 D  film_cpk        Sega FILM/CPK format
 DE flac            raw flac
 D  flic            FLI/FLC/FLX animation format
 DE flv             flv format
  E framecrc        framecrc testing format
 DE gif             GIF Animation
 DE gxf             GXF format
 DE h261            raw h261
 DE h263            raw h263
 DE h264            raw H264 video format
 D  idcin           Id CIN format
 DE image2          image2 sequence
 DE image2pipe      piped image2 sequence
 D  ingenient       Ingenient MJPEG
 D  ipmovie         Interplay MVE format
 D  libdc1394       dc1394 v.2 A/V grab
 D  lmlm4           lmlm4 raw format
 DE m4v             raw MPEG4 video format
 DE matroska        Matroska File Format
 DE mjpeg           MJPEG video
 D  mm              American Laser Games MM format
 DE mmf             mmf format
  E mov             mov format
 D  mov,mp4,m4a,3gp,3g2,mj2 QuickTime/MPEG4/Motion JPEG 2000 format
  E mp2             MPEG audio layer 2
 DE mp3             MPEG audio layer 3
  E mp4             mp4 format
 D  mpc             musepack
 D  mpc8            musepack8
 DE mpeg            MPEG1 System format
  E mpeg1video      MPEG video
  E mpeg2video      MPEG2 video
 DE mpegts          MPEG2 transport stream format
 D  mpegtsraw       MPEG2 raw transport stream format
 D  mpegvideo       MPEG video
  E mpjpeg          Mime multipart JPEG format
 DE mulaw           pcm mu law format
 D  mxf             MXF format
 D  nsv             NullSoft Video format
  E null            null video format
 DE nut             nut format
 D  nuv             NuppelVideo format
 DE ogg             Ogg format
 DE oss             audio grab and output
  E psp             psp mp4 format
 D  psxstr          Sony Playstation STR format
 D  pva             pva file and stream format
 DE rawvideo        raw video format
 D  redir           Redirector format
 DE rm              rm format
  E rtp             RTP output format
 D  rtsp            RTSP input format
 DE s16be           pcm signed 16 bit big endian format
 DE s16le           pcm signed 16 bit little endian format
 DE s8              pcm signed 8 bit format
 D  sdp             SDP
 D  shn             raw shorten
 D  siff            Beam Software SIFF
 D  smk             Smacker Video
 D  sol             Sierra SOL Format
  E svcd            MPEG2 PS format (VOB)
 DE swf             Flash format
 D  thp             THP
 D  tiertexseq      Tiertex Limited SEQ format
 D  tta             true-audio
 D  txd             txd format
 DE u16be           pcm unsigned 16 bit big endian format
 DE u16le           pcm unsigned 16 bit little endian format
 DE u8              pcm unsigned 8 bit format
 D  vc1             raw vc1
 D  vc1test         VC1 test bitstream format
  E vcd             MPEG1 System format (VCD)
 D  video4linux     video grab
 D  video4linux2    video grab
 D  vmd             Sierra VMD format
  E vob             MPEG2 PS format (VOB)
 DE voc             Creative Voice File format
 DE wav             wav format
 D  wc3movie        Wing Commander III movie format
 D  wsaud           Westwood Studios audio format
 D  wsvqa           Westwood Studios VQA format
 D  wv              WavPack
 D  x11grab         X11grab
 DE yuv4mpegpipe    YUV4MPEG pipe format

Codecs:
 D V    4xm
 D V D  8bps
 D V    VMware video
 D V D  aasc
  EA    ac3
 D A    adpcm_4xm
 DEA    adpcm_adx
 D A    adpcm_ct
 D A    adpcm_ea
 D A    adpcm_ea_r1
 D A    adpcm_ea_r2
 D A    adpcm_ea_r3
 D A    adpcm_ea_xas
 D A    adpcm_ima_amv
 D A    adpcm_ima_dk3
 D A    adpcm_ima_dk4
 D A    adpcm_ima_ea_eacs
 D A    adpcm_ima_ea_sead
 D A    adpcm_ima_qt
 D A    adpcm_ima_smjpeg
 DEA    adpcm_ima_wav
 D A    adpcm_ima_ws
 DEA    adpcm_ms
 D A    adpcm_sbpro_2
 D A    adpcm_sbpro_3
 D A    adpcm_sbpro_4
 DEA    adpcm_swf
 D A    adpcm_thp
 D A    adpcm_xa
 DEA    adpcm_yamaha
 D A    alac
 D V    amv
 D A    ape
 DEV D  asv1
 DEV D  asv2
 D A    atrac 3
 D V D  avs
 D V    bethsoftvid
 DEV    bmp
 D V D  c93
 D V D  camstudio
 D V D  camtasia
 D V D  cavs
 D V D  cinepak
 D V D  cljr
 D A    cook
 D V D  cyuv
 D A    dca
 DEV D  dnxhd
 D A    dsicinaudio
 D V D  dsicinvideo
 DES    dvbsub
 DES    dvdsub
 DEV D  dvvideo
 D V    dxa
 DEV D  ffv1
 DEVSD  ffvhuff
 DEA    flac
 DEV D  flashsv
 D V D  flic
 DEVSD  flv
 D V D  fraps
 DEA    g726
 DEV    gif
 DEV D  h261
 DEVSDT h263
 D VSD  h263i
  EV    h263p
 D V DT h264
 DEVSD  huffyuv
 D V D  idcinvideo
 D A    imc
 D V D  indeo2
 D V    indeo3
 D A    interplay_dpcm
 D V D  interplayvideo
 DEV D  jpegls
 D V    kmvc
 D A    liba52
  EA    libfaac
 D A    libfaad
 DEA    libgsm
 DEA    libgsm_ms
  EA    libmp3lame
  EV    libtheora
  EA    libvorbis
  EV    libx264
  EV    libxvid
  EV    ljpeg
 D V D  loco
 D A    mace3
 D A    mace6
 D V D  mdec
 DEV D  mjpeg
 D V D  mjpegb
 D V D  mmvideo
 DEA    mp2
 D A    mp3
 D A    mp3adu
 D A    mp3on4
 D A    mpc sv7
 D A    mpc sv8
 DEVSDT mpeg1video
 DEVSDT mpeg2video
 DEVSDT mpeg4
 D A    mpeg4aac
 D VSDT mpegvideo
 DEVSD  msmpeg4
 DEVSD  msmpeg4v1
 DEVSD  msmpeg4v2
 D V D  msrle
 D V D  msvideo1
 D V D  mszh
 D A    nellymoser
 D V D  nuv
 DEV    pam
 DEV    pbm
 DEA    pcm_alaw
 DEA    pcm_mulaw
 DEA    pcm_s16be
 DEA    pcm_s16le
 D A    pcm_s16le_planar
 DEA    pcm_s24be
 DEA    pcm_s24daud
 DEA    pcm_s24le
 DEA    pcm_s32be
 DEA    pcm_s32le
 DEA    pcm_s8
 DEA    pcm_u16be
 DEA    pcm_u16le
 DEA    pcm_u24be
 DEA    pcm_u24le
 DEA    pcm_u32be
 DEA    pcm_u32le
 DEA    pcm_u8
 DEA    pcm_zork
 D V    pcx
 DEV    pgm
 DEV    pgmyuv
 DEV    png
 DEV    ppm
 D V    ptx
 D A    qdm2
 D V D  qdraw
 D V D  qpeg
 DEV D  qtrle
 DEV    rawvideo
 D A    real_144
 D A    real_288
 DEA    roq_dpcm
 DEV D  roqvideo
 D V D  rpza
 DEV D  rv10
 DEV D  rv20
 DEV    sgi
 D A    shorten
 D A    smackaud
 D V    smackvid
 D V D  smc
 DEV    snow
 D A    sol_dpcm
 DEA    sonic
  EA    sonicls
 D V D  sp5x
 D V    sunrast
 DEV D  svq1
 D VSD  svq3
 DEV    targa
 D V    theora
 D V D  thp
 D V D  tiertexseqvideo
 DEV    tiff
 D V D  truemotion1
 D V D  truemotion2
 D A    truespeech
 D A    tta
 D V    txd
 D V D  ultimotion
 D V    vb
 D V    vc1
 D V D  vcr1
 D A    vmdaudio
 D V D  vmdvideo
 DEA    vorbis
 D V    vp3
 D V D  vp5
 D V D  vp6
 D V D  vp6a
 D V D  vp6f
 D V D  vqavideo
 D A    wavpack
 DEA    wmav1
 DEA    wmav2
 DEVSD  wmv1
 DEVSD  wmv2
 D V    wmv3
 D V D  wnv1
 D A    ws_snd1
 D A    xan_dpcm
 D V D  xan_wc3
 D V D  xl
 D S    xsub
 DEV D  zlib
 DEV    zmbv

Bitstream filters:
 text2movsub remove_extra noise mov2textsub mp3decomp mp3comp mjpegadump imxdump h264_mp4toannexb dump_extra
Supported file protocols:
 file: http: pipe: rtp: tcp: udp:
Frame size, frame rate abbreviations:
 ntsc pal qntsc qpal sntsc spal film ntsc-film sqcif qcif cif 4cif

Note, the names of encoders and decoders do not always match, so there are
several cases where the above table shows encoder only or decoder only entries
even though both encoding and decoding are supported. For example, the h263
decoder corresponds to the h263 and h263p encoders, for file formats it is even
worse.

--------------------
And now: 

cliff@cliff-laptop:~$ dpkg --get-selections | grep libavcodec
libavcodec-unstripped-51			install
libavcodec51					deinstall

---

### Post by FakeOutdoorsman on 2009-04-20
This should definitely not be this troublesome.  You have the correct packages installed it seems, and the listed formats indicate that FFmpeg should be able to recognize and decode the aac and h264 streams in your flv, but it obviously is not doing so.  I assume there may be a conflict with another package, but I am unsure.  You could try telling FFmpeg what the audio is supposed to be:
```
ffmpeg -acodec libfaad -i /home/cliff/Desktop/Sweden-Malena-La_Voix.flv -acodec libmp3lame -ab 192k /home/cliff/Desktop/audio.mp3
```

---

### Post by loobyloo on 2009-04-21
Thank you very much - again, the audio appears to output correctly but when I go to play it Rhythmbox reports simply "Not playing" and SMPlayer does nothing at all. I'm just going to leave it now as I have a dissertation to write and children to look after.

Thanks to everyone on this thread for their patience and assistance over the last few days. I do appreciate it.

---

### Post by poe on 2009-06-09
Could it be, that you've got scratchbox installed? Maybe you use an alternative to /usr/bin/ffmpeg, just try this :-) helped me

---

### Post by loobyloo on 2009-06-10
> **poe said:**
> Could it be, that you've got scratchbox installed? Maybe you use an alternative to /usr/bin/ffmpeg, just try this :-) helped me

Hi thanks Poe - I've lost interest in this now to be perfectly honest, but thanks for the suggestion.

---

### Post by maitrebart on 2011-02-06
> **loobyloo said:**
> [...]
In another thread here someone recommended installing the libaveccodec 51 unstripped, which I have done, but the problem persists.  Does anyone know how I can solve this?

I installed the unstripped version 52 and it started working.

---


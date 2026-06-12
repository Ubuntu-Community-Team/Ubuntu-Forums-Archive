---
title: "ffmpeg installation problem"
date: 2011-03-22
forum: New to Ubuntu
---

### Post by nkdnkd on 2011-03-22
hi all,
I am trying to install ffmpeg and the x264 codecs using this guide
> [http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)
However, I ran into some trouble with the make step of the ffmpeg compilation. The error reads as under :-
>  nishith@nishith-Aspire-4720:~/ffmpeg$ make
LD    ffmpeg_g
/home/nishith/ffmpeg/libavcodec/libavcodec.a(libx264.o): In function `X264_init':
/home/nishith/x264/ffmpeg/libavcodec/libx264.c:308: undefined reference to `x264_encoder_open_114'
collect2: ld returned 1 exit status
make: *** [ffmpeg_g] Error 1

can someone plz advice me what to do ?
btw the dir structure is as under
> /home/nishith/x264     -- after a okay compilation and installation
/home/nishith/ffmpeg  -- the config step worked fine but the make is giving above error.

thanks in advance
nishith

---

### Post by FakeOutdoorsman on 2011-03-22
I am guessing that *libx264-dev* is interfering. The first step of the guide should have removed this package. Did you skip that step?  Did you follow the guide word-for-word or did you modify anything? What Ubuntu version are you using?

Try this:
```
sudo apt-get remove libx264-dev
cd ~/ffmpeg
make distclean
git pull
```
Now continue with the FFmpeg *./configure* command as shown in the guide.

---

### Post by nkdnkd on 2011-03-24
thanks for the response,
No I didnot modify the installation steps in the guide. Also I am using ubuntu 10.10.
I donot have the libx264-dev installed presently. The apt-get remove libx264-dev confirmed same.
I am presently getting the following error after I followed the steps suggested in the above post :-
> CC    libavformat/rtspdec.o
libavformat/rtspdec.c: In function &#8216;rtsp_read_play&#8217;:
libavformat/rtspdec.c:62: error: expected expression before &#8216;<<&#8217; token
libavformat/rtspdec.c:76: error: expected expression before &#8216;>>&#8217; token
libavformat/rtspdec.c:76: error: invalid suffix "fd41c9067fc67b40f80e9cbd4787018009040db" on integer constant
make: *** [libavformat/rtspdec.o] Error 1

what else to do ?
thanks
nkd

---

### Post by FakeOutdoorsman on 2011-03-24
I am guessing that a recent commit may have broken compilation. This happens once in a while and is usually fixed quickly. This may fix it:
```
cd ~/ffmpeg
make distclean
git pull
```
Now, once again, continue with the *./configure* command.

---

### Post by nkdnkd on 2011-03-25
thanks a lot for the help.
But it didnot work and still gives the same error. BTW my ubuntu software centre informs me that I have ffmpeg installed as part of gstreamer plugins and also libx264-98. I could find the libx264-98.so file also.
But the problem is whenever I execute the command 
> nishith@nishith-Aspire-4720:~$ ffmpeg -f alsa -ac 2 -i pulse -f x11grab -r 30 -s 1024x768 -i :0.0 -acodec pcm_s16le -vcodec libx264 -vpre lossless_ultrafast -threads 0 output.mkv

I get the following error 
> Input #1, x11grab, from ':0.0':
  Duration: N/A, start: 1301073166.408464, bitrate: 754974 kb/s
    Stream #1.0: Video: rawvideo, bgra, 1024x768, 754974 kb/s, 30 tbr, 1000k tbn, 30 tbc
Unknown encoder 'libx264'

is there anyway I can fix my installation to execute the above command ?
thanks in advance
nishith

---

### Post by FakeOutdoorsman on 2011-03-25
Can you show the complete FFmpeg console output from your command?

---

### Post by nkdnkd on 2011-03-25
the complete output of ffmpeg :-
> nishith@nishith-Aspire-4720:~$ ffmpeg -f alsa -ac 2 -i pulse -f x11grab -r 30 -s 1024x768 -i :0.0 -acodec pcm_s16le -vcodec libx264 -vpre lossless_ultrafast -threads 0 output.mkv 
FFmpeg version 0.6-4:0.6-2ubuntu6, Copyright (c) 2000-2010 the FFmpeg developers
  built on Oct  5 2010 22:35:47 with gcc 4.4.5
  configuration: --extra-version=4:0.6-2ubuntu6 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  WARNING: library configuration mismatch
  libavutil   configuration: --extra-version=4:0.6-2ubuntu6 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavcodec  configuration: --extra-version=4:0.6-2ubuntu6 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavformat configuration: --extra-version=4:0.6-2ubuntu6 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavdevice configuration: --extra-version=4:0.6-2ubuntu6 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavfilter configuration: --extra-version=4:0.6-2ubuntu6 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libswscale  configuration: --extra-version=4:0.6-2ubuntu6 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libpostproc configuration: --extra-version=4:0.6-2ubuntu6 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavutil     50.15. 1 / 50.15. 1
  libavcodec    52.72. 2 / 52.72. 2
  libavformat   52.64. 2 / 52.64. 2
  libavdevice   52. 2. 0 / 52. 2. 0
  libavfilter    1.19. 0 /  1.19. 0
  libswscale     0.11. 0 /  0.11. 0
  libpostproc   51. 2. 0 / 51. 2. 0
[alsa @ 0x88a1420]capture with some ALSA plugins, especially dsnoop, may hang.
[alsa @ 0x88a1420]Estimating duration from bitrate, this may be inaccurate
Input #0, alsa, from 'pulse':
  Duration: N/A, start: 1301078461.990021, bitrate: N/A
    Stream #0.0: Audio: pcm_s16le, 44100 Hz, 2 channels, s16, 1411 kb/s
[x11grab @ 0x88b2fa0]device: :0.0 -> display: :0.0 x: 0 y: 0 width: 1024 height: 768
[x11grab @ 0x88b2fa0]shared memory extension  found
[x11grab @ 0x88b2fa0]Estimating duration from bitrate, this may be inaccurate
Input #1, x11grab, from ':0.0':
  Duration: N/A, start: 1301078462.491795, bitrate: 754974 kb/s
    Stream #1.0: Video: rawvideo, bgra, 1024x768, 754974 kb/s, 30 tbr, 1000k tbn, 30 tbc
Unknown encoder 'libx264'
regards
nishith

---

### Post by FakeOutdoorsman on 2011-03-25
You're using FFmpeg from the repository. If you want to use this then you'll need to enable some additional encoders including libx264. See option B or C in:

[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoders in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

Also, I've been unable to duplicate your *rtspdec* issue.

---

### Post by nkdnkd on 2011-03-30
thanks for the help. I opted to install ffmpeg using the medibuntu repo.
It worked like a charm.
regards
nishith

---


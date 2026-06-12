---
title: "BASH: Stream USB microphone of ALSA to the Intranet?"
date: 2010-09-18
forum: New to Ubuntu
---

### Post by honeybear on 2010-09-18
Hello, 

I usually use : 
```
        arecord -Dplughw:1,0 -f cd -vv file.wav
``` to record from microphone. 

I would like to stream it on a specific port over the intranet. how to simply do it without icecast or vlc or complicated way? Is there something like streaming for mplayer?

---

### Post by honeybear on 2010-09-18
first try with a simple mp3 : 

```
 $ ffmpeg -i test.mp3 -f mp2 http:localhost:8090/feed1.ffm
FFmpeg version SVN-r24504, Copyright (c) 2000-2010 the FFmpeg developers
  built on Jul 26 2010 11:43:14 with gcc 4.4.4
  configuration: '--enable-libdc1394' --prefix='/usr' --extra-cflags='-Wall -g ' --cc='ccache cc' '--enable-shared' '--enable-libmp3lame' '--enable-gpl' '--enable-libvorbis' '--enable-pthreads' '--enable-libfaac' '--enable-libxvid' '--enable-postproc' '--enable-x11grab' '--enable-libgsm' '--enable-libtheora' '--enable-libopencore-amrnb' '--enable-libopencore-amrwb' '--enable-libx264' '--enable-libspeex' '--enable-nonfree' '--disable-stripping' '--enable-avfilter' '--enable-libdirac' '--enable-avfilter-lavf' --disable-decoder='libdirac' '--enable-libschroedinger' --disable-encoder='libschroedinger' '--enable-version3' '--enable-libopenjpeg' '--enable-libvpx' '--enable-librtmp' --extra-libs='-lgcrypt' '--disable-altivec' '--disable-armv5te' '--disable-armv6' '--disable-vis'
  libavutil     50.23. 0 / 50.23. 0
  libavcore      0. 0. 0 /  0. 0. 0
  libavcodec    52.84. 0 / 52.84. 0
  libavformat   52.77. 0 / 52.77. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libavfilter    1.26. 1 /  1.26. 1
  libswscale     0.11. 0 /  0.11. 0
  libpostproc   51. 2. 0 / 51. 2. 0
[mp3 @ 0x97aec30] max_analyze_duration reached
[mp3 @ 0x97aec30] Estimating duration from bitrate, this may be inaccurate
Input #0, mp3, from 'test.mp3':
  Metadata:
    TT2             : Dark Side Of The Moon
    TP1             : Pink Floyd
    TP2             : Pink Floyd
    TAL             : Dark Side Of The Moon
    TRK             : 1/1
    TYE             : 1973
    TCO             : Rock
    TEN             : iTunes 8.0.2
  Duration: 00:42:41.35, start: 0.000000, bitrate: 255 kb/s
    Stream #0.0: Audio: mp3, 44100 Hz, 2 channels, s16, 256 kb/s
Output #0, mp2, to 'http:localhost:8090/feed1.ffm':
  Metadata:
    TSSE            : Lavf52.77.0
    Stream #0.0: Audio: mp2, 44100 Hz, 2 channels, s16, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
Press [q] to stop encoding
```

error :(

---

### Post by honeybear on 2010-09-18
OK, works beetter, now 

I have video over the net

but the delay - time is so huge 

about 10 seconds 


viewer:
> mplayer http://${SERVER}:8090/test.asf 




> 



Port 8090 
# bind to all IPs aliased or not 
BindAddress 0.0.0.0 
# max number of simultaneous clients 
MaxClients 1000 
# max bandwidth per-client (kb/s) 
MaxBandwidth 10000 
# Suppress that if you want to launch ffserver as a daemon. 
NoDaemon 



<Feed feed1.ffm> 
File /tmp/feed1.ffm 
FileMaxSize 20k 

ACL allow localhost
ACL allow 192.168.0.0 192.168.255.255
</Feed> 



<Stream test.asf> 
# the source feed 
Feed feed1.ffm 
# the output stream format - ASF 
Format asf 
VideoCodec msmpeg4 

Author "Me"
Copyright "Super MegaCorp"
Title "Test stream from disk"
Comment "Test comment"
</Stream>


<Stream status.html>
Format status

# Only allow local people to get the status
ACL allow localhost
ACL allow 192.168.0.0 192.168.255.255
</Stream>


> 
killall -e ffserver
killall -e ffserver ffmpeg

rm /tmp/feed1.ffm 
rm /tmp/feed1.ffm 


ffserver -f ffmpeg-server.conf &

ffmpeg -f alsa -i hw:1,0 -r 5 -s 320x240 -f video4linux2 -i /dev/video0  [http://localhost:8090/feed1.ffm](http://localhost:8090/feed1.ffm)


killall -e ffserver





---


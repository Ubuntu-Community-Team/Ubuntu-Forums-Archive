---
title: "Splicing and Pasting Audio to/from Video Files"
date: 2010-09-23
forum: New to Ubuntu
---

### Post by Roger Allott on 2010-09-23
I have two video files which are pretty much identical. They both run for 32 mins 54 secs at 25 frames per second.

**Vid A** - avi - good quality video, audio is barely audible even at max volume.
S-Mpeg 4 v3 (S-Mpeg 4 v3), 1530Kbps, 25.000 fps
MPEG Audio (MPEG-2 Audio layer 3), 32.0 Kbps (CBR), 24.0 KHz, 1 channel, 1 stream

**Vid B** - wmv - inferior quality video, audio good.
WMV2 (WMV2), 512 Kbps, 25.000 fps
WMA (WMA2), 64 Kbps (CBR), 44.1 KHz, 2 channels, 1 stream

What I want to do therefore is to splice out the audio component from Vid B and paste it into Vid A.

I have PiTiVi and Avidemux on my system, but if I need something else I'm quite happy to get it. I prefer to use GUI tools.

Could someone suggest how I go about achieving this?

---

### Post by PriceChild on 2010-09-23
I believe 'ffmpeg' will be what you're after. Reading its manual I believe that you are definitely able to add new audio tracks to video.

I'm afraid I haven't got much personal experience with it though and could only offer what you can read in the manual.

---

### Post by Roger Allott on 2010-09-23
> **PriceChild said:**
> I believe 'ffmpeg' will be what you're after. Reading its manual I believe that you are definitely able to add new audio tracks to video.


Thanks, but before I can add a new audio track, I need to get rid of the one that's there at the moment.

---

### Post by sydbat on 2010-09-23
I find Kdenlive (found via Synaptic) a much better video editor than PiTiVi. You can extract audio from the video and replace it quite easily. As long as they sync, there should be no problem.

---

### Post by acreech on 2010-09-23
I think that this is what you are looking for. 

install ffmpeg 

```
sudo apt-get install ffmpeg
```

Then extract the sound from the video 2

```
Extracting sound from a video, and save it as Mp3

ffmpeg -i source_video.avi -vn -ar 44100 -ac 2 -ab 192 -f mp3 sound.mp3

Explanations :
Source video : source_video.avi
Audio bitrate : 192kb/s
output format : mp3
Generated sound : sound.mp3
```

Delete the sound from video 1 with this

```
ffmpeg -i input.flv -an -vcodec copy output.flv
```

Combine the Video 1 and Sound 2 with this command

```
Mix a video with a sound file

ffmpeg -i son.wav -i video_origine.avi video_finale.mpg
```

good luck

acreech

---

### Post by FakeOutdoorsman on 2010-09-23
> **Roger Allott said:**
> Could someone suggest how I go about achieving this?
You can do this with FFmpeg in one command:
```
ffmpeg -i vida.avi -i vidb.wmv -vcodec copy -acodec copy -map 0:0 -map 1:1 -shortest out.mkv
```
What this does is copy the video from *vida.avi* and the audio from *vidb.wmv* into *out.mkv*.  It does not re-encode anything, so it is quick and preserves the quality of your inputs.  I used the Matroska (MKV) container format in this example because it seems to be able to handle most mixed formats.  AVI may work as well, but I haven't tried that one.

---

### Post by Roger Allott on 2010-09-24
Many thanks for all of your suggestions, chaps. Sorry I haven't responded sooner, but I found that I had to be in Windoze all day yesterday so couldn't implement any ideas.

My first attempt is to use the one line code offered by FakeOutdoorsman. Unfortunately, I got errors and the resulting mkv file is 0 bytes.

```
:~$ ffmpeg -i vida.avi -i vidb.wmv -vcodec copy -acodec copy -map 0:0 -map 1:1 -shortest vidc.mkv
FFmpeg version SVN-r19352-4:0.5+svn20090706-2ubuntu2.2, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5+svn20090706-2ubuntu2.2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --extra-cflags=-I/build/buildd/ffmpeg-0.5+svn20090706/debian/include --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Apr 23 2010 15:05:49, gcc: 4.4.1
Input #0, avi, from 'vida.avi':
  Duration: 00:32:54.32, start: 0.000000, bitrate: 1571 kb/s
    Stream #0.0: Video: msmpeg4, yuv420p, 512x384, 25 tbr, 25 tbn, 25 tbc
    Stream #0.1: Audio: mp3, 24000 Hz, mono, s16, 32 kb/s

Seems stream 1 codec frame rate differs from container frame rate: 1000.00 (1000/1) -> 25.00 (25/1)
Input #1, asf, from 'vidb.wmv':
  Duration: 00:32:50.93, start: 3.000000, bitrate: 579 kb/s
    Stream #1.0: Audio: wmav2, 44100 Hz, stereo, s16, 64 kb/s
    Stream #1.1: Video: wmv2, yuv420p, 400x300, 512 kb/s, 25 tbr, 1k tbn, 1k tbc
Output #0, matroska, to 'vidc.mkv':
    Stream #0.0: Video: 0x0000, q=2-31, 200 kb/s, 90k tbn
    Stream #0.1: Audio: 0x0000, 44100 Hz, stereo, s16, 64 kb/s
Codec type mismatch for mapping #1.1 -> #0.1
```

It's odd that the durations for the elements are a few seconds different, because that's certainly not what's being reported when I get the Properties screen up when I right-click the vids.

---

### Post by Roger Allott on 2010-09-24
> **acreech said:**
> 
Then extract the sound from the video 2

```
Extracting sound from a video, and save it as Mp3

ffmpeg -i source_video.avi -vn -ar 44100 -ac 2 -ab 192 -f mp3 sound.mp3

Explanations :
Source video : source_video.avi
Audio bitrate : 192kb/s
output format : mp3
Generated sound : sound.mp3
```


This stage implemented well, except the first time I tried it I got a warning message telling me the bitrate was set too low, as the -ab parameter takes arguments in bps, not kbps.

On that first pass, it overrode the 192 setting and forced its default value of 128 kbps.

I think you're right though that it makes sense for the interim files to be quite highly encoded, so I re-ran it with -ab 192000.

Onto stage 2....

---

### Post by Roger Allott on 2010-09-24
> **acreech said:**
> 
Combine the Video 1 and Sound 2 with this command

```
Mix a video with a sound file

ffmpeg -i son.wav -i video_origine.avi video_finale.mpg
```


It was all going rather well until this final stage!

My two input files were:
vida-muted.avi (361.3 Mb)
vidb.mp3 (45.2 Mb)

So logically, the combined file (vidc.avi) should be about 406.5 Mb, but it turns out to be just 65.3 Mb, and when I play it the video quality is poor.

Unwanted re-encoding and quite severe compression has occured for reasons I don't understand. Can you tell why?

Do I need to add "-acodec copy -vcodec copy" to the command?

This is what Terminal displayed while it was processing:
```
:~$ ffmpeg -i vidb.mp3 -i vida-muted.avi vidc.avi
FFmpeg version SVN-r19352-4:0.5+svn20090706-2ubuntu2.2, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5+svn20090706-2ubuntu2.2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --extra-cflags=-I/build/buildd/ffmpeg-0.5+svn20090706/debian/include --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Apr 23 2010 15:05:49, gcc: 4.4.1
Input #0, mp3, from 'vidb.mp3':
  Duration: 00:32:54.49, start: 0.000000, bitrate: 191 kb/s
    Stream #0.0: Audio: mp3, 44100 Hz, stereo, s16, 192 kb/s
Input #1, avi, from 'vida-muted.avi':
  Duration: 00:32:54.32, start: 0.000000, bitrate: 1535 kb/s
    Stream #1.0: Video: msmpeg4, yuv420p, 512x384, 25 tbr, 25 tbn, 25 tbc
Output #0, avi, to 'vidc.avi':
    Stream #0.0: Video: mpeg4, yuv420p, 512x384, q=2-31, 200 kb/s, 90k tbn, 25 tbc
    Stream #0.1: Audio: mp2, 44100 Hz, stereo, s16, 64 kb/s
Stream mapping:
  Stream #1.0 -> #0.0
  Stream #0.0 -> #0.1
Press [q] to stop encoding
frame=25036 fps=180 q=18.3 size=   32944kB time=1001.40 bitrate= 269.5kbits/s   frame=25119 fps=180 q=14.8 size=   33044kB time=1004.72 bitrate= 269.4kbits/s   frame=25201 fps=180 q=13.6 size=   33145kB time=1008.01 bitrate= 269.4kbits/s   frame=25280 fps=180 q=23.0 size=   33252kB time=1011.17 bitrate= 269.4kbits/s   frame=25363 fps=180 q=17.7 size=   33361kB time=1014.49 bitrate= 269.4kbits/s   frame=25445 fps=180 q=16.5 size=   33473kB time=1017.80 bitrate= 269.4kbits/s   frame=25530 fps=180 q=15.1 size=   33583kB time=1021.18 bitrate= 269.4kbits/s   frame=25615 fps=179 q=19.2 size=   33696kB time=1024.57 bitrate= 269.4kbits/s   frame=25697 fps=179 q=18.5 size=   33807kB time=1027.84 bitrate= 269.4kbits/s   frame=25780 fps=179 q=17.6 size=   33918kB time=1031.18 bitrate= 269.5kbits/s   frame=25845 fps=179 q=23.2 size=   34006kB time=1033.80 bitrate= 269.5kbits/s   frame=25907 fps=179 q=19.9 size=   34090kB time=1036.25 bitrate= 269.5kbits/s   frame=25975 fps=179 q=18.7 size=   34174kB time=1038.99 bitrate= 269.4kbits/s   frame=26038 fps=179 q=21.7 size=   34253kB time=1041.50 bitrate= 269.4kbits/s   frame=26106 fps=179 q=13.3 size=   34338kB time=1044.22 bitrate= 269.4kbits/s   frame=26173 fps=178 q=17.7 size=   34418kB time=1046.88 bitrate= 269.3kbits/s   frame=26238 fps=178 q=18.8 size=   34505kB time=1049.50 bitrate= 269.3kbits/s   frame=26326 fps=178 q=17.6 size=   34616kB time=1053.02 bitrate= 269.3kbits/s   frame=26415 fps=178 q=16.4 size=   34731kB time=1056.57 bitrate= 269.3kbits/s   frame=26499 fps=178 q=13.9 size=   34844kB time=1059.94 bitrate= 269.3kbits/s   frame=26589 fps=178 q=11.1 size=   34959kB time=1063.52 bitrate= 269.3kbits/s   frame=26677 fps=178 q=11.2 size=   35086kB time=1067.05 bitrate= 269.4kbits/s   frame=26750 fps=178 q=13.2 size=   35198kB time=1069.98 bitrate= 269.5kbits/s   frame=26817 fps=178 q=11.3 size=   35287kB time=1072.64 bitrate= 269.5kbits/s   frame=26888 fps=178 q=14.4 size=   35388kB time=1075.49 bitrate= 269.6kbits/s   frame=26959 fps=178 q=14.4 size=   35487kB time=1078.33 bitrate= 269.6kbits/s   frame=27031 fps=178 q=12.6 size=   35585kB time=1081.21 bitrate= 269.6kbits/s   frame=27101 fps=177 q=12.8 size=   35683kB time=1084.00 bitrate= 269.7kbits/s   frame=27190 fps=177 q=23.3 size=   35803kB time=1087.58 bitrate= 269.7kbits/s   frame=27277 fps=177 q=14.4 size=   35916kB time=1091.06 bitrate= 269.7kbits/s   frame=27368 fps=177 q=22.4 size=   36038kB time=1094.69 bitrate= 269.7kbits/s   frame=27455 fps=177 q=16.9 size=   36154kB time=1098.16 bitrate= 269.7kbits/s   frame=27541 fps=177 q=15.7 size=   36268kB time=1101.61 bitrate= 269.7kbits/s   frame=27629 fps=177 q=18.1 size=   36388kB time=1105.14 bitrate= 269.7kbits/s   frame=27716 fps=177 q=17.6 size=   36501kB time=1108.64 bitrate= 269.7kbits/s   frame=27801 fps=177 q=21.6 size=   36613kB time=1112.04 bitrate= 269.7kbits/s   frame=27888 fps=177 q=21.7 size=   36724kB time=1115.48 bitrate= 269.7kbits/s   frame=27975 fps=177 q=19.3 size=   36841kB time=1118.98 bitrate= 269.7kbits/s   frame=28061 fps=177 q=20.4 size=   36953kB time=1122.40 bitrate= 269.7kbits/s   frame=28147 fps=177 q=16.7 size=   37058kB time=1125.85 bitrate= 269.6kbits/s   frame=28233 fps=177 q=13.1 size=   37164kB time=1129.30 bitrate= 269.6kbits/s   frame=28323 fps=177 q=12.0 size=   37285kB time=1132.90 bitrate= 269.6kbits/s   frame=28404 fps=177 q=13.4 size=   37386kB time=1136.14 bitrate= 269.6kbits/s   frame=28469 fps=177 q=21.5 size=   37478kB time=1138.76 bitrate= 269.6kbits/s   frame=28537 fps=177 q=14.5 size=   37565kB time=1141.45 bitrate= 269.6kbits/s   frame=28603 fps=177 q=13.6 size=   37658kB time=1144.08 bitrate= 269.6kbits/s   frame=28666 fps=177 q=13.6 size=   37741kB time=1146.62 bitrate= 269.6kbits/s   frame=28735 fps=176 q=15.5 size=   37838kB time=1149.36 bitrate= 269.7kbits/s   frame=28790 fps=176 q=19.1 size=   37912kB time=1151.58 bitrate= 269.7kbits/s   frame=28880 fps=176 q=19.2 size=   38037kB time=1155.16 bitrate= 269.7kbits/s   frame=28974 fps=176 q=21.1 size=   38166kB time=1158.95 bitrate= 269.8kbits/s   frame=29062 fps=176 q=18.6 size=   38281kB time=1162.48 bitrate= 269.8kbits/s   frame=29149 fps=176 q=19.4 size=   38395kB time=1165.92 bitrate= 269.8kbits/s   frame=29231 fps=176 q=27.9 size=   38506kB time=1169.24 bitrate= 269.8kbits/s   frame=29318 fps=176 q=19.5 size=   38620kB time=1172.69 bitrate= 269.8kbits/s   frame=29404 fps=176 q=19.2 size=   38737kB time=1176.14 bitrate= 269.8kbits/s   frame=29490 fps=176 q=24.2 size=   38849kB time=1179.59 bitrate= 269.8kbits/s   frame=29562 fps=176 q=22.8 size=   38942kB time=1182.46 bitrate= 269.8kbits/s   frame=29630 fps=176 q=15.6 size=   39025kB time=1185.18 bitrate= 269.7kbits/s   frame=29700 fps=176 q=22.5 size=   39117kB time=1187.97 bitrate= 269.7kbits/s   frame=29771 fps=176 q=23.6 size=   39210kB time=1190.82 bitrate= 269.7kbits/s   frame=29843 fps=176 q=17.9 size=   39303kB time=1193.69 bitrate= 269.7kbits/s   frame=29912 fps=176 q=20.1 size=   39394kB time=1196.46 bitrate= 269.7kbits/s   frame=29984 fps=175 q=31.0 size=   39492kB time=1199.33 bitrate= 269.7kbits/s   frame=30056 fps=175 q=27.5 size=   39577kB time=1202.21 bitrate= 269.7kbits/s   frame=30127 fps=175 q=23.3 size=   39660kB time=1205.05 bitrate= 269.6kbits/s   frame=30198 fps=175 q=18.3 size=   39743kB time=1207.92 bitrate= 269.5kbits/s   frame=30270 fps=175 q=29.5 size=   39841kB time=1210.78 bitrate= 269.6kbits/s   frame=30342 fps=175 q=24.5 size=   39932kB time=1213.65 bitrate= 269.5kbits/s   frame=30409 fps=175 q=29.8 size=   40024kB time=1216.34 bitrate= 269.6kbits/s   frame=30479 fps=175 q=18.8 size=   40109kB time=1219.13 bitrate= 269.5kbits/s   frame=30551 fps=175 q=25.2 size=   40200kB time=1222.01 bitrate= 269.5kbits/s   frame=30622 fps=175 q=23.9 size=   40292kB time=1224.86 bitrate= 269.5kbits/s   frame=30698 fps=175 q=13.5 size=   40397kB time=1227.89 bitrate= 269.5kbits/s   frame=30771 fps=174 q=21.9 size=   40497kB time=1230.81 bitrate= 269.5kbits/s   frame=30846 fps=174 q=18.5 size=   40597kB time=1233.82 bitrate= 269.5kbits/s   frame=30922 fps=174 q=19.0 size=   40695kB time=1236.85 bitrate= 269.5kbits/s   frame=30995 fps=174 q=19.9 size=   40790kB time=1239.77 bitrate= 269.5kbits/s   frame=31067 fps=174 q=20.1 size=   40885kB time=1242.67 bitrate= 269.5kbits/s   frame=31143 fps=174 q=26.8 size=   40988kB time=1245.70 bitrate= 269.5kbits/s   frame=31216 fps=174 q=20.6 size=   41081kB time=1248.60 bitrate= 269.5kbits/s   frame=31288 fps=174 q=25.7 size=   41171kB time=1251.50 bitrate= 269.5kbits/s   frame=31360 fps=174 q=16.6 size=   41267kB time=1254.37 bitrate= 269.5kbits/s   frame=31433 fps=174 q=21.2 size=   41365kB time=1257.30 bitrate= 269.5kbits/s   frame=31506 fps=174 q=30.5 size=   41463kB time=1260.23 bitrate= 269.5kbits/s   frame=31576 fps=174 q=24.3 size=   41560kB time=1263.04 bitrate= 269.6kbits/s   frame=31647 fps=173 q=27.4 size=   41661kB time=1265.84 bitrate= 269.6kbits/s   frame=31722 fps=173 q=18.4 size=   41763kB time=1268.85 bitrate= 269.6kbits/s   frame=31799 fps=173 q=22.2 size=   41863kB time=1271.93 bitrate= 269.6kbits/s   frame=31873 fps=173 q=17.3 size=   41960kB time=1274.88 bitrate= 269.6kbits/s   frame=31948 fps=173 q=25.6 size=   42066kB time=1277.92 bitrate= 269.7kbits/s   frame=32021 fps=173 q=19.6 size=   42161kB time=1280.81 bitrate= 269.7kbits/s   frame=32096 fps=173 q=25.5 size=   42248kB time=1283.81 bitrate= 269.6kbits/s   frame=32170 fps=173 q=19.9 size=   42337kB time=1286.77 bitrate= 269.5kbits/s   frame=32248 fps=173 q=16.9 size=   42428kB time=1289.90 bitrate= 269.5kbits/s   frame=32324 fps=173 q=21.9 size=   42519kB time=1292.96 bitrate= 269.4kbits/s   frame=32401 fps=173 q=16.5 size=   42616kB time=1296.01 bitrate= 269.4kbits/s   frame=32480 fps=173 q=13.6 size=   42706kB time=1299.17 bitrate= 269.3kbits/s   frame=32554 fps=173 q=13.9 size=   42802kB time=1302.16 bitrate= 269.3kbits/s   frame=32631 fps=173 q=16.8 size=   42901kB time=1305.21 bitrate= 269.3kbits/s   frame=32703 fps=173 q=19.9 size=   43001kB time=1308.08 bitrate= 269.3kbits/s   frame=32777 fps=173 q=16.9 size=   43101kB time=1311.06 bitrate= 269.3kbits/s   frame=32850 fps=172 q=18.3 size=   43198kB time=1313.99 bitrate= 269.3kbits/s   frame=32926 fps=172 q=13.8 size=   43289kB time=1317.02 bitrate= 269.3kbits/s   frame=33003 fps=172 q=13.1 size=   43384kB time=1320.10 bitrate= 269.2kbits/s   frame=33076 fps=172 q=13.7 size=   43469kB time=1323.04 bitrate= 269.2kbits/s   frame=33153 fps=172 q=15.2 size=   43561kB time=1326.08 bitrate= 269.1kbits/s   frame=33229 fps=172 q=15.1 size=   43657kB time=1329.14 bitrate= 269.1kbits/s   frame=33299 fps=172 q=15.7 size=   43743kB time=1331.96 bitrate= 269.0kbits/s   frame=33373 fps=172 q=19.8 size=   43848kB time=1334.88 bitrate= 269.1kbits/s   frame=33448 fps=172 q=18.8 size=   43953kB time=1337.92 bitrate= 269.1kbits/s   frame=33524 fps=172 q=16.9 size=   44055kB time=1340.94 bitrate= 269.1kbits/s   frame=33599 fps=172 q=17.4 size=   44157kB time=1343.92 bitrate= 269.2kbits/s   frame=33675 fps=172 q=18.9 size=   44264kB time=1346.98 bitrate= 269.2kbits/s   frame=33750 fps=172 q=22.5 size=   44368kB time=1349.98 bitrate= 269.2kbits/s   frame=33824 fps=172 q=15.5 size=   44467kB time=1352.93 bitrate= 269.2kbits/s   frame=33901 fps=172 q=16.9 size=   44572kB time=1356.02 bitrate= 269.3kbits/s   frame=33973 fps=172 q=28.6 size=   44674kB time=1358.89 bitrate= 269.3kbits/s   frame=34045 fps=172 q=23.9 size=   44773kB time=1361.76 bitrate= 269.3kbits/s   frame=34117 fps=171 q=19.5 size=   44869kB time=1364.66 bitrate= 269.3kbits/s   frame=34188 fps=171 q=15.8 size=   44957kB time=1367.48 bitrate= 269.3kbits/s   frame=34262 fps=171 q=20.2 size=   45055kB time=1370.46 bitrate= 269.3kbits/s   frame=34334 fps=171 q=22.9 size=   45152kB time=1373.34 bitrate= 269.3kbits/s   frame=34409 fps=171 q=17.1 size=   45247kB time=1376.34 bitrate= 269.3kbits/s   frame=34485 fps=171 q=21.1 size=   45342kB time=1379.37 bitrate= 269.3kbits/s   frame=34557 fps=171 q=27.1 size=   45435kB time=1382.24 bitrate= 269.3kbits/s   frame=34631 fps=171 q=19.1 size=   45536kB time=1385.24 bitrate= 269.3kbits/s   frame=34705 fps=171 q=18.0 size=   45637kB time=1388.17 bitrate= 269.3kbits/s   frame=34783 fps=171 q=20.5 size=   45742kB time=1391.28 bitrate= 269.3kbits/s   frame=34861 fps=171 q=18.7 size=   45848kB time=1394.42 bitrate= 269.4kbits/s   frame=34939 fps=171 q=18.2 size=   45949kB time=1397.52 bitrate= 269.3kbits/s   frame=35018 fps=171 q=15.0 size=   46057kB time=1400.71 bitrate= 269.4kbits/s   frame=35097 fps=171 q=20.8 size=   46159kB time=1403.85 bitrate= 269.4kbits/s   frame=35172 fps=171 q=15.6 size=   46262kB time=1406.85 bitrate= 269.4kbits/s   frame=35251 fps=171 q=16.8 size=   46371kB time=1410.01 bitrate= 269.4kbits/s   frame=35328 fps=171 q=16.9 size=   46474kB time=1413.09 bitrate= 269.4kbits/s   frame=35407 fps=171 q=25.9 size=   46583kB time=1416.25 bitrate= 269.4kbits/s   frame=35481 fps=171 q=19.8 size=   46683kB time=1419.24 bitrate= 269.5kbits/s   frame=35562 fps=171 q=16.9 size=   46790kB time=1422.45 bitrate= 269.5kbits/s   frame=35640 fps=170 q=17.3 size=   46891kB time=1425.58 bitrate= 269.5kbits/s   frame=35717 fps=170 q=23.1 size=   46997kB time=1428.68 bitrate= 269.5kbits/s   frame=35796 fps=170 q=17.9 size=   47097kB time=1431.82 bitrate= 269.5kbits/s   frame=35876 fps=170 q=20.3 size=   47203kB time=1435.01 bitrate= 269.5kbits/s   frame=35955 fps=170 q=20.1 size=   47309kB time=1438.17 bitrate= 269.5kbits/s   frame=36033 fps=170 q=23.4 size=   47411kB time=1441.28 bitrate= 269.5kbits/s   frame=36111 fps=170 q=20.1 size=   47512kB time=1444.44 bitrate= 269.5kbits/s   frame=36189 fps=170 q=16.8 size=   47609kB time=1447.52 bitrate= 269.4kbits/s   frame=36265 fps=170 q=27.3 size=   47711kB time=1450.58 bitrate= 269.4kbits/s   frame=36342 fps=170 q=21.4 size=   47803kB time=1453.66 bitrate= 269.4kbits/s   frame=36419 fps=170 q=19.4 size=   47898kB time=1456.74 bitrate= 269.4kbits/s   frame=36495 fps=170 q=20.0 size=   47997kB time=1459.77 bitrate= 269.4kbits/s   frame=36571 fps=170 q=22.9 size=   48093kB time=1462.80 bitrate= 269.3kbits/s   frame=36647 fps=170 q=20.2 size=   48188kB time=1465.86 bitrate= 269.3kbits/s   frame=36723 fps=170 q=18.1 size=   48282kB time=1468.89 bitrate= 269.3kbits/s   frame=36801 fps=170 q=15.5 size=   48375kB time=1472.00 bitrate= 269.2kbits/s   frame=36879 fps=170 q=19.2 size=   48469kB time=1475.13 bitrate= 269.2kbits/s   frame=36957 fps=170 q=14.8 size=   48562kB time=1478.24 bitrate= 269.1kbits/s   frame=37034 fps=170 q=17.5 size=   48660kB time=1481.35 bitrate= 269.1kbits/s   frame=37104 fps=170 q=15.0 size=   48745kB time=1484.12 bitrate= 269.1kbits/s   frame=37186 fps=170 q=12.6 size=   48864kB time=1487.44 bitrate= 269.1kbits/s   frame=37269 fps=170 q=15.2 size=   48981kB time=1490.76 bitrate= 269.2kbits/s   frame=37343 fps=170 q=19.5 size=   49085kB time=1493.68 bitrate= 269.2kbits/s   frame=37418 fps=170 q=20.5 size=   49193kB time=1496.71 bitrate= 269.3kbits/s   frame=37495 fps=170 q=19.7 size=   49307kB time=1499.77 bitrate= 269.3kbits/s   frame=37575 fps=170 q=14.4 size=   49416kB time=1502.98 bitrate= 269.3kbits/s   frame=37656 fps=170 q=16.8 size=   49528kB time=1506.22 bitrate= 269.4kbits/s   frame=37734 fps=170 q=22.6 size=   49639kB time=1509.36 bitrate= 269.4kbits/s   frame=37812 fps=169 q=23.3 size=   49739kB time=1512.46 bitrate= 269.4kbits/s   frame=37890 fps=169 q=20.7 size=   49844kB time=1515.57 bitrate= 269.4kbits/s   frame=37963 fps=169 q=24.7 size=   49942kB time=1518.50 bitrate= 269.4kbits/s   frame=38041 fps=169 q=22.1 size=   50044kB time=1521.61 bitrate= 269.4kbits/s   frame=38118 fps=169 q=22.6 size=   50149kB time=1524.69 bitrate= 269.4kbits/s   frame=38195 fps=169 q=23.3 size=   50250kB time=1527.80 bitrate= 269.4kbits/s   frame=38272 fps=169 q=20.2 size=   50354kB time=1530.85 bitrate= 269.5kbits/s   frame=38349 fps=169 q=18.6 size=   50451kB time=1533.94 bitrate= 269.4kbits/s   frame=38427 fps=169 q=22.3 size=   50552kB time=1537.04 bitrate= 269.4kbits/s   frame=38506 fps=169 q=24.5 size=   50659kB time=1540.21 bitrate= 269.4kbits/s   frame=38583 fps=169 q=21.2 size=   50760kB time=1543.29 bitrate= 269.4kbits/s   frame=38658 fps=169 q=23.5 size=   50861kB time=1546.29 bitrate= 269.5kbits/s   frame=38736 fps=169 q=20.6 size=   50957kB time=1549.44 bitrate= 269.4kbits/s   frame=38814 fps=169 q=18.3 size=   51058kB time=1552.54 bitrate= 269.4kbits/s   frame=38890 fps=169 q=23.3 size=   51156kB time=1555.59 bitrate= 269.4kbits/s   frame=38966 fps=169 q=31.0 size=   51254kB time=1558.64 bitrate= 269.4kbits/s   frame=39039 fps=169 q=23.3 size=   51347kB time=1561.52 bitrate= 269.4kbits/s   frame=39117 fps=169 q=17.5 size=   51452kB time=1564.66 bitrate= 269.4kbits/s   frame=39199 fps=169 q=16.0 size=   51559kB time=1567.92 bitrate= 269.4kbits/s   frame=39280 fps=169 q=16.8 size=   51665kB time=1571.19 bitrate= 269.4kbits/s   frame=39354 fps=169 q=21.8 size=   51765kB time=1574.14 bitrate= 269.4kbits/s   frame=39433 fps=169 q=22.7 size=   51867kB time=1577.30 bitrate= 269.4kbits/s   frame=39508 fps=169 q=20.2 size=   51969kB time=1580.30 bitrate= 269.4kbits/s   frame=39587 fps=169 q=19.1 size=   52069kB time=1583.46 bitrate= 269.4kbits/s   frame=39667 fps=169 q=19.5 size=   52174kB time=1586.65 bitrate= 269.4kbits/s   frame=39742 fps=169 q=31.0 size=   52278kB time=1589.66 bitrate= 269.4kbits/s   frame=39813 fps=169 q=26.1 size=   52370kB time=1592.50 bitrate= 269.4kbits/s   frame=39887 fps=169 q=30.8 size=   52470kB time=1595.45 bitrate= 269.4kbits/s   frame=39961 fps=168 q=19.9 size=   52563kB time=1598.41 bitrate= 269.4kbits/s   frame=40043 fps=168 q=20.0 size=   52663kB time=1601.70 bitrate= 269.3kbits/s   frame=40121 fps=168 q=24.5 size=   52764kB time=1604.81 bitrate= 269.3kbits/s   frame=40197 fps=168 q=27.3 size=   52862kB time=1607.86 bitrate= 269.3kbits/s   frame=40268 fps=168 q=17.9 size=   52957kB time=1610.72 bitrate= 269.3kbits/s   frame=40344 fps=168 q=21.0 size=   53056kB time=1613.74 bitrate= 269.3kbits/s   frame=40417 fps=168 q=15.8 size=   53150kB time=1616.68 bitrate= 269.3kbits/s   frame=40496 fps=168 q=20.0 size=   53256kB time=1619.80 bitrate= 269.3kbits/s   frame=40572 fps=168 q=17.2 size=   53353kB time=1622.86 bitrate= 269.3kbits/s   frame=40652 fps=168 q=25.1 size=   53461kB time=1626.04 bitrate= 269.3kbits/s   frame=40728 fps=168 q=18.5 size=   53559kB time=1629.10 bitrate= 269.3kbits/s   frame=40808 fps=168 q=23.3 size=   53667kB time=1632.29 bitrate= 269.3kbits/s   frame=40884 fps=168 q=27.7 size=   53767kB time=1635.34 bitrate= 269.3kbits/s   frame=40957 fps=168 q=22.5 size=   53860kB time=1638.24 bitrate= 269.3kbits/s   frame=41036 fps=168 q=15.9 size=   53961kB time=1641.40 bitrate= 269.3kbits/s   frame=41114 fps=168 q=23.4 size=   54062kB time=1644.54 bitrate= 269.3kbits/s   frame=41185 fps=168 q=22.9 size=   54152kB time=1647.36 bitrate= 269.3kbits/s   frame=41258 fps=168 q=17.2 size=   54242kB time=1650.29 bitrate= 269.3kbits/s   frame=41333 fps=168 q=25.1 size=   54347kB time=1653.32 bitrate= 269.3kbits/s   frame=41407 fps=168 q=31.0 size=   54447kB time=1656.24 bitrate= 269.3kbits/s   frame=41482 fps=168 q=25.4 size=   54548kB time=1659.25 bitrate= 269.3kbits/s   frame=41557 fps=168 q=24.8 size=   54649kB time=1662.28 bitrate= 269.3kbits/s   frame=41634 fps=168 q=15.2 size=   54749kB time=1665.33 bitrate= 269.3kbits/s   frame=41714 fps=168 q=19.4 size=   54848kB time=1668.55 bitrate= 269.3kbits/s   frame=41795 fps=168 q=15.6 size=   54951kB time=1671.78 bitrate= 269.3kbits/s   frame=41876 fps=168 q=12.4 size=   55057kB time=1675.02 bitrate= 269.3kbits/s   frame=41954 fps=168 q=16.2 size=   55157kB time=1678.13 bitrate= 269.3kbits/s   frame=42031 fps=168 q=18.4 size=   55261kB time=1681.21 bitrate= 269.3kbits/s   frame=42108 fps=168 q=19.6 size=   55369kB time=1684.30 bitrate= 269.3kbits/s   frame=42184 fps=168 q=26.3 size=   55474kB time=1687.33 bitrate= 269.3kbits/s   frame=42261 fps=168 q=21.0 size=   55574kB time=1690.41 bitrate= 269.3kbits/s   frame=42341 fps=168 q=22.2 size=   55678kB time=1693.62 bitrate= 269.3kbits/s   frame=42420 fps=167 q=21.7 size=   55783kB time=1696.78 bitrate= 269.3kbits/s   frame=42497 fps=167 q=23.6 size=   55884kB time=1699.87 bitrate= 269.3kbits/s   frame=42571 fps=167 q=28.2 size=   55981kB time=1702.82 bitrate= 269.3kbits/s   frame=42649 fps=167 q=16.6 size=   56081kB time=1705.93 bitrate= 269.3kbits/s   frame=42734 fps=167 q=17.0 size=   56171kB time=1709.32 bitrate= 269.2kbits/s   frame=42813 fps=167 q=15.5 size=   56278kB time=1712.48 bitrate= 269.2kbits/s   frame=42889 fps=167 q=21.7 size=   56387kB time=1715.56 bitrate= 269.3kbits/s   frame=42967 fps=167 q=22.4 size=   56490kB time=1718.65 bitrate= 269.3kbits/s   frame=43044 fps=167 q=20.2 size=   56593kB time=1721.73 bitrate= 269.3kbits/s   frame=43120 fps=167 q=27.8 size=   56700kB time=1724.80 bitrate= 269.3kbits/s   frame=43195 fps=167 q=25.6 size=   56800kB time=1727.76 bitrate= 269.3kbits/s   frame=43266 fps=167 q=27.7 size=   56894kB time=1730.61 bitrate= 269.3kbits/s   frame=43332 fps=167 q=24.8 size=   56981kB time=1733.25 bitrate= 269.3kbits/s   frame=43407 fps=167 q=24.4 size=   57083kB time=1736.28 bitrate= 269.3kbits/s   frame=43481 fps=167 q=27.0 size=   57179kB time=1739.21 bitrate= 269.3kbits/s   frame=43558 fps=167 q=25.2 size=   57280kB time=1742.29 bitrate= 269.3kbits/s   frame=43634 fps=167 q=20.7 size=   57383kB time=1745.35 bitrate= 269.3kbits/s   frame=43710 fps=167 q=18.2 size=   57479kB time=1748.38 bitrate= 269.3kbits/s   frame=43790 fps=167 q=16.3 size=   57584kB time=1751.56 bitrate= 269.3kbits/s   frame=43871 fps=167 q=17.3 size=   57675kB time=1754.80 bitrate= 269.2kbits/s   frame=43949 fps=167 q=19.3 size=   57775kB time=1757.94 bitrate= 269.2kbits/s   frame=44026 fps=167 q=21.4 size=   57881kB time=1761.02 bitrate= 269.3kbits/s   frame=44106 fps=167 q=18.0 size=   57983kB time=1764.21 bitrate= 269.2kbits/s   frame=44181 fps=167 q=24.6 size=   58088kB time=1767.21 bitrate= 269.3kbits/s   frame=44256 fps=167 q=26.3 size=   58191kB time=1770.21 bitrate= 269.3kbits/s   frame=44332 fps=167 q=27.0 size=   58292kB time=1773.24 bitrate= 269.3kbits/s   frame=44410 fps=167 q=22.9 size=   58395kB time=1776.38 bitrate= 269.3kbits/s   frame=44488 fps=167 q=19.0 size=   58494kB time=1779.49 bitrate= 269.3kbits/s   frame=44566 fps=167 q=22.1 size=   58599kB time=1782.62 bitrate= 269.3kbits/s   frame=44642 fps=167 q=24.8 size=   58694kB time=1785.65 bitrate= 269.3kbits/s   frame=44718 fps=167 q=23.8 size=   58793kB time=1788.68 bitrate= 269.3kbits/s   frame=44794 fps=167 q=20.8 size=   58891kB time=1791.74 bitrate= 269.3kbits/s   frame=44870 fps=167 q=23.3 size=   58988kB time=1794.77 bitrate= 269.2kbits/s   frame=44947 fps=167 q=27.1 size=   59090kB time=1797.85 bitrate= 269.2kbits/s   frame=45025 fps=167 q=20.3 size=   59190kB time=1800.96 bitrate= 269.2kbits/s   frame=45102 fps=167 q=16.0 size=   59286kB time=1804.04 bitrate= 269.2kbits/s   frame=45181 fps=167 q=16.3 size=   59387kB time=1807.20 bitrate= 269.2kbits/s   frame=45262 fps=166 q=16.1 size=   59493kB time=1810.44 bitrate= 269.2kbits/s   frame=45343 fps=166 q=17.7 size=   59595kB time=1813.68 bitrate= 269.2kbits/s   frame=45423 fps=166 q=15.5 size=   59700kB time=1816.89 bitrate= 269.2kbits/s   frame=45502 fps=166 q=17.8 size=   59807kB time=1820.06 bitrate= 269.2kbits/s   frame=45579 fps=166 q=22.6 size=   59911kB time=1823.14 bitrate= 269.2kbits/s   frame=45657 fps=166 q=19.6 size=   60018kB time=1826.25 bitrate= 269.2kbits/s   frame=45735 fps=166 q=23.9 size=   60127kB time=1829.38 bitrate= 269.2kbits/s   frame=45814 fps=166 q=19.5 size=   60235kB time=1832.54 bitrate= 269.3kbits/s   frame=45891 fps=166 q=20.6 size=   60336kB time=1835.62 bitrate= 269.3kbits/s   frame=45969 fps=166 q=16.6 size=   60437kB time=1838.73 bitrate= 269.3kbits/s   frame=46048 fps=166 q=19.9 size=   60544kB time=1841.89 bitrate= 269.3kbits/s   frame=46127 fps=166 q=20.1 size=   60652kB time=1845.05 bitrate= 269.3kbits/s   frame=46206 fps=166 q=24.1 size=   60755kB time=1848.22 bitrate= 269.3kbits/s   frame=46284 fps=166 q=23.1 size=   60861kB time=1851.32 bitrate= 269.3kbits/s   frame=46363 fps=166 q=26.4 size=   60964kB time=1854.48 bitrate= 269.3kbits/s   frame=46442 fps=166 q=19.7 size=   61071kB time=1857.65 bitrate= 269.3kbits/s   frame=46517 fps=166 q=27.4 size=   61175kB time=1860.65 bitrate= 269.3kbits/s   frame=46591 fps=166 q=28.5 size=   61275kB time=1863.60 bitrate= 269.4kbits/s   frame=46668 fps=166 q=24.5 size=   61371kB time=1866.68 bitrate= 269.3kbits/s   frame=46744 fps=166 q=31.0 size=   61474kB time=1869.74 bitrate= 269.3kbits/s   frame=46822 fps=166 q=28.6 size=   61572kB time=1872.85 bitrate= 269.3kbits/s   frame=46900 fps=166 q=24.8 size=   61675kB time=1875.98 bitrate= 269.3kbits/s   frame=46980 fps=166 q=21.3 size=   61774kB time=1879.17 bitrate= 269.3kbits/s   frame=47058 fps=166 q=22.5 size=   61878kB time=1882.31 bitrate= 269.3kbits/s   frame=47134 fps=166 q=22.5 size=   61976kB time=1885.34 bitrate= 269.3kbits/s   frame=47207 fps=166 q=28.7 size=   62074kB time=1888.26 bitrate= 269.3kbits/s   frame=47281 fps=166 q=27.2 size=   62174kB time=1891.21 bitrate= 269.3kbits/s   frame=47359 fps=166 q=22.9 size=   62277kB time=1894.32 bitrate= 269.3kbits/s   frame=47436 fps=166 q=21.4 size=   62372kB time=1897.40 bitrate= 269.3kbits/s   frame=47516 fps=166 q=23.6 size=   62476kB time=1900.62 bitrate= 269.3kbits/s   frame=47594 fps=166 q=17.7 size=   62579kB time=1903.75 bitrate= 269.3kbits/s   frame=47673 fps=166 q=23.9 size=   62679kB time=1906.89 bitrate= 269.3kbits/s   frame=47750 fps=166 q=17.9 size=   62777kB time=1909.97 bitrate= 269.3kbits/s   frame=47826 fps=166 q=23.5 size=   62881kB time=1913.03 bitrate= 269.3kbits/s   frame=47904 fps=166 q=22.2 size=   62982kB time=1916.13 bitrate= 269.3kbits/s   frame=47981 fps=166 q=23.4 size=   63086kB time=1919.24 bitrate= 269.3kbits/s   frame=48054 fps=166 q=26.8 size=   63182kB time=1922.16 bitrate= 269.3kbits/s   frame=48131 fps=166 q=23.4 size=   63282kB time=1925.22 bitrate= 269.3kbits/s   frame=48209 fps=166 q=23.9 size=   63387kB time=1928.33 bitrate= 269.3kbits/s   frame=48287 fps=166 q=23.7 size=   63487kB time=1931.44 bitrate= 269.3kbits/s   frame=48362 fps=166 q=21.3 size=   63585kB time=1934.45 bitrate= 269.3kbits/s   frame=48441 fps=166 q=23.0 size=   63690kB time=1937.61 bitrate= 269.3kbits/s   frame=48517 fps=166 q=25.9 size=   63788kB time=1940.66 bitrate= 269.3kbits/s   frame=48593 fps=166 q=31.0 size=   63893kB time=1943.69 bitrate= 269.3kbits/s   frame=48670 fps=166 q=22.2 size=   63994kB time=1946.78 bitrate= 269.3kbits/s   frame=48750 fps=166 q=20.7 size=   64099kB time=1949.96 bitrate= 269.3kbits/s   frame=48835 fps=166 q=23.5 size=   64213kB time=1953.38 bitrate= 269.3kbits/s   frame=48935 fps=166 q=31.0 size=   64344kB time=1957.38 bitrate= 269.3kbits/s   frame=49022 fps=166 q=21.7 size=   64455kB time=1960.86 bitrate= 269.3kbits/s   frame=49116 fps=166 q=24.4 size=   64571kB time=1964.62 bitrate= 269.2kbits/s   frame=49206 fps=166 q=20.7 size=   64685kB time=1968.22 bitrate= 269.2kbits/s   frame=49299 fps=166 q=14.8 size=   64815kB time=1971.93 bitrate= 269.3kbits/s   frame=49358 fps=166 q=3.6 Lsize=   66889kB time=1974.32 bitrate= 277.5kbits/s    
video:48428kB audio:15426kB global headers:0kB muxing overhead 4.752246%
```

---

### Post by Roger Allott on 2010-09-24
> **Roger Allott said:**
> 
Do I need to add "-acodec copy -vcodec copy" to the command?


I thought I'd give this a shot and so adjusted my command to read:
```
ffmpeg -i vidb.mp3 -i vida-muted.avi -acodec copy -vcodec copy vidd.avi
```

It seemed to be going well but then I got an error message:
```
[NULL @ 0x9d02df0]error, non monotone timestamps 57600 >= 57600
av_interleaved_write_frame(): Error while opening file
```

The resultant file (vidd.avi) plays fine and the video quality is fine, but it is only 25 mins 4 secs long and 310.1 Mb in size.

Can someone please explain (in layman's language, preferably) what that error message means?

---

### Post by perspectoff on 2010-09-24
There are several video editors which will do this.

I have used and liked Avidemux to do what you are describing.

FFMPEG is good, but is not GUI based. I have found it worthwhile to learn and use FFMPEG, but it is a steep learning curve. For fine-grained control, it is hard to beat, though. Older versions had a problem correctly synchronizing video and audio for large files, but that has been rectified.

Other GUI video editors to check out include:

OpenShot, PitiVi, KDENLive, Cinelerra, LiVES, OpenMovieEditor.

These are listed at

[http://ubuntuguide.org/wiki/Ubuntu:Lucid#Video_Applications](http://ubuntuguide.org/wiki/Ubuntu:Lucid#Video_Applications)

or

[http://kubuntuguide.org/Lucid#Video_Applications](http://kubuntuguide.org/Lucid#Video_Applications)

---

### Post by FakeOutdoorsman on 2010-09-24
> **Roger Allott said:**
> Many thanks for all of your suggestions, chaps. Sorry I haven't responded sooner, but I found that I had to be in Windoze all day yesterday so couldn't implement any ideas.

My first attempt is to use the one line code offered by FakeOutdoorsman. Unfortunately, I got errors and the resulting mkv file is 0 bytes.

```
:~$ ffmpeg -i vida.avi -i vidb.wmv -vcodec copy -acodec copy -map 0:0 -map 1:1 -shortest vidc.mkv
FFmpeg version SVN-r19352-4:0.5+svn20090706-2ubuntu2.2, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5+svn20090706-2ubuntu2.2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --extra-cflags=-I/build/buildd/ffmpeg-0.5+svn20090706/debian/include --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Apr 23 2010 15:05:49, gcc: 4.4.1
Input #0, avi, from 'vida.avi':
  Duration: 00:32:54.32, start: 0.000000, bitrate: 1571 kb/s
    Stream #0.0: Video: msmpeg4, yuv420p, 512x384, 25 tbr, 25 tbn, 25 tbc
    Stream #0.1: Audio: mp3, 24000 Hz, mono, s16, 32 kb/s

Seems stream 1 codec frame rate differs from container frame rate: 1000.00 (1000/1) -> 25.00 (25/1)
Input #1, asf, from 'vidb.wmv':
  Duration: 00:32:50.93, start: 3.000000, bitrate: 579 kb/s
    Stream #1.0: Audio: wmav2, 44100 Hz, stereo, s16, 64 kb/s
    Stream #1.1: Video: wmv2, yuv420p, 400x300, 512 kb/s, 25 tbr, 1k tbn, 1k tbc
Output #0, matroska, to 'vidc.mkv':
    Stream #0.0: Video: 0x0000, q=2-31, 200 kb/s, 90k tbn
    Stream #0.1: Audio: 0x0000, 44100 Hz, stereo, s16, 64 kb/s
Codec type mismatch for mapping #1.1 -> #0.1
```

It's odd that the durations for the elements are a few seconds different, because that's certainly not what's being reported when I get the Properties screen up when I right-click the vids.

My command failed because I assumed that the audio of *vidb.wmv* would be listed as the first stream.  The FFmpeg output shows the order of these streams, and you used the *-map* option to tell FFmpeg which streams you want.  So, if you want the video from the first input then use *-map 0:0*.  The first 0 means "the first input", and the second 0 means "the first stream", and in computerese 0 often means "the first whatever".  So, *-map 0:0* correlates to (copied directly from your FFmpeg output):
```
Stream #0.0: Video: msmpeg4, yuv420p, 512x384, 25 tbr, 25 tbn, 25 tbc
```
It's usually safe to assume that video is often the first stream, but not always as you just encountered.  Now the next option will be *-map 1:0* and tells FFmpeg to use the first stream from the second input, *vidb.wmv*:
```
Stream #1.0: Audio: wmav2, 44100 Hz, stereo, s16, 64 kb/s
```
Now for the new command:
```
ffmpeg -i vida.avi -i vidb.wmv -vcodec copy -acodec copy -map 0:0 -map 1:0 -shortest vidc.mkv
```

---

### Post by Roger Allott on 2010-09-24
> **perspectoff said:**
> 
I have used and liked Avidemux to do what you are describing.


I thought I knew my way around Avidemux fairly well, so I took a look around it again to see what features you must be talking about, and indeed I found them! Yes, Avidemux had everything I needed to resolve this problem without recourse to the ffmpeg CLI.

Oh well, at least I've learned something....

---

### Post by Roger Allott on 2010-09-24
> **FakeOutdoorsman said:**
> 
Now for the new command:
```
ffmpeg -i vida.avi -i vidb.wmv -vcodec copy -acodec copy -map 0:0 -map 1:0 -shortest vidc.mkv
```

Thanks for that. I tested it exactly as you wrote it, and it does indeed produce an mkv file of roughly the size that one would expect. It plays excellently in Movie Player, but there's no sound at all when I load it into Avidemux.

I then tried it with avi at the end instead of mkv. I got an output file of pretty much the same size as the mkv, but the audio playback was jerky in places in Movie Player, although it plays fine when I load it into Avidemux. As I think you mentioned earlier, avi containers accept wma audio elements, but they don't like them.

Personally, I prefer to avoid mkv files for the moment, as Avidemux and other vid editors (and quite a few players) don't seem to be competent yet at handling them.

---

### Post by FakeOutdoorsman on 2010-09-24
I couldn't reproduce and jerkyness in Movie Player with the avi from my test, but this was on Lucid.

Maybe *.asf* or *.wmv* would be worth experimenting with as the output format.  I, however, have little experience with these Windows formats.  I also don't ever use Movie Player (I prefer MPlayer, SMPlayer, or sometimes ffplay).

---

### Post by Roger Allott on 2010-09-24
> **FakeOutdoorsman said:**
> I couldn't reproduce and jerkyness in Movie 
Maybe *.asf* or *.wmv* would be worth experimenting with as the output format.

I'm very surprised to find that one can create wmv files in Linux! I thought the code for creating that format was only available for Windows machines. Well, I tried the little experiment and the resulting file played great on Movie Player and MPlayer, but when I loaded it into Avidemux the sound sych was about 12 seconds out.

Something I don't understand is how a file can have perfect sound synching in one player but then be completely unsynched when loaded into another player. Any thoughts?

---


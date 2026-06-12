---
title: "Perl Audio Converter - 4.0.5 problems"
date: 2009-11-03
forum: New to Ubuntu
---

### Post by nadian on 2009-11-03
New to ubuntu and i'm trying to use Perl Audio Converter - 4.0.5

to convert to wma files to mp3's. The are stored on my second laptop hardrive, but PAC won't recognise the directory they are in - /media/local disk/music. It doesn't see the directory and gets lost after cd /media, I've tried local_disk, and localdisk, but reading some other posts I think it has something to do with the way ubuntu mounts hard drives, and the path it allocates isn't recognised within PAC. Is there a way to change or temporarily alter the path?. Perhaps there is another solution.?
any help much appreciated  ;)
ok figured out how to get to directory using quotation marks..but can't get pacpl to convert wma to mp3 folders in recursive folders, i run this

 /media/Local Disk/Music/Music$ pacpl -t mp3 -r -o wma

it just returns help listing!

Perl Audio Converter - 4.0.5

-t, --to             destination format
-r, --recursive      recursively convert directory(s)
-p, --preserve       preserve directory structure
-f, --formats        list supported encode/decode formats
-o, --only           only convert files matching extension
-k, --keep           keep files matching destination format
-h, --help           this help menu
-l, --longhelp       complete list of options
-v, --verbose        show detailed information

usage: pacpl --to <format> <options> [file(s)/directory(s)]

and just get help listing no processing indicated, am i doing something wrong?

---

### Post by r00tDemon on 2009-11-04
try using
```
pacpl -v --to mp3 /media/Local Disk/Music/Music -r -k -o wma -p --outdir /media/Local Disk/Music/Musicalso 
```
make sure you have the right codecs installed with $pacpl -f

---

### Post by nadian on 2009-11-04
Thanks for your help- I'm getting there , i had to put " " around Local Disk, and mkdir musicalso, but the the command script you posted seems to be running. I'll let you know if it's successful.

---

### Post by nadian on 2009-11-04
Problems - I interupted the process as it didn't seem to be working:
Total files converted: 0, failed: 337
heres part of the log:
Converting:  [04 Don't You Want Me.wma] -> [mp3] 

FFmpeg version SVN-r19352-4:0.5+svn20090706-2ubuntu2, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5+svn20090706-2ubuntu2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --extra-cflags=-I/build/buildd/ffmpeg-0.5+svn20090706/debian/include --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Oct 13 2009 22:15:16, gcc: 4.4.1
Input #0, asf, from '/media/Local Disk/Music/Music/Various Artists/90's Dance/04 Don't You Want Me.wma':
  Duration: 00:05:53.95, start: 1.579000, bitrate: 193 kb/s
    Stream #0.0: Audio: wmav2, 44100 Hz, stereo, s16, 192 kb/s
Output #0, wav, to '/media/Local Disk/Music/Musicalso/Various Artists/90's Dance/04 Don't You Want Me.7616.wav':
    Stream #0.0: Audio: pcm_s16le, 44100 Hz, stereo, s16, 1411 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
Press [q] to stop encoding
size=       0kB time=10000000000.00 bitrate=   0.0kbits/s    
video:0kB audio:0kB global headers:0kB muxing overhead inf%
[COLOR=Red]sox FAIL formats: no handler for file extension `mp3'
encode failed with exit status: 512[/COLOR]

I think its something to with the above line?
but when i ran pacpl -f I got:
mp3       Y   Y   toolame         lame               Y          Y
the above response for mp3 , which makes me think I do have neccessary encoder?
and:
wma       Y   Y   ffmpeg          ffmpeg             Y          N
for wma , which i think means it can read wma files if not output them.
any ideas what the problem is or what i could do next?

---

### Post by cschooley on 2010-01-16
Dude you were almost there. I thought the same thing you did, but you also need to install lame (mp3 encoder).

sudo apt-get install lame

or open Synaptic package manager and install Lame. I guess pacpl is just telling you it has the ability to rip mp3 using lame - not that lame is actually installed. I assumed (incorrectly) that it would say "no" or indicate that lame is missing or something.

---

### Post by fahadayaz on 2010-02-09
how can i specify the bitrate and khz to encode at?

EDIT:  pacpl -l gave helpful information

i want to convert to ogg. i could have used  --bitrate x --freq y
where x and y are the values wanted for each, but i wanted to use an ogg quality default of 0 (for my mobile device (nexus one  :D)), for this i used  --oggqual 0  instead

job done.. many thanks to everyone for helping me get where i wanted to be!  :)

---

### Post by zubinparihar on 2010-08-01
Hey Nadian,

Try This:

sudo aptitude install libsox-fmt-all

Hope that works,

Cheers,

Zubin Parihar

---


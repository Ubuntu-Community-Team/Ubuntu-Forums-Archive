---
title: "how to record the webcam with command line?"
date: 2009-11-25
forum: New to Ubuntu
---

### Post by frenchn00b on 2009-11-25
I tried thsi but no possible :( 

>   mencoder -tv device=/dev/video0   tv://   -ovc xvid -oac null -xvidencopts bitrate=-700000 -o mywebcam.avi 


this is not working either :( 
> 
mencoder tv:// -tv driver=v4l:width=320:height=240:device=/dev/video0:forceaudio:adevice=/dev/null  -ovc lavc -oac mp3lame -lameopts cbr:br=64:mode=3 -o webcam.avi

Any ideas? 
--
the webcam is fully working nad permissions ok too.

---

### Post by loell on 2009-11-25
try the gstreamer way,

[http://noraisin.net/~jan/diary/?p=40]("http://noraisin.net/~jan/diary/?p=40")

---

### Post by frenchn00b on 2009-11-25
thansk !! 
works °!!

```
4.1.1. Streamer

Streamer is a versatile program that allows a capture from a webcam or video device using only the command line. It may be offered in your Linux distribution's Xawtv package, or may need to be fetched separately as in Debian. You can find it and more information at Gerd Knorr's Xawtv homepage.

To take a standard JPEG picture from the command line where the camera is accessed through /dev/video0:

[COLOR="Red"]   $  streamer -c /dev/video0 -b 16 -o outfile.jpeg[/COLOR]

...where -b is the number of colors (in bpp, whether 15, 16, 24 or 32) and -o is the output filename that will be dropped into the current directory (specify -o /path/outfile.jpg to place it elsewhere). If you are going to capture multiple images be sure to append the output file name with zeros, as streamer can name the capture files in sequence, i.e., -o outfile000.jpeg becomes outfile001.jpeg, outfile002.jpeg, and so on.

To make an .avi file:

  [COLOR="Red"] $  streamer -q -c /dev/video0 -f rgb24 -r 3 -t 00:30:00 -o /home/jhs/outfile.avi
[/COLOR]
...where -q is for 'quiet' execution (no message output), -f is 'format' (rgb24 is Tru
```

---

### Post by frenchn00b on 2009-11-25
record 2 seconds

```
streamer -t 0:0:2 -c /dev/video0 -f rgb24 -r 3  -o   outfile.avi
```

the format is not ok, it is a 
RIFF AVI LIST  hdrlavih8

it needs to be compressed with a pipe

---

### Post by frenchn00b on 2009-11-25
```
 streamer  -c /dev/video0    -o   outfile.jpeg
```

beware jpg is not ok
jpeg shall be !!

**[COLOR="Red"]how to increase the brightness under streamer ???[/COLOR]**



how to stream it? 
> while [ 1 ] ; do  streamer -t 0:0:2 -c /dev/video0 -f rgb24 -r 3  -o   outfile.avi  # has right brignthmess in avi;                          echo " llkj" | mutt -a outfile.avi  robert ; done


---

### Post by frenchn00b on 2009-12-08
apt-get install streamer

SOLVED, here is the script


```
#!/bin/sh
# arg1 is minutes and arg2 is format output.avi for instance
streamer -t 0:$1:0 -c /dev/video0 -f rgb24 -r 3  -o  $2


```

---


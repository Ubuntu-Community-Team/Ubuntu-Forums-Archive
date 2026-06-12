---
title: "Sound not synced recording using transcode"
date: 2009-12-14
forum: New to Ubuntu
---

### Post by djftl on 2009-12-14
Hi there, 

I recorded a video from composite 2 of my tv card using this script code:
#!/bin/sh
killall tvtime
sleep 4 && amixer -q set "Line" 100% unmute;
sleep 1 && amixer -q set "Analog Mix" 100% unmute &

TODAY=$( date +%Y%m%d )
NOW=$( date +%H:%M )

gnome-terminal --execute transcode -x v4l2,v4l2 \
           -M 2 \
           -i /dev/video1 \
           -p /dev/dsp \
           -w 6000 \
           -y ffmpeg \
           -F mpeg4 \
           -c 02:30:00 \
           -g 720x480 \
           -f 0,4 \
           -I 1 \
	   -J resample,levels,smartyuv,pv \
           -u 100 \
           -Q 3 \
           -Z 640x480,fast \
           -E 48000,16,2 \
           --lame_preset medium \
           -o /Multimedia/myfiles/My_Videos_Projects/tvtime-recorded/-${TODAY}-${NOW}.avi \




amixer -q set "Line" 0% mute &I changed the -E 48000, 16, 2 to -E 44100, 16, 2 but still the sound plays very fast as if it's playing at a higher sample rate.
Can someone help.
I found the tutorial from here: [http://ubuntuforums.org/showthread.php?t=921233](http://ubuntuforums.org/showthread.php?t=921233).

Thanks.

Tobela

---


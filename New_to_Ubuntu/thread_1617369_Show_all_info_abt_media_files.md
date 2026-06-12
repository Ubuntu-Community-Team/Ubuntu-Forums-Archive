---
title: "Show all info abt media files"
date: 2010-11-09
forum: New to Ubuntu
---

### Post by dhiman33 on 2010-11-09
:mrgreen:Hey I was wondering if there's some way to show codec info,frame rate,video size,bitrate, and EVERY information about a video/audio file in the file properties dialog box.Pls someone tell me how to do this.:tongue:

---

### Post by ivarn on 2010-11-09
Yes, right click on the audio or video file, click preferences and goto the last tab

---

### Post by toekneewood on 2010-11-09
This is a bash script that might give you what you need.
```

#!/bin/bash
FILENAME="$1"

echo "Properties for $FILENAME:"

if [ -f $FILENAME ]; then
  echo "Size is $(ls -lh $FILENAME | awk '{ print $5 }')"
  echo "Type is $(file $FILENAME | cut -d":" -f2 -)"
  echo "Inode number is $(ls -i $FILENAME | cut -d" " -f1 -)"
  echo "$(df -h $FILENAME | grep -v Mounted | awk '{ print "On",$1", \
which is mounted as the",$6,"partition."}')"
else
  echo "File does not exist."
fi

```

---

### Post by pers3vs on 2010-11-09
"mediainfo" provides the information you want. Information is available on their website including how to add their repository and key.

[https://launchpad.net/~shiki/+archive/mediainfo]("https://launchpad.net/~shiki/+archive/mediainfo")

For example:
> 
username@computername:~/$ mediainfo hfp160-3-broadband.wmv
General
Complete name                    : hfp160-3-broadband.wmv
Format                           : Windows Media
File size                        : 3.68 MiB
Duration                         : 4mn 14s
Overall bit rate mode            : Constant
Overall bit rate                 : 121 Kbps
Maximum Overall bit rate         : 359 Kbps
Movie name                       : hfp160-3
Encoded date                     : UTC 2009-03-20 01:33:24.703
Application                      : Windows Movie Maker 2.1.4026.0

Video
ID                               : 2
Format                           : VC-1
Format profile                   : MP@LL
Codec ID                         : WMV3
Codec ID/Info                    : Windows Media Video 9
Codec ID/Hint                    : WMV3
Description of the codec         : Windows Media Video 9
Duration                         : 4mn 14s
Bit rate mode                    : Constant
Bit rate                         : 308 Kbps
Width                            : 320 pixels
Height                           : 240 pixels
Display aspect ratio             : 4:3
Frame rate                       : 30.000 fps
Resolution                       : 8 bits
Scan type                        : Progressive
Bits/(Pixel*Frame)               : 0.134
Stream size                      : 9.35 MiB

Audio
ID                               : 1
Format                           : WMA
Format version                   : Version 2
Codec ID                         : 161
Codec ID/Info                    : Windows Media Audio
Description of the codec         : Windows Media Audio 9.2 -  32 kbps, 32 kHz, stereo (A/V) 1-pass CBR
Duration                         : 4mn 14s
Bit rate mode                    : Constant
Bit rate                         : 32.0 Kbps
Channel(s)                       : 2 channels
Sampling rate                    : 32.0 KHz
Resolution                       : 16 bits
Stream size                      : 995 KiB (26%)



Integrating this information into Nautilus (or other file manager), is going to be a little trickier, I fear.

:guitar:

---

### Post by dhiman33 on 2010-11-10
:shock:YESSS,mediainfo is what exactly what I need\\:D/! Someone pls tell how to integrate it in the rt-click menu of media files. [-o<Pls pls pls pls pls....[-o<

---

### Post by dhiman33 on 2010-11-11
:grin:I've found the solution!!! First, go to the link provided by pers3vs and add the source to ur repository and install mediainfo(still not updated for maverick,so I installed the lucid lynx version). Now, install nautilus actions configuration from software center. Open nautilus action config tool and then add a new entry named mediainfo. Use these settings---

context label-Mediainfo,path-/usr/bin/mediainfo-gui,parameters-%M,under conditions enter *.* for filenames and uncheck match case. In advanced condition I've enabled everything though I don't know what are webDAV files,SSh files, Windows files(*.exe?) etc. Save and restart ubuntu; and voila:tongue:--now every file will show mediainfo in it's context menu.

PS: ](*,)Though this brings up mediainfo gui from rt. click, the mediainfo window by default shows only basic info's abt a file. To show the advanced info, select html/text from the view menu. I really think it's a shame that html view/text view can't be made default view for mediainfo-gui. If anyone knows how to do this, pls tell the way.

---

### Post by Prodoc on 2010-11-27
(forget I said anything, I shouldn't have responded at this time of day)

---

### Post by dhiman33 on 2010-11-28
what does that mean?:confused:

---


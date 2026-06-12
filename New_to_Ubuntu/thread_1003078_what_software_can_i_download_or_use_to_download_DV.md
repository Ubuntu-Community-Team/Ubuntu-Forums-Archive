---
title: "what software can i download or use to download DVD's and save the file to my harddri"
date: 2008-12-05
forum: New to Ubuntu
---

### Post by duquer on 2008-12-05
what software can i use to download dvd's from a hard disk and save them to my drive so that i may be able to store them on my phone or scan disk card? thank you for you help

---

### Post by nhasian on 2008-12-05
first you will need to rip the DVDs to store them on your hard disk.  you can do that with dvd::rip

```
sudo apt-get install dvd::rip
```

then you can use this script to convert the video to the iphone format

```
#!/bin/bash
ffmpeg -i "$1" -r 29.97 -vcodec h264 -s 480x320 -aspect 16:9 -flags +loop -cmp +chroma -deblockalpha 0 -deblockbeta 0 -b 1000k -maxrate 1250k -bufsize 4M -bt 256k -refs 1 -coder 0 -me umh -me_range 16 -subq 7 -partitions +parti4x4+parti8x8+partp8x8 -g 250 -keyint_min 25 -level 30 -qmin 10 -qmax 51 -qcomp 0.6 -trellis 2 -sc_threshold 40 -i_qfactor 0.71 -acodec aac -ab 80k -ar 48000 -ac 2 "$2"
```

this link may also help

[https://help.ubuntu.com/community/iPodVideoEncoding](https://help.ubuntu.com/community/iPodVideoEncoding)

---

### Post by duquer on 2008-12-05
will that script also work for my black berry storm

---

### Post by duquer on 2008-12-05
it also say couldnt find dvd package

---

### Post by nhasian on 2008-12-06
sorry try it without the ::

```
sudo apt-get install dvdrip
```

dvd::rip is a full featured DVD ripping program written in Perl. It provides
an easy to use but feature-rich Gtk+ GUI to control almost all aspects of
the ripping and transcoding process. It uses the widely known video
processing swissknife transcode and many other Open Source tools.

---


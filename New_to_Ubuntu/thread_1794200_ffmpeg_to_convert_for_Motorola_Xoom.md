---
title: "ffmpeg to convert for Motorola Xoom"
date: 2011-06-30
forum: New to Ubuntu
---

### Post by Zeedok on 2011-06-30
I am trying to convert some home videos for playback on my motorola xoom.

I have used OpenShot and Handbrake, as well as an CLI ffmpeg command that was recommended to work well for the xoom.  

Unfortunately, with OpenShot and ffmpeg I get great pictures, but no sound (I've tried using the aac codec).  With handbrake, I am using a profile recommended for the xoom -- I get sound, but the picture is choppy+++.

The video from all three methods plays perfectly well on Ubuntu (11.04)

Here is some background info on the supported media formats for the xoom -- although it doesn't mean much to me:

[http://developer.android.com/guide/appendix/media-formats.html#core](http://developer.android.com/guide/appendix/media-formats.html#core)

Here is the ffmpeg command I have tried:

ffmpeg -i <in file> -vcodec mpeg4 -b 4048k -s 720x480 -acodec libfaac -ab 128k -ac 2 -ar 48000 -f mp4 <out file>

I got the handbrake profile for xoom from Chris DiBona:

[https://sites.google.com/a/dibona.com/www/www/filestorage](https://sites.google.com/a/dibona.com/www/www/filestorage)

Any ideas how to solve this problem?

EDIT: I changed the handbrake video codec from H264 to mp4 (ffmpeg) and now Handbrake produces good video with sound (hooray!), but I would still like to understand all of this a little better to I can use the right codec on OpenShot (for editing home videos) and maybe batch some old videos using the CLI or a script.

---

### Post by samo_nz on 2012-01-16
I found some ffmpeg command line options here:
[https://develop.participatoryculture.org/index.php/ConversionMatrix]("https://develop.participatoryculture.org/index.php/ConversionMatrix")

I had to modify a few commands to get it to work, am encoding now, test shortly.

```

ffmpeg -i INPUT -y -acodec libfaac -ac 2 -ab 160k -vcodec libx264 -vpre ipod640 -vpre lossless_slow -f mp4 -threads 0 OUTPUT.mp4

```

---


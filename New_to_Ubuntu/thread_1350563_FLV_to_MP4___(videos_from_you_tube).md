---
title: "FLV to MP4   (videos from you tube)"
date: 2009-12-09
forum: New to Ubuntu
---

### Post by mal_conductor on 2009-12-09
Is there a program to convert FLV to MP4?

Also, is it possible to convert FLV to MP3, what application would convert FLV to MP3?

Thank you all

This board rocks

---

### Post by SuperSonic4 on 2009-12-09
> **mal_conductor said:**
> Is there a program to convert FLV to MP4?

ffmpeg ```
ffmpeg -i input.flv -vcodec libx264 -sameq -acodec copy output.mp4
```



> Also, is it possible to convert FLV to MP3, what application would convert FLV to MP3?

ffmpeg ```
ffmpeg -i input.flv -vn -acodec libmp3lame -ac 2 -ab 128k output.mp3
```

You may need to follow FakeOutdoorsMan's guide to get restricted codecs in there and remember that you cannot make a better file via transcoding
Also the man page has good info on options

---

### Post by nothingspecial on 2009-12-09
The instructions are [[COLOR="Red"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=786095")

It all looks very complicated but it`s just copy and paste.

---

### Post by CaptainMark on 2009-12-09
if using firefox you could use this [https://addons.mozilla.org/en-US/firefox/addon/10137](https://addons.mozilla.org/en-US/firefox/addon/10137) to download in mp4

---

### Post by jmore9 on 2009-12-09
Use  winff its in the repos

---

### Post by nothingspecial on 2009-12-09
But you`ll still need to compile ffmpeg to get it to make mp4s

---

### Post by CaptainMark on 2009-12-09
> **nothingspecial said:**
> But you`ll still need to compile ffmpeg to get it to make mp4s
it runs mp4s with ubuntu-restricted-extras and libavcodec-extra-52 installed no problem, dont need to compile

---

### Post by FakeOutdoorsman on 2009-12-09
> **mal_conductor said:**
> Is there a program to convert FLV to MP4?

Also, is it possible to convert FLV to MP3, what application would convert FLV to MP3?

Thank you all

This board rocks

FLV is a container format that can contain some of the same video types as MP4, which is also a container format.  So, you may be able to simply copy the video from the FLV to the MP4.  Show the output of:
```
ffmpeg -i the_name_of_your_flv_file_that_you_want_to_convert.flv
```
This will give some info that can be used to come up with an appropriate FFmpeg command.


> **SuperSonic4 said:**
> ffmpeg ```
ffmpeg -i input.flv -vcodec libx264 -sameq -acodec copy output.mp4
```

The *-sameq* option should generally be avoided when encoding with libx264.  Also, newer FFmpeg require use of encoding presets when using libx264:
```
ffmpeg -i input.flv -vcodec libx264 -vpre hq -crf 22 -threads 0 -acodec copy output.mp4
```


> **CaptainMark said:**
> it runs mp4s with ubuntu-restricted-extras and libavcodec-extra-52 installed no problem, dont need to compile

Not necessarily.  In Karmic, **ubuntu-restricted-extras** unfortunately installs the "stripped" libavcodec for some odd reason.  Not very intuitive if you ask me.  Also, Karmic's **libavcodec-extra-52** does not include *libfaac*, an AAC audio encoder, which is a popular audio format for MP4.  Medibuntu is in the process of releasing a somewhat dated version of libavcodec that will address this issue.

Or you can compile a recent FFmpeg yourself as mentioned by nothingspecial if you don't want to wait a week or so for Medibuntu.

---

### Post by rainjam on 2009-12-09
I use keepvid.com, seems the easiest way to do it! You can download the video at original quality too, so if it was uploaded at 1280x720 that's what you'll get.

---

### Post by mc4man on 2009-12-09
> in Karmic, ubuntu-restricted-extras unfortunately installs the "stripped" libavcodec for some odd reason

Well there seems to be no movement to changing that, and atm expect the same in lucid.

Even when correctly configured, the recommendation to install u-r-e is certainly overused and somewhat ill advised. ( the installation of the ms....fonts can fail for many people and cause further hassles.

Maybe further comments can spur either action or reason why not needed.

karmic
[https://bugs.launchpad.net/ubuntu/+source/ubuntu-restricted-extras/+bug/462366](https://bugs.launchpad.net/ubuntu/+source/ubuntu-restricted-extras/+bug/462366)

lucid
[https://bugs.launchpad.net/ubuntu/+source/ubuntu-restricted-extras/+bug/494745](https://bugs.launchpad.net/ubuntu/+source/ubuntu-restricted-extras/+bug/494745)

(( find the whole matter  very curious, at the same time as repoting karmic bug also made 3 suggestions to improve vlc. Was expecting no real action on vlc, and this to be corrected. Instead 2 of the three vlc's were implemented for lucid, and this goes nowhere..?

---


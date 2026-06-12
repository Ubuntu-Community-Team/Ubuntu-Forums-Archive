---
title: "Convert WMV. to FLV"
date: 2011-03-21
forum: New to Ubuntu
---

### Post by aznaiveboi on 2011-03-21
I'm trying to convert a wmv file to flv in the terminal. I believe I'm missing something since it doesn't recognize the file. Please advise. Thank you!

lin@lin-workstation:~$ ffmpeg -i ~/Videos/speaking_for_science.wmv -acodec libfaac -ar 22050 -ab 64k -vol 768 -vcodec libx264 -vpre dreamhost_flv -crf 30 -f flv ~/Videos/speaking_for_science.flv
FFmpeg version git-ea7f080, Copyright (c) 2000-2011 the FFmpeg developers
  built on Feb  1 2011 15:41:21 with gcc 4.4.5
  configuration: --enable-gpl --enable-version3 --enable-nonfree --enable-postproc --enable-libfaac --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libvorbis --enable-libvpx --enable-libx264 --enable-libxvid --enable-x11grab
  libavutil    50. 36. 0 / 50. 36. 0
  libavcore     0. 16. 1 /  0. 16. 1
  libavcodec   52.108. 0 / 52.108. 0
  libavformat  52. 94. 0 / 52. 94. 0
  libavdevice  52.  2. 3 / 52.  2. 3
  libavfilter   1. 74. 0 /  1. 74. 0
  libswscale    0. 12. 0 /  0. 12. 0
  libpostproc  51.  2. 0 / 51.  2. 0
/home/lin/Videos/speaking_for_science.wmv: Invalid data found when processing input

---

### Post by MrNatewood on 2011-03-24
I don't know much about the command line parameters of FFmpeg but you might want to try an easy GUI tool such as Transmaggedon or Arista.

---

### Post by FakeOutdoorsman on 2011-03-24
I would guess this is a corrupted file because FFmpeg doesn't seem to be able to read it.

---

### Post by stmiller on 2011-03-24
```
/home/lin/Videos/speaking_for_science.wmv: Invalid data found when processing input
```

Yeah corrupted or odd formatted wmv file that ffmpeg can't read. :/

---

### Post by kn0w-b1nary on 2011-03-24
You could try VLC media player. That is, if the file is readable.

---

### Post by andrew.46 on 2011-04-03
Mind you the name of the preset is a little odd:

```

ffmpeg -i ~/Videos/speaking_for_science.wmv \
       -acodec libfaac -ar 22050 -ab 64k -vol 768 \
       -vcodec libx264 **[COLOR="Red"]-vpre dreamhost_flv[/COLOR]** \
       -crf 30 -f flv ~/Videos/speaking_for_science.flv

```

Is this a custom preset you have written or an error in syntax?

---


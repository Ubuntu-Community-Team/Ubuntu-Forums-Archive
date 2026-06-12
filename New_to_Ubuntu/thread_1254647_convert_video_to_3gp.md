---
title: "convert video to 3gp"
date: 2009-08-31
forum: New to Ubuntu
---

### Post by gigaferz on 2009-08-31
hello, what can i use to convert video to 3gp format?

i tried winff  with this error:
Unknown encoder 'libamr_nb'

Also I tried Mobile Media Converter
with this error:
/MobileMediaConverter: line 3:  5639 Segmentation fault      ./lib/mmc "$@"

 Any sugestions?

---

### Post by gigaferz on 2009-08-31
using wine i installed :
[http://www.download3k.com/Install-Freez-3GP-Video-Converter.html](http://www.download3k.com/Install-Freez-3GP-Video-Converter.html)

is fast and it works!!! (for me, :P)

---

### Post by Uzi304 on 2009-08-31
I use ffmpeg. As far as I know, it's CLI. So it'd be like 
```
ffmpeg -i NameOfVid.avi NameOfVid.3gp
```
Doesn't have to be avi though. Haven't ever converted to 3gp but it's worth a try for you

---

### Post by andrew.46 on 2009-09-01
Hi,

If you wanted 3gp files with *aac* sound and h263 video the straight commandline FFmpeg should be your friend. Simply follow the directions on this page to get the most out of your copy of FFmpeg:

HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg
[http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)

Unfortunately I don't know enough about WinFF to offer any guidance with it :(.

Andrew

---

### Post by ken_do_san on 2009-09-01
I use mobile media converter (there is a version of it for Ubuntu)

---

### Post by paul.gevers on 2009-09-01
> **andrew.46 said:**
> Hi,

If you wanted 3gp files with *aac* sound and h263 video the straight commandline FFmpeg should be your friend. Simply follow the directions on this page to get the most out of your copy of FFmpeg:

HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg
[http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)

Unfortunately I don't know enough about WinFF to offer any guidance with it :(.

Guidance on WinFF in this context is easy. If your ffmpeg can do it, winff can do it. @gigaferz, your ffmpeg did not have amr_nb build in. Which version of Ubuntu are you running? If Intrepid or newer, do you have libavcodec-unstripped-51 or -52 installed, or just libavcodec5X (I think you need the unstripped version)?

---

### Post by gigaferz on 2009-09-04
@ ken do san, 
  i tried it but it gives me a segmentation fault
not even the wine version works
@ andrew
  I ve been trying that (looks like ffmpeg is ok)  but it always gives me a bitrate error or incorrect framesize , from commands copied and pasted from websites

  and that software just expired, and me as usual with no cash, lol
@ paul 
i have the unstripped version

I KNOW  so far :
video codec h263
video fps   15
video size 176x144

audio codec libmp3lame,ac3
audio bitrate  64         (however ive seen 10.200?)
audio frequncy  8000

Im gonna try mpeg4 as a video codec to see if this works....  thanks for your help

this is an error i got 

 could not find tag, codec not currently supported in container
Could not write header for output file #0 (incorrect codec parameters ?)

this is my command line so far
ffmpeg -i 1.flv -vcodec mpeg4 -s 176x144 -r 15 -b 100k -acodec libmp3lame -ac 1 -ar 8000 1.3gp

same with errors with h263

---

### Post by SuperSonic4 on 2009-09-04
3gp is simply a container format so you can stick any audio and video codec in. All of my mobile videos have mp3 or m4a sound and they play just fine. If you post what you want from the video we can suggest something? For me it's usually

```
ffmpeg -i input.flv -b 300k -s 320x240 -vcodec mpeg4 -ac 2 -ab 128k -acodec libfaac output.3gp
```

---

### Post by gigaferz on 2009-09-07
i got a fully functional 3gp video working!!!!

thnx supersonic4  , but what was wrong with the command i figured out?

 anywas thnx again,

i was just getting those setting from different programs, Ill see if the videos play in diferent phones,
ive heard the resolution has to be smaller.

Thank you anyways

---

### Post by SuperSonic4 on 2009-09-07
I don't know, that bottom command looks pretty accurate, I would guess something to do with the mp3 audio and codecs, especially if mpeg4 works in the command I posted.

It could have also been a dodgy video you tried to encode

edit: yeah 320x240 is the right size for my phone but as usual it varies

---

### Post by OakGill on 2009-10-11
> **gigaferz said:**
> using wine i installed :
[http://www.download3k.com/Install-Freez-3GP-Video-Converter.html](http://www.download3k.com/Install-Freez-3GP-Video-Converter.html)

is fast and it works!!! (for me, :P)

How do you download applications on to wine?

---

### Post by isa.dsouza on 2012-11-10
Thanks a lot, I tried this out

ffmpeg -i *filename.flv* -s qcif -vcodec mpeg4 -b 200k -acodec libvo_aacenc -ab 64k -y *filename.3gp*

It works!:) I am also using winff, it's great!

---

### Post by overdrank on 2012-11-10
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---


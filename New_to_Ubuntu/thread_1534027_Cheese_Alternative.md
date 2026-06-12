---
title: "Cheese Alternative?"
date: 2010-07-18
forum: New to Ubuntu
---

### Post by maryalesia on 2010-07-18
Hello again!

I've got a webcam problem. Well, actually it's a software problem.

See, I use youtube regularly, but I can't record videos on my laptop. Everyone I've asked says that cheese is by far the best software available for linux users, but it saves in an unusable format: ogv, or ogg, or something in a "theora" codec. I have read in multiple places that a cheese software glitch makes it impossible to reformat video files recorded in cheese, and have been unsuccessful thus far. 

Is there an alternative webcam application that will record video in a usable format? In the software center it says that wxcam is not available for my computer.

---

### Post by Mike_IronFist on 2010-07-19
> **maryalesia said:**
> Hello again!

I've got a webcam problem. Well, actually it's a software problem.

See, I use youtube regularly, but I can't record videos on my laptop. Everyone I've asked says that cheese is by far the best software available for linux users, but it saves in an unusable format: ogv, or ogg, or something in a "theora" codec. I have read in multiple places that a cheese software glitch makes it impossible to reformat video files recorded in cheese, and have been unsuccessful thus far. 

Is there an alternative webcam application that will record video in a usable format? In the software center it says that wxcam is not available for my computer.
Chese really is the best webcam app available for Linux, even though it only outputs in stuff like ogv. If you want your video in a usable format, you can open your video in Pitivi video editor and export it to a format usable by YouTube. This takes a little bit of time, but it works.

---

### Post by maryalesia on 2010-07-19
> **Mike_IronFist said:**
> Chese really is the best webcam app available for Linux, even though it only outputs in stuff like ogv. If you want your video in a usable format, you can open your video in Pitivi video editor and export it to a format usable by YouTube. This takes a little bit of time, but it works.

I've tried, but it never loads. As in, I can leave it for an hour and come back and nada. The application doesn't freeze, it's just that nothing happens.

How long does it take when you use it?

---

### Post by marshmallow1304 on 2010-07-19
VLC will do it.  Media->Convert/Save, Capture Device tab, change settings as you like (Video device name can be blank) and hit Convert/Save.  Choose a filename and a YouTube-supported format for Profile and click Start.

---

### Post by maryalesia on 2010-07-19
> **marshmallow1304 said:**
> VLC will do it.  Media->Convert/Save, Capture Device tab, change settings as you like (Video device name can be blank) and hit Convert/Save.  Choose a filename and a YouTube-supported format for Profile and click Start.

Thanks! This will probably keep me busy for a while. I appreciate the help!

---

### Post by HermanAB on 2010-07-19
Also try Webcamstudio.  It works very well, when it works.

---

### Post by beew on 2010-07-19
> **Mike_IronFist said:**
> Chese really is the best webcam app available for Linux, even though it only outputs in stuff like ogv. If you want your video in a usable format, you can open your video in Pitivi video editor and export it to a format usable by YouTube. This takes a little bit of time, but it works.

Huh?? If it outputs files in unusable formats how is it the best??:p

---

### Post by jerenept on 2010-07-19
.ogv and .ogg are Free and Open source media codecs. If you wish to convert the files to the more common .mp3, .mp4 or .avi, you can use WinFF, which is probably the best program for this purpose.

---

### Post by no2498 on 2010-07-19
i like wxcam my self

read and install all the page tells you to

[http://wxcam.sourceforge.net/](http://wxcam.sourceforge.net/)

---

### Post by marshmallow1304 on 2010-07-19
> **jerenept said:**
> .ogv and .ogg are Free and Open source media codecs. If you wish to convert the files to the more common .mp3, .mp4 or .avi, you can use WinFF, which is probably the best program for this purpose.

This is true, but there's a bug in Cheese that prevents many converters from being able to handle files it saves.  The formats themselves are fine.

---

### Post by Hooya on 2011-02-04
> **marshmallow1304 said:**
> VLC will do it.  Media->Convert/Save, Capture Device tab, change settings as you like (Video device name can be blank) and hit Convert/Save.  Choose a filename and a YouTube-supported format for Profile and click Start.

I've tried doing this and nothing happens. No errors in any log, no output, nothing. If I choose the "file" option instead of "capture device" some of the files will output to a 10Kb junk file, but none of the conversions I do will work. VLC will play these media files fairly well (seeking is broken).

What a crappy program Cheese is to output corrupt files and not offer any other file type options or codecs.... Now my whole morning doing filming with it is out the window because I have these worthless files sitting on my drive. There's got to be a way to convert these things.

---

### Post by Bucky Ball on 2011-02-04
> **beew said:**
> Huh?? If it outputs files in unusable formats how is it the best??:p

Unusable when attempting to upload to Youtube I think is the point. They are usable files elsewhere. ;)

---

### Post by Hooya on 2011-02-04
> **Bucky Ball said:**
> Unusable when attempting to upload to Youtube I think is the point. They are usable files elsewhere. ;)

Only VLC reliably can play the files back. Some of the files won't even play in any of the other media players I have.

---

### Post by no2498 on 2011-02-05
cheese and vlc make the same ogg files for me 
wxcam makes avi file type
but its only for 32 bit not 64 they need to work to get it installed

---

### Post by MestreLion on 2012-01-27
> **maryalesia said:**
> See, I use youtube regularly, but I can't  record videos on my laptop.Everyone I've asked says that cheese is by far the best software available for linux users, but it saves in an unusable format.

Actually, YouTube accepts Ogg Theora just fine. I just uploaded some videos recorded using gtkRecordMyDesktop, which uses exactly the same encoder as Cheese. 

> **maryalesia said:**
> ogv, or  ogg, or something in a "theora" codec.

- Ogg is the name of the media container (like AVI or Matroska)
- .ogv is its filename extension (like .avi or .mkv)
- Theora is the name of the video format (the "codec", like MPEG-2 or H.264)

And Ogg/Theora were, until very recently, the the only (or at least most popular) patent-free, open source, open standard for media container and video encoder, thus being the standard in nearly all free video software.

> **maryalesia said:**
>  Is there an alternative webcam  application that will record video in a usable format?

You friends were right: Cheese is the best, in terms of ease of use and integration with the OS. It record videos, take single pictures, burst pictures, apply cheesy effects, etc, all in a simple app. It's not Cheese's fault if the the facto standard video format available in Ubuntu is Ogg/Theora.

But you can play it in Totem, Gnome MPlayer, VLC, and it works fine in YouTube. Looks like pretty usable for me ;)

In the future, probably **WebM** will replace Theora as the default video format.

---


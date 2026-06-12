---
title: "mencoder ffmpeg"
date: 2009-11-20
forum: New to Ubuntu
---

### Post by dzon65 on 2009-11-20
I've got some ogg files that need to be converted to avi.I've installed mencoder first but couldn't find a way to get it to work.I then tried ffmepg with the same result.Can't find those tools anywhere.Do they only work with commandlines?

---

### Post by lavinog on 2009-11-20
eventually handbrake will work with ubuntu again.  It is pretty nice.
avidemux is a good program to use.

keep in mind avi is just a container...why do you think you need to convert the file to avi?
if it is for a media device you need to determine what codecs it supports.  If it is for another computer, you will need to make sure that the codec is available for that machine...windows doesn't come with support for many of the advanced codecs.  In that case you may want to just install a ogg player for windows.

---

### Post by dzon65 on 2009-11-20
Aha.Ok I'll give handbrake a try.Actually,it was indeed for converting files that can be read on a windows machine.

---

### Post by lavinog on 2009-11-20
Converting files will degrade the quality and takes some time...you would be better off using a ogg player.
handbrake currently is broken, so avidemux would be your next best option.

---

### Post by dzon65 on 2009-11-20
Yeah,handbrake was a nogo.The other one is unable to open the ogg files.So,like you said,I'll stick with my totemplayer and them windows guys,well,let them figure it out.Thanks for the tips !

---

### Post by 3rdalbum on 2009-11-20
Mencoder and ffmpeg are command-line programs. But ffmpeg is easy to use on the command line if you know what codecs you want to use.

Just type 'man ffmpeg' on the command line to see how to use it. Also, 'ffmpeg -formats' to find out what codecs are supported and what their names are.

---

### Post by underquark on 2009-11-20
Them Windows guys can play .ogg files with VLC [from here](http://www.vlc-media-player-get.info/).

---

### Post by dzon65 on 2009-11-20
Yep,they can.
(dual boot vista,haven't used it ever since)
Wait a minute,twice one terra?Jeezes!

---

### Post by dzon65 on 2009-11-20
3dalbum.I'm trying to avoid the terminal since the text is veryyy hard to read.Don't know why but I only got this problem in 9.10 and I haven't found a solution yet.
But thanks for the info.

---

### Post by lavinog on 2009-11-20
> **dzon65 said:**
> 3dalbum.I'm trying to avoid the terminal since the text is veryyy hard to read.Don't know why but I only got this problem in 9.10 and I haven't found a solution yet.
But thanks for the info.

you can change the font in the terminal preferences.

---

### Post by lavinog on 2009-11-20
I am really dissapointed that avidemux cant handle ogg.  It was supposed to at some point...what good are open formats if open source applications are not going to adopt them.

---

### Post by FakeOutdoorsman on 2009-11-20
> **underquark said:**
> Them Windows guys can play .ogg files with VLC [from here](http://www.vlc-media-player-get.info/).

Why not link to the [official VLC site](http://www.videolan.org/) instead of some third-party site of unknown intent that offers an outdated VLC?

---

### Post by lavinog on 2009-11-20
> **FakeOutdoorsman said:**
> Why not link to the [official VLC site](http://www.videolan.org/) instead of some third-party site of unknown intent that offers an outdated VLC?
```

md5sum vlc-1.0.1-win32.exe 
eca3cad01ddc80dfdfef1a0df2ed4501  vlc-1.0.1-win32.exe

```

Fortunately, the md5sum checks out with the official version.
That could have been disastrous if it turned out to be malicious.

---

### Post by 3rdalbum on 2009-11-20
> **lavinog said:**
> I am really dissapointed that avidemux cant handle ogg.  It was supposed to at some point...what good are open formats if open source applications are not going to adopt them.

To be fair to the Avidemux developers, the name of the program is not Oggdemux :-)

But I have noticed this with other programs; they work better with proprietary formats than with Ogg Theora/Vorbis. It's very disappointing.

---

### Post by dzon65 on 2009-11-21
I played around with the settings(terminal)already.Doesn't change much.The bad reading is due to overlapping text and split words.Quickly took a shot,here it's still ok but mostly it's worse

---

### Post by dzon65 on 2009-11-21
Sorry,bad shot.

---

### Post by frenchn00b on 2009-11-21
> **dzon65 said:**
> I've got some ogg files that need to be converted to avi.I've installed mencoder first but couldn't find a way to get it to work.I then tried ffmepg with the same result.Can't find those tools anywhere.Do they only work with commandlines?

```
#!/bin/bash
# ogv to avi
mencoder "$1" -ovc xvid -oac mp3lame -xvidencopts pass=1 -o "$2"

```

---


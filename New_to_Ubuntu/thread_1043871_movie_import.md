---
title: "movie import"
date: 2009-01-18
forum: New to Ubuntu
---

### Post by metallicamike on 2009-01-18
is there any sort of app that can import movies to an ipod, like a rhytmbox for mpeg's? (excuse the bad metaphor)

---

### Post by metallicamike on 2009-01-18
bumpity bump

---

### Post by PurposeOfReason on 2009-01-18
Please wait a while to bump your own thread, 7 minutes is not justified. Gtk-pod should work.
[http://ramblings.narrabilis.com/wp/howto-import-songs-and-videos-onto-an-ipod-in-linux/](http://ramblings.narrabilis.com/wp/howto-import-songs-and-videos-onto-an-ipod-in-linux/)

---

### Post by metallicamike on 2009-01-18
but hey, i got someones attention tho

---

### Post by metallicamike on 2009-01-19
for some reason gtkpod won't let me import videos?

---

### Post by metallicamike on 2009-01-19
aw come on now

---

### Post by metallicamike on 2009-01-19
ok, i will explain a little better. I installed gtkpod and for some reasone it will not let me import videos. I tried to get VO0.99.2-1 but that is only for dapper. the one for hardy is VO0.99.14-1. is there any way for me to import videos on there or any other apps to do so? I don't know if this matters but the video file is a .ogv

---

### Post by PurposeOfReason on 2009-01-19
Ipods can only play mp4.

---

### Post by metallicamike on 2009-01-19
so how can i convert the ogv to mp4?

---

### Post by billgoldberg on 2009-01-19
I've never heard of .ogv, but try winff (gui frontend for ffmpeg).

You'll need to google for it and use the .deb installer you downloaded.

Double click it to install.

---

### Post by metallicamike on 2009-01-19
which type should i convert it to since there is no mp4? im doing WMV right now, i hope that is the right one.

---

### Post by metallicamike on 2009-01-19
*sigh*

---

### Post by metallicamike on 2009-01-19
come on, some one please help me out on this......

---

### Post by PurposeOfReason on 2009-01-19
[What you are looking for.](http://www.google.com)

---

### Post by metallicamike on 2009-01-19
actually it isn't

---

### Post by lavinog on 2009-01-19
avidemux should let you convert it.
it is in the repositories.
I don't have an Ipod, so I cant help you with the settings, but I do know it can handle converting many videos to mp4

---

### Post by metallicamike on 2009-01-19
it wont let me do anything with it to convert, and it crashes anyway. anything else people?

---

### Post by metallicamike on 2009-01-19
bump

---

### Post by chrisblack on 2009-01-19
Is Handbrake available for Ubuntu/linux -I've just discovered it on Windows, for converting .vob to .avi/.mp4 etc.... but 'aint looked for the linux version yet????



Chris

---

### Post by metallicamike on 2009-01-19
it may be, im pretty sure that it is for mac, ill look

---

### Post by chrisblack on 2009-01-19
Have a look here [http://handbrake.fr/?article=download](http://handbrake.fr/?article=download) there's a download for Ubuntu both CLI and GUI.

Just grabbing it myself

Chris

---

### Post by lavinog on 2009-01-19
mencoder (part of mplayer) is another option, but it isn't user friendly...if you want to use it, do a google search for *mencoder ipod examples*

---

### Post by metallicamike on 2009-01-19
it is! but it won't open...

---

### Post by metallicamike on 2009-01-19
i *really* dont want anything that is not user friendly, iv had enough problems as it is. :lolflag:

---

### Post by lavinog on 2009-01-19
If i recall Ipods are far from user friendly too.
I can only recommend trying it.
Or figuring out why avidemux crashed...it might be a simple fix.
Where is the source video coming from?

---

### Post by metallicamike on 2009-01-19
desktop

---

### Post by lavinog on 2009-01-19
> **metallicamike said:**
> desktop

Are you recording your desktop, or the file is on the desktop?
If it is a file what type of file? (avi, mov, wmv...etc) Where did it come from? (internet site, torrent, video camera, dvd...etc)

---

### Post by andrew.46 on 2009-01-20
Hi,

If you can get hold of a copy of ffmpeg run the following command on one of your files:

```
$ ffmpeg -i myfile.ogv
```

and this will show what is inside the container. With this known conversion should not be too difficult. Now some people say that ffmpeg is not user-friendly but that is not true, ffmpeg is simply a little choosy with its friends :-).

Andrew

---


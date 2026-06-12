---
title: "What is the best program to use to convert WMV files?"
date: 2011-06-03
forum: New to Ubuntu
---

### Post by TAspr on 2011-06-03
I trying to find a program, paid or not that will convert a WMV file into a DVD format so you can watch it through your DVD player.  Is there such a software?

---

### Post by ron999 on 2011-06-03
Hi
There's a program called '**DeVeDe**'.

If it doesn't work out for you, it's quite easy to do the job using command line.
Like this:-

1) Convert the wmv file to mpeg2.
(Makes a file named **video.mpg**)

```
ffmpeg -i filename.wmv -target pal-dvd video.mpg
```
or
```
ffmpeg -i filename.wmv -target ntsc-dvd video.mpg
```


2) Create the file system.
(Makes a folder named **DVD** containing VIDEO_TS and AUDIO_TS folders)
```
dvdauthor -o DVD/ -t video.mpg && dvdauthor -o DVD/ -T

```
3) Create an iso image (optional).
(Makes a file named **DVD.iso**)
```
genisoimage -dvd-video -v -o DVD.iso DVD
```


Then burn the DVD using a program such as **K3b**.

---

### Post by TAspr on 2011-06-03
> **ron999 said:**
> Hi
There's a program called '**DeVeDe**'.

If it doesn't work out for you, it's quite easy to do the job using command line.
Like this:-

1) Convert the wmv file to mpeg2.
(Makes a file named **video.mpg**)

```
ffmpeg -i filename.wmv -target pal-dvd video.mpg
```or
```
ffmpeg -i filename.wmv -target ntsc-dvd video.mpg
```
2) Create the file system.
(Makes a folder named **DVD** containing VIDEO_TS and AUDIO_TS folders)
```
dvdauthor -o DVD/ -t video.mpg && dvdauthor -o DVD/ -T

```3) Create an iso image (optional).
(Makes a file named **DVD.iso**)
```
genisoimage -dvd-video -v -o DVD.iso DVD
```
Then burn the DVD using a program such as **K3b**.


Wow, how awesome!  Thank you.  I will try it.

---

### Post by JohnBonne on 2011-06-03
> **TAspr said:**
> I trying to find a program, paid or not that will convert a WMV file into a DVD format so you can watch it through your DVD player.  Is there such a software?

Try Arista Transcoder. The best for converting _to_ wmv is Youtube Downlander. Great little tools that takes up so little space and time.

---

### Post by 3rdalbum on 2011-06-04
Brasero comes preinstalled on Ubuntu and should be able to do what you want. If the Totem Movie Player can play the WMV file then Brasero should be able to convert it to DVD, and will probably do a better job than Devede (I've always found Devede puts audio and video out of sync).

---

### Post by Jagoly on 2011-06-04
> **ron999 said:**
> Hi
There's a program called '**DeVeDe**'.

If it doesn't work out for you, it's quite easy to do the job using command line.
Like this:-

1) Convert the wmv file to mpeg2.
(Makes a file named **video.mpg**)

```
ffmpeg -i filename.wmv -target pal-dvd video.mpg
```
or
```
ffmpeg -i filename.wmv -target ntsc-dvd video.mpg
```


2) Create the file system.
(Makes a folder named **DVD** containing VIDEO_TS and AUDIO_TS folders)
```
dvdauthor -o DVD/ -t video.mpg && dvdauthor -o DVD/ -T

```
3) Create an iso image (optional).
(Makes a file named **DVD.iso**)
```
genisoimage -dvd-video -v -o DVD.iso DVD
```


Then burn the DVD using a program such as **K3b**.

not the most efficient method, but probably the coolest.

---

### Post by andrew.46 on 2011-06-04
> **ron999 said:**
> Then burn the DVD using a program such as **K3b**.

Or continue the fine commandline work with:

```

growisofs -dvd-compat -Z /dev/dvd=**[COLOR="Red"]movie_name.iso[/COLOR]**

```

Of course putting the *actual* iso name in place...

---

### Post by TAspr on 2011-06-04
> **andrew.46 said:**
> Or continue the fine commandline work with:

```

growisofs -dvd-compat -Z /dev/dvd=**[COLOR=Red]movie_name.iso[/COLOR]**

```Of course putting the *actual* iso name in place...


Ok, Andrew, please explain the process on what to do as in convert, burn using another program, etc.  Please, I am a serious newbie.

---

### Post by andrew.46 on 2011-06-05
> **TAspr said:**
> Ok, Andrew, please explain the process on what to do as in convert, burn using another program, etc.  Please, I am a serious newbie.

This line simply burns the iso to dvd, the actual *process* is described by ron999 in his post above :).

---

### Post by TeoBigusGeekus on 2011-06-05
Just beware that devede, as well as other dvd authoring apps, are currently broken regarding subtitles' support (inconsistency between spumux and them).
If you want to add subtitles, follow this procedure:
1)Create an xml file
```
<subpictures format="PAL">
    <stream>
        <textsub filename=/path/subtitle.srt"
        font="arial.ttf"
        characterset="CP1253"
        horizontal-alignment="center"
        movie-width="712"
        movie-height="568"
        left-margin="57"
        right-margin="57"
        bottom-margin="27"
        top-margin="27"
        fontsize="28.0"
        movie-fps="25"
        subtitle-fps="25"
        vertical-alignment="bottom" />
    </stream>
</subpictures>
```
Make the necessary changes of course according to your needs (PAL/NTSC, encoding, fps, etc.).
The font (arial in this case) must be in the ~/.spumux folder.
Save it as sub.xml

2) With the xml, mpeg and srt file in the same folder, do
```
spumux -s0 -m dvd -P sub.xml < movie.mpeg > movie_with_subs.mpeg
```
This will the subtitle in your mpeg in the first position ( -s0 ). If you want to add more subtitles, repeat the procedure with -s1, -s2, etc.

3) Finally. Author the dvd with dvdauthor and burn it.

---

### Post by Paqman on 2011-06-05
> **JohnBonne said:**
> Try Arista Transcoder.

+1

Arista is awesome. By far the best video converter on the Linux desktop. Couple of clicks and you're done, no need to faff about with mystical settings.

---

### Post by gandaran on 2011-06-05
> **TAspr said:**
> I trying to find a program, paid or not that will convert a WMV file into a DVD format so you can watch it through your DVD player.  Is there such a software?
any linux dvd player will play normal WMV files if you got the windows codecs installed theres no need to convert them, some WMV file type are DRM protected and can only be played in windows media player, if yours are DRM protected forget it.

---

### Post by Legendary_Bibo on 2011-06-05
Handbrake.

---

### Post by Jagoly on 2011-06-06
handbrake can't burn to DVD's or convert to mpeg2. It's purpose is to convert any other video (wmv or dvd ect.) to mpeg4 or H.264, for playback on almost any computer or portable media player (like ipods). That it does very well.

---

### Post by TAspr on 2011-06-07
Ok, thanks again for all of your help.

---


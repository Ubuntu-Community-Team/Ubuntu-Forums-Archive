---
title: "Spumux error subtitles...? plz help.."
date: 2008-12-25
forum: New to Ubuntu
---

### Post by hopelessone on 2008-12-25
Hi All,


I get this error while trying to add korean subtitles:
> some@some-one:~/Music$ spumux -s0 /home/some/Music/subtitle.xml < /home/some/Music/Max.mpg > /home/some/Music/Max.mpg.temp
DVDAuthor::spumux, version 0.6.14.
Build options: gnugetopt magick iconv freetype
Send bugs to <dvdauthor-users@lists.sourceforge.net>

INFO: Locale=en_US.UTF-8
INFO: Converting filenames to UTF-8
INFO: Detected subtitle file format: sami
INFO: Opened iconv descriptor. *UTF-8* *EUC-KR*
**[COLOR="Red"]WARN: Error recoding line (1). *(null)* ip:&#65533; il:1 op:&#45768;&#51648; ol:495 l:0[/COLOR]**
INFO: Unicode font: 2802 glyphs.
ERR: Couldn't load file /home/some/Music/Max.smi.
some@some-one:~/Music$ 


Here is the subtitle.xml
> <subpictures> <stream> <textsub filename="/home/some/Music/Max.smi" characterset="EUC-KR" fontsize="18.0" font="FreeSans.ttf" horizontal-alignment="center" vertical-alignment="bottom" left-margin="60" right-margin="60" top-margin="20" bottom-margin="30" subtitle-fps="29.97" movie-fps="29.97" movie-width="720" movie-height="478"/> </stream> </subpictures>

How can i fix this?

thanks...

---

### Post by hopelessone on 2008-12-25
Hi I'm having a lot of trouble converting movie files with Korean subs...

I just cant do it...!!!???

I can convert .avi's to dvd no probs...Anyone know how to add korean subs?

Thanks...

---

### Post by nhasian on 2008-12-25
did you try DeVeDe?  It allows you to take video files like avi and burn them to DVD.  it also supports subtitles.

```
sudo apt-get install devede
```

---

### Post by hopelessone on 2008-12-25
i tried it gives me an error(attached)

The sub file is .smi

any ideas?

Thanks..it plays well with Totem...

---

### Post by Sef on 2008-12-25
Merged threads.

---

### Post by lobo-tuerto on 2009-05-12
Seems like an error in the codification specified.

I had a similar error when I added some Spanish subs and I thought they were UTF8, but they actually were ISO-8859-1. When changed from UTF8 to ISO-8859-1, no more errors from spumux.

---

### Post by sistematico on 2010-07-03
Same error here, without subtitles.

---


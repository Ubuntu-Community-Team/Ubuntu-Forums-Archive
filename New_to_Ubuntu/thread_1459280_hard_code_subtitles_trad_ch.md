---
title: "hard code subtitles trad ch"
date: 2010-04-21
forum: New to Ubuntu
---

### Post by powel212 on 2010-04-21
Hey

Anybody know what to add to this command to make this awesome hardcore subtitles work for Chinese traditional?

```
mencoder movie.avi -sub movie.srt -o movie.hardsubs.avi -oac copy -ovc lavc -lavcopts vbitrate=1200
```

I am sure I just need to add something to the string for Chinese traditional encoding. But I don't know what or where to add it.

thanks

P

---

### Post by MooPi on 2010-04-21
When I encode I use the command ```
-alang en
``` This uses English as the audio language. ```
-slang ** 
``` to set the subtitle language. Now for the font and other settings I'm not certain. Try searching man for references to subtitle```
man mencoder
```

---

### Post by powel212 on 2010-04-21
Thanks

I'll give that a shot.

Where do I insert it into the command?

Like this?

```
mencoder movie.avi -sub movie.srt -o -alang ch movie.hardsubs.avi -oac copy -ovc lavc -lavcopts vbitrate=1200
```
P.

---

### Post by powel212 on 2010-04-21
Tried all of these. Some I pulled from a chinese ubuntu forum. My chinese is pretty weak though.

anyway, fail, fail, fail.

Seems close though. Get the subtitles at bottom just encoding is wrong so just a bunch of randome goop instead of words.

```
mencoder /home/user/Desktop/imag.avi -sub subfont-encoding unicode /home/user/Desktop/imag.srt -o /home/user/Desktop/imagdone.avi -oac copy -ovc lavc -lavcopts vbitrate=1200

```
fail
```
mencoder -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=4000 -ofps 25 -of avi -oac copy -font /usr/share/fonts/truetype/freefont/FreeSerif.ttf -subcp UTF-8 -subfont-text-scale 4 -sub /home/user/Desktop/gos.srt /home/user/Desktop/gos.avi -o /home/user/Desktop/gosdone.avi

```
fail
```
mencoder -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=4000 -ofps 25 -of avi -oac copy -font mp.ttf -subcp cp950 -subfont-text-scale 4 -sub /home/user/Desktop/gos.srt /home/user/Desktop/gos.avi -o /home/user/Desktop/gosdone2.avi

```
fail
```
mencoder -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=4000 -ofps 25 -of avi -oac copy -font mp.ttf -subcp big5 -subfont-text-scale 4 -sub /home/user/Desktop/gos.srt /home/user/Desktop/gos.avi -o /home/user/Desktop/gosdone3.avi
```

any insight?

P.

---

### Post by MooPi on 2010-04-21
I didn't notice your trying to get subtitles from an .avi file. I don't think your able to get subtitles from an already encoded file. Getting them from a dvd is another question.

---


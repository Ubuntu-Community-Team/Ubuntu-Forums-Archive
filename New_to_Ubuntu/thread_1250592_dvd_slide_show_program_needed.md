---
title: "dvd slide show program needed"
date: 2009-08-26
forum: New to Ubuntu
---

### Post by Peterfc on 2009-08-26
Hi All

I am using 9.04 with all updates as from the Update manager informs me of. I need a program to allow me to create a slide show and load it onto a dvd. Any body have any ideas as what to use to create a dvd with a auto run slide show.

Thanks

---

### Post by sydbat on 2009-08-26
Open Office (which comes with Ubuntu) has something called 'Presentation'. You can create the slide show there, but I am not entirely sure if, when burned to DVD, it will automatically "run".

Perhaps someone better versed can help.

---

### Post by JustJ on 2009-08-26
After writing what follows, I found the linux package dvd-slideshow on the web:

[http://dvd-slideshow.sourceforge.net/wiki/Main_Page]("http://dvd-slideshow.sourceforge.net/wiki/Main_Page")

Check out the links near the bottom of that page as I'm sure one or two will point to user-friendly interfaces you might like, if the main package doesn't supply one that is?  Looks like what you need!  

Here's what I had originally typed:

I suspect there are some better automated solutions, but consider making a movie using mencoder and putting that on the dvd. 

from:  [http://electron.mit.edu/~gsteele/ffmpeg/](http://electron.mit.edu/~gsteele/ffmpeg/)

```
mencoder "mf://*.jpg" -mf fps=10 -o test.avi -ovc lavc -lavcopts vcodec=msmpeg4v2:vbitrate=800
```

Note that the mf:// prefix is required for the jpeg image to actually play.
Test it with
  ```
 mplayer "mf://*.jpg" -mf fps=0.1
```
You can use fps=.5 for 2 second delay, 1/x for x seconds  1/10=0.1, 1/20=002  etc.

This guy mentions adding an audio track using -audiofile=song.mp3 :
[http://www.goblinx.com.br/en/?p=385]("http://www.goblinx.com.br/en/?p=385")

---


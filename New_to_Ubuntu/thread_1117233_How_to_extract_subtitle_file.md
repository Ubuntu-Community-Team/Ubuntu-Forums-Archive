---
title: "How to extract subtitle file"
date: 2009-04-05
forum: New to Ubuntu
---

### Post by conryf on 2009-04-05
I have a DVD with a big fat scratch and an avi file. The DVD is itself unplayable. However, the avi works fine. The catch is, the movie is in thai and it kind of hard to watch without subtitles. Is ther a way to extract jus tthe subtitles from the DVD?

---

### Post by bertolo on 2009-04-05
why don't search for them on google.

---

### Post by conryf on 2009-04-05
I did. Unforunately there's nothing availble. It's not a terribly common movie.

---

### Post by Didius Falco on 2009-04-05
I haven't used it, but you could try Avidemux. It's available on Synaptic Package Manager.

Here is a link to a tutorial on how to do it with Avidemux:
[http://en.flossmanuals.net/Avidemux/ExtractingDVDSubtitles](http://en.flossmanuals.net/Avidemux/ExtractingDVDSubtitles)

Here is the SourceForge site, with further documentation:
[http://avidemux.sourceforge.net/](http://avidemux.sourceforge.net/)

I hope this helps...

---

### Post by conryf on 2009-04-08
Worked like a charm! Thanks so much!

---

### Post by Didius Falco on 2009-04-08
No worries. I'm a newbie at Ubuntu, but I'm pretty good at research. <G>

---

### Post by billgoldberg on 2009-04-08
You could just rip the movie with subitles (burned into the movie) using K9copy.

Just saying.

---

### Post by conryf on 2009-04-08
that's the problem. It won't rip, k9copy, OGMrip k3b, all choke about halfway through. I had an mpg4 for the movie, but not subtitles for it. Was trying to get the subtitles off the broken DVD to play with the mpg4...

The subtitles I got were actually kind of bad, missing large chunks of dialogue, etc. But I think the method here is solid, it was likely this broken DVD.

Thanks again averybody.

---

### Post by Nepherte on 2009-04-08
This method requires you have mplayer installed.

To see the available subtitles:
```
mplayer dvd://streamnumber -v -vo null -ao null | grep "subtitle
```

To rip a subtitle:
```
mencoder dvd://streamnumber -nosound -ovc frameno -o /dev/null -slang yourlanguage -vobsubout outputfilename
```

All you have to do is determine the stream number of the movie (it's usually 1) and substitute streamnumber, yourlanguage and outputfilename with the correct data. You don't have to give an extension to outputfilename.

---


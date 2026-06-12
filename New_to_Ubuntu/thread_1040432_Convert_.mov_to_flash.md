---
title: "Convert .mov to flash?"
date: 2009-01-15
forum: New to Ubuntu
---

### Post by slughappy1 on 2009-01-15
I was wondering if there was a way to convert movies in .mov format to .flv? I was also wondering if there was a way to remove the sound from the videos as well? I found, [http://www.linux.com/feature/121385](http://www.linux.com/feature/121385). But I didn't see any options to disable sound in them.

---

### Post by darrelljon on 2009-01-16
Most experts would use mencoder or ffmpeg. Search for these tools and "remove audio".

---

### Post by StOoZ on 2009-01-16
I do it easily with ffmpeg... give it a try.

---

### Post by HotShotDJ on 2009-01-16
+1 ffmpeg -- this can do pretty much any conversion you need, especially if you have ubuntu-restricted-extras and the [medibuntu repositories]("http://www.medibuntu.org").

---

### Post by zzHanks on 2009-01-16
I think Avidemux can do it also.

It's easy to use.

---

### Post by FakeOutdoorsman on 2009-01-16
```
ffmpeg -i input.mov -an -sameq output.flv
```
The -an options tells ffmpeg to ignore the audio and -sameq (optional) will cause ffmpeg to try to match the quality of the input file.
> **HotShotDJ said:**
> +1 ffmpeg -- this can do pretty much any conversion you need, especially if you have ubuntu-restricted-extras and the [medibuntu repositories]("http://www.medibuntu.org").
If you don't want to install all the other extra junk **ubuntu-restricted-extras** supplies you can just install **libavcodec-unstripped-51** which will enable some restricted codecs in ffmpeg.  Medibuntu will not offer anything you need, unless you're using an earlier version than Intrepid.  If you're on Hardy and some older versions, Medibuntu can offer a more capable ffmpeg.

---

### Post by HotShotDJ on 2009-01-16
> **FakeOutdoorsman said:**
> Medibuntu will not offer anything you need, unless you're using an earlier version than Intrepid.  If you're on Hardy and some older versions, Medibuntu can offer a more capable ffmpeg.This may very well be true.  I've included the Medibuntu repositories as a matter of habit on all my installations since Dapper.  Perhaps I should stop doing that and see what happens. :)

---


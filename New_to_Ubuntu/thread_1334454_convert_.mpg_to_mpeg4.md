---
title: "convert .mpg to mpeg4"
date: 2009-11-22
forum: New to Ubuntu
---

### Post by Commisar Jimp on 2009-11-22
I've got some .MPG files that I need to convert to .mpeg4, what's a good program for that?
Thanks

---

### Post by danill2008 on 2009-11-22
You can try Arista Transcoder or Iriverter. Not sure how they work, but you can get them under Applications > Ubuntu Software Center

---

### Post by SuperSonic4 on 2009-11-22
command line ffmpeg

```
ffmpeg -i input.mpg -sameq -vcodec mpeg4 -ac 2 -ab 128k -acodec libmp3lame output.mpeg
```


```
man ffmpeg
``` has a *lot* more info

---

### Post by Commisar Jimp on 2009-11-22
thanks guys

---


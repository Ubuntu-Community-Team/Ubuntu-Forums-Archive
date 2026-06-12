---
title: "Is there a &quot;flac&quot; to Apple LossLess &quot;.m4a&quot; converter?"
date: 2010-07-29
forum: New to Ubuntu
---

### Post by hdtvman on 2010-07-29
Does any one know if there is a "flac" to Apple LossLess audio converter available for Ubuntu?

---

### Post by jerenept on 2010-07-30
1) m4a is not lossless.
2)winff should be good.

---

### Post by MrWES on 2010-07-30
I have a flac2mp3 bash script if you're interested.

Bill

---

### Post by Bachstelze on 2010-07-30
> **jerenept said:**
> 1) m4a is not lossless.

.m4a is a container.  It can contain a variety of audio formats, including the lossless ALAC.

@hdtvman:

```
ffmpeg -i foo.flac -acodec alac foo.m4a
```

---

### Post by ron999 on 2010-07-30
.....................

---

### Post by otaniyul on 2012-10-14
thank you for the terminal solution. i guess i'll use this conversion until my apple iphone dies and i switch to a flac portable playing device. cheers.

---

### Post by wildmanne39 on 2012-10-14
Old thread closed.

---


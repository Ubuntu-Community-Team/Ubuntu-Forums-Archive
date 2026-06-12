---
title: "Converting Metacafe and Youtube FLV to mpg files"
date: 2009-12-13
forum: New to Ubuntu
---

### Post by darkchest on 2009-12-13
Hi all,

I got videos off the /tmp folder when they were streaming on youtube or metacafe or some other flash player and I am trying to convert them to mpg files. 

I searched for a solution and saw people mention Avidemux, when I open a video flv file, i get an error message saying sound will be a problem. Is there any software that will perform my conversion needs without a hassle.

Thanks.

---

### Post by garryknight on 2009-12-13
If you don't mind using the command line, you could try this:
ffmpeg -i myfile.flv myfile.mpg

---

### Post by darkchest on 2009-12-13
Thank you very much, i tried it on one video and it worked fine. I want to test it on the others then i will test it in windows. And i will get back to tag the post solved or not.

Thanks once again garryknight

---

### Post by darkchest on 2009-12-15
using ffmpeg worked well for youtube videos, but metacafe and some other online video formats did not convert.
Thanks

---

### Post by garryknight on 2009-12-15
You're welcome. As for the other formats, you could try passing different options to ffmpeg.

---

### Post by dinw3 on 2009-12-23
try using winFF it is GUI interface for ffmeg

---

### Post by gwenn on 2009-12-23
Audacity if you preffer  GUI

---


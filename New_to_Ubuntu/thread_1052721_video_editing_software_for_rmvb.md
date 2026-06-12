---
title: "video editing software for rmvb"
date: 2009-01-28
forum: New to Ubuntu
---

### Post by vincent chin on 2009-01-28
Hi, I am newbie of Unbuntu 8.10.Is there any video editor which support editing of rmvb video file?

Thank you.

---

### Post by stoogiebuncho on 2009-02-01
The popular Linux video editors that I know of are Kino and Cinelerra.  As for rmvb, I'm really not sure.  It would probably say on their websites.

---

### Post by HotShotDJ on 2009-02-01
> **vincent chin said:**
> Hi, I am newbie of Unbuntu 8.10.Is there any video editor which support editing of rmvb video file?Could you link to a sample rmvb video file?  I'll be happy to test this format on the editors that I have, but I can't find any to use for testing.

EDIT:  Found one.  Kino imported it. Cinelerra did not.  Also successfully converted it to an AVI using:```
mencoder in.rmvb -oac mp3lame -lameopts preset=128 -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=1200 -ofps 25 -of avi -o out.avi
```

---


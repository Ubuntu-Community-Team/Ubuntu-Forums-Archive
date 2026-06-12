---
title: "[SOLVED] mkv in avi container"
date: 2008-12-30
forum: New to Ubuntu
---

### Post by lad3391 on 2008-12-30
i have a few movies in .mkv format, i read an article online about how to store them as avi without a complete re encoding, thus allowing one to play these file types from a portable harddrive onto the xbox 360. i was wondering if ne1 knew how to do this in ubuntu?

[http://www.afterdawn.com/guides/archive/how_to_play_mkv_content_on_xbox_360.cfm](http://www.afterdawn.com/guides/archive/how_to_play_mkv_content_on_xbox_360.cfm)

thats the article i read, but im pretty sure its for windows


ubuntu 8.10, dell insprion 6000

---

### Post by jpkotta on 2008-12-30
mkv is a container like avi.  Try avidemux.  Or maybe mencoder:```
mencoder -ovc copy -oac copy -of avi -o foo.avi foo.mkv
```

---

### Post by lad3391 on 2008-12-30
im guessing the foo.avi and foo.mkv are the names of the files?

---

### Post by jpkotta on 2008-12-31
Yes.  [http://en.wikipedia.org/wiki/Foo](http://en.wikipedia.org/wiki/Foo)

---


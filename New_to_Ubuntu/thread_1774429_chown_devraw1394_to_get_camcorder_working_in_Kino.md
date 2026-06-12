---
title: "chown /dev/raw1394 to get camcorder working in Kino"
date: 2011-06-03
forum: New to Ubuntu
---

### Post by eriktheblu on 2011-06-03
Just started playing with my minidv camcorder last night, but Kino wasn't connecting normally.

After a little searching, I decided to try
```
sudo chown eriktheblu /dev/raw1394
```

It works very well now; no opening Kino with gksudo, and the video transfers nicely.

Looking into it a little more, my solution does not seem typical, and I'm starting to wonder if there is a potential danger to changing ownership as I did. My machine has only one user account.

---


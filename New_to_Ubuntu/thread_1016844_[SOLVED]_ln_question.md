---
title: "[SOLVED] ln question"
date: 2008-12-20
forum: New to Ubuntu
---

### Post by ant2ne on 2008-12-20
/mnt/net.media/*mediafiles*
```

ln -sf /mnt/net.media ~/Desktop/media

```
executing this command, there is a dir 
~/Desktop/media/net.media/*mediafiles*

what I want is 
~/Desktop/media/*mediafiles*

What am I doing wrong.

---

### Post by cmnorton on 2009-01-08
I am assuming that you don't want '*' as part of the file name.

I tried your command and got what I would have assumed were the desired results, except I did not use -f.

---

### Post by ant2ne on 2009-01-10
Woa,.. I swear got another response to this thread that answered my problem. I wonder shat happend to it. The problem was that I thought I had to create the direcotry ~/Desktop/media. When the ln creates it.


The *mediafiles* is to demonstrate any random media files that might be in that location.

---


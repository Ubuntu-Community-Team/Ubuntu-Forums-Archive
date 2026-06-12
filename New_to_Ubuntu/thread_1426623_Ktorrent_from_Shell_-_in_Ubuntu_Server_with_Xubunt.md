---
title: "Ktorrent from Shell - in Ubuntu Server with Xubuntu"
date: 2010-03-10
forum: New to Ubuntu
---

### Post by gottijr on 2010-03-10
-newbie in linux-

  I mannaged to install ktorrent from Xubuntu on my ubuntu server

  The question is how can i start it in shell mode without the x running? Is that possible? thank you

  would like advice against ktorrent vs transmission?

  thank you

---

### Post by marshmallow1304 on 2010-03-10
You could try [rtorrent]("apt://rtorrent"), which is CLI-based.  Here's a [good guide]("http://kmandla.wordpress.com/2007/05/02/howto-use-rtorrent-like-a-pro/").

---

### Post by gottijr on 2010-03-10
> **marshmallow1304 said:**
> You could try [rtorrent]("apt://rtorrent"), which is CLI-based.  Here's a [good guide]("http://kmandla.wordpress.com/2007/05/02/howto-use-rtorrent-like-a-pro/").

  how do i install rtorrent in xubunut? on ubuntu server?

  thanks

---

### Post by marshmallow1304 on 2010-03-10
```
sudo apt-get install rtorrent
```

You'll need to enable the universe repository if it isn't already enabled.

---


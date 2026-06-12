---
title: "Neither Movie Player nor VLC will play"
date: 2011-01-27
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2011-01-27
This URL:

mms://2x4.telecomdatacenter.com.ar/2x4

won't play on any player I have. I know this site uses only-the-latest Adobe Flash products, yet, is there a way to get it to play?

---

### Post by Wobblybob on 2011-01-27
can we have a like to the actual site please

---

### Post by sandyd on 2011-01-27
> **Mark_in_Hollywood said:**
> This URL:

mms://2x4.telecomdatacenter.com.ar/2x4

won't play on any player I have. I know this site uses only-the-latest Adobe Flash products, yet, is there a way to get it to play?
Server side issue
```

sandy@sandyd-laptop /usr/src/linux-2.6.38-rc2-git5 $ mplayer -vo vdpau -nosound mms://2x4.telecomdatacenter.com.ar/2x4
MPlayer SVN-r32624-4.4.4 (C) 2000-2010 MPlayer Team

Playing mms://2x4.telecomdatacenter.com.ar/2x4.
STREAM_ASF, URL: mms://2x4.telecomdatacenter.com.ar/2x4
Resolving 2x4.telecomdatacenter.com.ar for AF_INET6...

Couldn't resolve name for AF_INET6: 2x4.telecomdatacenter.com.ar
Resolving 2x4.telecomdatacenter.com.ar for AF_INET...
Connecting to server 2x4.telecomdatacenter.com.ar[200.82.126.78]: 1755...

connect error: Connection refused


```

---

### Post by Mark_in_Hollywood on 2011-01-27
> **Wobblybob said:**
> can we have a like to the actual site please

Please see:


[http://www.la2x4.gov.ar/](http://www.la2x4.gov.ar/)

---

### Post by Mark_in_Hollywood on 2011-01-27
It works on Windooo$ without problem, however. SO, as I read your post, the connection is refused because I use Linux?

---

### Post by sandyd on 2011-01-27
initially, you listed the wrong url.
go to 
[http://www.la2x4.gov.ar/index.swf](http://www.la2x4.gov.ar/index.swf)

---

### Post by Mark_in_Hollywood on 2011-01-28
> **sandyd said:**
> initially, you listed the wrong url.
go to 
[http://www.la2x4.gov.ar/index.swf](http://www.la2x4.gov.ar/index.swf)

I don't know what a "wrong url" for this site is. I used your's with the .swf extension. I get a slightly different looking page than without the .swf. Neither yours nor mine play the music. At least not here at my 'puter. 

Please compare attached screenshots for clarification.

---


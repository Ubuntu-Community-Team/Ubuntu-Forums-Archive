---
title: "adobe player in firefox"
date: 2009-08-05
forum: New to Ubuntu
---

### Post by Dave.E on 2009-08-05
When playing a youtube video with Firefox in Ubuntu, the vid has all sorts of problems.
 if I  right click the vid as it's running and click 'about' it is running something called SWFDEC. 
Is there any way I can get it to use adobe flash player?

I've tried all sorts & failed!

Cheers,

Dave.

---

### Post by Lampi on 2009-08-05
SWFDEC is another flash player - if you don't like it, here's how to get rid of it:

Exit firefox, then
```
sudo aptitude purge swfdec-mozilla
```
Now install flash player from adobe:
```
sudo aptitude install adobe-flashplugin
```

---

### Post by DrDevice on 2009-08-05
Here's a comprehensive guide to multimedia, codecs, and all that shiny goodness:

[http://ubuntuforums.org/showthread.php?t=766683]("http://ubuntuforums.org/showthread.php?t=766683")

Step-by-step and easy, got all my stuff working in about 10 minutes with it.

---

### Post by LunaticHiatus on 2009-08-05
There are three players for flash in ubuntu. Adobe Flash works the best. SWF player and Gnash are free (as in freedom) players where you can look and edit the source code yourself and etc. However, they are not up to the level of the adobe version yet.

---

### Post by colau on 2009-08-16
> **Dave.E said:**
> When playing a youtube video with Firefox in Ubuntu, the vid has all sorts of problems.
 if I  right click the vid as it's running and click 'about' it is running something called SWFDEC. 
Is there any way I can get it to use adobe flash player?

I've tried all sorts & failed!

Cheers,

Dave.
```

sudo aptitude install adobe-flashplugin

```

---

### Post by coldReactive on 2009-08-16
Or
```
sudo apt-get install flashplugin-nonfree
```

---

### Post by oboedad55 on 2009-08-16
Thanks for the help guys. I was having the same problem in hardy. I got rid of the shockwave plugin. That fixed things

---


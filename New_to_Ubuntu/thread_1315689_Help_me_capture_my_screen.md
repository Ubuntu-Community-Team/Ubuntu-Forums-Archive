---
title: "Help me capture my screen"
date: 2009-11-05
forum: New to Ubuntu
---

### Post by nadian on 2009-11-05
I want to capture screen into a movie file that will play on the web. Capturemyscreen only outputs to .ogg, xvidcap captures but won't let me edit the saved video, Wink - which I've used on other OS does exactly what I want - various web friendly outputs, ability to edit add text, speech bubbles, highlight areas e.tc. But is no longer in the repositories sudo apt gets a 404 and downloading it as a tar.gz extracting gives an exe that won't execute. Has anyone got any ideas about either an alternative that does what i want and works in ubuntu 9.10 or a way to install wink in ubuntu 9.10 so that it works?

---

### Post by Ant59 on 2009-11-05
Can you not just convert the ogg video after?

---

### Post by nadian on 2009-11-05
i didn't think of that, i'll try crecordMyDesktop and a convert, thanks I'll let you know if it works

---

### Post by nadian on 2009-11-05
> **nadian said:**
> i didn't think of that, i'll try crecordMyDesktop and a convert, thanks I'll let you know if it works
ok I managed to 'recordmydesktop' used pitiki to convert to flv - other options resulted in too large a file, it worked...but, quality is poor, file size still too big, not simple to add text and annotate (unlike wink) and no sound.
go here to see results of test:
[http://www.gwilkinson4.btinternet.co.uk/](http://www.gwilkinson4.btinternet.co.uk/)
any more suggestions?

---

### Post by Ant59 on 2009-11-06
If the video is for viewing on your site only, then why not stream it in flash player? That way you can have a rather large flv, but the viewer can watch as it buffers/loads.

---

### Post by nadian on 2009-11-06
Thanks that sounds like a good idea - how  do i do it?

---

### Post by Ant59 on 2009-11-06
You could use Flash CS4 to create a video streaming app for your site. Or you could use something like this one: [http://flowplayer.org/download/index.html](http://flowplayer.org/download/index.html)

Try Google for others.

---

### Post by nadian on 2009-11-06
Hey thats much better! [http://www.gwilkinson4.btinternet.co.uk/](http://www.gwilkinson4.btinternet.co.uk/) thanks very much Ant59, I used to live in bristol and cycled down to the mendips many a time, a beautiful part of the country.
Still want wink to work on ubuntu 9.10, any ideas anyone?

---

### Post by nadian on 2009-11-06
Here's where I've got to with wink - followed instructions at [http://ubuntuforums.org/showthread.php?t=227536](http://ubuntuforums.org/showthread.php?t=227536) but get this error on run:

[COLOR=Navy]g@g-laptop:/home$ sudo sh ./installer.sh
[sudo] password for g: 
sh: Can't open ./installer.sh
g@g-laptop:/home$ sudo apt-get install build-essentials
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package build-essentials

[COLOR=Black]can anyone help?[/COLOR]
[/COLOR]

---

### Post by andrew.46 on 2009-11-07
Hi nadian,

> **nadian said:**
> 
```
E: Couldn't find package build-essentials
```


You have made a small typo (duplicated from the post you referred to):

```
sudo apt-get install build-essential
```

But these are tools for *compiling *software, is this really what you had in mind?

All the best,

Andrew

---

### Post by nadian on 2009-11-07
thanks andrew, your right I did misquote build essentials, but they actually did install. Here's where I've got to with this now. Downloaded and ran install.sh  and get this error
:
Wink requires that the following packages be installed to run properly. Please install them and try again.

libexpat.so.0
 so I went to synaptic but only listed libexpat 1- i installed that to see if it would help, but it didn't.
this may be a solution?:
[http://www.debugmode.com/userforums/viewtopic.php?t=7100&sid=24319506299d9f88e9ec6c596ce1be8e](http://www.debugmode.com/userforums/viewtopic.php?t=7100&sid=24319506299d9f88e9ec6c596ce1be8e) 
leading to
[https://bugs.launchpad.net/ubuntu/+source/wink/+bug/185868](https://bugs.launchpad.net/ubuntu/+source/wink/+bug/185868) 
but i'm not sure I want to try it or exactly what to do..., things seem to be getting very complicated...

---

### Post by Ant59 on 2009-11-07
I think this may be what you're looking for: [http://hulles.supersized.org/archives/13-Installing-Wink-in-Ubuntu-Hardy-Heron.html](http://hulles.supersized.org/archives/13-Installing-Wink-in-Ubuntu-Hardy-Heron.html)

---

### Post by nadian on 2009-11-09
I finally got WInk working - see this other thread from page two for solution to issues:
[http://ubuntuforums.org/showthread.php?t=938838&page=2](http://ubuntuforums.org/showthread.php?t=938838&page=2)
thanks everbody for all your help

---


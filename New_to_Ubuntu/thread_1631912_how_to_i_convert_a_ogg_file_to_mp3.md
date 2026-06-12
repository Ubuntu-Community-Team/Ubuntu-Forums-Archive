---
title: "how to i convert a ogg file to mp3"
date: 2010-11-27
forum: New to Ubuntu
---

### Post by rburkartjo on 2010-11-27
i need to convert to post to my facebook page. file is located on my computer and i can use soundbite to update. however they only accept mp3. tried ogg just for the heck of it and wouldnt upload/tks

---

### Post by speedofdark on 2010-11-27
You can try the program  ogg2mp3, think it's in the repository.

---

### Post by nothingspecial on 2010-11-27
```
ffmpeg -i song.ogg song.mp3
```

Need to get ffmpeg with mp3 support, see here

[http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)

---

### Post by motorcity909 on 2010-11-27
For a GUI, there is the Gnome Sound Converter, it's in the software centre.

---

### Post by HermanAB on 2010-11-27
sox

---

### Post by rburkartjo on 2010-11-27
motor, sound converter did the trick/tks

---

### Post by andrew.46 on 2010-12-09
Hi Herman,

> **HermanAB said:**
> sox

I believe the Ubuntu repository package of sox has had the ability to convert to mp3 removed. However I wrote up a mini repackaging guide a while back to get over this:

[http://ubuntuforums.org/showpost.php?p=9859875&postcount=8](http://ubuntuforums.org/showpost.php?p=9859875&postcount=8)

I have always been a little saddened that I wrote all this up and nobody appears to have used the information :(.

Andrew

---

### Post by nothingspecial on 2010-12-10
> **andrew.46 said:**
> 

I have always been a little saddened that I wrote all this up and nobody appears to have used the information :(.

Andrew

I used it :D

many times........

.....and your abcde confs

---

### Post by andrew.46 on 2011-01-12
Hi nothingspecial,

> **nothingspecial said:**
> I used it :D

many times........

.....and your abcde confs

Good to know :).

Andrew

---


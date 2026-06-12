---
title: "Got Flash anyone?"
date: 2009-06-16
forum: New to Ubuntu
---

### Post by trinidadflores on 2009-06-16
I have a question is there a version of adobe Flash that will work on the 64 bit os?

---

### Post by SuperSonic4 on 2009-06-16
Yes there is, adobe released a plugin for 64 bit browsers. It is alpha but works astoundingly well
There are two methods to get it:

1. Use the repos to get it, as of 9.04 it is known as the flashplugin-nonfree package and is in the medibuntu repos.

2. Make a plugins directory in the firefox settings: ```
mkdir ~/.mozilla/firefox/plugins
```
Download and extract the file from [Adobe]("http://labs.adobe.com/downloads/flashplayer10.html") and extract it onto your desktop
Copy it to the folder just created ```
mv -v ~/Desktop/libflashplayer.so ~/.mozilla/plugins
```

Restart FF in both cases

---

### Post by gn2 on 2009-06-16
Or alternatively: [do it the GUI way]("http://news.softpedia.com/news/How-to-Install-Adobe-Flash-Player-64-bit-on-Ubuntu-8-10-98076.shtml").

Download the latest version (bottom of page) [here]("http://labs.adobe.com/downloads/flashplayer10.html").

---

### Post by rbueno on 2009-06-16
yep!
just choose .deb extension and open using software installer then finish!

---

### Post by oldos2er on 2009-06-16
> **trinidadflores said:**
> I have a question is there a version of adobe Flash that will work on the 64 bit os?

 [http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz)

---


---
title: "Save youtube vids"
date: 2010-07-09
forum: New to Ubuntu
---

### Post by Whatrymes on 2010-07-09
Hey:

Total newbie. Can't remember how to save youtube videos to hard disk. Seems there was a folder to check while the vid was running??

Thank you,
Ed

---

### Post by Planetes on 2010-07-09
Not exactly sure what your talking about but you can download youtube-dl through synaptic and then use it to download your videos off of youtube. If that is what you were wanting.

its a CLI so in terminal you would type 

youtube-dl "the url here"

---

### Post by uRock on 2010-07-09
Whenever I find a vid worthy of saving I boot Windows and use RealPlayer. I am not sure whether the RealPlayer for Linux does that.

---

### Post by Devi1903 on 2010-07-09
I use the Video DownloadHelper addon for firefox.

You can also just pull them out of the firefox cache folder. its at /home/user/.Mozilla/firefox/somecrazynonesense/

---

### Post by nothingspecial on 2010-07-09
/tmp

---

### Post by lisati on 2010-07-09
Friendly reminder: using Youtube videos in a manner other than approved by Youtube is a violation of the Youtube terms of use. 

See here: [http://ubuntuforums.org/showthread.php?t=1165163](http://ubuntuforums.org/showthread.php?t=1165163)

---

### Post by stmiller on 2010-07-09
[http://keepvid.com](http://keepvid.com)

[http://vixy.net/](http://vixy.net/)

[http://www.savetubevideo.com/](http://www.savetubevideo.com/)

dozens of other sites...


Or there is a Linux program you can install:

```
sudo apt-get install youtube-dl
```

Then do this:

```
youtube-dl -d http://www.youtube.com/watch?v=i8g_Z4_DkXI
```

---


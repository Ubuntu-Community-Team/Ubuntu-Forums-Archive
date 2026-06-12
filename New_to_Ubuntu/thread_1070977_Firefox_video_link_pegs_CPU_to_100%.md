---
title: "Firefox video link pegs CPU to 100%"
date: 2009-02-15
forum: New to Ubuntu
---

### Post by jmacWA0 on 2009-02-15
I have just installed V8.10 and I find that when I run firefox the cpu goes to 100% whenever I click on a video link.

Any help would be appreciated.

---

### Post by diablo75 on 2009-02-15
If the video is Flash (Youtube and many other websites are), then you should expect high CPU usage.  Flash is not very efficient and there isn't much you can do other than try a less functional open-source alternative like gnash.

---

### Post by photonian on 2009-02-15
gnash is worse

---

### Post by kansasnoob on 2009-02-15
Try going to Tools > Add-ons > Get Add-ons and searching for flashblock. 

You should end up with either flashblock 1.5.7 or 1.5.8.

I have to get busy with something else so here's my best explanation:

Flash in Linux is an energy hog! Modern webpages have crap-loads of Flash loaded/loading constantly!

Flashblock replaces these random flash images with a "button". Just click the button and you'll see the flash image or a "launcher" for the Flash video.

I tend to like Ubuntuzilla because once you have the official Mozilla build of Firefox all of your extensions get updated too!

---

### Post by gn2 on 2009-02-15
Are you running 32-bit or 64-bit Ubuntu?

I found that in 64-bit this problem was eliminated by using the new 64-bit Flash 10, downloaded from [here]("http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.d21.1.linux-x86_64.so.tar.gz") and installed using [this guide]("http://news.softpedia.com/news/How-to-Install-Adobe-Flash-Player-64-bit-on-Ubuntu-8-10-98076.shtml").

---


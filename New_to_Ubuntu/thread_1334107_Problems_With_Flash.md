---
title: "Problems With Flash"
date: 2009-11-22
forum: New to Ubuntu
---

### Post by jose187 on 2009-11-22
I'm having problems with flash in my browser.

I have installed all the restricted extras, and i am able to view videos. What I am NOT able to do is use any buttons inside the flash animation / movie, or interact wiht it in any way. As a result, unless a video starts automatically, i have no way of viewing it. If the video does play autom,atically, I can't increase/decrease volume, go backl or forward, mute, or do a full screen....

I have already tried reinstalling the Restricted Extras...but the same thing happens.

This is what i have

Ubuntu 9.10 64-bit
Intel Duo Core
9500GT Nvidia
Firefox 3.5

---

### Post by 3rdalbum on 2009-11-22
Known problem. Lots of links to HOWTOs in the forums for your situation (where you are using 32-bit Flash in 64-bit Firefox).

If this doesn't work, or if you're using 64-bit Flash in a 64-bit browser, you can simply click outside the Flash frame and then your next click inside the Flash movie will work.

---

### Post by jose187 on 2009-11-22
OK,
Now i have a different problem.

I tried several things and none of them worked. Then I followed some instructions in a website I found and it made things worst.

the instructions were

```
sudo apt-get remove flashplugin-installer flashplugin-nonfree swdec-mozilla mozilla-plugin-gnash
cd /tmp
wget http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz
tar xf libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz
sudo mv libflashplayer.so /usr/lib/mozilla/plugins/
```

No the browser crashes any time it tries to load a video.

Can somebody please help be undo these things....thanks

---


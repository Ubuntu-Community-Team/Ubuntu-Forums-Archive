---
title: "flash player"
date: 2009-08-05
forum: New to Ubuntu
---

### Post by potatoehead64 on 2009-08-05
Running Jaunty.
After installing the latest updates this morning, I now seem to have a problem with flash. In particular this refers to flash games and you tube video. 
There seems to be some kind of ad block now involved in that the display page is grey with a video forward style icon. just click on this appears to remove it, but I get the games hang or with you tube video, just audio with a delayed video (very choppy). 
On other sites such as Facebook, any video material will not play at all with facebook reporting and error. 
Any advice?
It is possible to back track the update?

I do appear to have the latest flash player (10). I tried downloaded the latest from Adobe website (debian package) and it tells me I have a later version installed?.
This does not appear to be a firefox issue. I get the same problems when using the epiphany browser.

---

### Post by swoll1980 on 2009-08-05
Go to tools>addons on your browser, and see if there's an add block installed. If there is disable, or remove it.

---

### Post by potatoehead64 on 2009-08-05
> **swoll1980 said:**
> Go to tools>addons on your browser, and see if there's an add block installed. If there is disable, or remove it.

There is no adblock installed.

---

### Post by potatoehead64 on 2009-08-05
Aha!  I have just fixed this by removing swiff dec (swfdec) via synaptic. It obviously interferes with flash in some way.

---


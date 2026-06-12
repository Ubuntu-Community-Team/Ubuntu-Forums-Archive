---
title: "I can play all music streams except this one"
date: 2011-05-06
forum: New to Ubuntu
---

### Post by ellwoodcolahan on 2011-05-06
Hello, all. I have been using Ubuntu on and off for a few years but have limited technical knowledge. I have always been able to play music streams using Firefox (sometimes they open in Movie Player), but I am unable to open streams from Alexander Street Press, such as this one: [http://goasp.it/gtll](http://goasp.it/gtll). When I click on the "play" button, a little flash-type player opens but then returns the message "connectionError". I can listen to the stream in Windows, Mac OS, Android, even WindowsCE, so I am a little mystified. I am running 11.04 (had the same problem in 10.04) on an Asus netbook. Any help would be greatly appreciated.

Best,

Woody Colahan

---

### Post by fballem on 2011-05-06
When I clicked on your link, I had no issues. I am wondering if you have the correct codecs installed.

Make sure that you have the Medibuntu repository enabled. You can find instructions for that here: [http://www.medibuntu.org](http://www.medibuntu.org) Click the Repository Howto tab. It needs a terminal, but it is easy.

Once you have the repository, then check that the following are installed:

gstreamer0.10-plugins-bad
gstreamer0.10-plugins-bad-multiverse
gstreamer0.10-ffmeg
gstreamer0.10-plugins-ugly
gstreamer0.10-plugins-ugly-multiverse

If they are not installed, then install them.

Try your link. If that does not work, then you may need to purchase codecs. I have purchased the codecs from fluendo.com - they are inexpensive and include the codec and the license to use them.

With this combination, I have yet to find anything that I cannot play.

I hope this helps,

---

### Post by sammiev on 2011-05-06
Tried the addie from the 1st post and have no problems at all. So no special codec are required. GL :)

---


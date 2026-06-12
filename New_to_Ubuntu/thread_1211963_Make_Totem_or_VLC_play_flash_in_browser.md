---
title: "Make Totem or VLC play flash in browser?"
date: 2009-07-13
forum: New to Ubuntu
---

### Post by SpinningAround on 2009-07-13
Is't possible to make VLC or totem play flash in firefox on sites like youtube?

---

### Post by hyperdude111 on 2009-07-13
I dont think so. Firefox automatically uses the adobe flash plugin for flash files and mplayer for avi. I dont think it is easy to change.

---

### Post by HavocXphere on 2009-07-13
Yes and no.

Neither are capable of handling flash afaik. However, flash is only used to initialize the video & handle the stop/pause/play thing. The video itself can be played by a video player.

VLC has a plugin for firefox.

---

### Post by Mornedhel on 2009-07-13
It's *possible* to play a flv in Youtube from an external media player seamlessly. I have a friend who does this. His setup however is a custom Python script with heavy magicking to load the page, extract the video url, modify the page source to replace the flash application with the .flv, and have the external player/plugin handle it.

At the moment his hack is not really releasable, exists only on his computer, and he's busy with real life at the moment, so it will be done when it will be done.

---

### Post by kerry_s on 2009-07-13
on youtube yes, other sites not really.

grab the greasemonkey extension & this script: [http://userscripts.org/scripts/show/50771](http://userscripts.org/scripts/show/50771)

i use it all the time for youtube, i have gnome-mplayer & gecko-mediaplayer.

---

### Post by vinutux on 2009-07-13
Vlc and totem both are palying just .flv not .swf (flash)

so sites like youtube player .flv in background witha .swf player in froentend...

---


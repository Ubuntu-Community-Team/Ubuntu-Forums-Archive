---
title: "Associating Listen Music Player with .pls"
date: 2009-02-09
forum: New to Ubuntu
---

### Post by brons2 on 2009-02-09
Upon installing Xubuntu 8.10 onto an older machine I am intending on selling, I was delighted to see that the Listen Music Player that is part of the default install has a category for Webradio including Shoutcast.  Yet when I press the Shoutcast button from within the application, nothing happens.  If I go to Shoutcast.com in Firefox, and try to click on a stream, Firefox asks me what to do with .pls files.  If I save it to the desktop and then try to double click on it, Totem Movie Player launches.

How do I browse Shoutcast from within Listen?

How do I set Listen to be the default application for .pls within Firefox?

---

### Post by arkmundi on 2009-04-13
You need to open Firefox, then
Edit-->Preferences-->Applications tab-->Content type: MP3 Shoutcast Playlist
The "Action" you want is "use totem"
You may need to select "use other" first, to set the action.  If so, locate the totem run time, which is found at /usr/bin/totem if you have a normal install.

I have tried all kinds of different ways to play shoutcast playlists, and this is the one I prefer above others.  That list of trials includes realplayer, xine as a Mozplugger, VLC and others.  I prefer totem because:
* the totem player is mainstream to Ubuntu
* I've got totem based on gstreamer, the mainline for linux based streaming media, all the available codecs, included the restricted set
* libvisual-projectm is aimed at totem for the primary {for those who migrated from Windows and the Winamp player, you'll remember truly awsome music visualizations - this projects is purposed as a replacement}       

As I'm writing this, I just upgraded to Intrepid 8.10 and am listening to Nirvana radio, from the Shoutcast list, and watching the GOOM visualizer.  I have to be careful or I'll enter alpha state and not want to do anything useful ... like getting libvisual working ... uh oh, that'll really trip me over.  Good luck!

---


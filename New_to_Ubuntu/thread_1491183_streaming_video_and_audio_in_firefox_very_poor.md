---
title: "streaming video and audio in firefox very poor"
date: 2010-05-23
forum: New to Ubuntu
---

### Post by darkeale on 2010-05-23
Hi,

When streaming video and audio in firefox the quality is very poor.  this is true when streaming tv or radio stations.  If the video is in flash player, like youtube or the bbc website the quality is fine, but any other type of video or audio stream is very poor.

Here are some websites which I am having problems with:-

3abn.org
3abnradio.org
amazingfacts.tv

if anyone can help it would be much appreciated.  These sites work fine in windows vista.

By the way, I installed the gstreamer ugly, bad and ffmpeg plugins to view video and audio

Thanks,
Alex

---

### Post by darkeale on 2010-05-23
update:-

When I select the real player or winamp stream for radio stations (where possible) the audio is fine.  but when I choose the wma stream or watch any videos the quality is still very poor.

Thanks,
Alex

---

### Post by darkeale on 2010-05-25
oh my graphics card is an ATI Radeon 200m. 

Any help would be much appreciated.

Thanks,
Alex

---

### Post by clhsharky on 2010-05-25
darkeale

It probable has to do with windows media files being poorly supported on Linux, thanks Microsoft.

Sharky

---

### Post by sedwardcarr@gmail.com on 2010-05-25
I have a lot of plug ins, and I don't seem to have many streaming issues.
Tell me the streams you are trying to listen to/watch and I'll see if I can use them without problems.  If it's fine for me I'll list my plug ins.

---

### Post by sedwardcarr@gmail.com on 2010-05-25
The plug ins are 5 of the 6 codec packs available in the software center for gstreamer plus Iced Tea (for Java)  The other gstreamer codec won't download for some reason.  My only media problem is that the sound in mplayer when I play dvds isn't quite right.  The sound skips every minute or so.

---

### Post by darkeale on 2010-05-25
thanks for getting back to me guys.

Here are some streams:-

3abn.org (the watch online tv stream)
3abnradio.org (the real player version works fine but the wma one is terrible quality)
amazingfacts.tv (audio and video poor)

If you could check those out for me on your computer sedwardcar it would be much appreciated.

Thanks,
Alex

---

### Post by darkeale on 2010-05-25
by the way, here are the plugins I have installed:-

Adobe Flash (from their website, all flash videos work fine)

and from terminal:-
sudo apt-get install gstreamer0.10-plugins-ugly
sudo apt-get install gstreamer0.10-plugins-bad
sudo apt-get install gstreamer0.10-ffmpeg

are there any others I should have that could be causing the problems?

Thanks
Alex

---


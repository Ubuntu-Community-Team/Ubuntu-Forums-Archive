---
title: "multimedia ubuntu question"
date: 2008-12-24
forum: New to Ubuntu
---

### Post by hellomoto on 2008-12-24
Hello everyone, 

I would like to enable a number of restricted file types on Ubuntu. I have always been able to do this by randomly clicking away on my desktop and it tells me what to download. I am however not satisfied with this and want to know what packages/metapackage or repository there is to enabled the vast majority of restricted files on my PC.

So far my understandings are this:
Totem 
-can use to different libs either xine or GStreamer. GStreamer consists of good/bad/ugly/extras/ffmpeg What does each of these enable?

Medibuntu 
-is a repository of packages that cannot be included with Ubuntu. It does contain some multimedia packages but not all. (GStreamer) Does adding this repository also mean I am downloading a lot of packages I won't use?

So my main question is what packages should I install to enable:
Mp3/wma
Avi/DivX/wmv other main video types
DVD playback
Encrypted dvd playback
Flash
Java

Its worth pointing out this is for a bog standard Ubuntu install using the standard apps. Aka rhythmbox, totem-gstreamer ect. I don't want or have Vlc player, mplayer, amarok ect. So please keep your replys relevant to a standard ubuntu install.

Thank you in advance!

---

### Post by hyper_ch on 2008-12-24
ubuntu-restricted-extra (either in universe or multiverse repository) for codecs
and medibuntu for dvd playback...
flash and java should also be in universe or multiverse

---

### Post by Xiong Chiamiov on 2008-12-24
[A guide]("http://ubuntuforums.org/showthread.php?t=766683").

Adding an extra repository does not download any packages unless you explicitly install them.

And mplayer is the king of video on Linux, although I'd recommend using one of the alternate GUIs for it (SMplayer's my current fav).

---


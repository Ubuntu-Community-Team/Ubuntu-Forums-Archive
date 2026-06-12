---
title: "Xmms2 not playing MP3s ....??"
date: 2009-10-20
forum: New to Ubuntu
---

### Post by wannabegeek on 2009-10-20
Hi all.....I just downloaded Xmms2 and Esperanza from the repo...
However, I tried getting some codecs, which I guess are old and no longer in the repository.

xmms-decoder-mad, I thought would give me mp3's...

So would someone please tell me what codex to get from the repo for mp3's....I will be so grateful....

---

### Post by ZankerH on 2009-10-20
You need to install "restricted codecs" - that is, codecs that are non-Free or have other licensing restrictions that prevented them from being included in the default Ubuntu install. Open Synaptic (System->Administration->Synaptic Package Manager), search for "ubuntu restricted extras", select it and press apply.

---

### Post by swoody on 2009-10-20
For all things audio/video, there is the great Multimedia thread:
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

Also for a couple other sources that you may find handy in the future:
[http://www.psychocats.net/ubuntu/mp3](http://www.psychocats.net/ubuntu/mp3)
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

Hope these are of help :)

---

### Post by carnagex420x on 2009-10-20
The gstreamer-fluendo package will allow you to play MP3s w/o downloading to whole ubuntu-restricted-extras package. Its just the codec to play MP3s.

---

### Post by wannabegeek on 2009-10-25
mp3's playing now....got codex from repo, Esperanza didn't play mp3's still..
So I uninstalled Esperanza, then reinstalled and it.

In fact, I tried launching Esp. from applications, it gave me an error and wouldn't close, so I opened the daemon from the terminal: xmms2d

That seemed to make it work...

Esperanza is OK, its streamlined which I like...I don't the way it searches my library, but it new and will take some time...so anyone interested in a stripped down player from the repo. with a relatively easy install, I think Xmms2 and Esperanza are a good.

---


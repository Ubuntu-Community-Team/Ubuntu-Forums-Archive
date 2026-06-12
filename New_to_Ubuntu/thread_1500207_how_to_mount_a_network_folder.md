---
title: "how to mount a network folder"
date: 2010-06-02
forum: New to Ubuntu
---

### Post by zryder94 on 2010-06-02
Hello everyone.
I am running Ubuntu 10.04, and I am trying to get the music I have stored on my unraid server to play with a player like banshee or rythmbox. Banshee seems to work relatively well with syncing music to my HTC Incredible, but I am unable to get it to point to my server. Does anyone know a way to mount a network share, and have programs think its a local drive, in such a way as to give Banshee the ability to see the media?

Does anyone have any other suggestions on a good way to get Flac's on a network drive to be sent to a media player, and be converted to mp3's on the way? Foobar seemed to work great for this in windows on an Ipod, I would hope we can do the same in linux..

Thanks everyone.

---

### Post by SoFl W on 2010-06-02
I had problems with rhythmbox and a network shared drive.  I gave up.
You can try this with Banshee.  (someone suggested this for another media player)
Connect to it as if it was a file share and see if you can browse.
Goto your home folder -> .gvfs  and see if the share appears in there.
Try dragging that into Banshee, or using that name for the path in Banshee.

---

### Post by zryder94 on 2010-06-02
pointing banshee to .gvfs seems to have worked great! thanks!!!!!

---

### Post by SoFl W on 2010-06-03
Fantastic.   You are welcome.

I see you are relative a new user (so am I) you can mark this thread "Solved" by clicking on the red "thread tools" on the right just above the top message.

---


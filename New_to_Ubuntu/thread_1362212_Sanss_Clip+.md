---
title: "Sanss Clip+"
date: 2009-12-22
forum: New to Ubuntu
---

### Post by pfeifferock on 2009-12-22
I just got a new mp3 player Sansa Clip + and it is not being recognized by my computer. I am running Karmic Koala on an Acer Aspire 4530 laptop and when i plug in the device when it is in auto detect mode it will bring up two folders full of more folders and some .sys files but rythombox or any other program will not recognize it. I used to have the old version of this the 2gb sansa clip and my computer recognized it fine. As far as i am aware the firmware version is V01.01.05A and there are no new versions out any ideas?

---

### Post by pfeifferock on 2009-12-23
bump...
please help

---

### Post by pfeifferock on 2010-01-02
Seriously i want to get some music on my MP3 player am i out of luck?

---

### Post by falconindy on 2010-01-02
The device may be usable with fuseMTP.

---

### Post by Dr Belka on 2010-01-02
I have a sansa view.  I used rythymbox to manage it and it did everything well except for playlists.  All I had to was enable the MTP plugin.  Go to edit>plugins and check "Portable Players - MTP" and you should see that your device will become recognised.

---

### Post by MoarningSun on 2010-01-12
Hi, on the SanDisk forums a newer firmware is available (v 01.01.32), maybe if you load this to your player things will work better:) see for download and instructions: [http://forums.sandisk.com/sansa/board/message?board.id=clip&thread.id=15109](http://forums.sandisk.com/sansa/board/message?board.id=clip&thread.id=15109)

Also I found that it works best if you set the clip to MSC mode. Go to Settings > USB Mode on your sansa clip. You then just copy the files over to the removable drive (root or music folder should work) and the clip will index these files when it is disconnected.

When its in MTP mode you can see the MTP filestructure, but you can't copy files over that easily (at least I couldn't). To use MTP mode with Rhytmbox I had to follow this guide: [http://forums.sandisk.com/sansa/board/message?board.id=clip&message.id=2803](http://forums.sandisk.com/sansa/board/message?board.id=clip&message.id=2803). Putting the .is_audio_player file on the player should be done in MSC mode!

Good luck\\:D/

---


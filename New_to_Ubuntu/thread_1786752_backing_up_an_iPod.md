---
title: "backing up an iPod"
date: 2011-06-20
forum: New to Ubuntu
---

### Post by Charlie Chick on 2011-06-20
Like most people with an iPod, I have spent a lot of time transferring my music onto my iPod, arranging playlists etc. and, as an Ubuntu user, I have never used iTunes. In fact, I only use GTKPOD.

Given the amount of time I have invested in it, is there a program that works on Ubuntu that can do a simple (preferably one click) backup of all the music and playlists so that, should I either lose it or it stops working, I can connect a brand new one, click Restore and have everything the same on the replacement? The thought of having to transfer and arrange all that all over again terrifies me!

---

### Post by inameiname on 2011-06-20
Rhythmbox works well. You often can simply open Rhythmbox and plug in device and it autodetects it. Then once you see all of your music, just drag and drop the whole artist/title playlist to the music library.

And if you ever want to restore your device, follow the same procedure, but instead of starting inside the Ipod directory, go to the Rhythmbox's Music Library one, and drag and drop that stuff back to the device. Easy.

One flaw though: Rhythmbox doesn't deal with Various Artists CDs/Albums well, and what it does it break those down into the artists/albums. However, if you are worried about that, you can simply install a Rhythmbox alternative, like Banshee. I know it sorts better, but I cannot remember off hand how hard or easy it was compared to Rhythmbox.

---

### Post by Charlie Chick on 2011-06-21
Thanks for the advice. I'll give it a try.

---

### Post by inameiname on 2011-06-21
No problem. Good luck with it.

---

### Post by Charlie Chick on 2011-07-09
> **inameiname said:**
> Rhythmbox works well. You often can simply open Rhythmbox and plug in device and it autodetects it. Then once you see all of your music, just drag and drop the whole artist/title playlist to the music library.

And if you ever want to restore your device, follow the same procedure, but instead of starting inside the Ipod directory, go to the Rhythmbox's Music Library one, and drag and drop that stuff back to the device. Easy.

One flaw though: Rhythmbox doesn't deal with Various Artists CDs/Albums well, and what it does it break those down into the artists/albums. However, if you are worried about that, you can simply install a Rhythmbox alternative, like Banshee. I know it sorts better, but I cannot remember off hand how hard or easy it was compared to Rhythmbox.

I tried backing up, as suggested, with Banshee, but it was a disaster! Banshee wiped all the playlists on the iPod, leaving only a disorganised mess behind. This was just the thing I wanted to avoid, as it has taken me, literally, a couple of years to get things as I want them to be.

Fortunately, before allowing Banshee to mess up my iPod, I had connected the iPod as a drive and backed the all the files and folders up. This proved to be invaluable in restoring it. I discovered that the folder that contains the playlists and audio is called iPod_control . Copying this back restored my iPod to good health.

So, to answer the question I originally posed, the best way to back up your iPod for disaster recovery is to treat it as a drive and back up all the files and folders within it.

---

### Post by inameiname on 2011-07-09
> **Charlie Chick said:**
> I tried backing up, as suggested, with Banshee, but it was a disaster! Banshee wiped all the playlists on the iPod, leaving only a disorganised mess behind. This was just the thing I wanted to avoid, as it has taken me, literally, a couple of years to get things as I want them to be.

Fortunately, before allowing Banshee to mess up my iPod, I had connected the iPod as a drive and backed the all the files and folders up. This proved to be invaluable in restoring it. I discovered that the folder that contains the playlists and audio is called iPod Files. Copying this back restored my iPod to good health.

So, to answer the question I originally posed, the best way to back up your iPod for disaster recovery is to treat it as a drive and back up all the files and folders within it.

Eek. I'm sorry Banshee did that to you. I knew Banshee had issues like that, but never that bad. Definitely a smart thing to back it up beforehand.

I was actually thinking you wanted a backup of your IPOD music so you can not only retain a backup of all of it, but also to have it organized and playable on your machine, not just the 1s and 0s on the IPOD. As that was what you wanted, treating it like a drive was the best solution all around. Granted, you cannot easily play back whatever's on it inside Linux, but you do have a back up.

Well, glad you figured it out yourself, and was able to back things up.

---

### Post by Charlie Chick on 2011-07-17
Thank you for your help and advice. I always learn something from these forums!

---

### Post by inameiname on 2011-07-18
Sure. Yep, there is always something new to learn from here.

---


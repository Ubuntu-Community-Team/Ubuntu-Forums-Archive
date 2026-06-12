---
title: "YouTube crashing in Xubuntu 8.04"
date: 2009-04-04
forum: New to Ubuntu
---

### Post by LinuxFox on 2009-04-04
Last night installed Xubuntu 8.04 on an older computer via Wubi.  It runs great, but Firefox keeps crashing whenever I view a YouTube video.

To compare, I'm using Ubuntu on my current PC and it doesn't crash with YouTube.  Is there any way to fix this problem.  I installed Xubuntu for a relative to have a safer way to use the internet, the crashing would make it frustrating for the person I did this for.  Could someone please help me out?

---

### Post by taurus on 2009-04-04
You need flash if you want to view youtube.

```
sudo apt-get update
sudo apt-get install xubuntu-restricted-extras
```

---

### Post by LinuxFox on 2009-04-04
> **taurus said:**
> You need flash if you want to view youtube.The thing is I already have Flash installed.  It shows the video player with the controls and a black screen, then Firefox closes.  When I didn't have flash installed, it showed the "Get flash player" link.

I also tried an all flash website, and it didn't crash on me.  Just YouTube videos.

---

### Post by billgoldberg on 2009-04-04
> **LinuxFox said:**
> The thing is I already have Flash installed.  It shows the video player with the controls and a black screen, then Firefox closes.  When I didn't have flash installed, it showed the "Get flash player" link.

I also tried an all flash website, and it didn't crash on me.  Just YouTube videos.

Check the flash player version you are running.

Flash player 9 caused that problem.

Remove the flash player and install Flash Player 10.

That should solve the problem.

Link to installing Flash Player 10:

[http://linuxowns.wordpress.com/2008/10/15/flash-player-10-final/](http://linuxowns.wordpress.com/2008/10/15/flash-player-10-final/)

---

### Post by LinuxFox on 2009-04-04
> **billgoldberg said:**
> Check the flash player version you are running.

Flash player 9 caused that problem.

Remove the flash player and install Flash Player 10.

That should solve the problem.

Link to installing Flash Player 10:

[http://linuxowns.wordpress.com/2008/10/15/flash-player-10-final/](http://linuxowns.wordpress.com/2008/10/15/flash-player-10-final/)Thanks a lot.  I was running Flash Player 9.  While waiting for a reply I went ahead and installed Flash Player 10 just to see what happens.  Everything works now. 8)

---

### Post by sanitycheck on 2009-04-09
The new Flash player 10 also shows up for Hardy 8.04 under the Partner repository.  

I uninstalled the old flashplugin-nonfree and installed adobe-flashplugin using Adept Manager (Kubuntu).  I renamed the libflashplayer.so file in my /.mozilla/plugins directory to libflashplayer.so.old.  I then had to manually copy the new libflashplayer.so file from /usr/lib/adobe-flashplugin/ to the ./mozilla/plugins directory (not sure why it doesn't install itself).  Running Firefox again and I confirm I'm up to version 10 (right-click YouTube video and version will display).

---


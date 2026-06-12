---
title: "Steam on ubuntu 11.04"
date: 2011-05-06
forum: New to Ubuntu
---

### Post by destrugter on 2011-05-06
Hello everyone. I have been trying to play Steam games on Ubuntu 11.04. I looked around on Google and found out about Wine and PlayOnLinux. I used PlayOnLinux to install Steam and it worked (yay!). I installed a game I bought, and it downloaded, completed and I press play and nothing happens. I've been searching for a fix. What can I do to play these games? I have many games I love playing ( Mount & Blade, BioShock, L4D, Counterstrike). Any help would be appreciated. I'll post back if I find anything.

---

### Post by rklapp on 2011-05-06
That's be cool.

---

### Post by chromatica86 on 2011-05-06
I'm using wine 1.3.19 which I've always found works better than POL.
But don't get too excited as the games have very low performance on ubuntu.
counter-strike source runs at about 170 fps on my windows 7 disk and is barely playable through wine. 
You can check here to see how well your games will perform.
[http://appdb.winehq.org/](http://appdb.winehq.org/)

---

### Post by era86 on 2011-08-18
I hate to be a necromancer for a thread, but I'm wondering if this was ever resolved or if anyone every got this working.  Let me know, thanks!

---

### Post by waynefoutz on 2011-08-18
Works for me, but I have to log out and log back into the "Ubuntu Classic= no effects" desktop for it to run well.

---

### Post by jfed on 2011-08-18
I don't use the new version of wine, because I can't stand it, but I can help you out with some things that are steam specific, because I myself had to get it running.

Right click your game, and go to its properties. Uncheck the box that says "enable steam community in-game"

Next, go to the launch options, and copy and paste this code into that box. Actually, I'm not sure if you can really copy and paste, but just copy it nonetheless.

```
-novid -dxlevel81
```

That might help, also, you may want to try adding a few strings to your wineconfig. This guide explains nicely how to do it. Doing all this helped me launch TF2 when it refused to do so, haha.

[http://ubuntuforums.org/archive/index.php/t-587780.html](http://ubuntuforums.org/archive/index.php/t-587780.html)

---

### Post by 3rdalbum on 2011-08-19
Just because Steam works on Wine, doesn't mean that the games it can download will also work. You should check on the AppDB on the Wine HQ website.

---

### Post by era86 on 2011-08-19
Thanks for the replies.  I can get the game to open, but I can't seem to get a game to load.  Or get a list of games to join for that matter.  Also, when I run the video test, it shows only black  background with a little bit of walls here and there.  Safe to say it's faulty on my machine.

I'll try some stuff later on and update here if anything changes.  I'm trying to get it working in 11.04 Classic Gnome on a x220.

---

### Post by BlinkinCat on 2011-08-19
You won't have classic gnome for much longer. - :)

---


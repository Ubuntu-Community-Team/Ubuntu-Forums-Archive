---
title: "gnome mplayer"
date: 2010-10-15
forum: New to Ubuntu
---

### Post by spoinka on 2010-10-15
i installed mplayer via apt-get install gnome-mplayer but it doesnt play anything. just says "stopped" when i hit play. sometimes i get sound but no picture. video frame just stays black.
when i run mplayer from terminal i get the following message:
"mplayer: error while loading shared libraries: libva-x11-0.31.1.1.so.1: cannot open shared object file: No such file or directory"
so i installed libva-x11 with the software center (version:1.0.1-3 (libva-x11-1)) but its obviously not the version mplayer is looking for...how can i use this version with mplayer?

---

### Post by Sealbhach on 2010-10-15
Why not use Totem or VLC? Do they work OK?

.

---

### Post by spoinka on 2010-10-15
its the same with totem.
i got it to work now when i run it from terminal with mplayer -vo vaapi -va vaapi filepath
but its not working from the gui. i want to use flashreplacer addon for firefox with it. its the same there. youtube for example loads the player gui , plays sound but shows just a black screen most of the time...

---

### Post by spoinka on 2010-10-15
whats the difference between adding the parameters to the commandline and setting the same options in the gui preferences? problem must be there...

---

### Post by matt_symes on 2010-10-15
Hi,

Yes. You have the wrong version of the video acceleration library installed on your machine. Have you tried creating a symbolic link between the the version it requires and the version you have. More often than not this will work if the libraries have not changed too much.

[http://ubuntuforums.org/showthread.php?t=1229345&page=141](http://ubuntuforums.org/showthread.php?t=1229345&page=141). explains the technique in one of the posts.

Also do you have the newest ubuntu restricted extras package installed.

sudo apt-get install ubuntu-restricted-extras from the terminal

---

### Post by matt_symes on 2010-10-15
Hi,

Just noticed you installed gnome-mplayer. Not sure if that is what you want.
I have just installed mplayer  and mplayer-gui on my laptop with a fresh install.

1. sudo apt-get install ubuntu restricted-extras
2. sudo apt-get install mplayer
3. sudo apt-get install mplayer-gui.
4. gmplayer & from terminal or applications->sound and video->mplayer

I have no dependency issues when i did this.

Maybe uninstall gnome-mplayer, mplayer and mplayer-gui (if installed) and try steps above

Kind regards.

---

### Post by spoinka on 2010-10-15
its working now with only mplayer installed. but only when i run it from a terminal. the thing is i want to use the flashvideoreplacer addon and that does obviously not work. all i get is a gui with a black/gray screen inside.

---


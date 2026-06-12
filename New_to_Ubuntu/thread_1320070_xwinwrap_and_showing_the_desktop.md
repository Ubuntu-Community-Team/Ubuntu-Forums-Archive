---
title: "xwinwrap and showing the desktop"
date: 2009-11-08
forum: New to Ubuntu
---

### Post by dirtlamb5 on 2009-11-08
I was having some fun this weekend and decided to try xwinwrap to let me display screensavers and videos as my desktop background. I got it to work, but if I click the "show desktop" button at the bottom left of the bottom panel the screensaver that I'm displaying as my wallpaper disappears. Is there any way to prevent this from happening so that if I click "show desktop" it just displays whatever screensaver xwinwrap is showing as my wallpaper? I've looked under the "show desktop" settings in the CompizConfig Settings Manager but I didn't see anything that could help. I'm currently running Ubuntu 9.10.

---

### Post by boblizar on 2011-05-13
```
xwinwrap -ni -ov -o 0.3 -fs -s -st -sp -b -nf -- /usr/bin/electricsheep -window-id WID &
```

use shantz xwinwrap....  digging up zombie thread 4 reason of first result of google search.

your missing the "-ov" flag to tell shants to behave =D

this is fairly transparent and works fine under a black background.  wait a second...  further testing has shown that the -ov flag conflicts with the -b flag...  looks like im just gonna have to live with 

```
xwinwrap -g 1280x1024 -ni -ov -o 0.3 -s -st -sp -b -nf -- /usr/bin/electricsheep -window-id WID &
```

i cant get gnome to auto start this, and have it stay at the background, it wants to go over the applications i load.  i have made this command into a simple bash script with a shorter name and made it executable, and execute that command via alt + f2

---

### Post by |Anthony| on 2011-11-03
I wrote a pretty lengthy bash script (500+ lines) as a frontend for xwinwrap. It has the autostart feature you are looking for. Also gives you the ability to set transparency and and adjust the volume (for videos) among lots of other features. It's called VDesk and you can get it for free at [gnome-look]("http://gnome-look.org/content/show.php/VDesk+-+Visual+Desktop?content=141678"). Enjoy and you're welcome. :)

---


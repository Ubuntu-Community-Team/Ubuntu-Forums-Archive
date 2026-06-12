---
title: "my desktop icons disappeared"
date: 2010-05-11
forum: New to Ubuntu
---

### Post by lolzwut on 2010-05-11
Hi,


I was moving some files from my Downloads folder to this other sub-folder on my Desktop and all of a sudden all of my desktop icons just disappeared for no reason. I had Conky running too which also disappeared. I tried switching workspaces but the same thing is happening. Also I can't right click on it. I can still see my wallpaper but everything else just seems to be gone. I opened up Places > Desktop and I can still see all my files there so it isn't like they just got deleted. Also I checked my processes to see if Conky was still running and it said it was.

```
checkityo@Da-BoX:~$ ps aux | grep Conky
checkityo  25263  0.0  0.0   3040   796 pts/0    R+   15:55   0:00 grep --color=auto Conky
```So does anyone have any idea what's going on? What should I do? I don't want to restart because I have a lot of stuff opened that I think I'll forget to re-open when I reboot lol. Btw I have very little space on my HDD if that matters. Thank you.

---

### Post by themusicalduck on 2010-05-11
Open a terminal and try this ```
killall nautilus
``` hopefully after that runs it will reload itself and re-appear (this will also close any open file manager windows), but if not then press alt+f2 and type ```
nautilus
```

If conky doesn't reappear then type ```
pkill conky
``` in a terminal, then alt+f2 and ```
conky
```

---

### Post by lolzwut on 2010-05-11
Wow it worked. Thank you very much!

---

### Post by pete_m on 2010-05-17
I've checked in gconf  show_desktop is checked and tried the killall nautilus trick.

I have a small script that toggles that gconf parameter and I can see that it is still working.

This problem arose after I installed a bunch of alternate WM's - Flux ,Ice, LXDE,OpenBox for evaluation purposes. The install was fine and these are now available as sessions at login.
At my first login to Gnome after this my background had disappeared.
Interestingly the background appeared behind the NBR interface when I ran netbook-launcher and disappeared when it was killed.

Incidentally does anyone know how to configure compiz skydome - the ultimate background?
I mention this as i suspect it may be relevant- maybe nautilus/gnome are drawing the icons on a surface that is not visible...

i've put some work into my current Ubuntu install based on 9.10 karmic nbr2 and am very happy with the results

First screenshots -more soon - of my work in progress at

[http://www.youtube.com/watch?v=YoI4wRVVjBs](http://www.youtube.com/watch?v=YoI4wRVVjBs)

---


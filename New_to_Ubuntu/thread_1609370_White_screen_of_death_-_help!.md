---
title: "White screen of death - help!"
date: 2010-10-30
forum: New to Ubuntu
---

### Post by Robert Buckmaster on 2010-10-30
Ubuntu 10.10 had been working just fine, but on logging in again I got a white screen - and nothing else. No taskbar, no background - nothing! Yet Cairo dock still appeared when I put my cursor over it and I could still launch applications with Kupfer. Even the desktop theme has remained. But still there is a white screen, and the functionality of the GUI has been impaired. And it's difficult to find my way around without the task bar at the top. Compiz is also disabled.

How do I fix this problem and bring back my old desktop?

---

### Post by ironic.demise on 2010-10-30
```
ctrl+alt+t
metacity --replace &
```
If that doesn't work try setting the environment before log-in?
or ```
sudo apt-get install gnome-desktop
metacity --replace &
apt-get install KDE
apt-get install gnome-shell
gnome shell --replace
```

then you can try the KDE interface, if reinstalling the ubuntu desktop fails, and you can try the gnome shell interface allowing us to see where the problems are specifically.

---


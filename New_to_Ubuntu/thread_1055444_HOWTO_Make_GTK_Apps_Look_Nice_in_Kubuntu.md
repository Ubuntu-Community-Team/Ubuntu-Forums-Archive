---
title: "HOWTO: Make GTK Apps Look Nice in Kubuntu"
date: 2009-01-30
forum: New to Ubuntu
---

### Post by Speed Demon on 2009-01-30
OK, there's a lot of reports on how ugly GTK apps look in KDE. There are two simple fixes. One will make GTK apps look exactly as they do in GNOME. You need to tell KDE to autostart
```
gnome-settings-daemon &
```
on login. This must be installed first, obviously. DO NOT forget the & at the end or startup will hang.

The other is installed by default in KDE. it is called GTK-QT-ENGINE. You can only use ONE of these at a time. This one has to be uninstalled for the other one to work. This tries its best to make GTK apps look like KDE apps, but IMO it is not very good. But thats just me. Enjoy! I plan to make other NOOB-friendly posts about HOW-TO's and a able of Contents to index them all too. :popcorn:

---


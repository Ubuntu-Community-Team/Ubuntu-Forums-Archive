---
title: "How to install Wallpaper Clock"
date: 2009-07-25
forum: New to Ubuntu
---

### Post by MarkTX on 2009-07-25
I found and downloaded WallpaperClock 2.3 from GnomeLook, below are the files it came with;

icon.svg
menu.xml
WallpaperClockScreenlet.py
themes
wallpapers

The bottom two being directories.

My question is, how do i install this???  It is supposed to show a clock on the desktop as part of the wallpaper (hence the name :D)

---

### Post by durand on 2009-07-25
Since I've never done this before either, I'm going to list the steps I just took.

1) Install Screenlets. WallpaperClock is a screenlet so you need the actual program first.
Click on Applications > Add/Remove...

At the top, change Show to "All available applications" and then type in screenlets in the box. Then tick the package that comes up and click on the Apply Changes button at the bottom.
If it doesn't show up, go tho System > Administration > Software Sources.
Then tick the universe option (I think) and close the window. It should reload the packages. Then try the screenlets bit again.

2) Install WallpaperClock
Go to Applications > Accessories > Screenlets and click Install. Select Install Screenlet and press ok. Then go to where the **tar.bz2** file is and select that. It may give you an error but it should still install correctly.

3) Configure it.
Type in Wallpaper and the clock screenlet should come up. Then double click on it and it should load it. It may be on your desktop, so press Ctrl + Alt + Right to go to another desktop and see that its there. Now right click on the screenlet and go to properties and follow the instructions. I need to work it out from here as well..

---

### Post by durand on 2009-07-25
Ok, worked out how to configure it as well though the Properties window should help you with that.

You just need to go to [http://vladstudio.com/wallpaperclock/](http://vladstudio.com/wallpaperclock/), download the one you want as a wcz file and then drag in into the screenlet on your desktop. You can then select it by right clicking on the screenlet, going to Change Wallpaper Clock > My Wallpapers. Your wallpaper should then change.

I tried this a few years ago and it didn't work too well but it works great now!

---

### Post by MarkTX on 2009-07-25
Perfect!

Thank you so much Durand, that was fantastic.  Screenlets looks like some fun!

---

### Post by durand on 2009-07-25
They are, just don't get carried away :) There's a section on gnome-look dedicated to them: [http://gnome-look.org/index.php?xcontentmode=6700](http://gnome-look.org/index.php?xcontentmode=6700)

---


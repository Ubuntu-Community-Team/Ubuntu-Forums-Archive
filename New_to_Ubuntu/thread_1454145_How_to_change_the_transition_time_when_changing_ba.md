---
title: "How to change the transition time when changing background image?"
date: 2010-04-14
forum: New to Ubuntu
---

### Post by karatedog on 2010-04-14
Is there a way to shorten or entirely turn off the transition time between the old & new wallpaper when changing wallpapers in Gnome? There is no difference if I do it with the GUI --> right-click on desktop, then select "Change Desktop Background", or with command line: $gconftool-2 --type string --set /desktop/gnome/background/picture_filename "/path/to/filename.jpg"

I installed Wallpaper Clock and this effect backfires. Wallpaper Clock generates a new wallpaper every minute and then changes the currently used wallpaper to this new one. This wouldn't be a problem as the two backgrounds looks almost entirely similar, so the transition shouldn't be noticeable, but Wallpaper Clock first deletes the background, then sets the new. The transition (the old wallpaper fading away, empty background showing in, and then the new background fading in) just kills the feeling. If all these were happening in a jiffy, I wouldn't notice it...

---

### Post by Jon Monreal on 2010-04-14
The only things I'm aware of are [disabling GTK+ animations]("http://burningpenguin.com/viewtopic.php?f=3&t=88") or compiling gnome-desktop from source to disable the animations.

If you need more help, don't hesitate to ask.

---

### Post by karatedog on 2010-04-16
> **Jon Monreal said:**
> The only things I'm aware of are [disabling GTK+ animations]("http://http://burningpenguin.com/viewtopic.php?f=3&t=88") or compiling gnome-desktop from source to disable the animations.

If you need more help, don't hesitate to ask.

I don't know what else it turned off, but on wallpaper change it works fine! 
Thanks.

---


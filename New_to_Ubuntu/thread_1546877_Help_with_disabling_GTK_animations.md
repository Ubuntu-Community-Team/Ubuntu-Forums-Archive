---
title: "Help with disabling GTK animations"
date: 2010-08-06
forum: New to Ubuntu
---

### Post by Catraphact on 2010-08-06
Hi guys,

I use the wallpaper clock screenlet, and unfortunately, the "fade" effect when changing wallpapers also applies to wallpaper clocks- they fade out and fade in after 60 seconds to reflect the new time.

This is highly annoying. I found a way to disable this:

> Unfortunately the only way to disable the nautilus wallpaper fade effect is to disable all GTK+ animations.

Add 
```

gtk-enable-animations = 0
```
to ~/.gtkrc-2.0 (create if it doesn't exist). For all users it would be /etc/gtk-2.0/gtkrc IIRC.

And then logout or pkill nautilus.

I do not understand how to implement this. Can someone explain how? How do I create .gtkrc-2.0 in "~/", and there is no gtkrc file in the /etc/gtk-2.0/ directory.

I'm a bit confused. Any help would be appreciated.

Thanks

---

### Post by jtarin on 2010-08-06
For the currently logged on user.
open gedit>enter text 
"gtk-enable-animations = 0">
save as ".gtkrc-2.0">
to your username folder. 
It will be a hidden file. You can show it by using the Nautilus menu and choosing 
"View">>"Show hidden files". 
The one in the /etc directory is the same creation only you open gedit with 
"sudo gedit" and save it in the 
"/etc/gtk-2.0" directory as 
"gtkrc IIRC". (Remove all quotes)

---

### Post by Catraphact on 2010-08-06
This worked. The fading effect is gone.

However, the wallpaper clocks now just clumsily go blank and reappear once every 60 seconds. Looks like the GTK animation thing wasn't the fix I needed.

Has anyone been able to run wallpaper clocks properly on 10.04?

---

### Post by hexamon on 2011-08-29
For me, I also had to disable show_desktop.  Note that this also causes desktop icons to not be displayed.  However, I just run a folder screenlet with desktop folder instead.  Google: gconftool-2 --get /apps/nautilus/preferences/show_desktop

to get more info.

---


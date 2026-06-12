---
title: "Best way to change wallpaper on set intervals? (fetching image from URL)"
date: 2010-06-11
forum: New to Ubuntu
---

### Post by MALONN on 2010-06-11
First, I'm sorry if this is in the wrong thread, but I'm pretty new to Linux/Ubuntu in general, but I'm pretty handy with scripting/programming.....my question is as follows:

What is the best way to automatically change the desktop wallpaper on a set interval?  I will be fetching the image from an HTTP url.  The URL will most likely be static since that's the easiest.  Can this be done with a terminal cron job?  I know the terminal can provide some pretty powerful scripting abilities.  Or maybe this should be a stand-alone application?

Thanks guys!

---

### Post by xsinsx on 2010-06-11
I would think if you could set it up right a script with wget might work. 
```
 wget http://www.this_is_the_Wallpapers_adress.com/12343446
```

once the wget command downloads the wallpaper to a specified directory you want them stored in. use a few quick commands that will change the wallpaper for you and you should be done. thats my guess. Then just use cron to automate it.

This also probably should be in the Programming discussion. Just as a reference. :)

And one final edit:
 [http://www.djlosch.com/dlo/bash-script-to-randomly-change-gnome-background/](http://www.djlosch.com/dlo/bash-script-to-randomly-change-gnome-background/) 
[http://ubuntuforums.org/showthread.php?t=1378108](http://ubuntuforums.org/showthread.php?t=1378108)

these might provide some insight for you.

---

### Post by xsinsx on 2010-06-11
You might also look into this. [http://maketecheasier.com/desktop-drapes-another-gnome-wallpaper-changer/2008/07/29](http://maketecheasier.com/desktop-drapes-another-gnome-wallpaper-changer/2008/07/29)

---

### Post by MALONN on 2010-06-11
Ok, after some searching, the app Webilder seems like it might actually do what I need.  However, I can't seem to install it.  GetDeb is down and I followed a bunch of command lines to install it via terminal and it said successful, but where is it?

This is what I followed:
[http://www.ubuntugeek.com/how-to-install-webilder-in-ubuntu-10-04-lucid-lynx.html](http://www.ubuntugeek.com/how-to-install-webilder-in-ubuntu-10-04-lucid-lynx.html)

Also, how do you change the wallpaper via terminal?  All google results are giving me info on how to set the terminal AS the wallpaper.

Thanks again!

---

### Post by xsinsx on 2010-06-11
This should explain the wallpaper from terminal situation. I havent tested it myself but heres something.

[http://ubuntuforums.org/showthread.php?t=955149](http://ubuntuforums.org/showthread.php?t=955149)

---


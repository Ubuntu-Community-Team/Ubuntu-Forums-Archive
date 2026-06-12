---
title: "Cairo-dock problem...it's gone"
date: 2009-11-01
forum: New to Ubuntu
---

### Post by djm227 on 2009-11-01
So I was messing around with my cairo dock settings when I probably should not have been.  However, I set "Lateral Gap" to positive 1,000 and clicked apply then OK.  

Honestly, I'm not sure what that tool is even for...but the dock immediately disappeared, and I can not find it anywhere on the screen.  I was able to get the configuration open through terminal, but when I set "Lateral Gap" back to it's original setting, 0, it did not make the dock reappear.  

I am really at a loss as to what to do.  I tried uninstalling it and reinstalling it, but it is still gone.  Is there a way I can do a complete uninstall (settings and everything), and then reinstall it in order for it to be usable again? 

Thanks for the help, this is killing me.

---

### Post by peculiar penguin on 2009-11-01
Settings should be in  ~/.config/cairo-dock somewhere... dunno if you need to delete specific files or can nuke the entire directory. Make a backup copy and try it yourself?

---

### Post by djm227 on 2009-11-01
> **peculiar penguin said:**
> Settings should be in  ~/.config/cairo-dock somewhere... dunno if you need to delete specific files or can nuke the entire directory. Make a backup copy and try it yourself?


I can't find a .config folder in home (If I remembered correctly, "~" stands for home?).  Is there another place it could be?

Is there a way I can just delete all of this in terminal?

---

### Post by peculiar penguin on 2009-11-01
The dot makes it a hidden directory, press CTRL+H in Nautilus to show those.

Or using the terminal do
```
cd
kill `pidof cairo-dock`
cd .config
mv cairo-dock cairo-dock-old
```This will make sure the program isn't running and rename its settings directory (it should create a new one when you run it again).

---

### Post by djm227 on 2009-11-01
Nevermind... I got it back somehow.  It appeared when I switched desktops for some reason, and I was able to reconfigure it really fast.  Thanks for the help!

---

### Post by fabounet on 2009-11-02
lateral gap to 1000 will make it go 1000 pixels to the right ! so out of tour screen.

Hint : you can always recall the configuration window by launching 
```
cairo-dock -m
```
in a terminal or with ALT+F2 ;-)

---


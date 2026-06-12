---
title: "workspace switcher is cool, BUT"
date: 2009-04-21
forum: New to Ubuntu
---

### Post by miltk on 2009-04-21
this thing has been driving me nutzzz.

i just installed ubuntu on my laptop and the switcher seems to randomly swith on me annoyingly, making me click the taskbar icon. i don't think i'm doing anything to initiate it, certainly not clicking the icon. sometimes i just move my cursor and the workspace just switches.

now,,,i like this thing but it's driving me nutzzz. what am i doing, and what can i do?

thanks from  this new newbie

---

### Post by NikoC on 2009-04-21
Hmmz, could this kind of switching behaviour be explained by accidently hitting the scroll function on your laptop's touchpad? e.g. near the right edge of the pad is a scroll zone (you can set one at the bottom of the pad too).

Cheers,

Niko

---

### Post by lisati on 2009-04-21
I've noticed that the workspace switcher sometimes kicks in at inappropriate moments too. I haven't noticed a definite pattern yet, but I'm beginning to suspect the place the mouse pointer is sitting when I'm using the scroll wheel can sometimes make a difference.

---

### Post by shazbut on 2009-04-21
It's probably happening when you are are touching the right hand edge of the touchpad, which is set to scroll like the wheel on a proper mouse.  If the cursor is over a bit of exposed desktop the scroll action causes it to switch.  Go into compizconfig settings manager -> viewport switcher and disable the mouse bindings for next and previous to stop it happening.  I prefer using the keyboard to switch viewports anyway.

---

### Post by nothingspecial on 2009-04-21
If this is happening while you type you can disable your mousepad for a specified amount of time after a keystroke by typing 

```
syndaemon -d -t -i 1
``` into a terminal.
 The digit at the end is the amount of time in seconds that you want to turn it off for.

If you want this to apply all the time go to System > Preferences > Sessions and add it there.

---

### Post by loobyloo on 2009-04-21
I found this annoying too, but if you right click on the little square workplace selection icon at the bottom right of your screen, then click "remove from panel" that will get rid of it.

---

### Post by miltk on 2009-04-21
i did right click to remove it from the panel, but it did it anyway. removing from the panel is not the same as disabling is it?

i'll try to "gingerly" use the touchpad and see if this continues.

thx,,,,i'm glad i'm not the only one.

BTW....the switcher isn't working at all on my desktop instillation. is there a fix?

---

### Post by northern lights on 2009-04-21
> **NikoC said:**
> Hmmz, could this kind of switching behaviour be explained by accidently hitting the scroll function on your laptop's touchpad? e.g. near the right edge of the pad is a scroll zone (you can set one at the bottom of the pad too).
+1
That's probably it.

Install ccsm```
sudo apt-get install compizconfig-settings-manager
```
open it, navigate to the *Rotate Cube* menu, select the *Bindings* tab and remove the mousewheel/scrolling binding.

Not going to happen again.

---

### Post by Timpotten on 2009-04-29
It may be the mouse-wheel - if the velocity is high, it seems to shift workspace (instead if scrolling the context menu options or whatever)

No doubt this is 'cool' but it just seems like a nuisance to me. Anyone know how to remove this feature?

---

### Post by northern lights on 2009-04-29
Check the bindings I described above.

---

### Post by mbzn on 2009-04-29
It can also be found in the CompizConfig Settings manager under viewpoint switcher>Desktop-based Viewpoint Switcher MoveNext & MovePrevious witch is the place i disabled mine as i dont have the desktop cube enabled.

---

### Post by JohnL2009 on 2009-05-21
This is a little different - but I just upgraded to 9.04 and my work space button will not work - anyone have the same problem and how do we fix it?  thanks

---


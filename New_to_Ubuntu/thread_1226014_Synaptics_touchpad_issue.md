---
title: "Synaptics touchpad issue"
date: 2009-07-29
forum: New to Ubuntu
---

### Post by BobJam on 2009-07-29
My pointer is very erratic . . . all over the place, and shaky most of the time.

I've [COLOR=green][FONT=serif]**_installed_**[/FONT][/COLOR] [COLOR=red][FONT=serif]**_qsynaptics_**[/FONT][/COLOR], [COLOR=red][FONT=serif]**_gsynaptics_**[/FONT][/COLOR], and of course have the "Mouse" settings in the System>Preferences menu.

None of the settings I've tried in those programs (and the mind boggles at the iterations) calms my pointer down except to completely disable tapping in [COLOR=red][FONT=serif]**_qsynaptics_**[/FONT][/COLOR].

But doing that [COLOR=red][FONT=serif]**_everytime_**[/FONT][/COLOR] I want to type something and not have the text roam because my palm had touched the pad is very bothersome and annoying and seems like a tedious workaround.

I can't find a setting that will both calm the pointer down and reduce the roaming because of random palm touches.

And, yes, I've tried that delay setting for touches and it really doesn't do anything (both [LEFT][COLOR=red][FONT=serif]**_qsynaptics _**[/FONT][/COLOR]and [COLOR=red][FONT=serif]**_gsynaptics _**[/FONT][/COLOR]have this).
[/LEFT]
 
So, is there a way I can calm my pointer down and still have the tapping activated?

In the alternative, if I have to live with the workaround, is there a way that I can set a [LEFT][COLOR=red][FONT=serif]**_hotkey _**[/FONT][/COLOR]so that I can toggle the mouse state back and forth with the keyboard instead of tediously going to the terminal and running [COLOR=red][FONT=serif]**_qsynaptics _**[/FONT][/COLOR]every time?[/LEFT]

---

### Post by nothingspecial on 2009-07-29
To stop the pointer moving if you accidentally touch the touchpad when typing go to system > preferences > startup applications. Add this entry

 
```
Command: syndaemon -d -t -i 1
 
```

Put whatever you like in the Name and comment fields.

The number at the end of that command is the number of seconds you want the touchpad disabled after each keystroke. Change it to whatever you like.

---

### Post by sandeepraj on 2009-07-29
which computer do u have? dell xps?

---


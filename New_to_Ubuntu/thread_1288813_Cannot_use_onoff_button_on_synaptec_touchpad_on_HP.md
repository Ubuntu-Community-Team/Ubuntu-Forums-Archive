---
title: "Cannot use on/off button on synaptec touchpad on HP G60 laptop"
date: 2009-10-11
forum: New to Ubuntu
---

### Post by hazypictures on 2009-10-11
I have just set up a dual boot system on my new HP G60 laptop (64bit). 

I'm loving the setup except that the touchpad is so sensitive, when I am typing, mysterious windows start opening and all kinds of unwanted actions occur, and I think that it is because the touchpad is too sensitive. I like that it came with an on/off button, but it is not working in Ubuntu 9.04. :( Instead I must type with a piece of cardboard over the touchpad and then move it aside when I need to use the touch pad. Not a good work around, really.

Is there a way to activate the touchpad on/off switch in Ubuntu?

Also, there is a button to turn the wireless on & off, and it doesn't work either. Any way to get that working too?

Many thanks!

---

### Post by falconindy on 2009-10-11
[https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)

The above may be of some interest to you.

---

### Post by dave01945 on 2011-08-23
i know this post is old but i wanted to explain how i got the touchpad button to work in ubuntu 11.04 just incase anyone gets to this thread like i did

it's quite simple really first i ran

```
xev
```

this will list events when keys are pressed if you use this version it will filter out the info you don't need

```
xev | sed -n 's/^.*state \([0-9].*\), keycode *\([0-9]\+\) *\(.*\), .*$/keycode \2 = \3, state = \1/p'
```

then when i pressed the touchpad button i was getting 2 different events 

```
XF86Touchpadoff
XF86Touchpadon
```

then i went to keyboard shortcuts and created 2 custom shortcuts these are the commands the shortcuts run

```
synclient Touchpadoff=1   ##this turns the touchpad off
synclient touchpadoff=0     ##this turns it back on again
```

then in the keyboard shortcuts menu i highlighted the shortcut column and pressed the touchpad button and it automatically picked up the keypress did this for on and off and it now works perfectly


while i was looking arround i was looking in gconf-editor and under /apps/gnome-settings-deamon/keybindings is the entry for turning the touchpad on and off but this value was set to 

```
XF86Touchpadtoggle 
```

i currently don't know enough about how gconf-editor works to change this as it didn't have a on and off option only a toggle and that is not the event given by the key press if anyone could explain something about this i would be greatfull

---


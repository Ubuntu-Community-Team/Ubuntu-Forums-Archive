---
title: "I'm a newie in dire need of help...."
date: 2009-06-30
forum: New to Ubuntu
---

### Post by pizza-is-good on 2009-06-30
I'm new to Ubuntu(& Linux), I have about six months of experience with it. I know it enough to get around and do things you tell me to do on it, but not enough to figure out problems on my own...
 
Anyway, my current problem is that every-time I boot into Ubuntu (using gnome), the menu bar (the one with the minimize, maximize, & close buttons) is missing from all my programs. Also, I always have 5 worskapces in my workspace switcher, and when I log on, it only shows one.
 
When I try to solve the workspace problem (Right click the switcher, go to properties), the editor is not the one that is usually there, and doesn't give the option of columns, only for rows.
 
I go to check my visual effects, and they are at none, but I always have them at Extra. So I switch it back to Extra, it does the usual check for drivers, and then the problem is solved!
 
I restart, to see if it stays that way, and nope, back to the same problem:confused:.
 
I can change it every-time I boot, which is what I have been doing now, but its a little non-practical, and I don't think that it's supposed to do that. (At least it didn't at the begining)
 
I don't recall changing any settings the last time that I logged off that the problems weren't there, so I'm really lost, and have no idea on what to try next.
 
Thanks in advance for your help!

---

### Post by ken22 on 2009-06-30
sounds like you're missing a window manager.

---

### Post by pizza-is-good on 2009-06-30
> **ken22 said:**
> sounds like you're missing a window manager.
How do I get one?

---

### Post by ken22 on 2009-06-30
I think this might help you.

[http://ubuntuforums.org/showthread.php?t=406225](http://ubuntuforums.org/showthread.php?t=406225)

---

### Post by pizza-is-good on 2009-07-02
OK, that did help, thanks, but not solved it. I am closer to solving it, however.

What I now need to know is how to set a program (Compiz Fusion Icon), to load at startup. I think that should take care of it.

OR. I know that Metacity is the problem. So if I could just set Compiz as default.... I think that would solve it too.

---

### Post by ~sHyLoCk~ on 2009-07-02
> **pizza-is-good said:**
> 

What I now need to know is how to set a program (Compiz Fusion Icon), to load at startup. I think that should take care of it.

OR. I know that Metacity is the problem. So if I could just set Compiz as default.... I think that would solve it too.

You can open System->Preferences->Startup Applications and add an entry ```
compiz --replace
```

---

### Post by oldos2er on 2009-07-02
To start fusion-icon on bootup, go to System, Preferences, Startup Applications, and add /usr/bin/fusion-icon.

---

### Post by pizza-is-good on 2009-07-02
> **~sHyLoCk~ said:**
> You can open System->Preferences->Startup Applications and add an entry ```
compiz --replace
```
~sHyLoCk~: Thanks! That took care of it. Everytime it boots, I get a glimpse of the malfunctioning Metacity, but its only about a second, and then it goes right on to Compiz. 
> **oldos2er said:**
> To start fusion-icon on bootup, go to System, Preferences, Startup Applications, and add /usr/bin/fusion-icon.
oldos2er: Thanks as well! Now the fusion icon shows at start-up.

To everyone else, thanks a ton for all your help.

~pizza

---


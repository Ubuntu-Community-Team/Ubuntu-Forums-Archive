---
title: "Terminal Dissapeared."
date: 2010-05-16
forum: New to Ubuntu
---

### Post by Zintha on 2010-05-16
Ubuntu Lucid 10.04 on a Desktop.
That should be all you need to know, if anything.

So, early on in my Ubuntu use (2 months now!) I saw a program called Tilda, basically a console/quake style drop down Terminal, I loved it.

But now in Applications -> Accessories there is no Terminal yet, just Tilda.

Sometimes i'd prefer a normal terminal.

Any idea how to get it back? I searched in the forums but apparently i'm uniquely stupid in somehow removing it!

---

### Post by ibuclaw on 2010-05-16
Is gnome-terminal installed on your system?

---

### Post by -humanaut- on 2010-05-16
sudo apt-get install gnome-terminal that should do it for you.

---

### Post by Zintha on 2010-05-16
> **ibuclaw said:**
> Is gnome-terminal installed on your system?
Synaptic says yes.

edit: and a reinstall doesn't put it back.

---

### Post by -humanaut- on 2010-05-16
Try hitting alt+f2 and type gnome-terminal see if that brings it up. You might just have to edit your menu's.

---

### Post by Ozymandias_117 on 2010-05-16
If you right click on the menu on your Panel, and select edit menus, is it under there, just not checked?

If it isn't, I would try going to ctrl + alt + f1 and ```
sudo aptitude reinstall gnome-terminal
``` see if that does anything.

---

### Post by Zintha on 2010-05-16
> **Ozymandias_117 said:**
> If you right click on the menu on your Panel, and select edit menus, is it under there, just not checked?

If it isn't, I would try going to ctrl + alt + f1 and ```
sudo aptitude reinstall gnome-terminal
``` see if that does anything.

It was simply not checked!
Thank you, issue 100% solved!

If I win the lottery next week, i'll give you both $1,000. :D

I didn't know about alt+f2, learn something everyday.

---

### Post by -humanaut- on 2010-05-16
> **Zintha said:**
> It was simply not checked!
Thank you, issue 100% solved!

If I win the lottery next week, i'll give you both $1,000. :D

I didn't know about alt+f2, learn something everyday.

lol, Thanks alot man! Glad it worked for you though.

---


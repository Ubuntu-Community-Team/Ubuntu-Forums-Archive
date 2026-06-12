---
title: "Workspace Edge Problem"
date: 2010-06-03
forum: New to Ubuntu
---

### Post by Hunter Morrell on 2010-06-03
Back when I first installed Lucid, I used Ubuntu Tweak to change the Workspace Edge settings. Last night, the window borders weren't working so I posted up a topic on here. Someone told me to put "metacity --replace" (or something along those lines) in the Startup Applications and I did. I didn't restart and test it immediately, but I went on and shut it off because it was late in the evening. So I started it up this morning and the window borders were back up, but now the Workspace Edge setting aren't working, yet it shows in Ubuntu Tweak that they're working. Any help would be greatly appreciated

---

### Post by nhasian on 2010-06-03
are you talking about moving windows to other workspaces by dragging them?  that requires compiz not metacity.  you can also move applications to other workspaces with control-alt-shift-arrow keys

---

### Post by Hunter Morrell on 2010-06-03
No. I'm talking about when I move my mouse to one of the four corners of the screen, something happens. [COLOR=#000000]Usually if I move my mouse to one of the corners of the screen, either all the windows will minimize and it'll take me straight to the desktop, or it'll display all the windows allowing me to easily choose which one I want to go to, or it'll show the workspaces which allows me to switch to another workspace if I wanted to.[/COLOR]

---

### Post by nhasian on 2010-06-03
yes that is one of the settings of compiz.  in System-> Preferences-> CompizConfig Settings Manager, then click on General, and go to the Key Bindings tab. There you can set things like "Show Desktop" if you move the mouse to one of the corners of the screen.

if you used metacity --replace that disables compiz and you will lose these extra features.

---

### Post by Hunter Morrell on 2010-06-03
I did all that. Nothing. I even removed the "metacity --replace" thing and restarted the computer. Nothing.

---

### Post by tom.swartz07 on 2010-06-03
so simple its stupid

hit ALT F2 and type 
```
compiz --replace
```

---

### Post by Hunter Morrell on 2010-06-03
And I bow to your superior intellect. Seriously though, thanks a ton dude. I'm literally smacking myself for not getting that :p

---


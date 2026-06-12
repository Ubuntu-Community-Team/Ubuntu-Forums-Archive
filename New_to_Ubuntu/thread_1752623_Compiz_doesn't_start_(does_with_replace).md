---
title: "Compiz doesn't start (does with replace)"
date: 2011-05-08
forum: New to Ubuntu
---

### Post by EvilBro on 2011-05-08
After Ubuntu 11.04 Classic has started, it appears that Compiz isn't working. I have no desktop effects. I open up a terminal and type 'compiz --replace &'. The result is:
```

Backend     : gconf
Integration : true
Profile     : default
Adding plugins
Initializing core options...done
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Initializing composite options...done
Initializing opengl options...done
Initializing decor options...done
Initializing gnomecompat options...done
Initializing resize options...done
Initializing wobbly options...done
Initializing move options...done
Initializing cube options...done
Initializing rotate options...done
Starting unity-window-decorator
Setting Update "run_command_terminal_key"
Setting Update "flip_time"

```
From that point on I have Desktop effects (Wobbly windows, cube, etc.). When I close the terminal, all the windows momentarily disappear, but when they return everything still works. The only messages I see in logs are of this kind: "Warning: Xalloc: requesting unpleasantly large amount of memory: 0 bytes."

What could be happening here and how can I fix it? How am I able to check whether compiz is running after startup?

---

### Post by CaptainMark on 2011-05-08
are you able to get unity in 3d mode? (so do you have the launcher bar pop up on the left of the screen) 

if so then compiz i think must be running fine because unity 3d needs compiz, but you can check by looking for system monitor in the ubuntu dashboard, compiz will be listed under processes if it is running

if youve got the classic look desktop and you have everything stacked into a tree from the top left ubuntu menu then unity isnt running and could suggest a graphics driver issue, try going to system>admin>additional hardware drivers and see if you options to install one

---

### Post by EvilBro on 2011-05-08
> **CaptainMark said:**
> are you able to get unity in 3d mode?
No, I am not able to do that. I don't expect to though as the result of "/usr/lib/nux/unity_support_test" says my card is blacklisted.

> if so then compiz i think must be running fine because unity 3d needs compiz, but you can check by looking for system monitor in the ubuntu dashboard, compiz will be listed under processes if it is running
Compiz isn't in the list of processes, but metacity is. So for some reason metacity is started instead of Compiz.

> if youve got the classic look desktop and you have everything stacked into a tree from the top left ubuntu menu then unity isnt running and could suggest a graphics driver issue, try going to system>admin>additional hardware drivers and see if you options to install one
I get the feeling you are answering a slightly different question than the one I am asking. This question is not about Unity. This question is about Compiz. But just for completeness: I am using nvidia 173 and it is working (otherwise Compiz wouldn't work when I run it manually). Note that I do have the issue that it says 'activated, but not in use', but from what I've read here, that message is untrue.

---

### Post by EvilBro on 2011-05-25
I found the problem. When I start ubuntu(classic) it looks at /usr/share/gnome-session/sessions/classic-gnome.session which contains:
```

[GNOME Session]
Name=Classic GNOME
Required=windowmanager;panel;filemanager;
Required-windowmanager=gnome-wm
Required-panel=gnome-panel
Required-filemanager=nautilus
DefaultApps=gnome-settings-daemon;
IsRunnableHelper=/usr/lib/nux/unity_support_test --compiz
FallbackSessionsID=GNOME2d
GNOME2d=2d-gnome

```
The problem is that IsRunnableHelper is set incorrectly. Probably because I have a graphics card that is blacklisted (FX5700 nvidia). If I delete the last three lines, compiz starts normally. 

Note that another way to 'solve' this is by adding /usr/bin/compiz to the list of startup applications. I think that is just wrong though. :)

One more thing: if I remove the same check from the ubuntu.session, unity does seem to start. I get a top panel and a side panel, but there are no icons on the side panel. If I figure out how to solve this, I'll post it here.

---


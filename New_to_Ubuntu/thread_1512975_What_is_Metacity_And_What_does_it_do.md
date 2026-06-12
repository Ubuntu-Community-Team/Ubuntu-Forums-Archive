---
title: "What is Metacity? And What does it do?"
date: 2010-06-18
forum: New to Ubuntu
---

### Post by captain_conrad on 2010-06-18
I have been seeing this word a lot. I searched threads a bit but I cannot find an explanation of what it is and what it does, I have no earthly idea what this thing is but I hear it often and I want to know about it because it apparently has to do with things similar to what compiz config settings manager does.
(compiz is a program/tool that enables all the cool effects like the famous desktop cube, the gears in the cube, wobbly windows, 3d windows, window decorations, etc etc.)

Ok so what is Metacity and What does it do?

---

### Post by drs305 on 2010-06-18
It's a windows manager. I had similar questions to you several years ago. I found this page, and then updated it as I learned a bit about it:
[https://help.ubuntu.com/community/Metacity]("https://help.ubuntu.com/community/Metacity")

---

### Post by jtarin on 2010-06-18
You probably won't find an answer per se on these forums as Metacity is circa 2001. A few years before Ubuntu's time.
Here's a [[COLOR="Blue"]link[/COLOR]]("http://en.wikipedia.org/wiki/Metacity") that will give you the lowdown.

---

### Post by J V on 2010-06-18
It's very hard to explain. I never understood the difference until I installed openbox. try out an openbox window manager and you should notice the difference. It manages some shortcuts, the way windows behave, how you switch desktops/applications, lots of stuff like that.

---

### Post by drs305 on 2010-06-18
Another way to explore what metacity does in Ubuntu is to open gconf-editor and see the settings it affects (things like titlebar fonts, button layout, keybindings, etc). If you aren't familiar with gconf-editor, highlight a folder in the left pane and then select a setting in the top right pane. An brief explanation of the setting is found in the lower right panel. Open gconf-editor with:
```

gconf-editor /apps/metacity

```

---


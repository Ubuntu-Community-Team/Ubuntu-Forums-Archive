---
title: "dpkg error"
date: 2009-02-05
forum: New to Ubuntu
---

### Post by drew.saltarelli on 2009-02-05
Hello, this is my first post here, so if i mess this up I'm sorry.

I'm having a weird problem, when I open synaptic, I get the error "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."

so I open up the terminal, type "dpkg --configure -a", and it says I need super user privileges? what am i doing wrong? :S

---

### Post by cyfur01 on 2009-02-05
It's trying to access/modify files that need administrator access, so you need to add "sudo" to the command:
```

sudo dpkg --configure -a

```

This will promote you to root for the dpkg command.

If you're wondering, my guess is that Synaptic doesn't tell you this because it uses "gksudo" to pop up the dialogue that asks you for your password, which promotes it to being a root-owned program which means it doesn't need to type sudo for anything, and I guess they didn't think to add "sudo" to certain warnings when you're most-likely not actually the root user.

---

### Post by jpeddicord on 2009-02-05
This thread or post has been moved from the Desktop Effects & Customization forum as the posted content is considered off-topic.

Desktop Effects & Customization is a forum for discussing:
[LIST]
[*]Compositing managers such as Compiz
[*]Themes (window themes, widget themes, backgrounds, etc)
[*]Appearance preferences
[/LIST]

Your post did not fit any of these categories, so it has been moved.

Common types of off-topic threads include:
[LIST]
[*]GNOME/KDE/XFCE help in general
[*]Hardware problems not directly related to compositing
[/LIST]

---


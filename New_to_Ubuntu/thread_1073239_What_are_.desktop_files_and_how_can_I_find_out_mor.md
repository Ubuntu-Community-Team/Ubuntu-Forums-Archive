---
title: "What are .desktop files and how can I find out more about them?"
date: 2009-02-18
forum: New to Ubuntu
---

### Post by lone_wolfII on 2009-02-18
Title's pretty explanatory... :)

Sorry if this has been talked about before. The search seems to strip the . from '.desktop'. 

Thanks in advance.

---

### Post by squaregoldfish on 2009-02-18
These are the small files that define the entries in your application menus, although they can be used to define links to folders and similar items - similar to shortcuts in Windows.

For a simple application launcher, they define the command to be run and the icon to be shown for that launcher. A simple example:

```

[Desktop Entry]
Name=GIMP
Exec=gimp
Icon=gimp.png
Type=Application
Categories=Graphics;2DGraphics;RasterGraphics
StartupWMClass=Gimp

```

The Name entry is the text to be displayed for the launcher.
Exec is the command to be run.
Icon is the icon :p
The Type and Category entries can be used by menu generators etc.
The StartupWMClass defines the window ID of the application when it's started.

There's lots of other stuff that can go in these files. All the info you need can be found in the [Desktop Entry Specification]("http://standards.freedesktop.org/desktop-entry-spec/0.9.7/").

Hope this gets you started.
Steve.

---

### Post by techstop on 2009-02-18
Are you asking because of this beatup?

[http://it.slashdot.org/article.pl?sid=09/02/17/1526244](http://it.slashdot.org/article.pl?sid=09/02/17/1526244)

---

### Post by lone_wolfII on 2009-02-18
Haha... Yeah. I'm assuming that's about the Linux 'virus' thing. 

It was talking about .desktop files but I didn't know how they were constructed normally.

EDIT: It kinda sucks that you can just put whatever you want in the exec section. 
Thanks for the link squaregoldfish!

---


---
title: "Can someone help me out with GEdit?"
date: 2010-01-18
forum: New to Ubuntu
---

### Post by papuccino1 on 2010-01-18
I'm trying to follow this tutorial, but I'm a bit confused.
[Link Here]("http://linil.wordpress.com/2008/05/31/using-gedit-to-auto-complete-python-code/")


For starters, how do find the gEdit folder? I don't see it anywhere.

Also, how do I just download a single .plugin file from GitHub? I can't find a download button anywhere. :)

Thank you for the help.

---

### Post by blackened on 2010-01-18
The folder the author is referring to is ~/.gnome2/gedit/plugins which is a subdirectory of your user's home folder. The easiest way to get to it is by opening the terminal and issuing
```
nautilus --no-desktop ~/.gnome2/gedit/plugins
```

---

### Post by lidex on 2010-01-18
> **papuccino1 said:**
> I'm trying to follow this tutorial, but I'm a bit confused.
[Link Here]("http://linil.wordpress.com/2008/05/31/using-gedit-to-auto-complete-python-code/")
Also, how do I just download a single .plugin file from GitHub? I can't find a download button anywhere. :)
Thank you for the help.

This page:
[http://github.com/fenrrir/geditpycompletion/blob/master/pythoncodecompletion.gedit-plugin]("http://github.com/fenrrir/geditpycompletion/blob/master/pythoncodecompletion.gedit-plugin")
Click on "Download Source" at top-right.

BTW, if you haven't installed any gedit plugins, that folder will not exist. You can create it however. Use this command:
```
mkdir ~/.gnome2/gedit/plugins/
```

---

### Post by PenguinInside on 2010-01-19
Although you can certainly hook gedit to do code completion and a lot more, in my opinion you'd be better off with a dedicated Python editor.

Gedit is good as a nice, featureful text editor. If you try to make an IDE out of it, it's neither here nor there.

Do your plugins work now?

---

### Post by J V on 2010-01-19
Files beginning with . are hidden, open your home folder and hit ctrl h

---


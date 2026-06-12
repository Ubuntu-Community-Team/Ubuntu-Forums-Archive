---
title: "Simple mouse configuration question"
date: 2010-03-25
forum: New to Ubuntu
---

### Post by jhy2a on 2010-03-25
So a simple question I have is how can I change the functions on a mouse? I have a standard laser mouse that has a left and right mouse button as well as a scroll wheel. I want to fix this mouse so that the right mouse button behaves exactly like the left mouse button (in other words, no ability to right click anywhere). I have heard there is a config file somewhere that allows me to modify my mouse button functions, can someone tell me where this file is and make some suggestions on editing it?

---

### Post by Gadgetech on 2010-03-25
You can change the mouse button mapping with the xmodmap command. You can make the settings permanent by saving them in a .Xmodmap file either in your home directory, or in the system wide configuration. However, it looks like you can't map the same button number twice, so I don't think you can map both left and right buttons as button #1. You could map it to a high number though like
```
xmodmap -e "pointer = 1 2 9 4 5 6 7 8 3"
```
This maps the right button as #9 instead of #3.
I have a writeup on my blog about the .Xmodmap files.
[http://tuxtweaks.com/2008/12/update-logitech-lx8-in-ubuntu/](http://tuxtweaks.com/2008/12/update-logitech-lx8-in-ubuntu/)

---


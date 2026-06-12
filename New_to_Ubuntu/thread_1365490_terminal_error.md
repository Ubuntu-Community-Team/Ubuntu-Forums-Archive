---
title: "terminal error"
date: 2009-12-27
forum: New to Ubuntu
---

### Post by dzon65 on 2009-12-27
I'm getting this error in the terminal every time I go into my home folder.
yui@ubuntu:~$ gksu gdm-setup.py
/home/yui/.themes/Kuler 2 v3/gtk-2.0/gtkrc:34: Kan invoegbestand ‘styles/panelstyles’ niet vinden
/home/yui/.themes/Kuler 2 v3/gtk-2.0/gtkrc:624: error: invalid string constant "panel", expected valid string constant
yui@ubuntu:~$ 
This refers to the theme I've got installed and of which I took the sub gtkrc "panel" and panel jpg out.Can this block any install (in this case the gdm setup)?

---

### Post by ankspo71 on 2009-12-28
Hi,

Does **sudo gdm-setup.py** make any difference? This only happens when you try to operate with root priveleges?

I imagine removing any of the theme files and or theme configurations could make some problems loading certain apps, as it fails to find those files or configurations. I haven't run into this problem before though. I'm not a theme designer, but I suppose you will have to look inside some other Kuler theme files, presumably the main gtkrc file, and find the lines that call on the sub gtkrc "panel", and do some changes there. Some theme files don't open with gedit, so you will have to right click on them and make them executable in the permissions.

I don't know if this will help... but I'll mention it anyways...
[http://tombuntu.com/index.php/2007/09/18/theme-applications-running-as-root-in-ubuntu/](http://tombuntu.com/index.php/2007/09/18/theme-applications-running-as-root-in-ubuntu/)

---

### Post by dzon65 on 2009-12-30
No,the error only shows when the theme isn't "whole".Like you said,I'll have to do some more changes in that gtkrc to make it work without errors.As for that link,pretty cool,check it out.Thanks for the reply.
Kind regards.

---


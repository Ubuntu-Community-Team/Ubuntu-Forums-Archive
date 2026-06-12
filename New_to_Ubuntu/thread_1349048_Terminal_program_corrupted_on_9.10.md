---
title: "Terminal program corrupted on 9.10"
date: 2009-12-07
forum: New to Ubuntu
---

### Post by lethalox on 2009-12-07
So I was trying to change from the default set of a background colors on the Terminal program and the bash shell.  But I seem to screwed up the program because now when I try to start it, the Terminal window is stuck in an infinite loop and just throws windows up to the class without end.  A window will appear and then disappear and then repeat.  Is there a way to reset the settings for the Terminal application without a full reinstall of the OS? 

Thanks,
Alex

---

### Post by blazemore on 2009-12-08
If you're using the default terminal in Ubuntu, you can reinstall it.
Press alt+F2, then type xterm then press Enter.
This will load a basic terminal.
In here, type
```
sudo apt-get install --reinstall gnome-terminal
```
This will reinstall the terminal for you, and should fix your problems.

---


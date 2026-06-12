---
title: "Editing .fdi file can't save changes."
date: 2010-01-01
forum: New to Ubuntu
---

### Post by bigaldizzler on 2010-01-01
I am trying to edit this file /usr/share/hal/fdi/policy/20thirdparty/11-x11-synaptics.fdi

but when I save it it said something like I dont have permission to save.  I am following instructions from linuxcentre wiki to disable a portion of my Dell Mini 10v Touchpad so its more usable...it didn't mention anything about not being able to save. :(  

Thanks!

---

### Post by falconindy on 2010-01-01
You need root privileges to edit that file. If your editor is a terminal based editor like nano, use 'sudo nano /path/to/file'. If you're using a graphical editor like gedit, use 'gksu gedit /path/to/file'.

---

### Post by m_duck on 2010-01-01
In addition to the above, I would advise copying the ***11-x11-synaptics.fdi*** file to the  ***/etc/hal/fdi/policy/ ***folder and editting the file there to ensure that your modifications are not overwritten when hal gets updated.

---

### Post by bigaldizzler on 2010-01-01
Perfect, got it to work! I took the nano route in terminal!!! :P

Thank you both for the help!

---


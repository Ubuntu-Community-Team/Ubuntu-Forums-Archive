---
title: "changing default/login resolution on 10.04"
date: 2010-05-02
forum: New to Ubuntu
---

### Post by ave2 on 2010-05-02
Hi my monitor doesnt support the default resolution/aspect ratio that ubuntu sets, and so pastes a large "input not support" block across the middle of my screen- thus the entire login block is covered

in 9.10 I entered the xorg.conf file and changed the screen modes to "1152x864" and that worked.

in 10.04 xorg.conf is no longer there, so how would I do it now?? any ideas?

---

### Post by sakisds on 2010-05-02
While you are at the login screen, press ctrl+alt+F1, login and run the following commands:
```
export DISPLAY=:0.0
sudo -u gdm gnome-control-center
```

After that, switch back to the login screen by pressing ctrl+alt+F7. You will see the gnome control panel. If you move the window around a bit you could click the Screen Resolution settings and change it.

---

### Post by kansasnoob on 2010-05-02
This first link worked for me with one caveat, it wouldn't work if I chose to auto-login:

[http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html](http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html)

So in my case the following worked better:

[http://www.linuxreaders.com/2009/11/04/change-ubuntu-9-10-resolution/](http://www.linuxreaders.com/2009/11/04/change-ubuntu-9-10-resolution/)

But from appearances using the second link leaves the gdm screen unchanged whereas the first link changes the resolution of both the gdm screen and the desktop.

---

### Post by kansasnoob on 2010-05-02
Actually I had a thought, which in itself can be scary :)

Anyway I now have in place both the edits to "/etc/gdm/Init/Default" as recommended here:

[http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html](http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html)

And the edits to "/etc/gdm/PreSession/Default" as recommended here:

[http://www.linuxreaders.com/2009/11/04/change-ubuntu-9-10-resolution/](http://www.linuxreaders.com/2009/11/04/change-ubuntu-9-10-resolution/)

And that changed the gdm screen resolution and also works great with auto-login :)

---

### Post by ave2 on 2010-05-04
> **sakisds said:**
> While you are at the login screen, press ctrl+alt+F1, login and run the following commands:
```
export DISPLAY=:0.0
sudo -u gdm gnome-control-center
```

After that, switch back to the login screen by pressing ctrl+alt+F7. You will see the gnome control panel. If you move the window around a bit you could click the Screen Resolution settings and change it.

I tried this- got error after typing in the sudo -u...... that said cannot open display

> **kansasnoob said:**
> Actually I had a thought, which in itself can be scary :)

Anyway I now have in place both the edits to "/etc/gdm/Init/Default" as recommended here:

[http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html](http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html)

And the edits to "/etc/gdm/PreSession/Default" as recommended here:

[http://www.linuxreaders.com/2009/11/04/change-ubuntu-9-10-resolution/](http://www.linuxreaders.com/2009/11/04/change-ubuntu-9-10-resolution/)

And that changed the gdm screen resolution and also works great with auto-login :)

also got errors following this- im going to try reinstall this weekend, maybe it will work after that

---


---
title: "gdm at startup"
date: 2010-07-21
forum: New to Ubuntu
---

### Post by masque7 on 2010-07-21
Sometimes, gdm doesn't start for me and I either have to:
```
/etc/init.d/gdm start
```or 
```
startx
``` if i just want to get into X which by default is using Gnome. 

I have some other wms, namely tiling ones like xmonad that I prefer to boot into sometimes. 


[LIST]
[*]Why is gdm starting/not sometimes? Is it because of my graphics drivers? nvidia 173.14.22 @ GeForce 6150SE nForce 430 (integrated on motherboard)
[*]How would I go about disabling gdm as I now prefer logging in via tty? Hey, getting into X/gnome is faster without loading gdm.
[*]Instead of 'startx' how would I specify? start <wm/de>?
[/LIST]

---

### Post by Brandon Williams on 2010-07-21
> **masque7 said:**
> [LIST]
[*]Why is gdm starting/not sometimes? Is it because of my graphics drivers? nvidia 173.14.22 @ GeForce 6150SE nForce 430 (integrated on motherboard)
[*]How would I go about disabling gdm as I now prefer logging in via tty? Hey, getting into X/gnome is faster without loading gdm.
[*]Instead of 'startx' how would I specify? start <wm/de>?
[/LIST]

[LIST]
[*]The log files in /var/log/gdm/ might give you some indication of why gdm isn't starting reliably. In a case when gdm doesn't start, use sudo to check /var/log/gdm/:0.log, /var/log/gdm/:0-greeter.log, and/or /var/log/gdm/:0-slave.log. Are there any useful error messages in any of them?
[*]To disable gdm entirely, just remove all content from the file /etc/X11/default-display-manager. If that file is empty, then gdm will not be started.
[*]Most window managers have their own scripts to start up a user session. For example, XFCE has startxfce4. If the WM has such a script, you can try just using that. In most cases, it will work better to run 'startx <startwm>' (e.g. 'startx startxfce4'), because you'll get all of the extra init that happens with a login from gdm. If you've written your own script, then just specify your script as the argument to startx.
[/LIST]

---

### Post by masque7 on 2010-07-23
> **Brandon Williams said:**
> 
[LIST]
[*]To disable gdm entirely, just remove all content from the file /etc/X11/default-display-manager. If that file is empty, then gdm will not be started.
[/LIST]
If I installed slim login manager would I select which one I want to use gdm/slim via this file?

---


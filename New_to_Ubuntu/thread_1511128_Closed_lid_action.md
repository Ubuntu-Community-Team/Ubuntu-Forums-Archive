---
title: "Closed lid action"
date: 2010-06-16
forum: New to Ubuntu
---

### Post by donescamillo on 2010-06-16
Hi,

In Ubuntu 10.04 is it possible to set action for notebook closed lid to "Do nothing"?Now I see only "Blank screen", "Suspend" and "Shutdown" options

thanks

---

### Post by iJohnE on 2010-06-16
"Blank Screen" and "Do Nothing" are the same thing. All it does is put a blank screen on your notebook when you close it, which is essentially the same as doing nothing.

---

### Post by chriuso on 2010-10-30
Hi iJohnE,

the amount of "nothing" of the action "blank screen" is evidently not nothing. For me it's already too much of something. When I have my notebook connected to an external monitor and mouse/keyboard, then I want to close my notebook and just put it under the desk. However, this is not possible when Ubuntu just offers the "blank screen" option - because the external display switched off then.

So - does anyone know a possibility to define a true "do nothing" option as action when closing the lid?

thank you :)

-----
meanwhile I found the solution here in this forum (when searching in the context of an external monitor):
[http://ubuntuforums.org/showthread.php?t=1307857](http://ubuntuforums.org/showthread.php?t=1307857)

the wanted option is there, but not available through the menu, it has to be set through the terminal:

gconftool-2 --type string --set /apps/gnome-power-manager/buttons/lid_ac "nothing"

---

### Post by ausairman on 2011-12-03
As this post came up when I googled the same problem, I thought I might as well provide a solution for the latest ubuntu version (11.10):

This is taken from here: [https://help.ubuntu.com/11.10/ubuntu-help/power-closelid.html](https://help.ubuntu.com/11.10/ubuntu-help/power-closelid.html)

On battery power:

```
gsettings set org.gnome.settings-daemon.plugin.power lid-close-battery-action "blank"
```


```
gsettings set org.gnome.settings-daemon.plugin.power lid-close-ac-action "blank"
```

I am not sure what the difference between "do nothing" and "blank" is, as I would have thought the monitor turning off when you close the lid was a hardware thing, in any case you can also replace "blank" in the above with "nothing".

---


---
title: "FVWM_Crystal on ubuntu 10,04"
date: 2010-05-23
forum: New to Ubuntu
---

### Post by cbbnewbie on 2010-05-23
hi to all I just want to know if fwvm crystal can be installed in ubuntu 10.04. I'm just curious about it and want to try. If its possible how would it appear? is it like installing lxde wherein you can select it in the login screen or like a different OS which is selected on boot? thanks

---

### Post by Skorzen on 2010-05-23
I've never tried it, but as long as it's documented, I believe it's possible to make it work under Ubuntu:
[https://help.ubuntu.com/community/FVWM](https://help.ubuntu.com/community/FVWM)

---

### Post by cbbnewbie on 2010-05-23
hi again i have fvwm-crystal installed, now i want to customize it and the way to do that is to read lot of forums or guides through the internet but my problem now is how to enable wireless network in fvwm? When i tried lxde the solution is to edit the startup txt and adding the command @nm-applet in it, is there a similar way in fvwm??

---

### Post by angry_johnnie on 2010-05-23
the solution would, in fact be pretty similar.

find the fvwm-crystal.desktop file (usually in /usr/share/xsessions/)

see where it points to (Exec=something??), by running

```
cat /path/to/fvwm-crystal.desktop
```

you could replace cat with nano, given you'll end up editing this file.

then, you'll need to edit the desktop file and change the Exec line, so that it points to a custom script, which would be something like this (with your own stuff, of course):

```
#!/bin/bash

nm-applet --sm-disable &
exec /path/to/fvwm-crystal


```


fvwm-crystal must be the last line, and it must begin with exec.

then you need to make this custom script executable:

```
sudo chmod a+rwx /path/to/custom/script
```

and that's it :)

---

### Post by cbbnewbie on 2010-05-23
@angry_johnnie

> the solution would, in fact be pretty similar.

find the fvwm-crystal.desktop file (usually in /usr/share/xsessions/)

see where it points to (Exec=something??), by running

Code:
cat /path/to/fvwm-crystal.desktop

when i check /usr/share/xsessions i find FVWM-Crystal but not the fvwm-crystal.desktop and from there I cant understand the steps you enumerated, sorry im a newbie in Linux and still learning. Can you please detail or explain the steps more? thanks

By the way i can enable nm-applet at the terminal but when i close it the nm-applet also disappears.

---

### Post by angry_johnnie on 2010-05-25
:-)

all the files in /usr/share/xsessions are of the .desktop type.
if you look at them through your file browser, however, it may not display the .desktop type.

as long as you've found it, it's perfectly safe to edit /usr/share/xsessions/fvwm-crystal.desktop, even if it's not showing you the .desktop part of its name.

so, suppose it is called FVWM-Crystal

you would

```
gksu gedit /usr/share/xsessions/FVWM-Crystal.desktop
```

it should open a text file with content very similar to this:


```
[Desktop Entry]
Encoding=UTF-8
Name=XMonad
Comment=Lightweight tiling window manager
Exec=xmonad
Icon=xmonad.png
Type=XSession
```

This is just an example.

Anyway, what we're looking for is the **Exec** line.

suppose yours reads  **Exec=fvwm-crystal**

you would need to change that to something else.

create a custom script:  open gedit and create a text file with the following content (for example):

```
#!/bin/bash

nm-applet --sm-disable &
exec /path/to/fvwm-crystal

```

(if the path to fvwm-crystal on the exec line is just fvwm-crystal, then you could just write fvwm-crystal in the script.

then just save the file.  suppose you name it /home/you/fvwm-crystal2.

then you'll need to make that file executable by running:

```
sudo chmod a+rwx /home/you/fvwm-crystal2
```

then, going back to the desktop file, you would change the **Exec** line to

**Exec=/home/you/fvwm-crystal2**

save the desktop file.

that way, when you choose fvwm-crystal, it will be executing your script, loading nm-applet before fvwm.

may sound like gibberish, but it's pretty simple once you've done it.



Also, if you run nm-applet from a terminal, it will dissapear as soon as you close that terminal, unless you run it like this:

```
nm-applet & disown
```

---

### Post by cbbnewbie on 2010-05-26
done. thanks angry_johnnie, learned a lot :)

---


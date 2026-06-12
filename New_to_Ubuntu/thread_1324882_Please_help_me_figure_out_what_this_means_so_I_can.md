---
title: "Please help me figure out what this means so I can use my computer! Urgent."
date: 2009-11-12
forum: New to Ubuntu
---

### Post by selenesagaz on 2009-11-12
I just upgraded to the 9.10 Netbook edition from 9.04 netbook edition and everything was great until I tried to switch to classic mode; now I can't seem to access anything. The only thing that appears is the desktop with no panels no nothing. 

I found...

[https://bugs.launchpad.net/desktop-switcher/+bug/349519](https://bugs.launchpad.net/desktop-switcher/+bug/349519)

But I do not speak this tech language it seems cause I have no clue what to do. 

Someone please help me!

I have a Dell MIni 9n.

---

### Post by sledge73 on 2009-11-13
I hate to be the one but after reading the report my suggestion would be to reinstall & not change to classic mode. Evidently they haven't fixed the bug yet.

---

### Post by selenesagaz on 2009-11-13
All because I tried to switch it to classic mode? Just to see what it was...

---

### Post by stoogiebuncho on 2009-11-13
I haven't tested this to see if it works, since I am not running netbook remix.  But judging from what I read on the bug report you linked to, this is what you need to do:

1) Press Alt+F2.  This brings up the "Run Application" box.  Type ```
gnome-terminal
``` and press enter.

2) Now you should have a terminal window open.  Enter the following command:
```
gconftool-2 --set /desktop/gnome/session/required_components_list --type list --list-type=string ["windowmanager","panel","filemanager"]
```

3) Reboot your computer.  You should be in working "Classic" mode now.

If you want to switch back to netbook mode, go ahead and try it.  If it does not display properly, follow the steps above to open a terminal window, but type in this command instead:
```
gconftool-2 --set /desktop/gnome/session/required_components_list --type list --list-type=string ["windowmanager","panel"]
```

I hope that makes sense to you.

---

### Post by selenesagaz on 2009-11-13
I can not get terminal to open

---

### Post by stoogiebuncho on 2009-11-13
Sorry for the delayed response.

Another way to get to a terminal is to press Ctrl+Alt+F1.  You can enter the command there, and when you're finished, press Ctrl+Alt+F7 to get back to your desktop.

---


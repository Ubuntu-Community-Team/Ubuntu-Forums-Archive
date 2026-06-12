---
title: "[SOLVED] No panels"
date: 2008-12-23
forum: New to Ubuntu
---

### Post by Mr.Kuchinawa on 2008-12-23
Hello and merry Christmas

After I accidentally shut down my system while the add/remove was updating, I have experienced strange problems. First of all, no panels are present, and neither can I add any (“panel” under setting manager does not respond). Secondly, add/remove boots at start-up, even though I have not set it to do so.

Any help would be extremely appreciated

---

### Post by Cannaregio on 2008-12-23
Is your panel lock on? 
Check [COLOR="#0000ff"]gconf-editor[/COLOR]

check default setup and more. 
Also see if 

[COLOR="Blue"]app/panel/global/locked_down[/COLOR]

is checked. 
Uncheck - log off & re-log again.

---

### Post by timandjulz on 2008-12-23
When you say "no panels", do you mean that even the panel containing the menus no longer displays?  e.g. You only have a background with icons and nothing else?

This is just a guess.  But if you still have the panel with the menu on it then I suggest you right click it and add a couple of new panels.  Hopefully this will clear up any problems that might be caused by the system looking for a panel.

---

### Post by Mr.Kuchinawa on 2008-12-23
> **timandjulz said:**
> When you say "no panels", do you mean that even the panel containing the menus no longer displays?  e.g. You only have a background with icons and nothing else? 

I mean: background and nothing else. I can't even open the panel config. from the settings manager, as I mentioned in the first post

---

### Post by Mr.Kuchinawa on 2008-12-23
> **Cannaregio said:**
> Is your panel lock on? 
Check [COLOR="#0000ff"]gconf-editor[/COLOR]

check default setup and more. 
Also see if 

[COLOR="Blue"]app/panel/global/locked_down[/COLOR]

is checked. 
Uncheck - log off & re-log again.

The first code downloaded a bunch of stuff, but it made no discernible difference. The second code did nothing (can't find directory)

---

### Post by adobrakic on 2008-12-23
The first code downloaded stuff?

You did alt + f2 and put 'gconf-editor' in there, right?

Then in the configuration editor that opens, you follow the location of 'app/panel/..'

---

### Post by Mr.Kuchinawa on 2008-12-23
A simple misunderstanding on my part, sorry. However, It doesn't even display a "panel" folder. Might this be the explanation? How to fix?

---

### Post by Coder543 on 2008-12-23
We will install gnome do to allow you to access settings, etc. so that the panels may be recovered easier.

Press Ctrl + Alt + F1
type your username
type your password (it will not appear)

type sudo apt-get install gnome-do
type your password (it will not appear)
say 'y' to any prompts that may appear

If an error occurs during the installation... report back here.

type exit (press enter)

press Ctrl + Alt + F7
login
if WinKey + Space does not make gnome-do appear on screen after login

press Ctrl + Alt + F1
login
type gnome-do &
press Ctrl + Alt + F7
press WinKey + Space
type an application's name to run it.

---

### Post by hellomoto on 2008-12-23
i think this is a bug with xfce as I had the exact same problem happen to me.

I had a crash and then on restart I had no pannels and could not re-addd them.

The only way I corrected it was by reinstalling. I know its a last resort but thats the only thing I could do to fix it.

See the following links with people with the same problem!
[http://ubuntuforums.org/showthread.php?t=322159]("http://ubuntuforums.org/showthread.php?t=322159")
[http://ubuntuforums.org/showthread.php?t=579576]("http://ubuntuforums.org/showthread.php?t=579576")
[https://bugs.launchpad.net/xfce4-panel/+bug/53897]("https://bugs.launchpad.net/xfce4-panel/+bug/53897")

---

### Post by fooman on 2008-12-23
have you tried pressing alt-f2 and see if that brings up a "run program" box?

if it does....try typing the following into it and pressing "run":

```
xfce4-panel &
```

see if that works.

---

### Post by Mr.Kuchinawa on 2008-12-23
> **fooman said:**
> have you tried pressing alt-f2 and see if that brings up a "run program" box?

if it does....try typing the following into it and pressing "run":

```
xfce4-panel &
```

see if that works.

My hero! Thanks a bunch!

---


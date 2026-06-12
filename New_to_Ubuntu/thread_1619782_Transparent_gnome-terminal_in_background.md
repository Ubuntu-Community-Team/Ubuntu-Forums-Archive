---
title: "Transparent gnome-terminal in background"
date: 2010-11-12
forum: New to Ubuntu
---

### Post by neonl on 2010-11-12
Hey everyone

I know there are some topics on this point yet, but none of them is recent and I guess the problems I'm having are due to the software has changed a bit since they were created.

I want to start (or more) gnome-terminal(s) instance(s) with GNOME startup, on Ubuntu 10.10, with some transparency-shading, and a specified geometry and positioning. I tried creating a profile with no menu bar and no scroll bar, launching it at gnome's startup and using devilspie, but all I can do is disabling the window's decorations. Size and position are, apparently, ignored.

Is there any other way to do this (I've heard compiz-fusion does the job, just don't know how). I'd appreciate some help.

Thanks! :)

---

### Post by toekneewood on 2010-11-12
This might help a little
```

from the menu select: System, Preferences, Start-up applications, OPTIONS

and tick the option (Remember Currently Running Applications)

```

The other option might be **compiz**

You could try some other terminals
tilda
Guake
Yakuake
or even Terminator 


Terminator is a little project to produce an efficient way of filling a large area of screen space with terminals.

Terminator is a little project to produce an efficient way of filling a large area of screen space with terminals.
[http://www.tenshu.net/terminator/]("http://www.tenshu.net/terminator/")

---

### Post by toekneewood on 2010-11-12
most of the terminal settings are also found in
```

cat /usr/share/vte/termcap/xterm

```

---

### Post by itisbasi on 2010-11-12
Why not use a terminal screenlet?

---

### Post by julio_cortez on 2010-11-12
I used compiz plus a new gnome-terminal profile (the way explained in the links below) and it works the way it should:
[http://ubuntuforums.org/showthread.php?t=535098](http://ubuntuforums.org/showthread.php?t=535098)

I followed those instructions quite easily, I don't think there's something to change from them to adapt them to the new compiz.. But I'll have a look when I'm back home.

---

### Post by toekneewood on 2010-11-12
**LOOKS LIKE [http://www.tenshu.net/terminator/](http://www.tenshu.net/terminator/) COULD COME CLOSE**

---

### Post by toekneewood on 2010-11-12
It also looks like the terminator can remember layout.  This is the template of the config file
```


twood ~ $ cat ~/.config/terminator/config 
[global_config]
  enabled_plugins = CustomCommandsMenu, ActivityWatch, TerminalShot, LaunchpadCodeURLHandler, APTURLHandler, LaunchpadBugURLHandler
[keybindings]
[profiles]
  [[default]]
[layouts]
  [[default]]
    [[[child1]]]
      type = Terminal
      parent = window0
      profile = default
    [[[window0]]]
      type = Window
      parent = ""
  [[Multi]]
    [[[child0]]]
      position = 0:25
      type = Window
      order = 0
      parent = ""
      size = 1920, 1124
    [[[terminal1]]]
      profile = default
      command = ""
      type = Terminal
      order = 0
      parent = child0
[plugins]

```

---


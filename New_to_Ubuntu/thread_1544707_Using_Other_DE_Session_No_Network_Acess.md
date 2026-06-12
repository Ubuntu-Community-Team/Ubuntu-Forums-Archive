---
title: "Using Other DE Session No Network Acess"
date: 2010-08-02
forum: New to Ubuntu
---

### Post by mamamia88 on 2010-08-02
when i select fluxbox or lxde session when loggin in I can't acess the internet.  is there a way to fix this?

---

### Post by jtarin on 2010-08-02
How do you connect to the internet? Place the command in one of two places.
There should be a .xinitrc file in /root or /home/username.

You can also use a script named "startup" which should be in /root/.fluxbox or /home/username/.fluxbox

Just edit either /root/.fluxbox/startup or /root/.xinitrc to start any apps you want

heres example /root/.fluxbox/startup
```
#!/bin/sh
#
# fluxbox startup-script:
#
# Lines starting with a '#' are ignored.

# Change your keymap:
xmodmap "/root/.Xmodmap"

# Applications you want to run with fluxbox.
# MAKE SURE THAT APPS THAT KEEP RUNNING HAVE AN ''&'' AT THE END.
#
# unclutter -idle 2 &
# wmnd &
# wmsmixer -w &
# idesk &

# And last but not least we start fluxbox.
# Because it is the last app you have to run it with ''exec'' before it.

exec fluxbox
# or if you want to keep a log:
# exec fluxbox -log "/root/.fluxbox/log"
```

does that help??

---

### Post by jimrz on 2010-08-02
> **mamamia88 said:**
> when i select fluxbox or lxde session when loggin in I can't acess the internet.  is there a way to fix this?

if you are able to connect from a gnome session, for fluxbox add 
```
nm-applet &
```

to ~/.fluxbox/startup ...which will cause network manager to fire up @ startup

---


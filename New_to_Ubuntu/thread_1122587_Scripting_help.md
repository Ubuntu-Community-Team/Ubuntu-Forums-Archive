---
title: "Scripting help"
date: 2009-04-11
forum: New to Ubuntu
---

### Post by Nagrom_17 on 2009-04-11
Hello, I have just started messing around in Ubuntu and found the desktop effect very cool. A few days ago I found this python script that makes all minimized windows unminimized then calls the scale effect for compiz, I would like to do something like that to play around with my own little tweaks but I cannot find out how to 'activate' a compiz plugin. Can someone Help me?

---

### Post by lfaraone on 2009-04-11
Have you read through the source of the python script?

---

### Post by Nagrom_17 on 2009-04-11
yes but I cant seem to find where he is accessing. heres the code which I think opens the scale plugin
```
 ************************************************************************
    # Launch the Scale plugin of the Compiz window manager
    # ************************************************************************
    # Aside from ESCaping out, Scale will exit upon one of three actions:
    #    Selecting a tasklist window, closing the last tasklist window, or
    #    showing the desktop
    # Activating a non-tasklist window in this script ensures that Scale will
    #    always generate an 'active_window_changed' event when it exits
    # Launch Scale
    scale=os.popen('dbus-send --type=method_call ' +
    '--dest=org.freedesktop.compiz ' +
    # ------------------------------------------------------------------------
    # Update this line as desired according to instructions at the top of this
    #    script
    '/org/freedesktop/compiz/scale/allscreens/initiate_key ' 
    # ------------------------------------------------------------------------
    + ' org.freedesktop.compiz.activate string:\'root\' ' +
    'int32:`xwininfo -root | grep id: | awk \'{ print $4 }\'`')
```
correct me if i am wrong but it looks like it is going to /org/freedesktop/ect. but I cannot find the org folder anywhere let alone the others.

---

### Post by unutbu on 2009-04-11
From what you posted, the command is 
```

dbus-send --type=method_call --dest=org.freedesktop.compiz /org/freedesktop/compiz/scale/allscreens/initiate_key  org.freedesktop.compiz.activate string:'root' int32:`xwininfo -root | grep id: | awk '{ print $4 }'`
```

---

### Post by Nagrom_17 on 2009-04-11
yes but how can I find out how to use it for commands other then scale? I would rather learn how the other guy got to that command and be able to explore around then just copy off him without learning how its working.

---

### Post by alphacrucis2 on 2009-04-11
> **Nagrom_17 said:**
> yes but how can I find out how to use it for commands other then scale? I would rather learn how the other guy got to that command and be able to explore around then just copy off him without learning how its working.


Some info here:

[http://wiki.compiz-fusion.org/Plugins/Dbus]("http://wiki.compiz-fusion.org/Plugins/Dbus")

---

### Post by Nagrom_17 on 2009-04-11
wow thanks a bunch! Ill be sure to read that and bookmark it for future reference so I don't have to ask so many questions in the future. :D

---


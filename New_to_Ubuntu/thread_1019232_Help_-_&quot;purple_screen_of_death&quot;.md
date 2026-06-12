---
title: "Help - &quot;purple screen of death&quot;?"
date: 2008-12-22
forum: New to Ubuntu
---

### Post by shatteredmindofbob on 2008-12-22
So, this has now happened to me two nights in a row. I'm using Firefox and suddenly the screen goes blank then comes back with purple lines all over the place and sometimes the X shaped cursor you see when Ubuntu first boots up appears but it doesn't respond. 

First I tried restarting X with Ctrl-Alt-Backspace but got no response, then tried Ctrl-Alt-Delete but only hear a system beep. 

Hitting the power button makes the screen go black and I see a few orange pixels, I think it's a TINY version of the Ubuntu shut-down screen before it shuts down. 

Um...what is going on and more importantly, how do I stop it from happening? 

Thanks. 

(my hardware is a Dell Inspiron, generic. Intel mobile graphics chip and whatnot.)

---

### Post by nhasian on 2008-12-22
can you give us more detail on what video adaptor your using?  in a terminal type

```
lshw -C display
```

---

### Post by shatteredmindofbob on 2008-12-22
> **nhasian said:**
> can you give us more detail on what video adaptor your using?  in a terminal type

```
lshw -C display
```

display:0 UNCLAIMED   
       description: VGA compatible controller
       product: Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0

---

### Post by nkri on 2008-12-22
Did you change any Compiz settings recently, such activating plugins?  If so, try disabling them...activating a plugin that isn't entirely stable can screw with the whole system:(

Good luck!
-nkri

---

### Post by shatteredmindofbob on 2008-12-22
> **nkri said:**
> Did you change any Compiz settings recently, such activating plugins?  If so, try disabling them...activating a plugin that isn't entirely stable can screw with the whole system:(

Good luck!
-nkri

The only change I've made recently was disabling "Legacy Fullscreen Support" since it was causing a host of problems (speaking of plug-ins that aren't stable...)

---

### Post by IamReck on 2008-12-23
You could disable compiz, or take a look at this thread.

[http://ubuntuforums.org/showthread.php?t=324928](http://ubuntuforums.org/showthread.php?t=324928)

Its old, but it may work.

---

### Post by shatteredmindofbob on 2008-12-23
> **IamReck said:**
> You could disable compiz, or take a look at this thread.

[http://ubuntuforums.org/showthread.php?t=324928](http://ubuntuforums.org/showthread.php?t=324928)

Its old, but it may work.

I'm going through it, but Compiz has worked for months and this computer without any issues. 

Of course, the most annoying part of this is that I have no idea how to reproduce it, it just happens.

---

### Post by shatteredmindofbob on 2008-12-23
Any other ideas as to what could be causing it/how to prevent it?

---

### Post by markbuntu on 2008-12-23
Check your connections.

---


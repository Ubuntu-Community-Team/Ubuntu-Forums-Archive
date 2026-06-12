---
title: "VNC broke after update"
date: 2006-07-17
forum: Networking &amp; Wireless
---

### Post by nomad311 on 2006-07-17
I had VNC up and running with persistant sessions ...I even made it through the last update problems by adding the -fp option ...which has since been fixed

Just friday I let Ubuntu install the like 50 updates and SURPRISE when I tried to log onto VNC this weekend it wasnt working

Heres the log file:
```

Xvnc: error while loading shared libraries: libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory
vncconfig: error while loading shared libraries: libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory

(gnome-session:13440): Gtk-WARNING **: cannot open display:

```

I checked and libstdc++6 is installed ...so how do I fix it?!

Thanks for the help
-nomad311

---

### Post by nomad311 on 2006-07-18
well i dunno how to fix this ...but i think the problem lies in the fact that libc was upgraded (i think because i see its version 2.36).

anyway if youve become dependent on vnc ...like me you can downgrade to v3 (vncserver on apt-get ...remove vnc4server first) and it works ...slowly from time to time and vncconfig still wont work so you cant copy/paste from your remot machine ...but hey it works for now

please lemme know if you get it working

BTW ...are there ppl out there who have the lastest update and restarted your comp with vnc 4 still working???

laters
-nomad311

---


---
title: "Maximum resolution not showing"
date: 2011-01-20
forum: New to Ubuntu
---

### Post by HyyDeff on 2011-01-20
I am brand new to Ubuntu. So forgive me if I sound dumb. But I just installed Ubuntu and the maximum screen resolution I'm getting is 1280x720. When I used windows it was 1400x900 or something like that. I installed the nVDIA drivers and now my screen sits low and to the left. I cant even see the whole screen. Can someone help me out? Thanks.


-Derek

---

### Post by cariboo on 2011-01-21
You may have to open a terminal and type:

```
sudo nvidia-xconfig
```

to create a new /etc/X11/xorg.conf. Once the file has been created, reboot and then open System->Administration->Nvidia X Server Settngs to set your resolution.

---


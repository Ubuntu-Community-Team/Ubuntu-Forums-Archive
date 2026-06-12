---
title: "Wifi selection icon disappeared"
date: 2009-05-02
forum: New to Ubuntu
---

### Post by Ninja13at on 2009-05-02
hey i just put my hp mininote to hibernate and the wifi selection icon at the upper righthand part of the desktop has disappeared.  i looked at the "add to panel" selections but i cant find it there.  can anyone tell me how to get it back there.  thanks a bunch

---

### Post by jbrown96 on 2009-05-02
It's part of a system notification area, so there's no way to add it to the panel. 

You can try several ways to fix it.

1) Alt+F2 then ```
nm-applet
```

2) In a terminal ```
sudo /etc/init.d/ restart
``` Once you type /etc/inti.d/ press tab a couple times and you should get a listing of what's in the directory. You are looking for network-manager. I just can't remember the capitialization and hypheniation of it. 

3) Same as above but restart networking. 

4) Restart should fix it.

---

### Post by Ninja13at on 2009-05-02
wait, just fixed my own problem.
add "notification" to panel

---


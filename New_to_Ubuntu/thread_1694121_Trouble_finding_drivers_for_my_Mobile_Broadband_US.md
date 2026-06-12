---
title: "Trouble finding drivers for my Mobile Broadband USB"
date: 2011-02-23
forum: New to Ubuntu
---

### Post by anonymous anarchist on 2011-02-23
:confused: Ok, I've set my laptop up with a dual boot - Ubuntu 10/Windows 7 but I'm having trouble with my ZTE CDMA Technologies MSM USB Mobile Broadband. The trouble is it came with a CD with drivers for Windows and Mac but not Linux systems!!!! :( I've looked around but to be honest get bloody confused, can anyone help me out? I really want to be able to access the net from Ubuntu as it'll really help with using online tutorials etc. I would just get a line connection but right now I'm moving around so much I'm not in one place long enough to get it sorted let alone use it, so that's just an option. If anyone can think of a better place to post this thread please suggest also as I'm new to forums also.......I know, late start! :confused:

---

### Post by cariboo on 2011-02-24
Just after you have plugged your device in. open a terminal and type:

```
dmesg | tail -n 15
```

and paste the output in you next post.

---


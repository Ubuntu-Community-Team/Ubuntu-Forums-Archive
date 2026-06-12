---
title: "Multiple Instances of nm-applet"
date: 2007-11-04
forum: Networking &amp; Wireless
---

### Post by gj15987 on 2007-11-04
When I installed Gutsy I had only 1 instance of nm-applet running. However, for some reason I can't remember I ran 2 more instances of it, and now every time I log in I get 3 instances of it running.

Any help would be appreciated.

Thanks.

---

### Post by gj15987 on 2007-11-04
Sorry...almost immediately after posting this I figured it out.

I just removed all lines similar to the following from the file ~/.gnome2/session.

```
Program=nm-applet
CurrentDirectory=/usr/bin
CloneCommand=nm-applet --sm-config-prefix /nm-applet-sKwU13/ 
RestartCommand=nm-applet --sm-config-prefix /nm-applet-sKwU13/ --sm
```

---


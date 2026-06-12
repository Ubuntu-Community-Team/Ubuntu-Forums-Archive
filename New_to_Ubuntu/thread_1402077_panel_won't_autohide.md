---
title: "panel won't autohide"
date: 2010-02-08
forum: New to Ubuntu
---

### Post by hsartoris on 2010-02-08
I have a computer with a small screen, and as a result it's important for me to be able to see the whole screen. I set the panel to autohide, and it does, at first, and then it just stops working. I can use the panel, but I can't make it hide, and the rest of my applications think it's hidden, so they get slightly masked by the panel.

---

### Post by umoreno_89 on 2010-02-08
please post on what method you used to make the panel go into autohide.

To autohide panel
- type gconf-editor in terminal
-go to apps->panel->top_panel_screen
       .tick the "autohide" box

doing this made my panel hide without any of the problems you're experiencing.

---

### Post by /etc/tmp on 2010-09-18
Hi, I have exactly the same problem, did you or anyone got it to stop-"stop autohiding"?

The problem isn't to activate the feature, I did that on gconf many times, but as hsartoris said, it works perfectly for sometime, then suddenly it stops hiding. 

You can see it's a bug because the opened windows don't shring back to fit the screen as they do when autohide isn't activated.

When autohide freezes like this I try to toggle in gconf but still this does nothing. Hibernate doesn't too.

One time I saw this happening when I ctrl+alt+tabbed to "Top expanded edge panel", if anyone wants to try it.

Any help would be greatly appreciated, because on the netbook some applications are very large for 1220x600, and any spare pixels help.

---


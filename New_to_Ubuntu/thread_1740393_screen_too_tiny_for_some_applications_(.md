---
title: "screen too tiny for some applications :("
date: 2011-04-27
forum: New to Ubuntu
---

### Post by guilleme on 2011-04-27
Hi, here's the problem: 
When I start some applications, like the evolution mail setup assistant or transmageddon video re-encoder (among others), I just can't reach the bottom panel, where you approve or disapprove the actions to be taken, so I can't get my email account synced or convert any videos.
The computer is an acer netbook from their aspire one series, and I'm using the normal, only gnome, interface, with no unity, I got tired of it.
The screen is 10.1 inches diagonally, with a 1024 x 600 Px resolution.
Thanks very much to everyone.
Ps-Maybe there's just a way to resize your apps to a more comfortable size, (?:)).

---

### Post by 5149.5 on 2011-04-27
I put the following line of code into startup applications. You can try it out in terminal to see how it works for you before putting it in startup apps.

```
xrandr --output LVDS1 --fb 1024x768 --panning 1024x768
```

---

### Post by StarZtorm on 2011-04-27
Just hold down Alt, click and drag the window with your mouse.

---

### Post by stinkeye on 2011-04-27
Reducing the size of your window title and application fonts can help.
Appearance preferences > fonts.

---

### Post by guilleme on 2011-04-28
Thanks, that made it admissible.
 The "holding Alt" method didn't solve it, but I can now work with the applications.
Thanks to everyone!

---


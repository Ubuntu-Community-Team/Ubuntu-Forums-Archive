---
title: "Gnome-Clock customization"
date: 2009-12-15
forum: New to Ubuntu
---

### Post by arvigeus on 2009-12-15
Hi, I need help with customizing gnome-clock. I want it to show time in left and int the right: day above and date below. Closest thing I managed to do is this:
```
gconftool-2 -t str -s /apps/panel/applets/clock_screen0/prefs/custom_format "<span weight='bold'> %H:%M </span><sub><span rise='3000' weight='normal' size='smaller' color='#606060'> %A </span></sub>%n<sup><span weight='normal' size='smaller' color='#606060'>             %d %b %y</span></sup>"

```
but it doesn't look pretty good. Any tips?

---

### Post by jerrrys on 2009-12-16
may find some ideas here

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=Clock+customization&as_qdr=all&sa=Google+Search&lang=en#1058](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=Clock+customization&as_qdr=all&sa=Google+Search&lang=en#1058)

---

### Post by ankspo71 on 2009-12-16
Hi,
Try here: [http://www.omgubuntu.co.uk/2009/11/gnome-panel-clock-themes.html](http://www.omgubuntu.co.uk/2009/11/gnome-panel-clock-themes.html) . I got these to work rather easily. They also might give you some ideas. Hope this helps.

---


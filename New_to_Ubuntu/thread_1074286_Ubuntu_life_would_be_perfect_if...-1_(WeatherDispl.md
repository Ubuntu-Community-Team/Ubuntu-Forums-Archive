---
title: "Ubuntu life would be perfect if...-1 (WeatherDisplay)"
date: 2009-02-19
forum: New to Ubuntu
---

### Post by dunbrokin on 2009-02-19
I have a weather station attached to my PC. I  use a program called WeatherDisplay to show the information on my PC.

What I do to start the program is a) go into the workspace on the right b) go cd weatherdisplay in a terminal c) go ./WeatherD in the terminal.

That all works fine.

However, if I go to the session Manager and point it at WeatherD, I get the software starting but no live date flows through (it does show historic data). What am I doing wrong.

Please help my ubuntu life become perfect by suggesting solutions...:)

Thanks

---

### Post by mister_pink on 2009-02-19
Maybe it starts up before the station is ready. Try changing the line in sessions to something like
```

sleep 30; ~/weatherdisplay/WeatherD;

```

---

### Post by dunbrokin on 2009-02-19
Thanks, I will try that.....any idea how I can get it to open in the right hand pane instead of the left one?

---

### Post by dunbrokin on 2009-02-19
Nope, that did not work....exactly same result as before.

---


---
title: "screensaver"
date: 2009-01-23
forum: New to Ubuntu
---

### Post by hellomoto on 2009-01-23
I have a screen saver (a picture slide show) that I like to come on after 1 min of no computer activity.

When I watch BBC i player it still comes on which is very irritating. So I have to change the settings to 2 hourly via the screen saver GUI, so i can watch BBC i player.

To save myself time in the future is the terminal command anyone knows which I can use to toggle the screen saver on/off?

I could then set this to an alias in .bashrc to save myself time when watching BBC i player/ doing Uni work.

Thank you in advance!

---

### Post by hellomoto on 2009-01-23
I did a bit of research and have been able to toggle the screen saver via the command line with the following commands:

Turn off:
```

gnome-screensaver-command -i

```

Turn on:
```

killall gnome-screensaver-command -i
Kill gnome-screensav(6886) ? (y/N) y

```

However i don't really like/know what I am doing with the kill command. So if anyone can surgest better commands please let me know.

---


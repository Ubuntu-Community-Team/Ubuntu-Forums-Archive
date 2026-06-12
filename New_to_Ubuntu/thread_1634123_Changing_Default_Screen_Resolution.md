---
title: "Changing Default Screen Resolution"
date: 2010-11-30
forum: New to Ubuntu
---

### Post by mr_luksom on 2010-11-30
I seem to have a bit of an odd problem with screen resolution in X.

I can set it to what I want without issues ( 1360x768 ), however when a program changes the mode for its own usage (say ZSNES), it changes it back to a different resolution than what it found it as ( 1024x768 ).

Is there some sort of 'Default' resolution that may be causing this?

---

### Post by mr_luksom on 2010-12-12
I'm using a script as a workaround to get the correct resolution on exit.

```

zsnes $1
xrandr --output VGA1 --mode 1360x768@59.9

```

---


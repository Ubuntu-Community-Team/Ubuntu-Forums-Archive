---
title: "Keyboard sensitivity"
date: 2009-03-09
forum: New to Ubuntu
---

### Post by Fox McCloud on 2009-03-09
I have a problem with holding down a key and how long it takes for that press to repeat. It doesn't take very long, iiif I hold ffffor a split second to long I get 4-5 extra character too much. I tired to turn it down but it makes no difference. I am using a laptop keyboard, haven't tried it on anything else.

---

### Post by unutbu on 2009-03-09
I suppose you went to System>Pref>Keyboard and turned up the Delay and reduced the Speed.

Since that did not work, try opening a terminal and typing
```

xset r rate 500 30
```

The first number (500) specifies the delay (in milliseconds) before  autorepeat  starts and the second number (30) specifies the repeat rate (also in milliseconds). 

Fiddle with the numbers until you get it as you like it.

If that works we can add this command to System>Pref>Sessions so it is set at login-time.

---

### Post by Fox McCloud on 2009-03-09
Thank you for the reply. That worked out. :)

---

### Post by rfruth on 2009-03-09
I have the same problem with my desktop(s) - tnx !

---


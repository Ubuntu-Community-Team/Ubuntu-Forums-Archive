---
title: "Karmic Sleep Timer"
date: 2010-03-16
forum: New to Ubuntu
---

### Post by Cuco3 on 2010-03-16
Is there a way to manually set the sleep timer rather than the values given in the drop down menu? 10 minutes is too short and 30 minutes is too long.

---

### Post by natravis on 2010-03-16
From [this video]("http://www.youtube.com/watch?v=IvWtJWe73is"), it would appear that an app called "gshutdown" does what you would like. If this works, please mark your thread solved.

---

### Post by Cuco3 on 2010-03-16
Actually, I meant the idle timer for Sleep functions.

[IMG]http://uppix.net/e/7/6/f2e2d301d2a896a94461593f87bd2.png[/IMG]

---

### Post by Cuco3 on 2010-03-17
anyone?

---

### Post by lotharmat on 2010-03-17
I think you can manipulate the settings by hitting Alt+F2 and typing 

```
gconf-editor
```

Then navigate to the following key. Apps --> gnome-power-manager

Then, have a play with the values.

---

### Post by Cuco3 on 2010-03-17
Thank you man, sounds like what I'm looking for! :)

I'll do some testing before I mark the thread solved.

---

### Post by lotharmat on 2010-03-17
Hope it works!

---

### Post by Cuco3 on 2010-03-18
It did work. Thank you!

---


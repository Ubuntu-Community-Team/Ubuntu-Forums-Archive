---
title: "how do i change the run level at boot up?"
date: 2009-05-28
forum: New to Ubuntu
---

### Post by bradfordmayne on 2009-05-28
could someone tell me how to change the run level at boot?  I want to see everything starting and then go to the gui logon.

---

### Post by QIII on 2009-05-28
> **bradfordmayne said:**
> could someone tell me how to change the run level at boot?  I want to see everything starting and then go to the gui logon.

Not entirely sure what you mean . . .

Do you want to see the scrolling tty display of everything?

---

### Post by bradfordmayne on 2009-05-29
yeah i think that's what it's called tty.  I'm tryin to do this from memory but I just came home from prison and I kinda forgot some stuff.

---

### Post by nandemonai on 2009-05-29
You don't need to change the run level, what you're talking about is turning off the splash screen right?

Easiest way is to install startup manager:

```
sudo apt-get install startupmanager
```

Then from the System menu -> Administration -> Startup-manager and uncheck 'Show splash' then exit the app. Reboot and you should see a verbose boot ;)

---

### Post by bradfordmayne on 2009-05-29
Thanks!

---


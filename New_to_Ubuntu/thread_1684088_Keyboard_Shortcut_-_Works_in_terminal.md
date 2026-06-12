---
title: "Keyboard Shortcut - Works in terminal"
date: 2011-02-08
forum: New to Ubuntu
---

### Post by NeoDevin on 2011-02-08
I'm trying to set up a keyboard shortcut to start synergy client, so I can activate it when I'm at work.

From the terminal if I type (using the proper IP address):

```
synergyc -f 123.123.123.12
```

Synergy starts as expected, and runs perfectly.

I go to System > Preferences > Keyboard Shortcuts, click "Add" and copy the above code directly into the "Command" field, and then set the shortcut to Ctrl+Alt+S.  Pressing this key combination does nothing.

How do I make this work?

---

### Post by Tyggna on 2011-02-08
> **NeoDevin said:**
> 
How do I make this work?
Been a while since I've done this--but I believe I had to make a desktop launcher for it, and set the shortcut combination there.

---

### Post by NeoDevin on 2011-02-08
> **Tyggna said:**
> Been a while since I've done this--but I believe I had to make a desktop launcher for it, and set the shortcut combination there.

Ok, I created the launcher, and it seems to work properly.  How do I set the shortcut combination there?

Thanks

---

### Post by Tyggna on 2011-02-08
Again--this is years old information I'm offering, but I think you just right click on it and it's under properties.

---

### Post by NeoDevin on 2011-02-08
> **Tyggna said:**
> Again--this is years old information I'm offering, but I think you just right click on it and it's under properties.

Can't find anything under properties to make a keyboard shortcut for it.

---

### Post by Old *ix Geek on 2011-02-08
> **NeoDevin said:**
> I go to System > Preferences > Keyboard Shortcuts, click "Add" and copy the above code directly into the "Command" field, and then set the shortcut to Ctrl+Alt+S.  Pressing this key combination does nothing.

How do I make this work?It works fine for me in KDE--but NOT with the key combo you're trying.

I just installed synergy, added a menu item for it, and assigned [ctrl][alt][s] as above. That didn't work, as that key combo does other things [at least in KDE].

So I changed it to [ctrl][shift][s] and it works fine.

---

### Post by NeoDevin on 2011-02-09
> **Old *ix Geek said:**
> It works fine for me in KDE--but NOT with the key combo you're trying.

I just installed synergy, added a menu item for it, and assigned [ctrl][alt][s] as above. That didn't work, as that key combo does other things [at least in KDE].

So I changed it to [ctrl][shift][s] and it works fine.

Shift+Ctrl+S works.  Odd that Ctrl+Alt+S doesn't, it did in 9.04.

Thanks.

---


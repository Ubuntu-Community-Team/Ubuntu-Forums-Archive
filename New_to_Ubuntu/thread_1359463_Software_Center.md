---
title: "Software Center"
date: 2009-12-19
forum: New to Ubuntu
---

### Post by darkeye123 on 2009-12-19
Hello everyone.

I want to remove the ubuntu software center because I never use it... mostly I just use sudo apt-get install [something] in the terminal.

Is it safe to remove this? Do I need it for anything?
How would I remove it?

One other thing I would like to remove is the update-notifier. I also update my computer via the command line, and I never forget to do so regularly. Can I remove this too?

Can I disable the graphical login? I still want to be able to boot up into LXDE but I don't need the graphical login either.

I'm running Ubuntu 9.10.

---

### Post by jerrrys on 2009-12-19
right click on the menu bar then go to edit menu and see if its there.  im not on ubuntu right now so i do not know for sure...

---

### Post by Cheesemill on 2009-12-19
> **darkeye123 said:**
> Hello everyone.

I want to remove the ubuntu software center because I never use it... mostly I just use sudo apt-get install [something] in the terminal.

Is it safe to remove this? Do I need it for anything?
How would I remove it?

```
sudo apt-get remove softwarecenter
```

Or you could just remove the menu entry.

---

### Post by Chesamo on 2009-12-19
Remove the update notifier:
```
sudo apt-get purge update-manager
```
I'm not sure about the graphical login... you could try```
sudo apt-get purge gdm
```but that may break a lot of things.

---


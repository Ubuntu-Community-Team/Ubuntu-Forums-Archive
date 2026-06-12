---
title: "Login Screen does not load"
date: 2010-01-21
forum: New to Ubuntu
---

### Post by Neuton on 2010-01-21
I've got Windows 7 and Ubuntu dual booted on my Dell Inspiron 15n. Both used to boot fine, and Windows 7 still works. The other day I tried to go back into Ubuntu to do some programming and it seems to load fine. I even get the Ubuntu progress bar but following that I get my mouse and no way to login. I can move the mouse, but I can't click on anything. It's almost like it's slow to load but nothing happens.

I tried to do the recovery mode option and I can drop into the terminal and look around. But when I tried running "xterm" it said no display was specified. That was just a guess, and I'm not really sure what I'm doing in the command line (beyond basic terminal unix stuff - navigation and directory junk) but I guess I'm looking for a way to start up the window system.

Are there any programs I should run in the command line or anything I can do to fix this situation?

---

### Post by USB_NL on 2010-01-21
you have tried this?

```
startx
```

and it didn't work?

---

### Post by Neuton on 2010-01-21
No, it doesn't work. If I go into Ubuntu normally (not recovery mode) the login doesn't show up. So I press ctrl + alt + F1 and try startx and it says "Fatal Server error: Server is already active for display 0".

If I go into recovery mode, drop into the root shell prompt and try startx I get the blank screen, with mouse showing, except I can't use the mouse. No login this way either.

It seems like it's not the window system starting that's the problem after all. I have no idea what the problem is. Any ideas?

PS is it at all possible that my Windows 7 partition is somehow writing over into my Ubuntu partition? Or is that impossible? (Thinking of buffer overload in website attacks...)

---


---
title: "Applications &amp; Files n' Folders Disappeared"
date: 2011-07-25
forum: New to Ubuntu
---

### Post by Pyprokid on 2011-07-25
Hello, again guys :)

Back with another issue, suddenly while configuring Compiz, the "Applications" and "Files and Folders" disappeared from the launcher... how do I get these back? :confused:

Help is appreciated.

- Matt :popcorn:

---

### Post by ubudog on 2011-07-25
Try this:
Go to System>Preferences>Appearance>Visual Effects tab, and set it to "None".  Also, run this command in a terminal (Applications>Accessories>Terminal)

```
killall gnome-panel
```
(Don't worry, it automatically restarts.)

---

### Post by Pyprokid on 2011-07-25
I tried the terminal command and I got: 

```

gnome-panel: no process found

```

---

### Post by ubudog on 2011-07-25
> **Pyprokid said:**
> I tried the terminal command and I got: 

```

gnome-panel: no process found

```

Oh, duh, you're using Unity.  Did disabling Compiz do anything?

---

### Post by Pyprokid on 2011-07-25
I found the problem ^_^ thanks for you assistance.

---

### Post by ubudog on 2011-07-25
> **Pyprokid said:**
> I found the problem ^_^ thanks for you assistance.

No problem.  How did you fix it?  Also, I recommend setting the thread to SOLVED.

---

### Post by Pyprokid on 2011-07-25
Really it was a stupid problem, :D
All it needed was rebooted. :KS

And I will, sorry forgot. :D
Once again, thanks a lot for your concern,

- Matt  :popcorn:

---

### Post by ubudog on 2011-07-25
> **Pyprokid said:**
> Really it was a stupid problem, :D
All it needed was rebooted. :KS

And I will, sorry forgot. :D
Once again, thanks a lot for your concern,

- Matt  :popcorn:

LOL.  I hate when that happens... 

Well, glad you got it fixed.  :-)

---


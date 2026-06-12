---
title: "Check how keyboard keys are mapped"
date: 2009-06-20
forum: New to Ubuntu
---

### Post by FormatSeize on 2009-06-20
How can I check how my keyboard keys are mapped? 
One of the letters on my keyboard stopped working after installation, and I don't know if it just went out, or I messed with something that I should not have. When I'm in terminal, and I press it, the cursor flashes white but a letter "cue";) doesn't appear.
And when I press it *now* the cursor just disappears. So I think I'm getting a "reaction" out of it, but I want to see if I can map it to something else or if I can see if I did something myself.

---

### Post by FormatSeize on 2009-06-20
I restarted my computer, then went into the BIOS. In there the key that doesn't work worked just fine. So it does work, it just doesn't work inside of Ubuntu. Any help would be appreciated.

---

### Post by FreewheelinFrank on 2009-06-20
Run this in a terminal:

```
xev
```

It will show you the output of each key stroke (and mouse movement).

---

### Post by mike555 on 2009-06-20
You could install "xkeycaps" , then just type " sudo xkeycaps " in terminal.........that will tell you know what keys are maped to , and let you change them (like capslock to L.shift).

---

### Post by FormatSeize on 2009-06-21
Hi,
The "Q" is not giving an output at all when pushed alone, but I do have Q. How do I install xkeycaps?

---

### Post by mike555 on 2009-06-21
xkeycaps in in your package manager, just type it in the search box.

---


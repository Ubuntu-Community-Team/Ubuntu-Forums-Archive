---
title: "[SOLVED] sudo chmod 755 file.txt, &amp;quot;permission denied&amp;quot;... WHAT?"
date: 2008-12-19
forum: New to Ubuntu
---

### Post by jmd9qs on 2008-12-19
hey,

i recently downloaded an e-book, and it came in a .rar file... the file contains a copy of the book in .txt, .pdf, and .lit. i only want the .pdf, so i:

```
sudo rm 'Baxter, Steven - Titan.lit'

```
and got this error:

```
rm: cannot remove `Baxter, Steven - Titan.lit': Permission denied
```

i thought this was very curious, maybe the permissions needed changing?:

> sudo chmod 755 'Baxter, Steven - Titan.lit'

and it gave me this:

> chmod: cannot access `Baxter, Steven - Titan.lit': Permission denied

What the heck? even if i log in as root it says the same thing... am i missing something here?

---

### Post by taurus on 2008-12-19
What's the output of this command, assuming you are in the same directory where that file is?

```
ls -la
```

---

### Post by jmd9qs on 2008-12-20
the output was:

```
-rwx------ 1 jmd9qs root 2029319 2008-12-19 21:39 Baxter, Stephen - Titan.lit
```

---

### Post by jmd9qs on 2008-12-20
the really weird thing is i CAN delete it via the gui no problem

---

### Post by logos34 on 2008-12-20
what about using tab:

sudo rm Baxter,[hit TAB key to complete]...

---

### Post by hardyn on 2008-12-20
double quote " i think?

---

### Post by igknighted on 2008-12-20
> **hardyn said:**
> double quote " i think?

In both it looked like there was a tick mark (`) for the first quote, and a single quote (') for the second.  The tick could be throwing it off, because it would be expecting another command there (as in, apt-get install linux-generic-`uname -r`)?

---


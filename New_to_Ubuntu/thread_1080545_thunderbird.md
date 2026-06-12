---
title: "thunderbird"
date: 2009-02-25
forum: New to Ubuntu
---

### Post by cowboy7305 on 2009-02-25
I was trying to load thunderbird email 
and i got this message 
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
iam using 8.1 
running from Applications
Add remove

---

### Post by opscure on 2009-02-25
open a terminal and type
```
sudo dpkg --configure -a
```

then try and install it again.

---

### Post by avtolle on 2009-02-25
Open the terminal (Applications>Accessories>Terminal) and type```
sudo dpkg --configure -a
```

---

### Post by llamabr on 2009-02-25
Did you try:

```
sudo dpkg --configure -a
```?

That was the instruction that it gave you.

I wonder why, if ubuntu knows what command is necessary to fix, it doesn't just run it, rather than telling you to do so.

---

### Post by Hobgoblin on 2009-02-25
> **llamabr said:**
> Did you try:

```
sudo dpkg --configure -a
```?

That was the instruction that it gave you.

I wonder why, if ubuntu knows what command is necessary to fix, it doesn't just run it, rather than telling you to do so.

Because it is not Windows and doesn't think it knows better than it's master. ;)

---

### Post by jakupl on 2009-02-25
> **Hobgoblin said:**
> Because it is not Windows and doesn't think it knows better than it's master. ;)

Well it could immediately ask you if you want it to run it. "y" or "n", and force the user to make a decision.
There are surprisingly many that don't understand that prompt. Probably because nobody really reads error prompts. Or because it is badly formulated for people that aren't used to the terminal... "run? run how?... I could manually run *...tecnobabble...*"

---


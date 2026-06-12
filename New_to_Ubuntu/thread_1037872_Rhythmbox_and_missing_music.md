---
title: "Rhythmbox and missing music?"
date: 2009-01-12
forum: New to Ubuntu
---

### Post by GeordieJedi on 2009-01-12
Hi all, I hope your all well.

My question is this.

Ive just installed 8.10, and set my usual progs up.

I ran Rhythmbox, added my music. (which resides on my external HDD).

Now the confusing thing is, Rhythmbox tells my there's 11,464 tracks available in the library.
 However if I use the properties dialogue on my music folder it tells me there's 18,353 files!!

(Now taking into account there's more folders to contain the music folders...
I still think there's a massive discrepancy).

Does anyone have any ideas on this?

Thanks in advance.

---

### Post by aheckler on 2009-01-12
Plug your drive in, open a terminal, "cd" into your music directory, and run:

```
ls -1R | grep -i .*.mp3 | wc -l
```

to count the exact number of mp3 files you have in all folders/subfolders.

---


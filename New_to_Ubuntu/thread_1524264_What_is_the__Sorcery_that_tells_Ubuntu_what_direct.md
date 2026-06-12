---
title: "What is the  Sorcery that tells Ubuntu what directory to launch a program?"
date: 2010-07-05
forum: New to Ubuntu
---

### Post by Grandma_DOG on 2010-07-05
Let us say I have a package called 'bp-instant-oilspill' and I have it in a directory /(username)/eviloilcompany/this-file-launches-ap.

If I were to go the command line in any directory and type 'pb-instant-oilspill'
How does Ubuntu know to find the executable in /(username)/eviloilcompany/ and to execute 'this-file-launches-ap'?


I'm having a hell of a time with ffmpeg, mainly because I tried to compile a version and broke ****. Now if I type ffmpeg Ubuntu looks at the wrong directory and can't launch ffmpeg.

So the sorcery crossreference magic needs some fixing. How do I find it?

---

### Post by CharlesA on 2010-07-05
It has a database of the locations of most of the programs. It is updated as they are installed.

I believe you can use the command:

```
sudo updatedb
```

---

### Post by Grandma_DOG on 2010-07-05
> **CharlesA said:**
> It has a database of the locations of most of the programs. It is updated as they are installed.

I believe you can use the command:

```
sudo updatedb
```

Yep, that fixed it.
Strange side effect. I had two terminals opened. In both I typed 'whereis ffmpeg', one terminal gave the correct answer, one the old (wrong) location.  So I closed both, and reopened a terminal, then it gave the correct location.  odd odd.

thanks!

---


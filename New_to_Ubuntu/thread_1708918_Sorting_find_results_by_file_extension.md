---
title: "Sorting find results by file extension"
date: 2011-03-17
forum: New to Ubuntu
---

### Post by gidra on 2011-03-17
I managed to get some good results using find. Now I want to sort the results with directories appearing first and then sort by file extension (as in windows). Can someone please help me out in doing this ? Thanks

---

### Post by _0R10N on 2011-03-17
Honestly, I don't think that feature would be possible on Linux, since it doesn't manage the file extension concept. You can always write a smal script to do so...

---

### Post by gidra on 2011-03-17
Can I at least, in a straight-forward manner, exclude folder from my find results and sort by file extension ?

---

### Post by gidra on 2011-03-17
Managed to get a workaround with something like this:


 find . -print|xargs ls -l -X

---

### Post by _0R10N on 2011-03-17
> **gidra said:**
> Managed to get a workaround with something like this:


 find . -print|xargs ls -l -X


I have tried your work around, but I'm having folders listed, only. I think you could use a combination of ls, grep and sort, though.

---

### Post by gidra on 2011-03-19
I didn't continue to dwell on the problem, yet if you figure it out please let me know the solution. Thanks for your input

---


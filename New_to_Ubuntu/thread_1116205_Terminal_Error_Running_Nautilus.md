---
title: "Terminal Error Running Nautilus"
date: 2009-04-04
forum: New to Ubuntu
---

### Post by Penguin Guy on 2009-04-04
When I try to run Nautilus with root privileges, this is what happens:

**[gksu]**
```

$ gksu nautilus
Initializing nautilus-dropbox 0.6.1

--- Hash table keys for warning below:
--> file:///root

(nautilus:6070): Eel-WARNING **: "nautilus-metafile.c: metafiles" hash table still has 1 element at quit time (keys above)
SSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSS
(nautilus:6070): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 1 element at quit time
Shutting down dropbox extension

```

**[sudo]**
```

$ sudo nautilus
[sudo] password for josh: 
Initializing nautilus-dropbox 0.6.1

** (nautilus:6113): WARNING **: Unable to add monitor: Operation not supported

--- Hash table keys for warning below:
--> file:///root

(nautilus:6113): Eel-WARNING **: "nautilus-metafile.c: metafiles" hash table still has 1 element at quit time (keys above)

(nautilus:6113): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 1 element at quit time
Shutting down dropbox extension

```

This does not appear to have any negative effect, I am simply curious as to what it means. Anyone know what could be causing this?

---

### Post by ronocdh on 2009-04-06
Why run Nautilus as root? I would create the directory as a normal user (simply with **mkdir**, *not* with **sudo mkdir**) and then use **chmod** to adjust permissions.

---

### Post by Penguin Guy on 2009-04-06
You have a point, thanks - but there are other things you would want to use root for; such as editing system files. So I am still looking for a solution.

---

### Post by llamabr on 2009-04-06
Are you trying to do this locally, or remotely?  What's that 

```
Unable to add monitor: Operation not supported
```

Error doing there?

---

### Post by Penguin Guy on 2009-04-06
That's what I'm asking *you*. And; no, I'm not trying to do this remotely.

---

### Post by Penguin Guy on 2009-09-04
Bump: Still looking for an answer.

---


---
title: "How do I sequentially rename files from the command line?"
date: 2009-05-09
forum: New to Ubuntu
---

### Post by zorblek on 2009-05-09
I am sure there are probably several ways to do this, but I just can't figure it out. I have several files that are part of a series, and I want to batch rename them so that they are numbered in order. For example:
"File A" "File B" "File C" -> "File 1" "File 2" "File 3"
I've tried for loops and find -exec with no luck. Any suggestions would be greatly appreciated.

---

### Post by unutbu on 2009-05-09
This prints the commands that will be run, but does not rename anything:
```
N=1; ls -tr -1 | while read file; do echo "mv $file File $N"; N=$((N+1)); done
```


When you are satisfied that the above renamings are correct, run this:
```
N=1; ls -tr -1 | while read file; do mv "$file" "File $N"; N=$((N+1)); done
```

---

### Post by zorblek on 2009-05-09
Thanks! That did the trick.

---


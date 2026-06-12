---
title: "defining a path as a variable in bash script"
date: 2011-02-26
forum: New to Ubuntu
---

### Post by cryptoxic on 2011-02-26
Dear friends,
  I ran into a problem while writing a simple bash script.
This is what I have so far:
```

#!/bin/bash
echo "input a path where the songs are:"
read path;

cd $path;
ls;

```
I think it is self explanatory, as to what the script does. The problem arises, when the path has a directory with spaces in it. So for example if I type in:
```
~/old music
``` or even ```
~/old\ music
``` with a backslash for space, it just reads ```
~/old
``` and therefore can't find the directory. What is the right syntax for that?
Thanks in advance.

---

### Post by TeoBigusGeekus on 2011-02-26
Make it
```
#!/bin/bash
echo "input a path where the songs are:"
read path;

cd "$path";
ls;
```

---


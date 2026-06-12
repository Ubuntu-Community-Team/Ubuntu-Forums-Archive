---
title: "Why this command doesn't work?"
date: 2010-06-14
forum: New to Ubuntu
---

### Post by DarknessMonk on 2010-06-14
I was expecting this to open a file on GEdit... 
```
find -iname \*postgres-\* | head -1 | gedit
```

---

### Post by epicoder on 2010-06-14
You are piping the filename to gedit's STDIN, which it then silently ignores. You want to use command substitution:
```
gedit $(find -iname \*postgres-\* | head -1)
```

---

### Post by kaibob on 2010-06-14
I agree with the answer by sh228. But, just as a point of information, you can get your command line to work with the use of xargs. For example, the following command did work for me:

```
find -iname testfile.txt | head -1 | xargs gedit
```

---

### Post by ibuclaw on 2010-06-14
You could also use "quotation marks" to loose the \backslashes.
```
find -iname "*postgres-*" | head -1 | xargs gedit
```

Regards

---

### Post by DarknessMonk on 2010-06-14
Thanks for the quick and effective answers :)

---


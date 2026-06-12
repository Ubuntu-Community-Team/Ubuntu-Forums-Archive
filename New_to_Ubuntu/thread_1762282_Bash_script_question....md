---
title: "Bash script question..."
date: 2011-05-19
forum: New to Ubuntu
---

### Post by HighCommander540 on 2011-05-19
Hello, I have a question about this bash script. I want to know how it does what it does, because I don't see how.

```
find /dir/ -type f -exec chmod ugo-x {} \;
find /dir/ -type d -exec chmod ugo+rx {} \;
```

How does it change the files that is finds? I must have something to do with the "{} \", but I don't know how it does I. Could someone explain, I don't want to use stuff without knowing how it works?

---

### Post by HermanAB on 2011-05-19
Howdy,

Just read the 'find' man page!

The -d looks for directories and the -f looks for files.

The braces {} are replaced by the file name it finds and then it executes the chmod command on that file, in a loop, till it runs out of files.

---

### Post by HighCommander540 on 2011-05-22
> **HermanAB said:**
> Howdy,

Just read the 'find' man page!

The -d looks for directories and the -f looks for files.

The braces {} are replaced by the file name it finds and then it executes the chmod command on that file, in a loop, till it runs out of files.

Lol, thanks. I thought it was something that was in all of batch not a feature of find. Thanks dude!

---


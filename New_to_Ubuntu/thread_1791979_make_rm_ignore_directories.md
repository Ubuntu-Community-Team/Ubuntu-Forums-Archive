---
title: "make rm ignore directories"
date: 2011-06-27
forum: New to Ubuntu
---

### Post by bettaproger on 2011-06-27
title says it all, i want to find out how to run rm from terminal, and have it ignore, as in don't delete directories in the current directory, but also not prompt and finish the rm job. 

example

in /home/username/example
run rm *
there exists /home/username/example/otherthing

rm should clear /home/username/example but leave /home/username/example/otherthing alone

---

### Post by dFlyer on 2011-06-27
From a terminal:

rm -rf /Test/Test1/Test2/*

This will clean out Test2 of all files.

---

### Post by m_duck on 2011-06-27
> **dFlyer said:**
> This will clean out Test2 of all files.It will also remove any subdirectories of the folder 'Test2'. The only way I can think to do it is with the ***find*** command, using the ***-type f*** option, so it only looks for files and not directories, with the final addition of an ***-exec*** switch with which to use ***rm***.

I would post an example but I don't know the proper format for find, but a quick search will soon provide an answer.

---

### Post by nothingspecial on 2011-06-27
If you mean, you don't want the errors, send them to /dev/null

```
rm * 2> /dev/null
```

---


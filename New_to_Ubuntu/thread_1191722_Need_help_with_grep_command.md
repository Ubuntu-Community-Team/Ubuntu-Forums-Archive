---
title: "Need help with grep command"
date: 2009-06-19
forum: New to Ubuntu
---

### Post by Temporary Saint on 2009-06-19
Did a search for this and couldn't find a helpful result.

This should be easy for you CLI mavens.  I just want to search  for a string of text within a text file.  I've tried **grep -ir "text"** from the "/" directory because I want the entire disk to be searched.  Nothing seems to happen when I run it.  No disk activity, no screen output after waiting 2-3 minutes.  Just a blinking cursor.  Do I need to wait longer?  Is the command in the correct format?  I have referred to the man page for the command, btw, but no examples are given that would help me.

Thanks,
Steve

---

### Post by Mornedhel on 2009-06-19
The following greps "YourString" on all text files in your filesystem :

```
find / -type f -iname "*.txt" -exec grep --color=auto "YourString" '{}' \;
```

Judging by the line you tried, grep was waiting for you to enter a list of files from the standard input, which is the default behavior when no file names are given.

---


---
title: "Using grep recursively with a filename pattern?"
date: 2009-11-14
forum: New to Ubuntu
---

### Post by rob86 on 2009-11-14
I know how to use grep recursively, grep -r 'hello world' . 
The thing I can't figure out is, how can I search recursively, and make it only check certain files? For example, all .py files. 

I've tried a bunch of things, like grep -r 'string' ./*.py but it didn't work right. Typing grep -r 'string' *.py only seaches the current dir.

---

### Post by diesch on 2009-11-14
The filename patterns are reslved by the shell, grep sees only the filenames they resolve to.

At least zsh supports the pattern ```
**/*.py
``` for "all *.py *files in the current dir and its subdirs" (but I don't know about bash).

Or you can use find:

```
find . -name \*.py -exec grep foo "{}" + ;
```

---

### Post by falconindy on 2009-11-14
You're using the proper flag (-r) for searching with grep recursively. You only need to specify *.py for the search term at the end of the command. Are you using double quotes or single quotes? There **is** a difference, particularly if you're using a pattern.

---

### Post by kaibob on 2009-11-14
I know next to nothing about grep but decided to run some tests and couldn't get things to work as desired by the OP without the find command. I googled a bit and found the following, which does seem to work.

```
grep -r --include=<pattern> <string> <directory>
```

[http://www.joeldare.com/wiki/linux:grep_recursively_through_single_file_extension](http://www.joeldare.com/wiki/linux:grep_recursively_through_single_file_extension)

The include option is shown in the grep man page as

> --include=GLOB. Search only files whose base name matches GLOB (using wildcard matching as described under --exclude).

---


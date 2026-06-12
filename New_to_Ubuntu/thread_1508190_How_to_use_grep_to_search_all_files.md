---
title: "How to use grep to search all files?"
date: 2010-06-12
forum: New to Ubuntu
---

### Post by zozza on 2010-06-12
Hi, 

I am trying to figure out how to do the following using grep.

I want to search for a word in all files in all directories.

I have tried many options but either grep does not find words in files I know exist or it gets stuck e.g. when using -r.  

What should I do?

Thanks.

---

### Post by marshmallow1304 on 2010-06-12
[http://www.linuxforums.org/forum/linux-newbie/3163-find-word-file.html](http://www.linuxforums.org/forum/linux-newbie/3163-find-word-file.html)

---

### Post by quadproc on 2010-06-12
> **zozza said:**
> ...
I want to search for a word in all files in all directories.

I have tried many options but either grep does not find words in files I know exist or it gets stuck e.g. when using -r.  

marshmallow1304 offered an excellent suggestion, and I wanted to add that you might be having a problem with upper/lower case not matching your grep string.  If you need to ignore case then use the -i option with grep.

quadproc

---

### Post by bashologist on 2010-06-12
Grep has a recursive option but I prefer using find since it gives me more options. Remember to use the -i switch with grep if your search is case-insensitive.

```
find "path" -type f -exec grep -i "pattern" {} +
```

Or you could use finds -iname option to find just txt files for example.

```
find "path" -type f -iname "*.txt" -exec grep -i "pattern" {} +
```

Or what if you only want to go 3 directories under the specified directory you could use the -maxdepth option of find for such a task.

---


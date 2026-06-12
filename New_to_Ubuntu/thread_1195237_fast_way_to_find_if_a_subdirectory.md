---
title: "fast way to find if a subdirectory"
date: 2009-06-23
forum: New to Ubuntu
---

### Post by coverslide on 2009-06-23
I am making a PHP application that traverses the directory structure, and to get a list of directories I run this command:

```
find $folder_name/ -maxdepth 1 -type d | sort
```this is fine, but for each directory found I want to detect whether there are more directories below it, so I could simply repeat this line

```
find $new_folder_name/* -maxdepth 1 -type d
```and just detect any output

Now this works for small directories, but I have plenty of large directories with many many more folders inside, so when my app runs this command on those directories, it becomes exponentially slow, when all I need is to detect whether just one exists. Is there a way to have find just stop at the first result?

---

### Post by Celauran on 2009-06-23
Might it not be faster to use something like this?

```
ls -l $dir | grep ^d
```

---


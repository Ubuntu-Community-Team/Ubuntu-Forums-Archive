---
title: "Command to remove all files except &quot;not.txt&quot;"
date: 2009-08-14
forum: New to Ubuntu
---

### Post by colau on 2009-08-14
Hi,
What's the command to remove all files except the file named "not.txt".

---

### Post by aeiah on 2009-08-14
[http://linux-journal.blogspot.com/2005/04/delete-all-files-in-directroy-except.html](http://linux-journal.blogspot.com/2005/04/delete-all-files-in-directroy-except.html)

---

### Post by colau on 2009-08-14
> **aeiah said:**
> [http://linux-journal.blogspot.com/2005/04/delete-all-files-in-directroy-except.html](http://linux-journal.blogspot.com/2005/04/delete-all-files-in-directroy-except.html)
Thank you.
```

rm $(ls * | grep -v '^my_file$') 

```
What does it mean by "$"?(why is it used)

---

### Post by sdennie on 2009-08-14
A slightly more readable way is to use find:

```

find . ! -name "not.txt"

```

If that gives you the files you want, then just add -delete:

```

find . ! -name "not.txt" -delete

```

Careful that this also finds files in subdirectories.  To prevent that, use maxdepth:

```

find . -maxdepth 1 ! -name "not.txt" -delete

```

Edit:

And, in the command you posted, ^my_file$ is a regular expression that means "begin line my_file end line".

---

### Post by colau on 2009-08-14
> **sdennie said:**
> A slightly more readable way is to use find:

```

find . ! -name "not.txt"

```

If that gives you the files you want, then just add -delete:

```

find . ! -name "not.txt" -delete

```

Careful that this also finds files in subdirectories.  To prevent that, use maxdepth:

```

find . -maxdepth 1 ! -name "not.txt" -delete

```

Edit:

And, in the command you posted, ^my_file$ is a regular expression that means "begin line my_file end line".
Thanks.

---


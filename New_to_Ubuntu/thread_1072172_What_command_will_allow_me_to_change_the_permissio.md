---
title: "What command will allow me to change the permission of ALL files/folder"
date: 2009-02-17
forum: New to Ubuntu
---

### Post by esender on 2009-02-17
What command will allow me to change the permission of ALL files/folders within a specified directory?

I am setting up a local virtualbox with linux on it and I randomly come up with file permission issues when running a CMS like Drupal.

I'd like to just give full permissions (777) to everything in that folder. I realize that is very insecure, but since this virtual box is in its own isolated world, I am not too worried. I am mostly looking to do debugging.

I know Filezilla can do this when I access something via FTP, so I am sure there is some command that will loop through every element within a directory and changes its permissions...


FYI: I am running Ubuntu 8.10 32bit.

Thanks!

---

### Post by stumbleUpon on 2009-02-17
> **esender said:**
> What command will allow me to change the permission of ALL files/folders within a specified directory?

I am setting up a local virtualbox with linux on it and I randomly come up with file permission issues when running a CMS like Drupal.

I'd like to just give full permissions (777) to everything in that folder. I realize that is very insecure, but since this virtual box is in its own isolated world, I am not too worried. I am mostly looking to do debugging.

I know Filezilla can do this when I access something via FTP, so I am sure there is some command that will loop through every element within a directory and changes its permissions...


FYI: I am running Ubuntu 8.10 32bit.

Thanks!


chmod -R ugo+rwx whateverDirectoryYouWant/


see also the documentation in the man files

man chmod

---

### Post by spikoley on 2009-02-17
Chmod is the command you are looking for.  The -R switch makes it recursive.  You would be better off to trouble shoot the issue instead of taking this short cut.  Use it as a learning exercise.  

> man chmod
              -R, --recursive
              change files and directories recursively


```
chmod -R 777 /path/to/folder
```

---


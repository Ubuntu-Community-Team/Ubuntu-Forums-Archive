---
title: "Question about &quot;ls&quot; command"
date: 2010-08-05
forum: New to Ubuntu
---

### Post by redfox1160 on 2010-08-05
When I type in the following code:
```
ls -lh
```
I get the following output:
```

total 1.1G
-rwxrwxrwx 1 eric eric 368M 2010-08-03 20:47 diggnation.wmv
-rwxrwxrwx 1 eric eric  79M 2010-07-28 17:08 filmriot.wmv
-rwxrwxrwx 1 eric eric 135M 2010-07-29 21:19 hak5.wmv
-rw-r--r-- 1 eric eric  133 2010-08-05 04:00 lastdiggnation.txt
-rw-r--r-- 1 eric eric  132 2010-07-30 05:00 lastfilmriot.txt
-rw-r--r-- 1 eric eric  131 2010-08-05 04:00 lasthak5.txt
-rw-r--r-- 1 eric eric  138 2010-07-30 05:00 lastscamschool.txt
-rw-r--r-- 1 eric eric  132 2010-07-30 05:00 lasttekzilla.txt
drwxr-xr-x 2 eric eric 4.0K 2010-08-03 12:01 saved
-rwxrwxrwx 1 eric eric 148M 2010-07-27 20:52 scamschool.wmv
-rwxrwxrwx 1 eric eric 316M 2010-07-29 22:22 tekzilla.wmv

```
"saved" is a directory, and in it is a file that is 190M. Why is the directory listed as 4.0K when there is a 190M file in it? Is the file size just in reference to the directory, not what is in it? Thanks

---

### Post by darolu on 2010-08-05
Yeah it won't tell you the size of the files in it, just the size of the directory itself.

One thing that may help you is to include the -R option, it will list all the files within subdirectories as well. For example:
```
:~$ ls -lhR files/
files/:
total 8.0K
drwxr-xr-x 2 dan dan 4.0K 2010-08-05 20:42 files1
drwxr-xr-x 2 dan dan 4.0K 2010-08-05 20:42 files2

files/files1:
total 0
-rw-r--r-- 1 dan dan 0 2010-08-05 20:42 file1
-rw-r--r-- 1 dan dan 0 2010-08-05 20:42 file2
-rw-r--r-- 1 dan dan 0 2010-08-05 20:42 file3
-rw-r--r-- 1 dan dan 0 2010-08-05 20:42 file4

files/files2:
total 0
-rw-r--r-- 1 dan dan 0 2010-08-05 20:42 file1
-rw-r--r-- 1 dan dan 0 2010-08-05 20:42 file2
-rw-r--r-- 1 dan dan 0 2010-08-05 20:42 file3
-rw-r--r-- 1 dan dan 0 2010-08-05 20:42 file4
```

---

### Post by redfox1160 on 2010-08-05
> **darolu said:**
> Yeah it won't tell you the size of the files in it, just the size of the directory itself.

One thing that may help you is to include the -R option, it will list all the files within subdirectories as well. For example:
```
:~$ ls -lhR files/
files/:
total 8.0K
drwxr-xr-x 2 dan dan 4.0K 2010-08-05 20:42 files1
drwxr-xr-x 2 dan dan 4.0K 2010-08-05 20:42 files2

files/files1:
total 0
-rw-r--r-- 1 dan dan 0 2010-08-05 20:42 file1
-rw-r--r-- 1 dan dan 0 2010-08-05 20:42 file2
-rw-r--r-- 1 dan dan 0 2010-08-05 20:42 file3
-rw-r--r-- 1 dan dan 0 2010-08-05 20:42 file4

files/files2:
total 0
-rw-r--r-- 1 dan dan 0 2010-08-05 20:42 file1
-rw-r--r-- 1 dan dan 0 2010-08-05 20:42 file2
-rw-r--r-- 1 dan dan 0 2010-08-05 20:42 file3
-rw-r--r-- 1 dan dan 0 2010-08-05 20:42 file4
```

Thanks, I forgot about that one

---


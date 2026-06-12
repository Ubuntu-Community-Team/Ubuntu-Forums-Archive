---
title: "how to remove particular files (say *.exe) from a folder, recursively"
date: 2009-02-23
forum: New to Ubuntu
---

### Post by munishvit on 2009-02-23
Aim: to delete all the files ending with .exe from a particular folder, recursively
Obstacles: sub-directoris or files may contain white spaces (specially spaces). 
Test directory: /home/username/test
directory contain following:
 test/dir1 (directory)
 test/new dir (directory)
 test/new.exe (file)
 test/new file.exe (file)
 test/dir1/new1.exe (file)
 test/dir1/new1 file.exe (file)
 test/new dir/new2.exe (file)
 test/new dir/new2 file.exe (file)

$ find /home/username/test -name '*.exe' -print > /home/username/file1
this creates a file (named 'file1') with a list of files, that ends with .exe, of 'test' directory. 
$ rm -vi `cat /home/username/file1`
Now this doesn't deleted 4 out of 6 exe files, probably because their pathname contain 'spaces'.
I tried 'find' command with -print0 and -ls, but in vain.

Then i edited file1 myself by adding quotes around pathnames of all the six files, even then it doesn't work.
Plz help.

---

### Post by zika on 2009-02-23
test/new dir/new2 file.exe (file) -> test/new dir/new2\ file.exe (file) ?

---

### Post by geirha on 2009-02-23
This will delete all .exe files, including the ones with spaces.
```
find /home/username/test -name '*.exe' -delete
```

EDIT:
or:
```
find /home/username/test -name '*.exe' -print0 | xargs -0 -- rm -vi
```

---

### Post by sisco311 on 2009-02-23
or:
```
find /path/to/dir -name "*.exe" -exec rm -vi {} \;
```

EDIT :)

or:
```
find ... > filename
IFS=$'\t\n'
rm -vi $(cat filename)
IFS=$' \t\n'
```

---

### Post by munishvit on 2009-02-27
it works...thnx
but there is still one doubt left
why i got the above problem indicates that some metacharacters, while taking input from text file, loose there meaning (such as single quotes, double quotes, backslash, I/O redirection operators). but some work (such as forward slash, % sign). 
Could you categorize metacharacter upon their behaviour. this would help one to avoid mistakes while taking input from files.

---


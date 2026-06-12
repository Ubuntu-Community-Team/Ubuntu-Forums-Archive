---
title: "Mass file movment"
date: 2009-01-22
forum: New to Ubuntu
---

### Post by eatberrys on 2009-01-22
there are a ton of files i need to sort based on words in there title how would i do this?
 if i sort them by running ```
ls | grep (/files/ im /looking /to /move)
``` how can i move them by useing the list form that output ?

---

### Post by vhegos on 2009-01-22
How about putting the list into a file?

```
ls | grep (what you are looking for) > move_list.txt
```

Now just write a little script that loops through the list and moves the files.

---

### Post by handydan918 on 2009-01-22
if all of the filenames have enough in common to use wildcards with ls, you should be able to just do a batch rename with mv. Just be sure to test your patterns with ls first....

---

### Post by DezSP on 2009-01-22
Simple bash code to do this:

```
for i in $( ls | grep stuff_to_find ); do mv $1 /our/new/home/; done
```

Best check it works on a few test files first, just in case you get the grep statement wrong or something. :P

---

### Post by eatberrys on 2009-01-22
Thanks every one =P i have 511 files to sort :P

*edit*i spoke to early it didnt work the bash code u gave me dosnt work correctly it runs the ls and but it trys to run the move with out the ls output and thinks what i want the ouput dirctory to be is the input so it says mv: missing destination file operand.

---


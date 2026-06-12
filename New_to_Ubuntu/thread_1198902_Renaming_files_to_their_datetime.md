---
title: "Renaming files to their date/time"
date: 2009-06-28
forum: New to Ubuntu
---

### Post by timandjulz on 2009-06-28
I have files named like FILE_00123.MOV distributed throughout my hard drive.  I want to recurse and rename them to YYYY-MM-DD_00123.MOV based on the file's date/time attribute.

The problem is the paths have spaces.  How can I rename them?

I tried something like this but the spaces throw it off:
```
find . -type f -name 'FILE_*.MOV' -printf 'mv %p %TY-%Tm-%Td_%f\0' | xargs -0

```
Thanks,
Tim

---

### Post by rraj.be on 2009-06-28
For space you can use %20 symbol.

for example

/media/New Volume 

can be written as

/media/New%20Volume.

---

### Post by timandjulz on 2009-06-28
rraj.be, that doesn't solve the challenge.

How can I recurse /home/Movies and rename 'FILE*.MOV' to yyyy-mm-dd_hhmmss.mov allowing for spaces in paths?

Thanks,
Tim

---

### Post by yabbadabbadont on 2009-06-28
First, use double quotes instead of single quotes.
Second, use double quotes to quote all filename/path variables.

I'm not sure if your original command is correct, but here is a version of it using my suggested changes:
```
find . -type f -name "FILE_*.MOV" -printf "mv \"%p\" \"%TY-%Tm-%Td_%f\"\0" | xargs -0
```

---


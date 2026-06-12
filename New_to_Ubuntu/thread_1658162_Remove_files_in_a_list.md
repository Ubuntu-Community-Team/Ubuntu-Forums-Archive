---
title: "Remove files in a list"
date: 2011-01-02
forum: New to Ubuntu
---

### Post by paddy100 on 2011-01-02
I have a file called, files.txt with the following

/home/username/file1
/home/username/file2
/home/username/file3 ...... etc (several hundred)

some of the file names have spaces in them. How can I write a script to delete these files. all file names are absolute.

I have tried to use ```
xargs rm < files.txt
``` but this throws an error if the file name has a space in it. Could I use FOR IN DO or something else??

Thanks in advance.
Paddy

---

### Post by sisco311 on 2011-01-02
Try something like:
```
while read file; do
  rm -v -- "$file"
done < files.txt
```

Be careful, test it first!

---

### Post by paddy100 on 2011-01-02
sisco, thanks works like a treat.
Thank you

---


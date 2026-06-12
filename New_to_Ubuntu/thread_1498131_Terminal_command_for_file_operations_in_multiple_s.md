---
title: "Terminal command for file operations in multiple sub-directories"
date: 2010-05-31
forum: New to Ubuntu
---

### Post by thunderdan on 2010-05-31
I want to run ufraw-batch to convert all my raw files to jpg. These files are located in various directories in my Pictures directory. I know I can navigate to a particular directory and do this:

```
daniel@daniel-desktop:~/Pictures/2010/05/05$ ufraw-batch --out-type=jpg --compression=100 *.nef *.NEF

```

That will convert all the .nef and .NEF files to .jpg in that directory, but I will have to go to each directory individually and do that command several times over. What I would like to do is navigate to the Pictures directory and type one command to perform this action in all the sub-directories without navigating to each one individually. I know there is a simple way to do this, but I just don't know what it is. Can you tell me what it is?

---

### Post by kyncani on 2010-05-31
Provided the directory names do not contain spaces or exotic characters :
for d in /fully/qualified/directory/name/with/photos/ -type d; do cd "$d/" && ufraw-batch --out-type=jpg --compression=100 *.nef *.NEF; done

---

### Post by thunderdan on 2010-05-31
> **kyncani said:**
> Provided the directory names do not contain spaces or exotic characters :
for d in /fully/qualified/directory/name/with/photos/ -type d; do cd "$d/" && ufraw-batch --out-type=jpg --compression=100 *.nef *.NEF; done

So if I navigate to the Pictures directory, then type this:

```
for d in /2010/ -type d; do cd "$d/" && ufraw-batch --out-type=jpg --compression=100 *.nef *.NEF
```

It will go to each directory in the 2010 directory and each directory in those directories and perform the ufraw-batch command?

---

### Post by kyncani on 2010-05-31
No, the little small code I gave you needs a fully qualified path name, that means not /2010/ but for example /home/thunder/Desktop/Pictures/NEW/2010/

Edit: and you'all also receive some error messages for each subdirectory that does not contain any .nef and .NEF files but no worry.

---


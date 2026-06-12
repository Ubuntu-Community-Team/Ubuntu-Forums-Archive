---
title: "Split"
date: 2010-11-05
forum: New to Ubuntu
---

### Post by {LCD}STELIOS on 2010-11-05
If I try to split a 67.3GB file into 2GB chunks using the split command what will happen the unequal part left over?
 Will I end up with 33x2 GB files and one smaller one? 
 Also is this the command that I would use?
 split 2048G largefile smallerfile    :confused:
Thanks.

---

### Post by sikander3786 on 2010-11-05
Not a perfet answer but you can see the man pages and sort it out yourself before someone else responds.

```
man split
```

---

### Post by {LCD}STELIOS on 2010-11-05
Yeah I have read the man page and I am still not sure. I don't want to try splitting it without knowing the exact syntax as I  don't have the space to make a back up copy of this file.
Cheers.

---

### Post by aeiah on 2010-11-05
i suggest practicing on a file that's smaller. create a 67mb file and try and split it into 2mb chunks, then rebuild it and compare the two. since you can't afford any mistakes, this should give you some confidence.

make the 67mb file:
```

dd if=/dev/zero of=67mb.file bs=1M count=67

```

read the file with cat, and pipe it to split:
```

cat 67mb.file | split -d -b 2m - 67mb.file.

```

this will create 67mb.file.01, 67mb.file.02 etc.

to reassemble, we'll use cat again:
```

cat 67mb.file.* > reassembled_67mb.file

```

then compare the two files with md5:
```

md5sum 67mb.file reassembled_67mb.file

```

hopefully you understand the process with enough confidence to do this to your big file, even though you havent the space reassemble.

edit: as described below, you can check the integrity of the split files against the original

---

### Post by aeiah on 2010-11-05
good news everyone.

you can easily just pipe your split files into md5sum to compare it with the original, so you'd only need enough space for the original file + all the splitfiles, and not a 3rd copy.

```

cat 67mb.file.* | md5sum

```

and compare it to:
```

md5sum 67mb.file

```

---

### Post by {LCD}STELIOS on 2010-11-05
Wow that is great. Really helpful thanks.

---


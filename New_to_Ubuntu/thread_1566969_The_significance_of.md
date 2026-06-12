---
title: "The significance of /"
date: 2010-09-03
forum: New to Ubuntu
---

### Post by donescamillo on 2010-09-03
Hi,

If I write:
**cd dir1/dir2**
I will go in dir2 which is under dir1 which is under the current dir

If I write:
** cd dir1/dir2/**  // note the forward slash at the end
the result is the same.

Now I had to edit the exports file recently (doing some lab) and found out that when I specify a directory like that:
**dir1/dir2/dir3**
something does not work (a nfs server in my case)
whereas when I write:
**dir1/dir2/dir3/**
it works fine.

What is teh significance of the slash at the end?

Thank you

---

### Post by migs73 on 2010-09-03
I am no expert by a long way, but I would think it is because the first to commands are change DIRECTORY commands, therefore the directory name is the end of the command, so the / can be ignored. In the other commands you are putting something IN the directory, so therefore the / is required, as what you are doing is at the sub-directory level.

As I said I am no expert and someone will no doubt blow me out of the water with the real answer:o

---

### Post by anewguy on 2010-09-03
It's also possible that in the 2nd case somewhere inside the workings of things that use the exports file it is making a file path with the string, which would cause it not to work without the trailing "/".  For example:

say there is a file "x" that is supposed to be in the subdirectory dir1/dir2/dir3.  If it is building a path to "x", the result would be dir1/dir2/dir3x, which would mean subdirectory dir3x, not file "x" in dir3.  So when you add the trailing "/", the built path would be dir1/dir2/dir3/x, which indeed points to file "x" in dir3.

Dave

---

### Post by CharlesA on 2010-09-03
Adding the "/" at the end means that the destination is a directory and not a file.

So if you copy a file like so:

```
cp ~/somefile dir1
```

and "dir1" isn't a directory, it'll copy somefile to the file dir1.

---

### Post by anewguy on 2010-09-04
Yes, but again if some process is using the file to build absolute paths, the trailing "/" would be required or it will think the built path is a directory, not a file.

Dave

---


---
title: "TAR Trouble"
date: 2010-11-04
forum: New to Ubuntu
---

### Post by mistypotato on 2010-11-04
Hi,

Trying to use the TAR command for listing files in a Tarballl "--list like this....

sudo tar --list --file=documents_11042010_1.tar  > documents_11042010_1.tar.txt

**Problem:**
The resulting list is incomplete.

Anyone know how to get a "Complete" list of Tarball contents to a text file?

---

### Post by bioterror on 2010-11-04
> **mistypotato said:**
> Hi,

Trying to use the TAR command for listing files in a Tarballl "--list like this....

sudo tar --list --file=documents_11042010_1.tar  > documents_11042010_1.tar.txt

**Problem:**
The resulting list is incomplete.

Anyone know how to get a "Complete" list of Tarball contents to a text file?


I did ```
tar -tvf package.tar |less
``` and it worked.

So you should do it like this
```
tar -tvf foobar.tar > list.txt

```

---

### Post by mistypotato on 2010-11-04
Do you think that will work if the resulting file is 4.5MB >

The problem seems to be related to **gedit** and **gvim** not being able to load 4.5MB of text.

But I'm not certain that's the problem.  Just seems like it.

---

### Post by mistypotato on 2010-11-05
No matter what text reader I use, I can never get the entire contents of the TAR in the list.

I checked and double checked the TAR file....it has quite a few files that simply are NOT added to the output list :confused:

Very odd

When I find the solution / cause I'll post it

---

### Post by bioterror on 2010-11-05
> **mistypotato said:**
> No matter what text reader I use, I can never get the entire contents of the TAR in the list.

I checked and double checked the TAR file....it has quite a few files that simply are NOT added to the output list :confused:

Very odd

When I find the solution / cause I'll post it

Something wrong with the tarball or with the filenames or something.

If you extract the tarball, do you get the files out of it?

---

### Post by mistypotato on 2010-11-05
As a test, I extracted one file from a folder that does not get listed and it extracted normally and as expected.

Could permissions have anything to do with the listing of the contents ?

---


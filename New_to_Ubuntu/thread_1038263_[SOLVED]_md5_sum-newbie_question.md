---
title: "[SOLVED] md5 sum-newbie question"
date: 2009-01-12
forum: New to Ubuntu
---

### Post by minsf on 2009-01-12
someone gave me a link to the source file and md5 sum.
i had no idea what to do with this.
i googled and found a nice md5sum article on wikipedia.
so after downloading the source from the link, say to source.tar.bz2, i ran
```
md5sum source.tar.bz2>source.md5
```
and i got a number/code that is identical to the given number.
[COLOR="Red"]my question is[/COLOR] how to do the reverse? i tried to save the given md5 sum as a text file given.md5 and then i ran "md5sum -c given.md5" with no success. 
so how should i create the given.md5 file so that "md5sum -c given.md5" checks source.tar.bz2?

---

### Post by ibuclaw on 2009-01-12
Is the md5sum file in the same directory as the source.tar.bz2 file?

What you are doing is right, by the way.

Example Usage:
```

iain@fredbuntu:~$ echo "hello" > testfile
iain@fredbuntu:~$ md5sum testfile > testfile.md5
iain@fredbuntu:~$ md5sum -c testfile.md5
**testfile: OK**
iain@fredbuntu:~$ echo "goodbye" > testfile
iain@fredbuntu:~$ md5sum -c testfile.md5 
[B]testfile: FAILED
md5sum: WARNING: 1 of 1 computed checksum did NOT match[/B]
iain@fredbuntu:~$ 

```

Regards
Iain

---

### Post by jmontelius on 2009-01-12
I'm not sure what you want to do here. The input file to md5sum -c is a file containing a digest (the md5 sum) a space and the name of a file. So in your case you could have a file called source.md5 containing:

6a49dc38f9473f0acf46682f71c66628  source.tar.bz

Now running

md5sum -c source.md5

will check that the file source.tar.bz actually has the md5 digest 6a9.... 

You do have the source.md5 so try it out.

---

### Post by newbee70 on 2009-01-12
> **minsf said:**
> someone gave me a link to the source file and md5 sum.
i had no idea what to do with this.
i googled and found a nice md5sum article on wikipedia.
so after downloading the source from the link, say to source.tar.bz2, i ran
```
md5sum source.tar.bz2>source.md5
```
and i got a number/code that is identical to the given number.
[COLOR="Red"]my question is[/COLOR] how to do the reverse? i tried to save the given md5 sum as a text file given.md5 and then i ran "md5sum -c given.md5" with no success. 
so how should i create the given.md5 file so that "md5sum -c given.md5" checks source.tar.bz2?

If I understand right you want to make an md5 file to test your file with the  -c option. 

if that is correct try.

md5sum <filename> >>  <outputfilename.txt>

then run md5sum -c on <outputfilename.txt>

---

### Post by minsf on 2009-01-12
i think i figured it out. the problem was that in the given.md5 file i had to put two spaces between the md5 sum and the name of the file.
thanks tinivole for the clear example and for confirming that i'm using the right steps. sometimes when one uses something for the first time, all he needs is some general confirmation like that, and then he knows he is using the right steps, and can look into the details and find out this double-space in the .md5 files
have fun :)

---

### Post by minsf on 2009-01-12
> **jmontelius said:**
> So in your case you could have a file called source.md5 containing:

6a49dc38f9473f0acf46682f71c66628  source.tar.bz



for future newbies reading this thread, please notice that there is a double space here between the digest and the file name (it looks like one space in this forum), but montelius is the right solution. 
thanks montelius (though i actually figure it out before reading your post...)

---


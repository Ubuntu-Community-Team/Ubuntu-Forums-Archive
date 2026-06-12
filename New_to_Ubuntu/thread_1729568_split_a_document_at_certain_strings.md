---
title: "split a document at certain strings"
date: 2011-04-15
forum: New to Ubuntu
---

### Post by Peter.Paul on 2011-04-15
Hello,

I am trying to write a linux shell script. A larger file $1 is supposed to be split EVERY TIME, when a certain string appears and then to be saved in smaller files, that are numerated. The string is "-0.800, ". I found this

```
csplit -s $1 --prefix output /-0.800, /
```but the document is just split at the first string, but I want to document to be split every time, when the -0.800 appears.

Do you know, what I can do about that?

---

### Post by KL_72_TR on 2011-04-15
Take a look at help:
> csplit --helpand the manual:
> man csplit
Also see this page here: [http://manpages.ubuntu.com/manpages/maverick/man1/csplit.1posix.html](http://manpages.ubuntu.com/manpages/maverick/man1/csplit.1posix.html)

---

### Post by blind2314 on 2011-04-15
To my knowledge, csplit will only split up to 99 times, no matter how many actual matches are in your file. If you have more than 99 matches, you'd have to run it in segments.
 
What about this?
 
```
csplit -k -s $1 /<regex Here>/ {99}
```
 
That's working from memory, so you may need to tweak it (or read the man pages, as suggested).

---

### Post by Peter.Paul on 2011-04-25
the problem is, that the string appears twice in the document, but the document is just cut at the first string and not at the second string. 

The document looks like 
```

something 
something
-0.800, 1 
-0.799, 2
-0.798, 7
-0.797, 10
...
...
-0.799, 8
-0.800, 6
-0.799, 2
...

```
and the document is just cut directly behind "something" and not before the line with the line -0.800,6. I used the command line of the original thread. Do you know, what is wrong here?

---


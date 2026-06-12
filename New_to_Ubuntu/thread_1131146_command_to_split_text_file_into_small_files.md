---
title: "command to split text file into small files?"
date: 2009-04-20
forum: New to Ubuntu
---

### Post by sheshbesh on 2009-04-20
Hi, I have one text file of about 1MB, say big.txt
I want to break it into many small text files of 4KB, say small0 01.txt to small250.txt
I am looking for a command line solution (probably involving a simple loop in a bash script).
In particular, can I use "cut" somehow but instead of a delimeter, use byte-size?

---

### Post by steve101101 on 2009-04-20
[http://ubuntuforums.org/showthread.php?t=652132](http://ubuntuforums.org/showthread.php?t=652132)

---

### Post by unutbu on 2009-04-20
```
split --bytes=4K --numeric-suffixes big.txt 
```
Will create 4 KiB files called x00, x01, etc.

---

### Post by steve101101 on 2009-04-20
lxsplit makes this very easy.

---

### Post by sheshbesh on 2009-04-21
thanks guys- split worked great
(where do i find lxsplit? what is the difference?)

---

### Post by hyperyoda on 2009-04-22
> **sheshbesh said:**
> Hi, I have one text file of about 1MB, say big.txt
I want to break it into many small text files of 4KB, say small0 01.txt to small250.txt
I am looking for a command line solution (probably involving a simple loop in a bash script).
In particular, can I use "cut" somehow but instead of a delimeter, use byte-size?

$ split –bytes=1{b,k,m} <src-file> <dest-prefix>

src-file = your big file
dest-prefix = the prefix each smaller file will have

b = bytes
k = kilobytes
m = megabytes

so for 1MB chunks you would do:

$ split –bytes=1m big-file.txt small


to restore the original file do:

$ cat small* > big-file-restored.txt

Enjoy!

---


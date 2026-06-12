---
title: "compiling software"
date: 2009-07-02
forum: New to Ubuntu
---

### Post by cygnis1 on 2009-07-02
I tried to install Firefox 3.5 today.  It comes in a tarball, and I tried to open and compile it, without success.  I saved the tarball (tar.bz2) to my desktop. I typed in tar xvzf firefox-3.5.tar.bz2.  This is the error message I got:john@dell-desktop:~$ tar xvzf Firefox-3.5.tar.bz2
tar: Firefox-3.5.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
john@dell-desktop:~$ 

This is the second attempt at compiling a program without success.  I don't know what I am doing wrong.  Please help.
Cygnis1

---

### Post by ddnev45 on 2009-07-02
use:

```
tar -xvjf 
```

to uncompress bz2 files.

And firefox won't need to be compiled. After uncompressing it, you can run the application.

---

### Post by Ptero-4 on 2009-07-02
you need to replace
```

tar xvzf

```
with
```

tar xvf

```
The invocation you tried forces tar to treat the archive as a gzip archive, which will fail since the archive you're trying to extract is a bzip2 archive. Using the invocation I mention allows tar to auto-detect the correct archive format.

---

### Post by cygnis1 on 2009-07-02
My problem is bash can not find the file.  I thought I was in the same directory (desktop)

---

### Post by jrusso2 on 2009-07-02
> **cygnis1 said:**
> I tried to install Firefox 3.5 today.  It comes in a tarball, and I tried to open and compile it, without success.  I saved the tarball (tar.bz2) to my desktop. I typed in tar xvzf firefox-3.5.tar.bz2.  This is the error message I got:john@dell-desktop:~$ tar xvzf Firefox-3.5.tar.bz2
tar: Firefox-3.5.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
john@dell-desktop:~$ 


This is the second attempt at compiling a program without success.  I don't know what I am doing wrong.  Please help.
Cygnis1

Firefox comes as a binary you don't need to compile it you were just trying to unpack it.

---

### Post by thomz92 on 2009-07-02
the problem is that you aren't in the Desktop directory.
run this first:

cd Desktop

you named your comp dell-desktop so it looks like you're in the Desktop directory. i've done that too before.

---

### Post by twright on 2009-07-02
There is no need to use the command line to run the latest firefox :-) All you need to do is right click, press extract and double click on firefox in the new folder (you can drag and drop it onto a panel).

---

### Post by cygnis1 on 2009-07-02
Thanks guys,  I now have firefox 3.5 up and running.  Tomorrow I will try to compile the latest Empathy.

---

### Post by lovinglinux on 2009-07-02
> **cygnis1 said:**
> Thanks guys,  I now have firefox 3.5 up and running.  Tomorrow I will try to compile the latest Empathy.

You didn't compile it. Compiling is a process where you take the source code of a program and convert it into binary code, generating an executable file. What you did was simply extract compressed files from a ziped archive. These files were already compiled when you downloaded and ready for use.

The file *firefox-3.5.tar.bz2* is a pre-compiled distribution release of Firefox 3.5 browser. If you actually want to compile Firefox yourself, than you need *firefox-3.5-**[color=#CC0000]source[/color]**.tar.bz2*. 

Compiling Firefox with optimizations for you CPU can increase performance considerably. When compared to the pre-compiled version you have, the optimized Firefox exhibits 30% gain in performance on my machine. 

I wrote a tutorial about compiling Firefox if you are interested. Check the "Compiling Firefox" section of the [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567)

---

### Post by cygnis1 on 2009-07-03
Thanks.  Now if I can figure out how to mark this as solved.:guitar:

---


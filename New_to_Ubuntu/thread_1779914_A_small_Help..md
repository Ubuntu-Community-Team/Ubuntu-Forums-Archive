---
title: "A small Help."
date: 2011-06-11
forum: New to Ubuntu
---

### Post by abnordude on 2011-06-11
My friends need ubuntu.
But they do not have an internet connection.
I've been using ubuntu for many days and I think that I have the software that is essential to them.
Is there any way to give them the software that I have in my computer.
Well, it may sound stupid, but I was thinking of doing a backup in my computer and copying the backup files and extracting it in my friends computer.
Will it work?
If it doesn't, please tell me another way to do it.

---

### Post by PFN on 2011-06-11
There is an application named 'aptoncd' which will suite your need exactly.I think it is available in the official repository. A google search will give you more details.Hope this will help.

---

### Post by cracker89 on 2011-06-11
aptoncd

---

### Post by abnordude on 2011-06-11
Yes I tried aptoncd.
Its great.
But, some programs aren't getting installed.
I think maybe because there is repository source problem.
How do I transfer my sources to another computer??

---

### Post by fabricator4 on 2011-06-11
> **abnordude said:**
> Yes I tried aptoncd.
Its great.
But, some programs aren't getting installed.
I think maybe because there is repository source problem.
How do I transfer my sources to another computer??

In the installer window, it should tell you why the app was not installed.  Regardless, it is most likely due to dependencies that have not been met.

Find out what the dependencies are and install those first.  Have a look at [this info on finding depencies.]("http://www.howtoforge.com/checking-package-dependencies-with-apt-rdepends-on-debian-ubuntu")

Chris

Edit:  To keep three computers updated and installed without downloading the files again I just copy the .deb files from /var/cache/apt/archives from one computer to the other.  I'm not sure if this still works OK on a machine with no internet connection, but I think the repository indexes at least have to be up to date. (so probably not)

---

### Post by abnordude on 2011-06-20
I'm continuing this thread in another thread as both are closely related.

Here is the link.

[http://ubuntuforums.org/showthread.php?t=1759265](http://ubuntuforums.org/showthread.php?t=1759265)

---

### Post by abnordude on 2011-07-02
I'm gonna try out using aptoncd, uck, and remastersys together.

I just hope it turns out well.

Thanks everyone.

---


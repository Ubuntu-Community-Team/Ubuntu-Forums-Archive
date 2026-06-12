---
title: "lucid: catfish --path removing last folder"
date: 2010-05-25
forum: New to Ubuntu
---

### Post by a.sarkar on 2010-05-25
Dear All,

After installing catfish in ubuntu lucid to find file/folder, I used the command

```

catfish --path=$HOME/folder1/folder2 &

```where $HOME/folder1/folder2 is the path where I want to find the file.
However, catfish simply omits the folder2 from its path, i.e it tries the file in $HOME/folder1. This would work, but it would take a longer time to find the file.

Catfish of Hardy works well. However, catfish of lucid has this problem.
Any suggestions or workarounds?

---

### Post by BBUCommander on 2011-02-19
I know this thread is almost a year old, but this is the top search result on the problem and it is still not resolved in the Natty Alpha 2 (Ubuntu 11.04).

Since Catfish is effectively becoming abandonware, we may need to take up future updates ourselves.

A fix for this bug is provided here:

[http://www.mail-archive.com/debian-bugs-dist@lists.debian.org/msg792711.html](http://www.mail-archive.com/debian-bugs-dist@lists.debian.org/msg792711.html)

I tested the fix in both Gnome and Xfce with success.

If someone knows where I can report this bug so that a fix can be committed for a future version of Xubuntu, please point me in the right direction.

---


---
title: "rsync-  local to local... bit level examination? what am i missing?"
date: 2007-04-10
forum: Networking &amp; Wireless
---

### Post by Underpants on 2007-04-10
I have to move lots of large files from point A to point B.

There is a windows file server at each end.

There is a Linux machine running next to point A.

Each server has a respective share in this case: POINT-A and POINT-B

POINT-A and POINT-B are mounted in the home folder of my admin user on the Linux machine.

I want to use rsync to mirror A to B.

So as far as the Linux machine is concerned, it’s copying files from a local source to a local destination. However, in this scenario I’m finding that rsync isn’t comparing the files and just transferring the different bits like it does if I were using two Linux machines (one on each end) it’s transferring the entire file. The files I’m trying to keep synced are 10 and 20gb and only have a T1 to move them across. I can use a linux box on both ends without any problems, but I’d rather keep it simple and only use the single machine.

Am I missing something?
Edit/Delete Message

---


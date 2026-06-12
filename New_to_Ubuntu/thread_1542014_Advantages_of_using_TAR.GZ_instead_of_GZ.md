---
title: "Advantages of using TAR.GZ instead of GZ"
date: 2010-07-29
forum: New to Ubuntu
---

### Post by richmaxw on 2010-07-29
Hi,
 
Why are some files converted to TARs, then compressed using GZIP? Why aren't they just compressed using GZIP instead of first converting them to TARs? I just created some TAR.GZ and GZ files using PeaZip, but the size of each file was the same.
 
Thanks,
 
Richard

---

### Post by renkinjutsu on 2010-07-29
There are several reasons. Compression programs like Gzip can't compress directories or multiple files, only single files. Tar is a program that archives files, this includes a mix of directories and files. Essentially, tar turns a bunch of files into a single file for Gzip to compress.

Another advantage to using tar is that it preserves file ownership, and permissions and symlinks and all that good stuff. Imagine an animal a million years ago dying in a vat of tar. If that animal were to be discovered today, the tar would've preserved it so well as if no time has passed (actually, i don't know if that's true)

---

### Post by richmaxw on 2010-07-29
ok. Thanks. :D

---

### Post by jerenept on 2010-07-29
mark thread as solved please.

---

### Post by lisati on 2010-07-29
> **renkinjutsu said:**
> There are several reasons. Compression programs like Gzip can't compress directories or multiple files, only single files. Tar is a program that archives files, this includes a mix of directories and files. Essentially, tar turns a bunch of files into a single file for Gzip to compress.

Another advantage to using tar is that it preserves file ownership, and permissions and symlinks and all that good stuff. Imagine an animal a million years ago dying in a vat of tar. If that animal were to be discovered today, the tar would've preserved it so well as if no time has passed (actually, i don't know if that's true)

Nice analogy. (I'd heard that "tar" originally meant "Tape ARchive")

---

### Post by adamjkok on 2010-07-30
I don't know if you knew this yet since you are apparently new to Ubuntu Forums (no offense if you did), but please mark a solved thread as "solved" by selecting the option off of the "thread tools" menu.

---

### Post by uRock on 2010-07-30
> **lisati said:**
> Nice analogy. (I'd heard that "tar" originally meant "Tape ARchive")
That was the original use of .tar. Gotta love the Intro to UNIX/Linux book. I've learned a bit lately.

---


---
title: "??? - the file header is corrupt"
date: 2010-04-13
forum: New to Ubuntu
---

### Post by Faith95 on 2010-04-13
this is shown whenever i trie to unrar a rar file... does it mean its corrupt? :( 
can i fix it? if so how?

---

### Post by undecim on 2010-04-13
Sounds like it. Unless the rar came with parity files, (.par, .par2, etc.) there's nothing you can do to fix it.

If you downloaded the file from a website, you might try downloading it again, in case it downloaded wrong.

---

### Post by kellemes on 2010-04-13
> **Faith95 said:**
> this is shown whenever i trie to unrar a rar file... does it mean its corrupt? :( 
can i fix it? if so how?

There are a bunch of tools (for Windows mainly) that promise to fix the rar, but they will at best fix just a small part. And even that is not sure..
Corrupt? Yes.
Fixable? Not in most cases.

---

### Post by Faith95 on 2010-04-13
well that sucks... thanx though!!! =D

---

### Post by Arthur King on 2011-07-10
If all rar files present this problem they can hardly all be really corrupt.
I am experiencing the same problem with Ubuntu 10.04..normally if you have unrar installed you just click on the file and then click "extract" to extract to your chosen location.  I have done this on many occasions without any problems, but suddenly it doesn't work anymore (including on rar files which I have kept although I had previously extracted them without problems).
The solution is simple enough..I have 11.04 on another partition and everything works fine, the same rar files present no problems.
It would be nice to know why this has stopped working on 10.04, but I haven't a clue.

---

### Post by Arthur King on 2011-07-13
Update on this problem, if I enter  unrar  in a terminal (in 10.04) I get the following: 
unrar: error while loading shared libraries: libstdc++.so.2.8: cannot open shared object file: No such file or directory.
When you enter  unrar  you should get a help page (as I do in 11.04).
Anyway I installed ark which works in 10.04.  (Right click on rar archive, select "open with Ark" then extract to desired location)

---


---
title: "move all the files to a subdirectory under current directoty"
date: 2010-02-06
forum: New to Ubuntu
---

### Post by techfish on 2010-02-06
I want to move all the files in the current directory, to a subdirectory under current directory using "mv" command. I know it should be easy but I am a beginner!

---

### Post by switch10 on 2010-02-06
use:
```
mv -r 
```

---

### Post by falconindy on 2010-02-06
the -r flag isn't needed as it is with copy. "mv * subdir/" is all you need.

---

### Post by techfish on 2010-02-06
> **falconindy said:**
> the -r flag isn't needed as it is with copy. "mv * subdir/" is all you need.

I get an error message:
mv: cannot move `subdir' to a subdirectory of itself, `subdir/subdir'

---

### Post by kaibob on 2010-02-07
> **techfish said:**
> I get an error message:
mv: cannot move `subdir' to a subdirectory of itself, `subdir/subdir'

The move command moves both files and directories. Your command attempts to move a directory into itself. You can simply ignore the error message or try one of the solutions noted in:

[http://serverfault.com/questions/63269/bash-snippet-to-move-all-files-in-a-directory-into-that-directory](http://serverfault.com/questions/63269/bash-snippet-to-move-all-files-in-a-directory-into-that-directory)

---

### Post by switch10 on 2010-02-07
Why don't you show us an example of what you are trying to move, and what directory you are in.  It would be a lot easier to just correct your mistake.  Its not a big one.





> **falconindy said:**
> the -r flag isn't needed as it is with copy. "mv * subdir/" is all you need.

I forgot about that, thanks :).  I have been using flags interchangeably lately.  Its a bad habit that I've gotten into.

---

### Post by switch10 on 2010-02-07
OK i just re-read your original post.  It sounds like you are going to have to use wild cards to move just those files, and not the directory you want to move them into.  do the files you want to move all have a similar name? or similar file type like .mp3?

---

### Post by switch10 on 2010-02-07
> **techfish said:**
> I get an error message:
mv: cannot move `subdir' to a subdirectory of itself, `subdir/subdir'

I just tested this out, out of curiosity.  It should have moved all of the files to that subdirectory, just how you wanted, anyway.  You can omit the error message.

---


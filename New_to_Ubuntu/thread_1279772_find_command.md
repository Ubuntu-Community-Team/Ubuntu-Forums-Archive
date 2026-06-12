---
title: "find command"
date: 2009-10-01
forum: New to Ubuntu
---

### Post by Drenriza on 2009-10-01
What filetypes can you use in the find command?.
Is their a overview of that somewhere.

thanks on advance:KS

---

### Post by linux-hack on 2009-10-01
First of all you have : ```
man find
```

and second you can use all the filetypes with this comand.

and you have another option sed or awk

---

### Post by wojox on 2009-10-01
```
man find
```

---

### Post by credobyte on 2009-10-01
find command uses patterns, not filetype list ( eg., *.*, *.mp3, song.* ).

---

### Post by unutbu on 2009-10-01
Suppose you wanted to find all audio/mpeg files in ~/Music, and didn't want to rely on the filename ending to recognize audio/mpeg files. Then you could do
```

find ~/Music/ -exec file -i {} \; | grep  audio/mpeg
```

The "find" command lists all the files in ~/Music.
The "-exec" flag tells find to run "file -i" on each file.

"file -i" outputs the name of the file and its mimetype. 
This output is piped to the "grep" command, which prints only those lines
which have mimetype "audio/mpeg".

---


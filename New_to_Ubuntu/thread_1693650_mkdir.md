---
title: "mkdir"
date: 2011-02-23
forum: New to Ubuntu
---

### Post by flee0308 on 2011-02-23
Okay, I understand that mkdir can help me make a directory in the terminal. But how exactly is it used? Can someone show an example of how it works? 

Oh by the way, just to doublecheck, creating a directory is the same as creating a folder, right?

---

### Post by nothingspecial on 2011-02-23
```
mkdir directory
```

will make a directory called "directory" in the directory you are currently in.

```
mkdir /media/music/flac/punk
```

will make a directory called punk in /media/music/flac but will fail if flac doesn't exist in /media/music

To make a directory in a directory (and so on and so on) that don't exist use the -p flag

so 

mkdir -p Documents/blah/blag/gubbins

will create all three of those directories inside Documents (if you see what I mean)

type ```
man mkdir
``` for more help

---

### Post by flee0308 on 2011-02-23
> **nothingspecial said:**
> ```
mkdir directory
```

will make a directory called "directory" in the directory you are currently in.

```
mkdir /media/music/flac/punk
```

will make a directory called punk in /media/music/flac but will fail if flac doesn't exist in /media/music

To make a directory in a directory (and so on and so on) that don't exist use the -p flag

so 

mkdir -p Documents/blah/blag/gubbins

will create all three of those directories inside Documents (if you see what I mean)

type ```
man mkdir
``` for more help

Thanks. :)

---


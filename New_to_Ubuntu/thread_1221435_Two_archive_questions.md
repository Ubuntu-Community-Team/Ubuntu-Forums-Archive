---
title: "Two archive questions"
date: 2009-07-23
forum: New to Ubuntu
---

### Post by Muscovy on 2009-07-23
I have two questions on archive commands.
  In zip, how do you say 'everything in this directory'? Running ```
zip /outlocation/file.zip ~/
``` does nothing. I tried ```
zip /outlocation/file.zip ~/**[SIZE="4"]*[/SIZE]**
```, but it only made files in my home folder, not other folders. I found adding /* to the end again now copied the files located in the folders in home too. When I tried using more I would get either error messages or not everything would copy. Is there a simple 'all'?

  Secondly, with 7zip, I'm trying to exclude hidden (.*) files, but I can't understand the code in the man page.
```
-x[r[-|0]]]{@listfile|!wildcard}
```

  Thanks.

---

### Post by Rocket2DMn on 2009-07-23
You need to use the -r option:
```
zip -r /outlocation/file.zip ~
```

---

### Post by Muscovy on 2009-07-23
Thanks, zip -r /outlocation/file.zip ~/*

---

### Post by Muscovy on 2009-07-23
Actually, while I'm at it, is there an exclude for copy (cp)? I couldn't see one.

---

### Post by Rocket2DMn on 2009-07-23
I haven't used 7z in linux, but I think the command you want is something like this:
(deleted)

I don't think there is any direct way to exclude files with cp, you would need a special script or more complex command for that.

---

### Post by Rocket2DMn on 2009-07-23
Got it! This one was definitely a bit of a pain in the rear.  To add all files in a folder except those beginning with a ".", run:
```
7z a -ax@\!.* testarchive .
```
7z = command
a = add
-ax@\! = exclude (the "\" is an escape character for the "!" symbol)
.* = the wildcard
testarchive - the archive name, i.e. testarchive.7z
. = the source directory.

The last "." means the current directory, you can substitute something like "/path/to/source/directory".


As far as I can tell, it is not possible to archive subdirectories, you will need to use another format for that.

---

### Post by Muscovy on 2009-07-24
Thanks, that worked.
  And you can archive all with a -t7z.

---


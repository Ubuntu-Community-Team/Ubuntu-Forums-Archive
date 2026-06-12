---
title: "problems zipping very large directory on XP for use on Ubuntu"
date: 2009-01-08
forum: New to Ubuntu
---

### Post by Old Jimma on 2009-01-08
Hi:

I work in 2 locations.

In one of those locations, I use an XP machine.

In the other I use an Ubuntu 8.10 machine.

When I want to move my work from the Ubuntu machine to the XP machine, I right click on the top directory and create zip archive. I don't seem to have any problem unzipping it on the XP machine.

When I want to move my work from the XP machine to the ubuntu machine, I use the XP zip facility (right click on top directory) and create a zip file that I transport to the ubuntu machine.

This has worked for a very long time.

However, lately I've had ALOT of trouble moving the zip file from the XP machine to the Ubuntu machine. The Ubuntu archive manager will not unzip the zip file created on the XP machine, completely, and gives error messages.

The file system I am zipping is about 3Gb.

What should I be doing to make this work right?

THanks,
Phil Smith
Duluth, GA

---

### Post by kaibob on 2009-01-08
> **Phil Smith said:**
> ...When I want to move my work from the XP machine to the ubuntu machine, I use the XP zip facility (right click on top directory) and create a zip file that I transport to the ubuntu machine. This has worked for a very long time. However, lately I've had ALOT of trouble moving the zip file from the XP machine to the Ubuntu machine. The Ubuntu archive manager will not unzip the zip file created on the XP machine, completely, and gives error messages....

To troubleshoot this issue, I would try to unzip it with the unzip command-line utility. Just open a terminal window, change to the directory containing the zip file, and enter:

```
unzip filename
```

As an alternative, you could check the zip file with the zipinfo command-line utility to see if it issues any errors.

BTW, I believe that unzip is installed by default; if not, it's in the repo's and is very small.

---

### Post by oldos2er on 2009-01-08
"The Ubuntu archive manager will not unzip the zip file created on the XP machine, completely, and gives error messages."

 What are the error messages?

---

### Post by Old Jimma on 2009-01-09
Hi Oldos2er and Kaibob:

In my frustration, I trashed the zip file.

I'll bring it home on Monday and try your suggestions.

Thank you,
Phil Smith
Duluth, GA

---

### Post by Facetious Falcon on 2009-01-09
Try right-clicking the zip file and click 'extract here' which is further down the menu. Archive manager has a lot of issues with various archive formats so I almost always use 'extract here'.

---

### Post by Old Jimma on 2009-01-17
Folks:

Here is why I had problems unzipping files.

1. The zip file was created on a Windows machine.

2. Winzip verion 8.0 was used. 8.0 can only zip directories smaller than 2 Gb or so, and "gets lost" when directories are larger. This may not be a problem with version 12.0 for 64 bit machines... but I am not certain about that.

[COLOR="Blue"]**IMHO Winzip web page should be more explicit about what it can and cannot do for each version. Let the buyer beware!**[/COLOR]

3. When archive managers detects that the zipped file (zipped using Winzip 8.0) had a problem in being created in the first place... it lets you know by giving cryptic messages.

Bottom line: try to zip things on Windows with a program that does not have constraints on the size of directories that it can zip.

Phil Smith
Duluth, GA

---


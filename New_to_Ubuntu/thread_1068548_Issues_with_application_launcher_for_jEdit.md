---
title: "Issues with application launcher for jEdit"
date: 2009-02-13
forum: New to Ubuntu
---

### Post by kogger on 2009-02-13
I'm trying to create a custom application launcher for jEdit. I have the program installed on a separate partition on my hard disk, so I have a shell script to run it:

```
#! /bin/bash
java -jar /media/disk/programs/jEdit/jedit.jar
```

This command works fine when I type it into the terminal, but when I create a launcher to run the script it doesn't do anything. I see a small flash on the screen, but nothing happens.

Any idea how to run a .jar file using an application launcher?

---

### Post by jenkinbr on 2009-02-13
Couln't you just run the .jar file by placing ```
java -jar /media/disk/programs/jEdit/jedit.jar
``` into the command portion of the launcher?



{btw, I think your problem has to do with the current working directory not getting set right, but I could be wrong.)

---

### Post by kogger on 2009-02-13
Nothing happens when I do that. I don't even get an error message.

---

### Post by jenkinbr on 2009-02-13
Another thing you might try:

Edit your script so that it reads

```
#!/bin/bash
cd /media/disk/programs/jEdit/
java -jar /media/disk/programs/jEdit/jedit.jar

```

Try that and see if it works.

---


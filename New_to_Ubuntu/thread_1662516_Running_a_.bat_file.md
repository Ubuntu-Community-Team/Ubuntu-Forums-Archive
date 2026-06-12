---
title: "Running a .bat file?"
date: 2011-01-08
forum: New to Ubuntu
---

### Post by d2earth on 2011-01-08
hey, So i've been playing runescape private servers, Now i have downloaded a client and need the .bat to run so i can gain access to the server. 
Here's what i think may be part needed to run it, my java location.
```
/usr/lib/jvm/java-6-openjdk/jre/bin/java
```and heres what the .bat looks like
```
@echo off 
title New Era 
start javaw -Xmx300m Jframe 10 0 highmem members 32 
EXIT
```Ok, so what do i have to do to make this work?
Thanks in advance.

---

### Post by essecks on 2011-01-08
The .bat extension gives away the fact that it's a [batch file]("http://en.wikipedia.org/wiki/Batch_file"), which is designed for and will only run on a Windows operating system. This means it won't run from your computer, if you're running Ubuntu.

---

### Post by d2earth on 2011-01-08
i have wine can it be done with that? I read you can also make an executable .sh file and give it chmod to run the rspc client? these are things i've read on, trying to find out how to do it is the hard part for me. I know for a fact it can be done.

---

### Post by d2earth on 2011-01-08
BUMP, really need help here

---

### Post by hugmenot on 2011-01-08
Forget the .bat file.

The only significant line in there is this one:
```
javaw -Xmx300m Jframe 10 0 highmem members 32 
```

There’s no javaw, just java.

The question is from which directory you have to run this. You probably need to cd into the folder with Jframe.class in it. Or you define the CLASSPATH to point to it.

---

### Post by psusi on 2011-01-08
Yep, just running java -Xmx300m Jframe 10 0 highmem members 32 should do it, if you have java installed.

---

### Post by cgroza on 2011-01-08
I had success with WINE running batch files. Those are simple files and WINE has a cmd.exe like program.

---

### Post by hugmenot on 2011-01-08
> **cgroza said:**
> I had success with WINE running batch files. Those are simple files and WINE has a cmd.exe like program.

Why? There’s quite evidently only one effective line in it.

---

### Post by cgroza on 2011-01-08
I know, the batch files are used to automate things usually.

---


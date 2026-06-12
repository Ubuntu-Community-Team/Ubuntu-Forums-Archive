---
title: "Running a bash script with an application launcher"
date: 2009-02-13
forum: New to Ubuntu
---

### Post by kogger on 2009-02-13
Whenever I try to run a bash script using an application launcher, I see a small flash instead of a terminal window actually opening and staying.

Any idea how to get the window to stay?

---

### Post by vambo on 2009-02-13
IMO, the best, and easiest way to achieve is to launch a terminal with the -e command, then the name of the script you want it to execute.
E.G

```
xterm -e "man ls"
```

will launch an xterm which displays the man page for ls.
If you put this in a launcher, the man page will pop up in a terminal and stay there.
So if you replace the "man ls" (keep the quotes) with your script you should get it running in it's own terminal.

I'm pretty sure every terminal ever wtitten has the -e option. If it doesn't, find a better terminal!

---

### Post by kogger on 2009-02-13
Okay, the code you gave me works, but I'm trying to use it to launch a .jar file (using java -jar), and even simply testing the java command I get a "there was an error creating the child process for this terminal" error. I'm using gnome-terminal (with Ubuntu 8.10), so here's the code that I have to test the java command:

```
gnome-terminal -e "java"
```

Any idea how to get this to work?

EDIT: I noticed that it has the same problem with any other script I try to execute; it won't even do Hello World. The man thing works fine, but nothing else does.

---

### Post by Terl on 2009-02-13
Are the scripts executable?  And also important, is the directory the scripts are in, in your PATH?

---

### Post by kogger on 2009-02-13
Okay, to test this I created a basic Hello World program. I ran chmod to make sure it was executable and used the full path name (I do have the directory in $PATH, but it's relative from ~, so I think that might be the problem there). After that, the window just disappears again. Here's the command I have for it:

```
gnome-terminal -e "/home/damien/commands/hello"
```

And here's what's in the hello file:

```
#! /bin/bash
echo Hello World
```

I got rid of the child process error, but now the window won't stay anymore.

---

### Post by Terl on 2009-02-13
[Check this link...]("http://ubuntuforums.org/showthread.php?t=33955")  I couldn't get it to stay open either so I went on a hunt for the answer.

---

### Post by kogger on 2009-02-13
Okay, adding "read" to the end of the script makes it stay open, but now I've got the "There was an error creating the child process for this terminal" problem again. >_>

---

### Post by vambo on 2009-02-13
Interesting problem this! Couldn't get initially myself.
Just a note a java ( .jar) is not the same as a bash script - just to clarify.
Anyway, I got the following to work

1. Create the script

```
#! /bin/bash

java -version
read
```

I called it javatest.sh
Make sure it's executable

2. Invoke with xterm -e "javatest.sh"

The result is an xterm which stays on screen with the java JRE info

Hopefully this will be a pointer to finding a solution.
AS you might have guessed I'm no java expert :lolflag:

EDIT: If you use java -? in the script (as opposed to java -version),
that works too. Hence java blah blah should be okay - hopefully

---

### Post by Terl on 2009-02-13
I wonder if it is related to [Bug 474693]("http://lists.alioth.debian.org/pipermail/pkg-gnome-maintainers/2008-April/044048.html")?  I have been playing with it too.

---

### Post by vambo on 2009-02-13
> **Terl said:**
> I wonder if it is related to [Bug 474693]("http://lists.alioth.debian.org/pipermail/pkg-gnome-maintainers/2008-April/044048.html")?  I have been playing with it too.

Don't think so, as Ive been using xterms.

---

### Post by Terl on 2009-02-13
I get the child process on gnome-terminal.  When I run it through rxvt it opens and closes fast.  This has me curious now.

---

### Post by kogger on 2009-02-13
With xterm it still vanishes, with gnome-terminal I get the child process error.

---


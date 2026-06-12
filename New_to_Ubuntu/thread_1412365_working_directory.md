---
title: "working directory"
date: 2010-02-21
forum: New to Ubuntu
---

### Post by bionicdude on 2010-02-21
Hey,

I've done a couple of searches on google and in the ubuntuforums, to no avail.
I'm concerned that this means my question is so very ignorant that I'm going to look a little silly, but i need the answer, so here goes..

How does one start an application with a specific working directory (not necessarily the directory that the file is in).

eg.

I created a bash script thusly (pseudo code):

disable screensaver
run xbmc
enable screensaver

I placed this script in a script folder in my home dir and created soft links in the /usr/local/bin directory so that i could run the script from ALT+F2.
This works great, but the log files of xbmc are created in my script folder.
I get a similar affect when starting PMS from a command line (the log is created in the program folder) as opposed to from ALT+F2 where the log is created in my home dir.

So how do i tell a program to start with a specific working directory?

Thanks in advance

---

### Post by HermanAB on 2010-02-21
$ cd /wherever;whatever

---

### Post by bionicdude on 2010-02-21
> **HermanAB said:**
> $ cd /wherever;whatever

Firstly thanks for the reply.
As i understood it, the semicolon simply allows you to chain commands together and so your suggestion would equate to

cd /wherever (the program directory)
whatever (run the program)

In this example the working directory would be the /wherever directory.

But what if i wanted to run that program from somewhere else (so that the log files were produced in that somewhere else folder)?

Or have i misunderstood?

I'd previously tried running something from a different directory to my current dir and it didn't work. That led me to believe that i had to do something more complicated. Nope - just had to get the syntax right :)
Sorry for the confusion, I've sorted it (and yes - you're suggestion worked - i simply had to cd to the dir i wanted to run from instead of the dir the app was in).

Thanks

---

### Post by J V on 2010-02-21
```
cd /my/working/directory
/usr/bin/appname
```Never used semicolon in bash but in most languages yes, you understand correctly.

---


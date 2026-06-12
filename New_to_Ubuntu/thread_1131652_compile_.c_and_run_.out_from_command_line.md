---
title: "compile .c and run .out from command line"
date: 2009-04-21
forum: New to Ubuntu
---

### Post by vilmos on 2009-04-21
Hello Everyone,

I am absolutely new without any backround in programming.
Now I want to learn programming in c, and I have several questions.

I have no Linux, but use a Mac, and may also want to learn Darwin.
When I looked for advice, I could hardly find anything - my questions are obviously too low level.
Google lead me to this site with a question, and here I found a perfect answer - that's why I am here. I realized Ubuntu is very similar to Unix, so with such community support this might be it for me!

The question was about running a freshly compiled c program from the command line.
What I have learned so far is this:
1) gcc source.c -o outfile.out
2) chmod +x outfile.out (I later found this unneccessary, obviously gcc sets executing permission for me)
3) ./outfile.out - and this runs th program!

But I do not understand why I have to put ./ before the program name.
All existing programs can be run simply typing the filename as a command.

Any kind of help would be very much appreciated!
Cheers - Vilmos

---

### Post by Alterax on 2009-04-21
> **vilmos said:**
> Hello Everyone,

I am absolutely new without any backround in programming.
Now I want to learn programming in c, and I have several questions.

I have no Linux, but use a Mac, and may also want to learn Darwin.
When I looked for advice, I could hardly find anything - my questions are obviously too low level.
Google lead me to this site with a question, and here I found a perfect answer - that's why I am here. I realized Ubuntu is very similar to Unix, so with such community support this might be it for me!

The question was about running a freshly compiled c program from the command line.
What I have learned so far is this:
1) gcc source.c -o outfile.out
2) chmod +x outfile.out (I later found this unneccessary, obviously gcc sets executing permission for me)
3) ./outfile.out - and this runs th program!

But I do not understand why I have to put ./ before the program name.
All existing programs can be run simply typing the filename as a command.

Any kind of help would be very much appreciated!
Cheers - Vilmos

It's a security feature.  Using ./ means literally, "IN THIS DIRECTORY".  Ideally, the current directory should not be a part of the path, because a damaging program could be run by accident.  For example, I could write a program and call it "ls".  This ls--far from the normal use of listing files in a directory--could, say, wipe the hard drive.  You wouldn't want to write something like this (or have someone sneak it into your home directory) and then accidentally run it.

Using ./ makes it very clear to you that the program you are running isn't one that's in the standard path, but instead is the one in the current directory.

---

### Post by vilmos on 2009-04-23
> **Alterax said:**
> It's a security feature.  Using ./ means literally, "IN THIS DIRECTORY".  Ideally, the current directory should not be a part of the path, because a damaging program could be run by accident.  For example, I could write a program and call it "ls".  This ls--far from the normal use of listing files in a directory--could, say, wipe the hard drive.  You wouldn't want to write something like this (or have someone sneak it into your home directory) and then accidentally run it.

Using ./ makes it very clear to you that the program you are running isn't one that's in the standard path, but instead is the one in the current directory.
Hi,
Many thanks!
Could you suggest some literature online where I could look up such things?
Vilmos

---


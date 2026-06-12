---
title: "cannot set Latex path"
date: 2010-10-18
forum: New to Ubuntu
---

### Post by bebops_lost on 2010-10-18
Hi everyone 

I had a question that I looked up on these forums, and found that somebody else asked essentially the  same question about how to include latex files.

[http://ubuntuforums.org/showthread.php?t=149896](http://ubuntuforums.org/showthread.php?t=149896)

and somebody else answered it, and the original person said "great thanks, that worked." and the thread was closed because presumably the problem was solved.
except the thing is it *didn't* work for me.

What I want to do is really quite basic: I use latex. I use a number of .cls and .sty files (that are actually quite common) and for the life of me I simply *cannot* get latex to find these files unless I actually include copies of them in the same folder as the .tex file I'm compiling (which is awfully messy and tedious when you have a number of tex projects using the same files.) 

There has got to be a way to put all my .sty and .cls files in one folder and tell Latex "hey, Latex, go _**Here**_ and find the files you need." i.e. I need to set the include path, which is turning out to be far more difficult than I had envisioned.

I've tried everything I've seen on every thread on this (i.e. I tried setting TEXINPUTS, I tried editing the /etc/texmf/texmf.d/05TeXMF.cnf file ) and nothing works. The only explanation is that I'm typing things in with the wrong syntax, or missing a space or something. I'd include my commands, except it seems that there's more than one way of doing this, and I'm willing to take any solution I can get.

Can someone tell me how they do this?

---

### Post by bebops_lost on 2010-10-18
ok, solved my own problem. I dunno if anyone is reading this, but after banging my head against a wall for a while I found this snippet in another thread:

> **jalirious** _March 30th, 2010, 09:57 AM _ What a licker. All I had to do was change revtex4 in my .tex document to revtex4-1.

So I tried that and then everything worked...
so just in case anyone is interested, if you stumble across the following error message:

```
! LaTeX Error: File `revtex4.cls' not found.
```

then you should try changing the documentclass at the head of your texfile to {revtex4-1}.

---


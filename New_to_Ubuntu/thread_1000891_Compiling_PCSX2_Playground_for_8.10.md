---
title: "Compiling PCSX2 Playground for 8.10?"
date: 2008-12-03
forum: New to Ubuntu
---

### Post by chris062689 on 2008-12-03
I tried following the steps in the forum, but I can't figure out how to get it to properly run, I think the guide's outdated.

[http://ubuntuforums.org/showthread.php?t=631979](http://ubuntuforums.org/showthread.php?t=631979)

---

### Post by cozmicharlie on 2008-12-03
Since you are posting on Absolute beginner" I assume you are new to Linux.  If so, this is a very complicated procedure for someone just starting and their are a lot of steps that could go wrong.  Make sure you read the procedure very carefully and follow each step.  I would say it is probably up to date since it was updated on 4-2008.  Though the update only covers Hardy not Intrepid.  You may want to post your question in that thread rather than start a new one. 
Make sure you read through the entire thread.  
Also, what version of Ubuntu are you using (Hardy, Intrepid, ??).
Does it run at all?  
What happens when you try and run it?

---

### Post by chris062689 on 2008-12-04
I can't reply to that post because it's achieved.
I am running 8.10, it crashes after I configure it.

---

### Post by DieB on 2008-12-04
so u did run ./configure and it aborts?

that should be due to dependencies go look in the text that configure prints and look what dependencies it did not find. (this might be a long way due to after u installed the dependency there might still be more, but it always aborts on the first unmet dep - so be prepared.

p.s.: if u install dependencies be sure u install the package ending with "-dev"

---

### Post by DieB on 2008-12-04
i just saw, that on [www.playdeb.net](www.playdeb.net) there is it already compiled. if u get their repository, get the hardy one due to intrepid has not yet many games ;(

---

### Post by chris062689 on 2008-12-06
That's a really outdated version.  I believe it's over a year and a half old.   PCSX2 has a SH file that automatically compiles / makes it.
Afterwords, I launch pcsx2, and it crashes after I pass the configuration screen.  8.10 64bit

---

### Post by DieB on 2008-12-07
did u take a svn-version? cause otherwise its the same version omn playdeb as in [sourceforge]("http://sourceforge.net/project/showfiles.php?group_id=79721")

---

### Post by Arjent on 2008-12-14
For those of you following along at home:

Here's a compile guide:
[http://forums.pcsx2.net/thread-2373.html](http://forums.pcsx2.net/thread-2373.html)

And here's a premade version:
[http://forums.pcsx2.net/thread-2375.html](http://forums.pcsx2.net/thread-2375.html)
(if you're using 8.10, use the appended ksmos lib)

---


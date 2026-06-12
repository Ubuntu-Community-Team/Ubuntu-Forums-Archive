---
title: "[SOLVED] What language to use"
date: 2008-12-29
forum: New to Ubuntu
---

### Post by WASHAD on 2008-12-29
I'm loving the new Ubuntu! I've switched all of my home computers, my relatives computers, and now my work computer. 

I'd love to get involved with some of the Ubuntu open source stuff. I've have a bit of programming experience (I'm going back to school for software engineering), but it is mainly in .Net stuff - though I've done some C++. 

My question is what language should I concentrate on to be most useful to the Ubuntu community?


> If C++ then....
   -- What do I use for GUI. 
   -- I still fear unmanaged code.
   -- What is a good IDE?

> If Java then....
   -- What IDE (Eclipse, NetBeans, other)?
   -- Is there an IDE with a GUI builder?

> What is a good web page designer
   -- supports code completion
   -- is WYSIWYG?
   -- supports CSS
   -- supports JavaScript, PHP?

> Is MonoDevelop a viable alternative or is it still too infant?

> How does one get a software package on Synaptic?
   -- How to make application auto-install?


That enough questions to get me started....


Thanks.

---

### Post by Sorivenul on 2008-12-29
You may be interested in these Sticky threads from the Programming Talk subforum:
[http://ubuntuforums.org/showthread.php?t=1006666]("http://ubuntuforums.org/showthread.php?t=1006666")
[http://ubuntuforums.org/showthread.php?t=1006662]("http://ubuntuforums.org/showthread.php?t=1006662")

Now for my personal thoughts:

C++ and Qt are a usual match for a language and GUI toolkit, and there are many IDEs available. Code::Blocks seems to be popular, and the KDevelop suite as well.

For Java I always turn to NetBeans, though Eclipse is also popular. NetBeans offers a GUI builder, I believe.

For web design, Amaya and Screem come to mind.

MonoDevelop, and Mono in general, are not my area of expertise, but the little bit of C# I have done has been greatly aided by MonoDevelop.

Good luck! Cheers!

---

### Post by Dr Small on 2008-12-29
> **WASHAD said:**
> 
> What is a good web page designer
   -- supports code completion
   -- is WYSIWYG?
   -- supports CSS
   -- supports JavaScript, PHP?



Never use WYSIWYG editors; they are evil.

---

### Post by Sorivenul on 2008-12-29
> **Dr Small said:**
> Never use WYSIWYG editors; they are evil.
I actually second this. I won't force anything on anyone, though. :D

---

### Post by directhex on 2008-12-29
> **WASHAD said:**
> it is mainly in .Net stuff

Nobody's forcing you to learn a new language if you don't want to. Ubuntu has had a C# compiler for about 3 years, and a VB.NET compiler will be in 9.04

---

### Post by WASHAD on 2008-12-29
Though a C# compiler is available, do I have access to the same libraries? For example, if I were to go to the MSDN docs and pick a random class, what are my chances of it working in Ubuntu?

SteveJ

---

### Post by Sorivenul on 2008-12-29
> **WASHAD said:**
> Though a C# compiler is available, do I have access to the same libraries? For example, if I were to go to the MSDN docs and pick a random class, what are my chances of it working in Ubuntu?

SteveJ

You may be interested in this [FAQ]("http://www.mono-project.com/FAQ:_General") from from the Mono project.

---

### Post by jpmelos on 2008-12-29
> **Dr Small said:**
> Never use WYSIWYG editors; they are evil.

Just enforcing it.

You will not get what you see, what will make you cry out loud. Then, you'll regret yourself and the time wasted, and go to gEdit, then get it done yourself.

But, your know, not forcing you. :)

---

### Post by WASHAD on 2008-12-29
WYSIWYGs are not perfect for sure. Generally I only use them in split screen mode, in conjunction with code. All bias aside, though, one has to admit that some things are just easier done visually. But alas, I don't want this thread to turn into a debate on the matter so I will withdraw the question :)

SteveJ

---

### Post by jpmelos on 2008-12-29
OK, hehe. Back to topic, I don't know what language you should focus to be the most useful. Both languages you said are widely used (Linux is made on C and loads of applications are made on Java). One language I'd like to add to your list, that you should do some research on to decide the best for you, is Python. It's widely used and it's growing. Fast. Especially for the open source community. So, yea, I'd consider that. :D

If you want to contribute, you will be able to do so with any of those languages, for sure. :) Research. You'd find out you'd learn even all three!

---

### Post by WASHAD on 2008-12-29
Thanks, All;

This should get me started. 

SteveJ

---

### Post by directhex on 2008-12-30
> **WASHAD said:**
> Though a C# compiler is available, do I have access to the same libraries? For example, if I were to go to the MSDN docs and pick a random class, what are my chances of it working in Ubuntu?

SteveJ

If it's in .NET 2.0, pretty high.

Generally speaking, though, there are better replacements for many Microsoft APIs, e.g. GTK# instead of Winforms (which looks like crap & is nasty pixel-based rubbish)

---


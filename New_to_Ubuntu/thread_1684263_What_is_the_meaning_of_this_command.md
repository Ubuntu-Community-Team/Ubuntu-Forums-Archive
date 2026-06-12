---
title: "What is the meaning of this command?"
date: 2011-02-08
forum: New to Ubuntu
---

### Post by beew on 2011-02-08
I have had several applications (always have something to do with video stuffs) that were not working properly (minitube, skype, smplayer) The solution always involved adding "env XLIB_SKIP_ARGB_VISUALS=1" or some of its  variations to the launcher commands. After that the problems were magically solved. 

Just wonder what that does. Does it have something to do with the Cairo Dock?

Thanks.

---

### Post by AlphaLexman on 2011-02-08
> **beew said:**
> env XLIB_SKIP_ARGB_VISUALS=1
It looks like you are just setting an environment variable. See 'man env' for more details.

---

### Post by beew on 2011-02-09
Yea, I know I am setting an env variable, I just want to know what it means in  a functional kind of way without having to wade through a manual full of other technical gibberish. By the way I did check man env, doesn't really tell you anything.

Sorry to say this, but RTFM is not much of help.

---

### Post by ad_267 on 2011-02-09
I think it's disabling transparency in the GTK theme. That's just a guess based on the name of the variable though.

---

### Post by Elfy on 2011-02-09
Found this after a search in gentoo - [http://www.x.org/archive/X11R6.8.0/doc/RELNOTES5.html](http://www.x.org/archive/X11R6.8.0/doc/RELNOTES5.html)

Might help you.

---

### Post by beew on 2011-02-09
> **forestpiskie said:**
> Found this after a search in gentoo - [http://www.x.org/archive/X11R6.8.0/doc/RELNOTES5.html](http://www.x.org/archive/X11R6.8.0/doc/RELNOTES5.html)

Might help you.


Thanks. That link basically answers my question.

---


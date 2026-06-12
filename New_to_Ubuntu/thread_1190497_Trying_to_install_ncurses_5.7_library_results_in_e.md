---
title: "Trying to install ncurses 5.7 library results in error"
date: 2009-06-17
forum: New to Ubuntu
---

### Post by AkaChan83 on 2009-06-17
I'm trying to install ncurses 5.7 and after running make and ultimately this is what I get (after pages and pages of output, I can post that if someone thinks it would help):

cd ../objects;   -I../c++ -I../include -I. -DHAVE_CONFIG_H -I. -I../include  -D_GNU_SOURCE -D_FILE_OFFSET_BITS=64  -DNDEBUG  -c ../c++/cursesf.cc
/bin/sh: -I../c++: not found
make[1]: *** [../objects/cursesf.o] Error 127
make[1]: Leaving directory `/home/lauren/Downloads/ncurses-5.7/c++'
make: *** [all] Error 2

Thoughts?

---

### Post by AkaChan83 on 2009-06-17
so i ran ./configure --without-cxx-binding (per the readme file :) ) and it seemed to work after that.  What kind of problems will I run into (if any) by telling it to configure without C++ bindings?

---

### Post by HappyPandaFace on 2013-05-02
Thank you for coming back here and posting that solution.

---

### Post by papibe on 2013-05-02
Please don't reply on old threads. It is much better to create a new one. Feel free to link this one if you want.

From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

**Thread Closed**.

---


---
title: "paths to libraries"
date: 2010-02-05
forum: New to Ubuntu
---

### Post by deathintheafternoon on 2010-02-05
I'm installing something and the documentation recommends putting the compiled libraries into /opt.  Is there a reason to put something in /opt instead of other directories like /usr/local? 

The syntax that is recommended has confused me a bit as well:

"./configure --prefix=/opt/filename" and "--with-filename=/filename"

Can someone provide some interpretation or tell me a keyword to "man" on to find out what this means? 

Thanks.

---

### Post by nothingspecial on 2010-02-05
Those are compile options.

It would be helpful if you posted a link to the documentation.

Basically, you are putting the libraries somewhere in your filesystem then telling the program, at compile time, where to find them.

But without seeing the documentation I can`t be anything more than very vague.

---

### Post by deathintheafternoon on 2010-02-05
> **nothingspecial said:**
> Those are compile options.

It would be helpful if you posted a link to the documentation.

Basically, you are putting the libraries somewhere in your filesystem then telling the program, at compile time, where to find them.

But without seeing the documentation I can`t be anything more than very vague.

[http://code.mwcollect.org/wiki/mwcollectd/Installing](http://code.mwcollect.org/wiki/mwcollectd/Installing)

I've already installed the libraries in /usr/src/.

---


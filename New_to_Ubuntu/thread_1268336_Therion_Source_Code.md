---
title: "Therion Source Code"
date: 2009-09-16
forum: New to Ubuntu
---

### Post by CJWW1989 on 2009-09-16
Hey guys,

I have a question. I'm in a Speleology class and I am trying to install Therion, which is an open source caving survey and mapping software program. My question is. the download comes in a source code, I am still unaware as what to do with this. Can I install and run from here, or do I need to do it through a terminal? Thanks.

---

### Post by dearingj on 2009-09-16
You can install a slightly out-of-date version of Therion (version 0.5.1; the latest is 0.5.2 so not much difference) using this command:

sudo apt-get install therion

If you really do want the latest version, the source code you downloaded probably comes with a readme file which will tell you how to compile and run it.

---

### Post by CJWW1989 on 2009-09-16
Okay so I did that and it worked, but now I can't find the damned thing to open it. I realize I can use the terminal and/or the GUI. So, if anyone can give me directions for either, it'd be much appreciated. Thank you.

---

### Post by cariboo on 2009-09-16
You will probably have to create a launcher manually for it. To find where the proper is located, type:

```
locate therion
```

It should be installed in /usr/bin.

---

### Post by aarongc on 2011-07-14
I know this is an old thread now, but you probably want to run xtherion rather than therion. Can I ask where you are that has a speleology class?

---


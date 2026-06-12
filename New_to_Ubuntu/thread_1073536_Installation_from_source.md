---
title: "Installation from source"
date: 2009-02-18
forum: New to Ubuntu
---

### Post by Jeconti on 2009-02-18
Alright, I'm sick of not knowing how to do this and it's time I confess. I have no idea how to install a program if its not in the repositories or comes in deb package.

So I decided it was time to do it. Well...failed.

I'm trying to install LiVES on my desktop, which is running Ubuntu Studio. I followed the installation instructions on the website, but when it gets to checking for a gtk+2.0 package, it doesn't locate it and the installation fails.

I don't know enough about this method of installation to figure out what is wrong, so could someone help me out to better understand what I'm doing and help me figure out what's wrong.

Oh, yes, I do have the gtk+2.0 package installed on my system. At least I think. the packages I have installed all call themselves engines. Am I missing a repository where the package should be cause nothing else shows up when I search for it.

---

### Post by geirha on 2009-02-18
When you build something from source that links against a certain library, it's not enough to just have the library installed, you'll also need its corresponding -dev package. In this case it wants to link against the gtk+ lib. Try ```
aptitude search libgtk.*-dev
```
Unfortunately you get a lot of hits on that particular search, but [libgtk2.0-dev](apt:libgtk2.0-dev) should be the one you want to install.

---


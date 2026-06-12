---
title: "Post Upgrade to 10.10: Can't Run Thunderbird"
date: 2010-10-29
forum: New to Ubuntu
---

### Post by Ron Carson on 2010-10-29
I can start Thunderbird by clicking on the thunderbird shell script, but I can't run the file from the application or Docky menus. I always get a "Failed to execute child process ... permission denied".

What do I need to change?

---

### Post by bioterror on 2010-10-29
> **Ron Carson said:**
> I can start Thunderbird by clicking on the thunderbird shell script, but I can't run the file from the application or Docky menus. I always get a "Failed to execute child process ... permission denied".

What do I need to change?

Easiest and quickest tryout could be this:

> 
sudo apt-get purge thunderbird
sudo apt-get install thunderbird


If that doesnt solve our problem, we gotta dig deeper :-k

---


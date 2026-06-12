---
title: "File search"
date: 2009-05-31
forum: New to Ubuntu
---

### Post by RobHK on 2009-05-31
One area where I find Ubuntu really lacking is file search. Compared with XP or Vista, it's inflexible slow and unreliable.  Anyone have any suggestions that might help? 

At the moment I have installed a theme which has a panel image I like. I'd like to use it with other themes, but I don't know where it's stored. I tried to search for ".png" from /usr/share but it took ages then froze. Anyone know more exactly where to look?

---

### Post by binbash on 2009-05-31
It may be located at /usr/share/themes or .themes folder.It is better to use CLI and find command >> man find

---

### Post by Gen2ly on 2009-05-31
```
find /usr/share -type d -name <themename>
```

This will search for directories use 'f' instead of d to look for files.  You could look for *.png but that would yield alot of results.

---

### Post by superprash2003 on 2009-05-31
use google desktop , really fast search..

---

### Post by andrew.46 on 2009-06-01
Hi RobHK,

I see several have mentioned 'find' which is part of the GNU findutils package. I suspect you may find the man page a little impenetrable as I certainly did when I first read it. So I wrote a guide that I believe makes it all a little easier:

Linux Basics: A gentle introduction to 'find'
[http://ubuntuforums.org/showthread.php?t=1128937](http://ubuntuforums.org/showthread.php?t=1128937)

Let me know if you find this at all useful.

Andrew

---

### Post by nothingspecial on 2009-06-01
> **andrew.46 said:**
> Hi RobHK,

I see several have mentioned 'find' which is part of the GNU findutils package. I suspect you may find the man page a little impenetrable as I certainly did when I first read it. So I wrote a guide that I believe makes it all a little easier:

Linux Basics: A gentle introduction to 'find'
[http://ubuntuforums.org/showthread.php?t=1128937](http://ubuntuforums.org/showthread.php?t=1128937)

Let me know if you find this at all useful.

Andrew

And what an excellent guide it is if I may say so.

---

### Post by andrew.46 on 2009-06-01
Hi nothingspecial,

> **nothingspecial said:**
> And what an excellent guide it is if I may say so.

Not only may you say it, but I strongly encourage you to say it :-). The 'find' guide is part of a projected 12 part series that will take a little while to complete.

Andrew

---

### Post by nothingspecial on 2009-06-01
> **andrew.46 said:**
> Hi nothingspecial,



Not only may you say it, but I strongly encourage you to say it :-). The 'find' guide is part of a projected 12 part series that will take a little while to complete.

Andrew

I know, I`m looking forward to the remainder. \\:D/

---


---
title: "bash question - can this be done with 'find'?"
date: 2009-05-10
forum: New to Ubuntu
---

### Post by deamo on 2009-05-10
Hello everyone, first post here. I've been using Ubuntu for two months or so now and, unlike the previous times, have actually managed NOT to switch back to, er, 'THE operating system'. 

I've been trying to focus on doing stuff via the shell, and I recently came across something I wanted to do, which I just couldn't figure out. 

Here's the thing: I want *find *to, um, find all the folders that contain a certain type of file (specifically, right now, MP3 files) so I can move all of them to the same place or something. Not the files but the folders. 

I'm not sure how to do this. *find -iname *mp3 -type d *of course doesn't work, and well that's basically where my imagination ends. 

How would you go about setting this up, if it is at all possible? Hit me with all you've got :), if there's something I can't understand I'll look it up. 

Thanks!

---

### Post by hw-tph on 2009-05-10
Quick and ugly...
```
find . -iname "*.mp3" -exec dirname {} \; | sort -u
```

---

### Post by deamo on 2009-05-10
> **hw-tph said:**
> Quick and ugly...
```
find . -iname "*.mp3" -exec dirname {} \; | sort -u
```

Awesome! I didn't know about *dirname *- thanks!

---

### Post by andrew.46 on 2009-05-11
Hi deamo,

If you are keen to make a good start with 'find' perhaps you could have a look at:

Linux Basics: A gentle introduction to 'find'
[http://ubuntuforums.org/showthread.php?t=1128937](http://ubuntuforums.org/showthread.php?t=1128937)

Mind you I had not heard of 'dirname' as well :-).

Andrew

---


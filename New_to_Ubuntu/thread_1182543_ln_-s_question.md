---
title: "ln -s question"
date: 2009-06-09
forum: New to Ubuntu
---

### Post by froggyswamp on 2009-06-09
Hi folks,
my user name is "fox", I open the terminal, go to the desktop dir and create a link to the home dir (on the desktop):
```

ln -s /home/fox

```A link is created, I right-click preferences and it says "target link "/home/fox".
But when I open it in a file browser (nautilus, dolphin, thunar) the location bar says "/home/fox/Desktop/fox". I'd need just "/home/fox" - can one achieve it?

---

### Post by justleen on 2009-06-09
oeps, mis read your question *blush*

---

### Post by BackwardsDown on 2009-06-09
> **froggyswamp said:**
> But when I open it in a file browser (nautilus, dolphin, thunar) the location bar says "/home/fox/Desktop/fox". I'd need just "/home/fox" - can one achieve it?

Thats just how they work I think. The file /home/fox/Desktop/fox/file.txt is exactly the same file as /home/fox/file.txt because of the symlink.

---

### Post by Dougie187 on 2009-06-09
I agree, I think they just work like that. Most people use it because you want to be able to go int othe symlink like it was a directory, and then follow your path back out. If you go into a terminal though, and you go into ```
/home/fox/Desktop/fox
``` and type ```
pwd
``` it should say ```
/home/fox
```

---

### Post by PmDematagoda on 2009-06-09
I don't really see how this thread has anything to do with programming. Therefore this thread is moved to the Absolute Beginner Talk section.

---


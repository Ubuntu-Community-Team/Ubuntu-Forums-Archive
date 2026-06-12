---
title: "Curiosity about Forkbomb"
date: 2010-04-07
forum: New to Ubuntu
---

### Post by shiv379 on 2010-04-07
Hi all :)
So I was reading the excellent [post]("http://ubuntuforums.org/announcement.php?a=54") by JDONG RE: malicious commands in posts, and I saw something I don't understand: the forkbomb...
**CODE REMOVED**

Could someone explain what exactly is happening with this line of code? My best guess is that it's something along the lines of :() being equivalent of "if true", and {} encapsulating the "then" code, finally ;: being an empty else clause. Am I on the right path? And if so, what does the ":|:&" mean? I vaguely remember the & meaning something about running a process in the background?

~Shiv

---

### Post by lvleph on 2010-04-07
It creates a bunch of forked do nothing processes very fast.

---

### Post by PocketDog on 2010-04-07
[http://www.cyberciti.biz/faq/understanding-bash-fork-bomb/](http://www.cyberciti.biz/faq/understanding-bash-fork-bomb/)

You may want to remove that code from your post, it isn't necessary for the understanding of the question, and it can only do harm. I can't say if you'll be banned but it's a possibility. :)

---

### Post by takisan on 2010-04-07
It just launches two instances of itself until the computer runs out of RAM.

---

### Post by shiv379 on 2010-04-07
> **PocketDog said:**
> [http://www.cyberciti.biz/faq/understanding-bash-fork-bomb/](http://www.cyberciti.biz/faq/understanding-bash-fork-bomb/)

You may want to remove that code from your post, it isn't necessary for the understanding of the question, and it can only do harm. I can't say if you'll be banned but it's a possibility. :)

Thanks for the warning, I didn't think it would be a problem since was quoting another user but I've removed the code and linked to the original post instead :)

Thanks for the link, that explained what I wanted to understand :) I love Bash, but sometimes I'm a left in the dark with the more advanced syntax and stuff :)

~Shiv

---

### Post by mick222 on 2010-04-07
I just used the code not a good idea. But no real harm done. Please don't try it unless you don't mind messing up your system mods will probably close this soon.

---

### Post by mick222 on 2010-04-07
By the way is there a way to block commands that you think are dangerous to your system.

---

### Post by CharlesA on 2010-04-07
Limit the number of processes that can be running.

---

### Post by mcduck on 2010-04-07
> **CharlesA said:**
> Limit the number of processes that can be running.

...and don't run commands if you don't know what they do. And of course don't give admin rights (or, really, any access) to people you don't trust. ;)

---


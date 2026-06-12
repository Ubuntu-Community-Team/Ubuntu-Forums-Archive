---
title: "terminal persistent command"
date: 2011-09-03
forum: New to Ubuntu
---

### Post by Pragu on 2011-09-03
Hi all, very easy question: Is there a way for you to run a command in a terminal shell, and then quit the shell without the command stopping.

For example, if I want caffeine, I run "caffeine -a". If I want to use that shell for other things, "caffeine -a &" but what if I want caffeine to run even when the terminal closes?

---

### Post by Tank Jr on 2011-09-03
I would try the nohup command. I think it stands for 'no hang up'.
```
$nohup kaffeine &
```

---

### Post by Pragu on 2011-09-03
That's  exactly what I was looking for. You sir, are a gentleman and a scholar.

---


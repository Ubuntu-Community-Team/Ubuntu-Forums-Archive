---
title: "server - exited tty and have no command prompt"
date: 2009-03-05
forum: New to Ubuntu
---

### Post by versai on 2009-03-05
so i ran a couple of commands and they got hung up. switched to another virtual console for a while to see if the command would complete. never did.

used
```
kill -HUP processid
```
replaced processid to an actual non-responsive process and switched back to the non-responsive console. it had said "hung up" and was back to command.

then switched back to tty2 and said "exit"

back to tty1

back to tty2 and i receive no command prompt, just a blinking underscore.

any thoughts?

versai

---

### Post by Xiong Chiamiov on 2009-03-07
Exit will log you out of a tty; you should get a login prompt again, though.  Usually the blinking cursor means that nothing's running on there.

I find pkill and killall much easier to use than kill, since you can specify processes by name.  Also, using GNU screen is more convienent than switching ttys.

---


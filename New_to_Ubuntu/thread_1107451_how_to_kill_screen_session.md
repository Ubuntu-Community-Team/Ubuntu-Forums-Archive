---
title: "how to kill screen session"
date: 2009-03-26
forum: New to Ubuntu
---

### Post by flylehe on 2009-03-26
Hi,

I am trying to kill screen session while under it, but "Ctrl-a Ctrl-\" doesn't work.

Also to kill several screen sessions that are detached, I searched online and found people using "screen -X kill" but I get "Use -S to specify a session."

Thanks!

---

### Post by yeats on 2009-03-26
Ctrl-D should do it.

---

### Post by flylehe on 2009-03-26
Thank you!
How about the second question:
> Also to kill several screen sessions that are detached, I searched online and found people using "screen -X kill" but I get "Use -S to specify a session."

---

### Post by williane on 2009-03-26
Use "screen -ls" to get a list of running sessions.

then use "screen -X -S {session # you want to kill} kill"

I actually just wrote a post (see sig) about a really similar issue. Only my problem was I was wanting to rename detached sessions. -X -S is the key.

---

### Post by flylehe on 2009-03-26
Thanks! 
If I want to kill all detached sessions, how to specify in "screen -X -S kill"?

---

### Post by williane on 2009-03-26
Umm I'm actually not sure how you will kill all sessions. I would think killing screen itself would do that. Just repeat that command changing the session number each time. Unless you have ton of sessions it shouldn't take long.

Edit, ooh did you mean just kill detached sessions? Yeah, I'm not sure. Just kill each session # with (detached) in the "screen -ls" list.

---


---
title: "tty"
date: 2009-06-12
forum: New to Ubuntu
---

### Post by arneman on 2009-06-12
Is it possible to go the tty, logon as a different usere and when you got back to X be logged on as that user?

---

### Post by ugriffin on 2009-06-12
Not that I am aware of. If you login to the terminal and then start X on it (this is assuming X is down), there will still be a login promt because it changes from session to session (tty1 or whatever to tty7).

You'd have to find a way to start X on your same terminal session and maybe it could then load logged in. Which I doubt.

---

### Post by arneman on 2009-06-12
Ok, thanks for the quick reply ;)

---

### Post by jward3010 on 2009-07-01
I don't mean to impose myself on somebody else's thread but I'm wondering what the "tty" spaces are useful for. Possibly something to do with running multiple commands on the one system and having different terminal workspaces to work with but I'm not sure and can they be used in relation to killing a command or app in another workspace? If I get my head together on this I'll set up a separate thread and get the hell out of here.

---


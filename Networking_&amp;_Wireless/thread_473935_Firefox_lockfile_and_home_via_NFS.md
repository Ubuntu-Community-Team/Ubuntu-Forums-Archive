---
title: "Firefox lockfile and /home via NFS"
date: 2007-06-14
forum: Networking &amp; Wireless
---

### Post by _mrv on 2007-06-14
Hi!

I have a setup where my primary computer (A) has exported /home via NFS and secondary computer (B) mounts the /home from A during the boot. Most of the applications seem to be working just fine, but Firefox is causing me grey hair; when I'm logged in both computers at the same time I can only start Firefox session on one computer. This is because the lockfile of Firefox is located under user profile in .mozilla/firefox.

Does anybody know if it would be possible to change the location of Firefox lockfile or some other workaround? I really like the setup, because most of the time my wife occupies the other computer and this way I'm still able to access my files etc. in the familiar environment :)

Br,
 _mrv

---

### Post by linux noooob on 2007-06-14
you could try reinstalling it on the other computer or use a different web browser on the other computer.

---

### Post by _mrv on 2007-06-14
Hi!

Thanks for your suggestions, but I think that reinstalling the browser doesn't really solve anything.

I could of course create another profile in Firefox, but then I would lose all my bookmarks etc.

Maybe I can take a look at Firefox sources and hack some kind of solution/workaround. Can anybody give some pointer to the source tree so I wouldn't have to spent so much time to inspect the source tree?

EDIT: Does anybody know how complex the source tree of Firefox actually is? I was thinking that maybe I could hack it to save the lockfile into /var/lock instead of user's home directory.

 _mrv

---

### Post by kenboo on 2008-04-19
I hit the same problem as yours.  It's easy to hack the lock file name to something like hostname.pid but the real problem, I guess, is that FF uses SQLlite which doesn't allow concurrent access.

---

### Post by niten on 2008-07-03
I'm running into this problem, too.

That's a good point, kenboo....would it be possible to lock on a file-by-file basis, and only when writing?

Of course, that could cause issues of one of the systems crashed while writing...but you could have some sort of timeout.  And it would only occur on NFS-home systems, anyway, so it'd be a big improvement on the current situation.

---


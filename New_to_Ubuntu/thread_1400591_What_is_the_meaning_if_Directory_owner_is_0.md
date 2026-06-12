---
title: "What is the meaning if Directory owner is 0?"
date: 2010-02-07
forum: New to Ubuntu
---

### Post by raziiq on 2010-02-07
Hi there.

I have seen some directories in different UNIX systems like in uBuntu and in Mac OS X and even in iPhone OS also, which have owner 0. What does this mean?

How can i make 0 the owner of some directory? Any command for it?

---

### Post by The Cog on 2010-02-07
0 is the userid of the user root. Nautilus usually looks up the userid and shows you the user name instead. But when you use sftp to look at a remote machine, the remote machine's username<->userid relationship might be different, so nautilus shows you the numeric userid instead.

So if you were logged onto that remote machine directly, you could change the ownership to root in the normal way, with **sudo chown root filename** or with a root nautilus. I haven't played with changing ownerships using sftp so I don't know what the limitations and gotchas are.

---


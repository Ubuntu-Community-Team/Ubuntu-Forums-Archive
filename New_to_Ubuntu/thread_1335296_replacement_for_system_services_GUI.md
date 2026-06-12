---
title: "replacement for system services GUI?"
date: 2009-11-23
forum: New to Ubuntu
---

### Post by bodhidharma on 2009-11-23
is there one?  Where is it?

THANKS!

---

### Post by bodhidharma on 2009-11-23
Sorry, I've been surfing the net and getting frustrated and
I made an indecipherable post.  What I meant to say was:

I just upgrade to Karmic Koala.  Oddly enough, I find there
is no longer a "System Services" in System>Administration.
Apparently this is because of a change in the booting
process and likewise for the starting and stopping of
services -- but I wonder if there is a simple, graphical
access to this new mechanism?

I would spend the time tinkering with scripts and learning
about the new boot process, etc., except (a) I don't really
have time just now and I want to be sure I'm not running
really any services (best way to be secure is not to offer
any services, is a motto I've heard); and (b) I have friends
and relatives who *will not ever* take the time to learn
how the scripts, etc., work, but it would be nice if they,
also, could have easy control of what their machines are
offering to the 'net.

So: any suggestions?  I've seen references to some package
called "bum", is this what I'm looking for?

Thanks in advance!

---

### Post by ukripper on 2009-11-23
install rcconf and run it in terminal 
```
rcconf
```

or use BUM:

```
sudo apt-get install bum
```

---


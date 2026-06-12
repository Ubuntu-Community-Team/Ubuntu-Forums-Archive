---
title: "Help with Ipod - unable to  mount"
date: 2011-05-08
forum: New to Ubuntu
---

### Post by djb6 on 2011-05-08
So when I plug in my IPOD Touch 4g, I get this message started with saying unable to mount my ipod:
> DBus error org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)

I'm new to linux and don't really understand what this means.

It worked one time and since then, I can not get it to mount.  I looked around and couldn't find anything to help me with this.  I'm sure IPOD stuff is talked about ALOT on here but I'm still at a loss.

Thanks for any help!

---

### Post by djb6 on 2011-05-08
New development: I created another user for myself to just see what would happen and it mounts there without any problem.  Not sure if that is helpful, but thought I would share.

---

### Post by Not unique on 2011-05-08
How old is your distro (Operating System)? Have you had previous problems? and do you have any specialist specific software for your Ipod on Ubu?

---

### Post by djb6 on 2011-05-08
I'm using Ubuntu 11.04, and nothing special on the IPOD.

---

### Post by rosencrantz on 2011-05-08
If it works with a different user, it looks like a config error. Good news, it's certainly fixable (worst case: migrate your settings piece-by-piece to the other user). Bad news, it's pretty time consuming to figure these out.
I'd start with checking user and group permissions: is there any difference between your user and the test user?

---


---
title: "change name of server?"
date: 2010-09-08
forum: New to Ubuntu
---

### Post by supermooshman on 2010-09-08
Hi all,
first off all, yes I am ashamed to come with this problem...

I just installed lucid lynx server, but I gave the wrong name (I started the name with a capital)

is it possible to change this?
it is a fresh install, but don't want to do a wipe

Thanks!

---

### Post by bodhi.zazen on 2010-09-08
Become root

```
sudo -i
```Edit /etc/hostname and /etc/hosts

```
nano /etc/hostname /etc/hosts
```Change the hostname in both files

log out or start a new shell. The effects should be immediate, you may need to restart Apache.

---


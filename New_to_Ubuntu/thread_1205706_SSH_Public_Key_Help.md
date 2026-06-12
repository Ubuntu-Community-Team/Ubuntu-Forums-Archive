---
title: "SSH Public Key Help"
date: 2009-07-06
forum: New to Ubuntu
---

### Post by Augsburg on 2009-07-06
Hello.

I am looking for an easy how-to for setting this up. I am creating a monitoring tool, and need to setup nodes in my network by ssh-ing to them. I would like to then send them an ssh-key so that they won't ever be asked to add this host to known_hosts. Is there an easy way to do this? Thanks!

---

### Post by ubudog on 2009-07-06
The easiest way I know is to scp your key to the authorized_keys folder in .ssh on the other computers that you want to ssh into.

---


---
title: "ecryptfs-mount-private secure??"
date: 2010-10-17
forum: New to Ubuntu
---

### Post by bbala2020 on 2010-10-17
Hi 
i used ecryptfs to save important files in Ubuntu 10.04. It created a folder called Private in my home directory and it worked fine. Now i installed ubuntu 10.10 in another partition and it shares the same home directory. I have the same username with same password. 
I thought I wouldnt be able to see my private directory but surprisingly it just worked fine and Im able to mount and unmount from here.
So anyone who gets access to my hard disk can access those files? or is it because of the same password? if i change my password, the contents will be secure?

---

### Post by robsoles on 2010-10-18
It is working because you retained your entire /home structure between versions and your home folder (~/ not /home) isn't encrypted.

If you make a new user (second user, don't delete main user account in either version!) and give them the same password as your main user you should find that they cannot access the data without the encryption hash that your login is unlocking out of your ~/ (home) directory - of course you can't give the second user the same username as the main user.

It is as secure as encryption can make it.

---


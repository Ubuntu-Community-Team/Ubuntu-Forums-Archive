---
title: "Change root permissions on my backup drive"
date: 2009-04-27
forum: New to Ubuntu
---

### Post by conphara on 2009-04-27
Hey

A long story short. I have moved all my files to a backup drive but the folders and files only have root permission and not under my username. Happened during a move using a live cd and I had to use sudo nautilus to move the content.
Is there a simpel terminal command that will change the permission to my username and not root?

---

### Post by MrWES on 2009-04-27
> **conphara said:**
> Hey

A long story short. I have moved all my files to a backup drive but the folders and files only have root permission and not under my username. Happened during a move using a live cd and I had to use sudo nautilus to move the content.
Is there a simpel terminal command that will change the permission to my username and not root?

```
sudo chown username:username /path/to/files
```
and if you have subdirectories in play user the -r flag

Bill

---


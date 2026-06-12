---
title: "Installing wamp"
date: 2009-12-27
forum: New to Ubuntu
---

### Post by mgbear on 2009-12-27
I installed Ubuntu a few hours ago & really like it. On XP I had a server That I installed called WAMP (simulating a real server) Is their such a program available in Ubuntu

mgbear

---

### Post by Cheesemill on 2009-12-27
WAMP stands for **W**indows **A**pache **M**ySQL **P**HP.

The equivilent for linux is (suprisingly) called LAMP (**L**inux **A**pache **M**ySQL **P**HP) and actually existed first.

You can install the LAMP stack on a Ubuntu machine by opening a terminal and typing:
```
sudo apt-get install lamp-server^
```Yes, the caret (^) is meant to be there.

Then just put your web files in /var/www and your ready to go.

---


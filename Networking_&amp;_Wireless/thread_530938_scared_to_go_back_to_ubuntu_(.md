---
title: "scared to go back to ubuntu :("
date: 2007-08-21
forum: Networking &amp; Wireless
---

### Post by rkakkar on 2007-08-21
don't get me wrong, i LOVE ubuntu. but i'm scared to go back to it now. I recently got a d-link wireless lan card. I wanted to installed kubuntu feisty. however during the installation process, my cpu would shut down automatically and on retrying, sometimes, on boot kubuntu would throw the following message:

BUG: soft lockup detected on CPU#2

after this happened a couple of times, i found out that my cpu fan stopped working!!!! i'm sure kubuntu did that somehow because i did not face any problem when i had windows...

i did a search for this problem and found out that ubuntu in general has this problem with wireless lan cards and that there is NO fix until a new kernel is out.

i want to try ubuntu feisty now but i can't afford my new cpu fan to fail again. anyone else faced this problem with wireless lan cards?

---

### Post by tak1150 on 2007-08-21
I'm not 100% sure this is relevant, but if you modify /etc/hosts file
```
sudo gedit /etc/hosts
```
and modify this line:
```
127.0.0.1 localhost
```
to
```
127.0.0.1 localhost *hostname*
```
Where "hostname" is your hostname.
This is a bug w/ Feisty that causes excessive heat related (presumably fan related as well) problems for my laptop. Once I did the above, the problem lessened by a lot.

---

### Post by rkakkar on 2007-08-21
Thanks man! I hope this works. Btw, how do I find out my hostname? I hope its not a problem with the make / model of my wireless card.

---

### Post by tak1150 on 2007-08-21
open your terminal. it would say

```
you@yourhostname:~$
```

---


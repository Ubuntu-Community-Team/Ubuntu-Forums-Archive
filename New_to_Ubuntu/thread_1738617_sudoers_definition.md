---
title: "sudoers definition"
date: 2011-04-25
forum: New to Ubuntu
---

### Post by node2network on 2011-04-25
I'm not good at English. Please answer easy English.:D

I'm editting /etc/sudoers. This file is too complicated to understand.

Format
```
user/group machine=(user) command
```

Set up as follows.
```
hoge 192.168.0.10=(ALL)NOPASSWD:/usr/bin/apt-get
```

I think only my computerA can execute 'apt-get' command, but it doesn't quite work as expected.
In computerB(192.168.0.20), execute 'ssh -t hoge@1921.168.0.10 sudo apt-get update'. 'apt-get update' is finished safely from computerB!

I don't know the meaning of this parameter, and how to use this?

---

### Post by rosencrantz on 2011-04-25
See this discussion:
[http://www.readmespot.com/question/f/90166/defining-hosts-in-sudoers-file](http://www.readmespot.com/question/f/90166/defining-hosts-in-sudoers-file)
If you are logged in via ssh on A, you are an authenticated user on A, even if you are sitting in front of B. You'll just not be able to run apt-get on B itself.

---


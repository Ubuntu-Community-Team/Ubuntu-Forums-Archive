---
title: "grep displays usage help response for searches that should work"
date: 2011-03-21
forum: New to Ubuntu
---

### Post by fejimush on 2011-03-21
I've used the follow commands before but they don't seem to work with 10.04 on my machine.

```
netstat -a | grep ftp
```
```
ps aux | grep someprocess
```

The response is a page and a half of the correct usage.

It works on my coworker's 10.04 setup.   I'm not sure how to troubleshoot this problem.

Thanks,
graham

---

### Post by DaithiF on 2011-03-21
is your grep aliased to something ?

in terminal, do:
```
type grep
```

---

### Post by fejimush on 2011-03-21
Wow thanks!  Here's the ouput:

```
user@user-laptop:/$ type grep
grep is aliased to `grep --color=auto/usr/share/gnuh8300_v10.03_elf-1/bin'
greitz@greitz-laptop:/$ 
```

I had set up a tool chain using eclipse for a Hitachi micro a few weeks ago.  Apparently it has set up some aliases in a rather undesirable way.   

Any ideas how I might be able to fix this and search for what other aliases have been created under the hood?  

I'm a little out of my element.

Kindly and thanks!
graham

---

### Post by DaithiF on 2011-03-21
have a look in the .bashrc file in your home directory.  other locations could include .profile or .bash_profile in your home dir, or /etc/profile, or /etc/bash.bashrc

---


---
title: "Broken package system"
date: 2010-10-22
forum: New to Ubuntu
---

### Post by Meliority on 2010-10-22
I installed Ubuntu for the first time and tried to get my first round of updates but the package system is broken. It has asked me to check if I am using third party repositories and I can only assume that I am not. There are no peripherals connected and Ubuntu was given the entire drive on my dell inspiron 1520.

The error message instructed me to run the command "apt-get install-f" in a terminal. This resulted in the error message 

E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root? 

Under the details tab it lists "libc6 libc6-dev".

I am feeling a little over my head since my prior experience with unicode is an intro to C++ using putty and emacs to scare us geology students away from trying to 'help' the IT department.

It wouldn't be surprising if the downloaded update was corrupt from connection interruption as my next issue to fix (or perhaps it should be first?) is frequent wireless dropping.

Also, I suppose its worth noting that the dell is completely sacrificial. Trying Ubuntu is just an experiment in learning more about computer systems in general so risky solutions are totally fine.

---

### Post by alexandari on 2010-10-22
you need to have root rights in order to execute such commands


```
sudo apt-get install -f 
```

---

### Post by Meliority on 2010-10-22
Awesome, where might I look up/ browse other commands I can use in the terminal?

---

### Post by alexandari on 2010-10-22
[http://ubuntuforums.org/showthread.php?t=73885](http://ubuntuforums.org/showthread.php?t=73885) 

Check this out :) There are many sites/threads about basic terminal commands

---


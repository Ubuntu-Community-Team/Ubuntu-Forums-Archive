---
title: "installed moblock, now synaptic won't run"
date: 2009-06-10
forum: New to Ubuntu
---

### Post by cwnobogie on 2009-06-10
Unable to get exclusive lock

This usually means that another package management application (like apt-get or aptitude) is already running. Please close that application first.


^ that is the message I get when trying to open synaptic manager. i opened aptitude and have 5 new packages. what do i do with them? 
any ideas what is going on?
i cannot add/remove programs either

---

### Post by michy99 on 2009-06-10
First, make sure that you don't have any package management program open That includes Synaptic Package Manager, Add/Remove, Update Manager, aptitude, apt-get. Then run this in a terminal and post any error message you get```
sudo apt-get update
```

---

### Post by cwnobogie on 2009-06-11
i couldn't figure out how to determine if an apt program was running. so i reinstalled ubuntu. i don't understand enough yet to install moblock and make it work with everything else.

---


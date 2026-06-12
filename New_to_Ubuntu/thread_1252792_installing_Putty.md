---
title: "installing Putty"
date: 2009-08-29
forum: New to Ubuntu
---

### Post by ~The~Killer~ on 2009-08-29
Hi.

Till Now i Failed to update my FF, and I failed to install anything.

ANyway Please i need help installing putty please tell me step by step how to do it ? Please make it simple because all the tutorials are really hards so far.

Thanks

---

### Post by halitech on 2009-08-29
do you need to do ssh from the ubuntu computer or from a windows computer?

Most programs are just a matter of opening Add/Remove and selecting it.

---

### Post by NoaHall on 2009-08-29
No, they aren't a matter of Add/Remove, because that only contains software that is supported. Unless you add your own, which many programs don't.

It looks like you'll have to compile it yourself...

cd /home/$yourusername/$whereeverthefilesare
make
make install

---

### Post by halitech on 2009-08-29
> **NoaHall said:**
> No, they aren't a matter of Add/Remove, because that only contains software that is supported. Unless you add your own, which many programs don't.

It looks like you'll have to compile it yourself...

cd /home/$yourusername/$whereeverthefilesare
make
make install

Add/remove or synaptic is the best way of getting software and while I don't have an exact number, with over 20,000 programs available, it is the best and easiest way for a newer user to get programs.
 
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by bear24rw on 2009-08-29
open a terminal type
```
sudo aptitude install putty
```
done.

---

### Post by bodhi.zazen on 2009-08-29
Putty is in the repositories and if it does not show on apt-get, add/remove, or synaptic you probably simply need to enable your repositories (universe and multiverse).

It installs and runs in Linux with no problem.

As has been stated though, ssh is "built in" to Linux, simply open a terminal and

```
ssh user@server
```

Putty can be nice if you wish a graphical interface to manage your connections, servers, keys, and options.

[Repositories/Ubuntu - Community Ubuntu Documentation]("https://help.ubuntu.com/community/Repositories/Ubuntu")

---


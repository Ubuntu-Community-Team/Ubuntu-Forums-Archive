---
title: "unable to install updates"
date: 2009-01-12
forum: New to Ubuntu
---

### Post by brian mellett on 2009-01-12
Problem using ubuntu 8-10- When installing updates, or entering codes into a terminal I get the message "error occurred E: dpkg was interupted you must manually run dpkg --configure -a" to correct problem. E: -cache->open() failed please report. I have reported this and looked at answeres to similar super user error messages but  when I enter password in root it is refused.Cannot now accept any updates. I'm new to Linux and do not understand Geek language but can follow instructions Thanks brian::KS

---

### Post by oilchangeguy on 2009-01-12
> **brian mellett said:**
> Problem using ubuntu 8-10- When installing updates, or entering codes into a terminal I get the message "error occurred E: dpkg was interupted you must manually run dpkg --configure -a" to correct problem. E: -cache->open() failed please report. I have reported this and looked at answeres to similar super user error messages but  when I enter password in root it is refused.Cannot now accept any updates. I'm new to Linux and do not understand Geek language but can follow instructions Thanks brian::KS

in the terminal type sudo dpkg --configure -a and press enter.

---

### Post by wolfen69 on 2009-01-12
```
sudo dpkg --configure -a
```

---

### Post by drs305 on 2009-01-12
Normally this is simply solved with:
```

sudo dpkg --configure -a

```
Since you have read other posts you know you won't see your password as you type.

You say your password is refused. Can you run any other sudo commands, such as:
```

sudo blkid

```

If you cannot run any sudo commands, if you type the following are you listed in the *admin* group?
```
groups
```
You should see something like: 
```
your.user.name adm dialout cdrom plugdev lpadmin admin sambashare
```

---

### Post by brian mellett on 2009-01-18
Thanks for help, I am getting the hang and running "dpkg --configure etc. has allowed downloads etc. Many thanks every one. brian mellett

---

### Post by tegnoto89 on 2009-01-18
I think that's a broken package - open Synaptic and go to the "broken" filter under "custom filters" and see if anything's there.  If there are broken packages, just go to Edit - Fix broken packages.

---


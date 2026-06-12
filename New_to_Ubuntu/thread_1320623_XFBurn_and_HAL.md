---
title: "XFBurn and HAL"
date: 2009-11-09
forum: New to Ubuntu
---

### Post by coldReactive on 2009-11-09
xfburn gives me this error when it tries to use hal:

```
ian@psumi:~$ xfburn
** Message: No existing settings file, using default settings
** Message: Using Thunar-VFS 1.0.1
** Message: Using HAL

** (xfburn:6246): WARNING **: Could not get list of devices from HAL: The name org.freedesktop.Hal was not provided by any .service files
Segmentation fault
```

So I can't use xfburn. How do I fix this issue?

---

### Post by coldReactive on 2009-11-10
Bug Report: [http://bugzilla.xfce.org/show_bug.cgi?id=5965](http://bugzilla.xfce.org/show_bug.cgi?id=5965)

---

### Post by XubuRoxMySox on 2009-11-10
I think that was one of the reasons that Xubuntu Karmic ships with Brasero instead of XFBurn. 

K3b is the best CD burning utility I've tried in Linux so far. It's flawless. The only thing I'd like to see them change is to offer slower burn speed.

-Robin

---

### Post by coldReactive on 2009-11-10
> **dixiedancer said:**
> I think that was one of the reasons that Xubuntu Karmic ships with Brasero instead of XFBurn. 

K3b is the best CD burning utility I've tried in Linux so far. It's flawless. The only thing I'd like to see them change is to offer slower burn speed.

-Robin

lubuntu comes with xfburn however.

---

### Post by mr_pouit on 2009-11-11
Hi,

You should check if 'hal' is installed (if not, install it with "sudo apt-get install hal"), and that it is running (if not, you can start it with "sudo start hal"). Xfburn works perfectly with hal and without devicekit here...

---

### Post by coldReactive on 2009-11-11
> **mr_pouit said:**
> Hi,

You should check if 'hal' is installed (if not, install it with "sudo apt-get install hal"), and that it is running (if not, you can start it with "sudo start hal"). Xfburn works perfectly with hal and without devicekit here...

HAL is installed. That's why it said "Ubuntu comes without **_*complete*_** hal support."

---

### Post by mr_pouit on 2009-11-11
Hal is probably not running on your system, and this shouldn't happen (crash, etc.). Moreover, xfburn should be able to handle this without crashing too. But anyway, there is complete hal support...

---

### Post by coldReactive on 2009-11-11
> **mr_pouit said:**
> Hal is probably not running on your system, and this shouldn't happen (crash, etc.). Moreover, xfburn should be able to handle this without crashing too. But anyway, there is complete hal support...

It didn't crash, as wodim (ie: brasero) was able to burn when xfburn couldn't.

---


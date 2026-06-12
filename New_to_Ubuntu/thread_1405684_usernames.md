---
title: "usernames"
date: 2010-02-12
forum: New to Ubuntu
---

### Post by BryanAbel on 2010-02-12
Anybody know of a way to override the username and password when turning the system on? I had a coworker install the Linux Mint sysem on my computer, but she cannot remember the codes. I do not have any disk. I would like to login and change the codes. Please help.

---

### Post by theozzlives on 2010-02-12
> **BryanAbel said:**
> Anybody know of a way to override the username and password when turning the system on? I had a coworker install the Linux Mint sysem on my computer, but she cannot remember the codes. I do not have any disk. I would like to login and change the codes. Please help.

I know how to in Ubuntu, why don't you try Mint's forums.

---

### Post by pizza-is-good on 2010-02-12
There might be a way to do what you want, but I don't know about it.

My reasoning tells me that without the root password, there will be no way to 'hack' it, considering how secure lunix OSs are.


I would just recommend that you do a fresh install of whatever OS you want. That will erase Mint, and let you install it again, where you can choose your own password.

---

### Post by jken146 on 2010-02-12
[http://ubuntuforums.org/showthread.php?t=1405676](http://ubuntuforums.org/showthread.php?t=1405676)

---

### Post by Vishal Agarwal on 2010-02-12
most of the nix systems give the root access while booting. while booting the machine, press the tab key at boot screen, and you will get clue. You need to boot the machine in single user mode and change the password with passwd command at  command prompt.  Try if you can recover from there. I don't have clear Idea, because I did it years ago with my RED system.

---

### Post by cariboo on 2010-02-13
Have a look at [this]("http:///www.psychocats.net/ubuntu/resetpassword") howto. If you aren't sure of the username, once at the prompt, type:

```
ls /home
```

the name in that directory should be your username. BTW there are no codes needed, just regular Linux commands.

---


---
title: "charged battery no boot Ubuntu"
date: 2009-02-28
forum: New to Ubuntu
---

### Post by hollowtd on 2009-02-28
Do you have any idea why my 100 charged battery will not power up Ubuntu? It will only start when it's plugged in? Is there a bug? I am just flabergasted as when it's plugged in, the computer boots with Ubuntu just fine. Very strange.

---

### Post by sydbat on 2009-02-28
More info is needed. Like what kind of laptop is it? How old is it?

Laptop batteries have a finite life, so yours could be completely dead and you may need a new one. If it is a new(er) laptop, is it still under warranty so you can have the manufacturer send you a new one?

---

### Post by Iowan on 2009-02-28
What happens if you power-up plugged in - then unplug?

BTW, there's another thread around here (in Networking?) about a network card that only works when laptop is plugged in...

---

### Post by hollowtd on 2009-02-28
If I power-up while plugged in, Ubuntu loads fine. If I shutdown, unplug the laptop, then turn the power on, the screen turns on, Ubuntu bounces around that little orange square and then it freezes. The battery holds charge and is not new but works great and holds power. It's at 100%. The computer works fine after Ubuntu is loaded and I unplug it. The computer is a dell d600 latitutde running Windowxs xp and Ubuntu Ibex 8.10. It really makes no sense to me.

---

### Post by unutbu on 2009-02-28
Perhaps you are experiencing this bug:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/146702](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/146702)

If you think it is the same bug, then the best thing to do would be to read [How to report a kernel bug]("http://wiki.ubuntu.com/KernelTeamBugPolicies"), and post a message in the [bug thread]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/146702") with a description of your hardware, kernel version and problem.

---

### Post by hollowtd on 2009-02-28
I will check that out. Sounds very similar but not exactly. Thanks and I'll let you know. Is is possible to "install" the kernel they are talking about in the lower threads??

---

### Post by unutbu on 2009-02-28
To check which kernel you are currently running, open a terminal (Applications>Accessories>Terminal) and type
```

uname -a
```

Since you mentioned that you are running Ubuntu 8.10, you probably are already using the 2.6.27 kernel mentioned by Leann Ogasawara.

---

### Post by hollowtd on 2009-03-01
terry@terry-laptop:~$ uname -a
Linux terry-laptop 2.6.27-11-generic #1 SMP Thu Jan 29 19:24:39 UTC 2009 i686 GNU/Linux
terry@terry-laptop:~$ 

(This is what is says when I type that in. I think you're right, I'm using the 2.6.27.11-generic #1 (Hope generic doesn't mean bad here.)

---

### Post by freak42 on 2009-03-01
what happens if you choose the safe boot option in your grub boot list (you might need to hit esc right after starting the machine to get to the menu).

if it stalls/freezes what are the last lines of output given?


hth

---

### Post by hollowtd on 2009-03-01
If I go to the safe mode, it will load and then I if I push cancel, it will then start up. There are no last lines of output, the orange things stops at about 2.5 bars and freezes there.

---


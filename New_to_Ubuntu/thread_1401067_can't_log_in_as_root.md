---
title: "can't log in as root"
date: 2010-02-07
forum: New to Ubuntu
---

### Post by oepott on 2010-02-07
This is a brand new install. The graphics are way out of whack, and I get a screen saying NXVIDA needs to be reset, and to do it as root. When I opened the terminal and entered my password, it said authentication failure.
 How do I log in if it won't accept my password?

---

### Post by halitech on 2010-02-07
you need to run it as gksudo nvidia-settings

there is no root user, it is sudo that gives you admin rights

---

### Post by oepott on 2010-02-07
Don't know if I did what it wanted. All I could see was "save the current settings," so that's what I went with, since there didn't seem to be any other options. Like I said, this is a fresh install, and I got a screen on start up saying that it was going into a "safe" or default graphics mode. I have no idea what the system is looking for as far as graphics, but it did request a proprietary software download before I rebooted, and the screen is oversize and sucks in on the side like an hourglass.

---

### Post by berktt on 2010-02-07
I'm new to Linux in general as well, and I was just reading the beginners guide from this forum.

You can type

```
sudo su
```

in the console, and you'll have root powers, until you type

```
exit
```

You can notice the change, before you type sudo su your username will have a $ sign next to it, which means regular user, and when you become root the $ will become a # sign, indicating root powers :)

---


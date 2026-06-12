---
title: "Disabling alt + ctrl + f1 - 6 in 10.04"
date: 2011-04-01
forum: New to Ubuntu
---

### Post by darknomel on 2011-04-01
Hi All,

I'm busy building a desktop image for users in my company and for security reasons, I don't want them to be able to access the other tty's, 1 - 6 :) I've checked the forum and all of the posts on it seem to be for OLD (5.04) versions etc.

Does anyone know a quick way to disable these?

Thanks!

---

### Post by andrewthomas on 2011-04-01
You could probably do this by commenting out

```

# start on runlevel [23]
# stop on runlevel [!23]

# respawn
# exec /sbin/getty -8 38400 tty2
```for each of the files tty1.conf to tty6.conf in /etc/init/

---

### Post by darknomel on 2011-04-02
I'll try that on Monday, I'm away from my machines at work. Correct me though, won't think just stop the terminals from being created and active? Won't the shortcut keys still take you to a blank screen?

---

### Post by andrewthomas on 2011-04-02
> **darknomel said:**
> I'll try that on Monday, I'm away from my machines at work. Correct me though, won't think just stop the terminals from being created and active? Won't the shortcut keys still take you to a blank screen?
Probably, but what security risk is a blinking cursor on a blank screen?

---

### Post by darknomel on 2011-04-03
> **andrewthomas said:**
> Probably, but what security risk is a blinking cursor on a blank screen?

Not much, but it will become an annoyance getting repeat calls on "I'm at a blinking curser on a blank screen" :P

---

### Post by darknomel on 2011-04-04
No-one?

Solved it myself.

---

### Post by vista_convert on 2011-04-15
How did you solve it? I'm working on the same problem myself. Turning off the getty services (by moving the tty* files from /etc/init) doesn't reclaim the Ctrl+Alt+Fn keys for other uses. I'm also curious about where these keys are trapped, since they clearly get eaten before Gnome sees them. 

Any help would be greatly appreciated.

---


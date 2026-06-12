---
title: "How do you switch users from the command line?"
date: 2009-01-04
forum: New to Ubuntu
---

### Post by ZootNerper on 2009-01-04
Hi Folks,

I've done a lot of searching for a command to switch users from the command line. I don't mean "su user2", but to switch like the applet in the top right corner does it.

I guess it will look like "gnome-switch-user", but I can't find anything.

-- Zoot

---

### Post by WelterPelter on 2009-01-04
*never mind*

---

### Post by ZootNerper on 2009-01-04
Hi Folks,

Well, I eventually found this command:

gdmflexiserver

which will start a new user session while keeping the current on going (not logging out).

I don't think it's the same as the switch user applet as it goes to a login screen asking for a user name, rather than a screen already knowing this and only asking for a password. But it keeps the old user session going.

-- Zoot

---

### Post by ilija139 on 2009-12-14
just use gdmflexiserver -xnest

---

### Post by cartisdm on 2009-12-14
wow, this thread is from January haha

---

### Post by natravis on 2009-12-14
Who let that necrothread back in here? Smells dead!

---

### Post by cartisdm on 2009-12-14
> **natravis said:**
> Who let that necrothread back in here? Smells dead!

hahahahahahahahahahaha maybe I'm just slow but I have never heard that before and it just made my night!:D

---


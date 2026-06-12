---
title: "network setup"
date: 2009-12-16
forum: New to Ubuntu
---

### Post by jnmjr on 2009-12-16
Hello;
I'm totally new to Ubuntu, I'm using 9.10, so far I've been able to run it and set it up
OK. My problem is I can't see my other Windex PCs on my network. Pinged them and they're there, but when I try to connect I get a message CAN'T MOUNT LOCATION, Failed to retieve sharelist from server. I'm unfamiliar with Linux commands etc, I would greatly appreciate a step by step helping hand (solution). THX.

Just want to say the Linux Community is absolutely fantastic. Great Work Guys!!!!!   

JNM:)

---

### Post by cariboo on 2009-12-16
It depends on how the shares are setup on your Windows computers, and if they are in the same workgroup. Ubuntu defaults to WORKGROUP, but you can chnge it by pressing Alt-F2 and typing:

```
gksudo gconf-editor
```

Navigate to system-->smb, right-click workgroup and select edit key, enter your workgroup, then quit.

---

### Post by audiomick on 2009-12-16
Hallo.
this sounds like a problem I had, but I don't remember the solution exactly. I can't go looking, because I am not at home, and all the links are on the desktop there....:(

However, I think you will find the answer in here. Be warned; it is a really long thread. The first thing might be to have a look at the links in dmizer's signature.
[http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149)

---

### Post by jnmjr on 2009-12-17
thanks guys you were very helpful:popcorn:

---


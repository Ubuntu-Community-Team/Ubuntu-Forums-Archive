---
title: "Help me before I throw my laptop at a wall!!"
date: 2010-11-12
forum: New to Ubuntu
---

### Post by skinjim on 2010-11-12
I want to use the hard drive on my Ubuntu desktop as a network drive. My netbook is a dual boot Ubuntu/XP machine and my desktop can 'see' it fine. However my netbook can't see my desktop, it doesn't matter if I boot in Ubuntu or XP it still can't see it. I've set up my public folder as a Samba share and the really annoying thing is that before I went on holiday it was working perfectly, now I've started my machines back up and it's as if they've forgotten how to share. I know it's something simple but I can't find it, please help!

---

### Post by sikander3786 on 2010-11-12
If both Windows and Ubuntu cannot access the shares, the problem is with your desktop Samba server.

Are you sure no firewalls are involved?

Check this

```
sudo ufw status
```

Post the output of this one

```
testparm -s
```

---


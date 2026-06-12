---
title: "Dump output to file"
date: 2009-05-14
forum: New to Ubuntu
---

### Post by Daimones on 2009-05-14
Not sure if I should be considered an "absolute" beginner or not but I'll post it here anyway.

I have set up several samba servers thus far, mostly as trials in my quest towards moving to linux, but I have always ignored the dumping of smb.conf without the comments. (mainly because I couldn't get it to work, and wasn't a big deal atm)

But now I am getting curious, I've read a lot of forums talking about how changing the root password is not a good idea, so I'm trying to avoid that.

But how do I use "testparm -s smb.conf.master > smb.conf" without logging in as root? 

I have tried >> and of course sudo, and variations of the command to no avail, anyone have any ideas?

Sorry for the long post, I'm wordy when I have a question that I can't find through forum searches/google. =)

---

### Post by spiderbatdad on 2009-05-14
```
sudo -i
```

---

### Post by Daimones on 2009-05-14
Ahhh, there we go thanks man. I'm slightly confused though, isn't that a huge security hole then, I mean, I almost think it would be better to not have that option and just type in an md5 password if I want to log into to root...

But I guess if they know my username/password I'm pretty much screwed anyway huh?

---

### Post by spiderbatdad on 2009-05-14
that's why it's not a huge security hole...an admin login is a pre-requisite to the command.

---


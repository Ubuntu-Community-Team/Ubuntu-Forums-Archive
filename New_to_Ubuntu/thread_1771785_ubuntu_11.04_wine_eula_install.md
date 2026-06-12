---
title: "ubuntu 11.04 wine eula install"
date: 2011-05-30
forum: New to Ubuntu
---

### Post by never-never-land on 2011-05-30
hey guys - it's a bit long so bear with me.
ever since I've installed ubuntu 11.04, wine doesn't run my games.
I'm using the latest wine version (beta build), and those games worked before with ubuntu 10.10.
I started sniffing around and came across this site :
[http://www.n00bsonubuntu.net/content/install-wine-on-ubuntu-11-04-natty-narwhal/](http://www.n00bsonubuntu.net/content/install-wine-on-ubuntu-11-04-natty-narwhal/)
which shows in a video (on minuet 1:42) that there is some EULA agreement that you need to agree when installing wine, I think this might be the problem. cause if I recall correctly - on my initial installation
I accidentally clicked NO.
in short: I've tried to remove (including manually removing .wine folder in home directory) & reinstalling
but this EULA agreement isn't there any-more

PLEASE HELP:confused:

---

### Post by frankbooth on 2011-05-30
The EULA in that video is just for some Microsoft fonts, they shouldn't be a deciding factor for your games to run or not.

But if you need them, launch a terminal and write:
```

sudo apt-get install msttcorefonts

```

Keep in mind that all games won't run under Wine, and there might also be regression when Wine updates. 
Have you tried installing the latest stable release instead of using the beta? It's usually not recommended to use the beta.

See [http://appdb.winehq.org/](http://appdb.winehq.org/) for more help or tips on how to get your games/programs running.

---

### Post by howefield on 2011-05-30
If following the above advice, you might want

> sudo apt-get install ttf-mscorefonts-installer

---

### Post by never-never-land on 2011-05-30
tnx for the answer, yes I've also tried the latest stable release - the games still didn't worked...
also just checked it & u were right the games still don't work:(

---

### Post by never-never-land on 2011-05-30
well my friends, thank U both, My games still don't run:(
I'll keep trying finding a fix/wait for one...
BTW: I'm open for suggestions
I'm pretty disappointed right now...

---


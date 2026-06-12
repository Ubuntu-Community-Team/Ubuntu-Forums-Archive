---
title: "devede error, needs mplayer"
date: 2011-01-18
forum: New to Ubuntu
---

### Post by wingedfish on 2011-01-18
I have mplayer and have searched for the solution but all the searches come back with update issues from 9.10. I'm using 10.10 and it's all up to date. I used devede for a few months and this error has come up in the last couple weeks. This weekend I reinstalled and besides a fresh install all that was added was geforce2 driver so I cannot help but think it has something to do with it, but I don't know where to start.

---

### Post by wojox on 2011-01-19
Where did you install Devede from? What does this return:

```
whereis mplayer
```

---

### Post by wingedfish on 2011-01-19
Thanks

installed from software center

```
 whereis mplayer
mplayer: /usr/bin/mplayer /etc/mplayer /usr/share/mplayer /usr/share/man/man1/mplayer.1.gz

```

---

### Post by wojox on 2011-01-19
I'm using 10.10 and have devede installed as well. All works fine here. I also have the medibuntu repo's enabled. Try adding those for extra codecs and packages:

```
sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update
```

```
sudo apt-get install non-free-codecs
```

---

### Post by wingedfish on 2011-01-19
thanks again

all installed, and nothing. still error, can't find the following programs, mplayer

Any suggestions of what to look for?

---

### Post by wingedfish on 2011-01-21
Reinstalled again, left out the nvidia drivers and just added devede. Works fine. Obviously a problem when adding the driver. Guess it's time for a new video card. Thanks for trying.

---


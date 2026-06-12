---
title: "Unable to play DVDs"
date: 2010-06-16
forum: New to Ubuntu
---

### Post by TwiztidChef on 2010-06-16
I'm having a strange problem. I can't play DVDs anymore. When I insert the DVD it prompts me which player to choose. I choose it and the player(VLC) just stutters and never starts.   I get a pop up from ubuntu saying: Unable to mount (DVD Name), and under it says A job is pending on /dev/sr0.  I am able to burn DVDs and CDs through K3B, but I can't play dvds. I can access data disks, but not movies.  This is really annoying. Any ideas? I tried using umount at the terminal, but it didn't work.  I'm using Ubuntu 10.04, 64 bit.

---

### Post by wojox on 2010-06-16
Try reinstalling file codec:

```
sudo apt-get install libdvdread4
```

```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

---

### Post by TwiztidChef on 2010-06-16
YES! Thank you. I first did nothing, but the second solved it. I guess I deleted it when I was cleaning up some disk space the other day.  thanks alot dude.

---

### Post by wojox on 2010-06-17
Your Welcome. :p

---


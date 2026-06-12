---
title: "Is there a way to disable Compiz via SSH from another machine?"
date: 2010-10-08
forum: New to Ubuntu
---

### Post by diablo75 on 2010-10-08
I have a computer at home that I like to have Compiz enabled on and rarely have to access by remote.  But on rare occasion I do, and it's times like this that I don't plan ahead for this by disabling Compiz, as there is a bug that's been confirmed for a couple years that hasn't been fixed yet; the best way around it for now is to disable Compiz.  I don't have anybody at home at the moment to do this for me but I do have access to this computer via SSH.  I may end up doing everything I need through that (have to grab a couple files) but if there's a way to disable Compiz while I'm at it I'd like to try.

---

### Post by rbc on 2010-10-08
This, maybe?:
[http://www.lamolabs.org/blog/2708/one-liner-getting-remote-desktop-sharing-compiz-to-play-nice-under-ubuntu-9-04-with-gnome/](http://www.lamolabs.org/blog/2708/one-liner-getting-remote-desktop-sharing-compiz-to-play-nice-under-ubuntu-9-04-with-gnome/)

---

### Post by blur xc on 2010-10-08
I don't know why you can't do a "metacity --replace" after logging into the host machine, but then again, I haven't done much of anything graphical via ssh, let alone logging in from outside my home network.

BM

---

### Post by CharlesA on 2010-10-08
Are you connecting via VNC?

If so, compiz will mess with it. Have you tried FreeNX instead?

---

### Post by JustinR on 2010-10-08
Couldn't you do this?

On the remote machine, login to the machine with compiz and do this:

```

export DISPLAY=:0.0
metacity --replace

```

---


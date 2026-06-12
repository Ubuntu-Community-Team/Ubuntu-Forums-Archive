---
title: "konqueror"
date: 2009-06-20
forum: New to Ubuntu
---

### Post by old_dope on 2009-06-20
I want to give Konqueror a try out and was hoping that forum members may be willing to give me some advice as to: using, security and the best version. Thanks all!

---

### Post by SuperSonic4 on 2009-06-20
The version in the repos should be the best version although I am using the KDE 4.3 version of Konqueror because I'm running KDE 4.3 beta xD. Remember it's one of the core KDE components so it's likely to haul in a lot of kde stuff.

As for usage and security, just use it like you would any other browser. Split view does what it says on the tin - you may split the screen and use two web pages at once.

Konqueror is also a file manager so you can use it as such

---

### Post by Lampi on 2009-06-20
I use konqueror myself on xfce4, so it's safe to install it from the ubuntu repos:

```
sudo aptitude install konqueror
```

Like SuperSonic4 mentioned it will install some kde core components as well. You can limit the amount of additional packages, if you skip optional packages:

```
sudo aptitude install -R konqueror
```

---

### Post by old_dope on 2009-06-20
Thanks for the info guys!

---


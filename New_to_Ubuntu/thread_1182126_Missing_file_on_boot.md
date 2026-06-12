---
title: "Missing file on boot"
date: 2009-06-08
forum: New to Ubuntu
---

### Post by Yed Ied on 2009-06-08
is a bother.  I ran this some time ago, and the resolution was, 'if it isn't bothering normal operations, put up with it'.  While it doesn't seem to be effecting anything in the performance of 9.04, it has become a bother on every boot to acknowledge the missing file, then giving my admin. name and password, and then giving my password again, before I can get busy.  The problem started when I upgraded from 8.10 to 9.04.  Desktop went well, but Gateway laptop developed this glitch.  If there is nothing I can do about it, so be it, but if I can fix it I would be good. The file ['/usr/share/gdm/themes/HumanCircle/../Human/ubuntu.png':].  [No such file or directory].  Any input?

---

### Post by eilios on 2009-06-08
Try manually adding a replacement file.

---

### Post by Yed Ied on 2009-06-08
I'm not sure how to enter that.  I put it in add. box, that didn't work.  This slump thing must be going around.;)

---

### Post by camper365 on 2009-06-08
It doesn't seem that that file exists. I don't have it on mine, and why is it inserting a /../ instead of just going straight to the directory.

Try reinstalling the gdm themes.

```
sudo aptitude reinstall ubuntu-gdm-themes
```.

When is the last time you ran the update manager?

```

sudo aptitude update
sudo aptitude safe-upgrade
```

---

### Post by Yed Ied on 2009-06-08
Camper, I did as you suggested, in Terminal, and a lot of things happened, that I didn't understand, but it doesn't take much to amaze me.  I was surprised though that it didn't work.  I restarted and got the same Error message.  Thanks for the input though.

---


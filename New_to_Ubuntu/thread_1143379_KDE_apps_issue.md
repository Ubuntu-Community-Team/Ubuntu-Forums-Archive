---
title: "KDE apps issue"
date: 2009-04-29
forum: New to Ubuntu
---

### Post by nemodot on 2009-04-29
I have this problem with KDE apps that it can only be described with this image:

[http://ubuntuforums.org/attachment.php?attachmentid=111708&d=1241034936](http://ubuntuforums.org/attachment.php?attachmentid=111708&d=1241034936)

It only happens with kde apps.

---

### Post by wispygalaxy on 2009-04-29
It looks like you aren't using KDE as a desktop environment, so I think that's why your KDE apps look funny.  That's the only reason I could think of, sorry.  :(  Good luck!

---

### Post by nemodot on 2009-04-29
They used to look OK. :(

---

### Post by wispygalaxy on 2009-04-30
> **nemodot said:**
> They used to look OK. :(

I think the issue is that KDE apps will look weird if you use Gnome, Xfce, etc.  If you really like KDE apps, then have a look at KDE in general.  It's simple to navigate, and I found it easier to get used to than Gnome.  I hope I helped you!  :D

---

### Post by stchman on 2009-04-30
> **nemodot said:**
> I have this problem with KDE apps that it can only be described with this image:

[http://ubuntuforums.org/attachment.php?attachmentid=111708&d=1241034936](http://ubuntuforums.org/attachment.php?attachmentid=111708&d=1241034936)

It only happens with kde apps.

KDE apps run fine under Gnome.  If you are having trouble you can try a more radical method:

```
rm -rf ~/.kde
```

This command will delete the .kde folder in your /home PERMANENTLY.  This folder contains KDE preferences.  Once this is done next time you run a KDE app it will recreate your .kde folder.

---

### Post by stchman on 2009-04-30
> **wispygalaxy said:**
> I think the issue is that KDE apps will look weird if you use Gnome, Xfce, etc.  If you really like KDE apps, then have a look at KDE in general.  It's simple to navigate, and I found it easier to get used to than Gnome.  I hope I helped you!  :D

No they don't.  I have my KDE apps looking almost like Gnome for consistency purposes.

---


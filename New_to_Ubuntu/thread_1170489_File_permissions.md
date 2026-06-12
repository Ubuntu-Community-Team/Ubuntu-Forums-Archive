---
title: "File permissions"
date: 2009-05-26
forum: New to Ubuntu
---

### Post by furialis on 2009-05-26
For the first time since I've installed Ubuntu, I had a crash. The browser was open and it seemed to wipe out the .mozilla folder. I had a backup and I replaced it. Then Firefox wouldn't open with the quick launch icon. I opened a terminal and firefox would open with ```
sudo firefox
``` I figured it was a file permissions problem and did```
sudo chown -hR user:user .mozilla
```And now it works.

My question is, is there a security risk involved or is it OK to leave it like that?

---

### Post by albinootje on 2009-05-26
> **furialis said:**
>  My question is, is there a security risk involved or is it OK to leave it like that?

Which Ubuntu release is it ? Did you install all the updates ?
And which Firefox version ? 
And which flash version do you have installed ?

```

lsb_release -r
dpkg -l|grep firefox
dpkg -l|grep flash

```

---

### Post by mcduck on 2009-05-26
No, user should own his own configuration files by default so that's just the normal ownership for ~/.mozilla and it's contents.

Running Firefox with sudo, on the other hand, is a security risk. And running any graphical application with sudo instead of gksudo isn't a good idea either as sudo doesn't load root's environment variables correctly for graphical applications. As a result you end running as root but using your normal user's configuration files. This might result to those files becoming owned by root.

---


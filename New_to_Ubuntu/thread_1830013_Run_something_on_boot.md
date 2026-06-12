---
title: "Run something on boot"
date: 2011-08-21
forum: New to Ubuntu
---

### Post by Chrissd on 2011-08-21
Hi,

I'm running XBMC under Ubuntu. I need to run the following when the computer boots, which mounts my file share over SSHFS.

```

./.scripts/mountmedia

```

When using XFCE I can just use the GUI and add it to that, but under XBMC obviously that's not loaded. 

Can anyone tell me how to get that to run every time XBMC is loaded, otherwise I'm left without any media to play through the computer.

I tried copying it to /etc/init.d/ without success. 

Thanks

---

### Post by sanderd17 on 2011-08-21
There are many files that are read on boot, all on a separate time.

I believe you need to have it read as a normal user (not root) and after the login screen (otherwise you can't have it as one user). In that case, putting the command in the ~/.profile file will be the best option. If that file doesn't exist, create it.

---

### Post by Chrissd on 2011-08-21
This does sound like a good option. Can you confirm what should be added to .profile?

Just put the following at the very bottom?```
./.scripts/mountmedia
```

Thanks

> **sanderd17 said:**
> In that case, putting the command in the ~/.profile file will be the best option. If that file doesn't exist, create it.

---

### Post by sanderd17 on 2011-08-21
the .profile gets executed as a bash script. So adding that command will do I suppose (if that command works in a bash terminal).

---

### Post by Chrissd on 2011-08-21
Can't believe I couldn't find a simple answer like that Googling!

Many thanks! :)

---

### Post by sanderd17 on 2011-08-21
It's like I said, there are a lot of files used, all in different use cases. Some after login, some when xorg starts, some after boot (whether or not xorg starts), some when you open a terminal ...

I don't know all those files either, and they are hard to find with google.

---


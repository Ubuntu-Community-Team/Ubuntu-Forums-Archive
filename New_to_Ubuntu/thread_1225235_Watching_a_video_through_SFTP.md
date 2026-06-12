---
title: "Watching a video through SFTP"
date: 2009-07-28
forum: New to Ubuntu
---

### Post by hetx on 2009-07-28
The title might be misleading, I can't say I understand exactly how it's done. I have an eeepc with 4GB SSD, so I can't fit much on it. I've been connecting it to my homeserver by SFTP in Nautilus to watch videos from the server, that way I don't need to download the videos first. I even succeeded doing this outside the network (although it was a bit laggy).

I've been playing around a bit with other DEs but I can't seem to find an alternative to Nautilus with this amazing feature. Anyone know of another File Manager or other program that can do this? I realise that I can get Nautilus on other DEs too but I want to avoid downloading the whole batch of dependencies.

Or is Nautilus simply the best file manager there is? =)

---

### Post by XCan on 2009-07-28
You should be able to do this with all DE if you mount the remote share using 'sshfs'.

For example, I mount a remote computer's drive with

```
sshfs user@127.0.0.1:/home/user /home/userlocal/mountpointlocal
```

---

### Post by hetx on 2009-07-28
Awesome, thanks man, exactly what I was looking for!

---


---
title: "problem in ubuntu 8.10"
date: 2009-04-07
forum: New to Ubuntu
---

### Post by linuxe on 2009-04-07
I install ubuntu 8.10 today.
the ext3 drive where ubuntu installed is working
but other ntfs drives not working..
when i click on any of these drives it shows 'Cannot mount volume,You are not privileged to mount the volume 'Softwares'(Softwares is the Drive's Label).

another message shows
Unable to mount location
DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

I am very new to ubuntu,i use these commands:: sudo apt-get update
sudo apt-get ntfs-config
sudo ntfs-config

but nothing happens..

plz someone help me.
I am a newer so plz dictate me step by step so that i resolved my problems...

---

### Post by taurus on 2009-04-07
Try running it with gksudo since ntfs-config is a GUI.

```
gksudo ntfs-config
```

---

### Post by phantom3113 on 2009-04-07
When it tells you that you don't have permissions to mount something, that means you need to mount it as root, which would probably be easier to do through the terminal. Unfortunately, I don't know the command for that. :( The second one actually happened to me the other day. I wasn't sure what it meant either, but I tried it again and it mounted fine.

---


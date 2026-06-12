---
title: "Auto detect and mount flash drives on startup"
date: 2009-11-24
forum: New to Ubuntu
---

### Post by B.Hat on 2009-11-24
So I use a workstation with a variety of USB flash drives and I dual boot between XP x64 and Ubuntu.

When I logout the default user and switch to my user name in Ubuntu, none of the plugged-in flash drives are mounted, meaning I have to unplug and re-plug the drive that I want to use. This can get rather annoying.

Now I have found some recommendations about modifying fstab to mount the drives, but that would not apply here as I do not usually have the same set (or even number) of drives in at any given time.

It seems like there would have to be a way for Ubuntu to simply see what drives are plugged in, and then mount those drives on login of a different user. Does this exist?

Thanks!

---

### Post by Paqman on 2009-11-25
Off the top of my head, does:
```
sudo mount -a
```
find and mount the USB sticks? If so you could put that in a wee bash script and run it at login.

---


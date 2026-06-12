---
title: "DBus error"
date: 2009-01-02
forum: New to Ubuntu
---

### Post by Goll on 2009-01-02
I am unable to mount 2 internal sda hard drives.
Error:
```
DBus error org.freedesktop.DBus.Error.NoReply: 
Did not receive a reply. 
Possible causes include: the remote application did not send a reply, 
the message bus security policy blocked the reply, 
the reply timeout expired, or the network connection was broken.

```

I've chowned it. I've tried mounting manually. I've mkdir'd. I've googled this.
Umm, I tried reinstalling gnome-mount. I reinstalled ubuntu-desktop.

I reformatted it.

I am still unable to mount this drive.

I haven't editted the fstab. This is Not an old drive.

---

### Post by Goll on 2009-01-02
Has anyone received this before?

---

### Post by irie on 2009-01-16
I'm receiving it constantly all of a sudden. I have to reboot to have access to the dvd drive.

---

### Post by Mthbk1 on 2009-11-13
I am having the same dbus error. org.desktop.dbus.error.spawn.execfailed

Will I have to re install ubuntu?

---

### Post by ukripper on 2009-11-13
Post output of the following commands:
```
sudo fdisk -l
```

```
blkid
```

```
df -h
```

---

### Post by Mthbk1 on 2009-11-15
> **ukripper said:**
> Post output of the following commands:
```
sudo fdisk -l
``````
blkid
``````
df -h
```


I tried doing this but following things prenveted me from posting the output here:
1. Not able to connect to internet (same error pops up)
2. Not able to explore "My computer" so as to save it as a text file(again the same error).

---

### Post by ukripper on 2009-11-16
can you boot into the ubuntu live cd and see if hdd mounts there and post the output of the commands posted earlier from within you live cd.

---


---
title: "USB Drives Not Automounting"
date: 2009-01-14
forum: New to Ubuntu
---

### Post by armada786 on 2009-01-14
I just installed Xubuntu 8.10 today on my computer. Everything's dandy so far but this. I have 3 port hub and 3 different drives. All of them can be plugged in and mounted using the "lsusb" command in the terminal, but none of them will automount. When I used a recommended command like "fdisk -l" nothing but the internal drive (sda) shows up. 

Also, the drives show up when rebooting them with them plugged in, but the technically do not "mount".I can see their icons, but an option to "mount volume" is under the right-click menu. After clicking the icon, that option is not available.

I checked the settings for removable media, and everything seems like it ought to automount fine according to what my computer says. Can anyone help me?

---

### Post by taurus on 2009-01-14
What's the output of this command from a terminal?

```
sudo fdisk -l
```

---

### Post by armada786 on 2009-01-14
> **taurus said:**
> What's the output of this command from a terminal?

```
sudo fdisk -l
```

Only the ext3 and swap partitions on the internal drive. No more, no less.

---

### Post by taurus on 2009-01-14
Since you said they show up if you boot your machines with those drives already plugged in, can you at least mount them from a terminal?

---

### Post by armada786 on 2009-01-14
> **taurus said:**
> Since you said they show up if you boot your machines with those drives already plugged in, can you at least mount them from a terminal?

Like I said, all I've managed was using "lsusb" to mount them. Can you give me a command if there's another?

---


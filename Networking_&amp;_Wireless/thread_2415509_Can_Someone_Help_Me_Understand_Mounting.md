---
title: "Can Someone Help Me Understand Mounting?"
date: 2019-03-27
forum: Networking &amp; Wireless
---

### Post by rebeltaz on 2019-03-27
I am mounting a USB drive in fstab:

```
UUID=fa9d3519-6125-4121-9810-b2822e398780	/mnt/shop.data	ext3	defaults,nofail,noatime	0	0
```

that I am sharing across the network via a samba share. First of all, I cannot find a way that will unmount that drive because even when **NOTHING** is accessing that share, it refuses to unmount telling me that it is in user. lsof and fuser both report nothing utilizing that share. 

Aside from that, though, I finally did a -l [lazy] unmount of the drive and when I unplugged it, I couldn't remount it with [**mount -a**] - I had to physically remove power from the system to regain control. 

What I need to know is... once a USB drive, that is samba shared, is mounted in fstab, how can I safely/effectively unmount that drive and then remount it when I want to.

---

### Post by TheFu on 2019-03-27
You need to shutdown samba, then manually umount it.
Most people avoid using some-times connected storage as network shares. Removing shared storage without umounting it properly is asking for file system corruption.

Normally, I would suggest using autofs to automatically mount and umount storage, but when it is shared over the network, it will always be marked as used as long as the sharing service runs.

---

### Post by rebeltaz on 2019-03-27
This actually isn't "sometimes connected storage", per se. It's normally always connected. I recently moved this external drive from an always on full-size computer to a raspberry pi that I am using a a media server. I rarely need to disconnect this drive, but on those rare occasions that I do, that was why I needed to know. For now, when I have needed to remove it, I've just been shutting the pi down before unplugging it. 

Autofs... you mean on the remote systems, right? I am using that. I was looking at autofs before I posted this and I didn't see anything that would allow me to use that to mount a local drive, unless I missed it... which is highly likely.

---


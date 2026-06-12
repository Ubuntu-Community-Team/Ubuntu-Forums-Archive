---
title: "NIS / Group ID / Hardware Access issue"
date: 2007-04-18
forum: Networking &amp; Wireless
---

### Post by wiggleroom on 2007-04-18
Here at [Access Space]("http://access-space.org/") we run a Mandrake NIS server to distribute usernames and passwords across our network clients.

The network clients are predominantly Mandriva 2006, but we're looking to migrate to Ubuntu 6.06 LTS.

Anyway, the upshot is that we have a problem with hardware devices - Ubuntu seems to allow hardware auto-mounting and unmounting via groups "floppy", "cdrom", "usb" and so on, which have GIDs around 20-25.

Ubuntu and Mandrake don't synchronise the same GID numbers - on one cdrom is GID 24, on the other it is GID 25.

Now users with distributed UIDs aren't members of these groups, and typically NIS discourages you from distributing GIDs less than 100 - presumably to accommodate different client distros.

I can see several approaches to solving this issue, but I'm not sure where to start...

1) Could we doctor the clients' /etc/passwd and /etc/group in such a way as to automatically make any UID greater than 5000 (all our distributed UIDs start at 5000) part of local hardware groups?

2) Could we achieve this same end more elegantly by engineering /etc/sudoers?

3) Should we delete local hardware groups from clients, and distribute those same group names by NIS (with higher GID's, and all NIS users members oif those groups). I can see that this might work, but it could
make clients inconvenient to use with a local username.

4) Would /etc/fstab help us to allow all users to mount and unmount hardware devices? Or was this the "old way" to achieve this, before hardware abstraction layers?

5) Is there a HAL configuration that could be our answer?

Any thoughts on the first place to try? Maybe there's another approach I haven't considered.

---

### Post by wiggleroom on 2007-04-26
Sorry to bump this up.  Does anyone have any advice for us on this?  It's quite a pressing issue for us, and we'd really rather be using Ubuntu than stuck on Mandriva...

---

### Post by blumi00GT on 2007-05-28
Same problem here (and wanting to bump this thread)

Bastian

---


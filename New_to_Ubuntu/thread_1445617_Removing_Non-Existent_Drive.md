---
title: "Removing Non-Existent Drive"
date: 2010-04-02
forum: New to Ubuntu
---

### Post by zonerover on 2010-04-02
Recently I ran into some problems with restoring a cloned drive, somehow accidentally overwriting my MBR (I'd class myself as an advanced newbie so bear up with me here). I ended up restoring GRUB2, but somehow I ended up messing up my fstab file, so I used the file on a Live CD to get me back up and running, and at least now everything except for one quirk is back to normal as you can see below.

[IMG]http://img594.imageshack.us/img594/540/screenshoty.png[/IMG]

The error message is referring to a 'Data' drive of some kind, but I already have a working Data drive mounted so clearly this is just a false duplicate of it. So how can I remove this, and brownie points if anyone can tell me how I ended up getting this in the first place?

---

### Post by oldfred on 2010-04-03
Post a copy of /etc/fstab. Do you have a double entry?

Did you label your partitions so when it trys to automount something it has the same name? This shows UUIDs & labels:
sudo blkid

---


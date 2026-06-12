---
title: "The loop device"
date: 2010-02-23
forum: New to Ubuntu
---

### Post by SteelCore on 2010-02-23
Is "the loop device" compiled by default into the Ubuntu kernel?

Thanks

---

### Post by cariboo on 2010-02-24
Yes it is, I've used it for years to mount iso's eg:

```
sudo mount -o loop ~/iso/lucid_mini.iso /mnt
```

---

### Post by SteelCore on 2010-02-24
Thanks cariboo907.  I didn't realize that it mounts iso images. I actually want to use it to mount a raw image of a hard disk. Although I'm reading now that I need to extract the partition coz mount doesn't recognize the primary partition table so the plain partition needs to be used alone (this guide is meant for a Slackware machine, if that makes any difference).

---


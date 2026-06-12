---
title: "CD/DVD drive not recognised"
date: 2011-03-12
forum: New to Ubuntu
---

### Post by jackson98 on 2011-03-12
just installed LG opt internal drive in mini ITX sys. Ubu 10.10 does not recognise the drive even tho it shows up in 'Places/Computer' - any help appreciated.

---

### Post by ohzopants on 2011-03-12
I'm having similar problems with my CD/DVD drive (it's an LG GH22NS30).

I believe it's a firmware issue.

If you do:
```

sudo lshw

```

In that command's output find the DVD drive section and check the end of it for the "status=" part. In my case, the drive always thinks it's in the "open" status.

If I reboot with a disk in the drive everything's fine, but I can't change disks with the PC running.

I'm currently looking for a way to upgrade the drives firmware using Linux... apparently this is non-trivial. (Note that using LG .exe firmware updater with wine does not work for me.)

---

### Post by jackson98 on 2011-03-13
thanks for that - i discovered one of the cd mounting screws was too long and preventing the cd drawer from opening - prob resolved but thanks for help

---


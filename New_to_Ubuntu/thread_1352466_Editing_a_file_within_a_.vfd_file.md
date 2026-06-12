---
title: "Editing a file within a .vfd file"
date: 2009-12-11
forum: New to Ubuntu
---

### Post by P3t3r on 2009-12-11
I have a .VFD file (virtual floppy drive) and I'd like to edit a file within it. I wonder: is this possible under (k)ubuntu? I find no program, so maybe it works with dd? How should I do this? Or are there better tools (like an Ubuntu equivalent of WinImage)?

Thanks!

---

### Post by P3t3r on 2009-12-13
Anyone? Is this possible at all or is this a windows-only feature?

---

### Post by P3t3r on 2009-12-27
No one? Please? I need it to be able to upgrade my kernel... :(

---

### Post by P3t3r on 2010-01-23
Ah well, apparently I'll need windows for this. Never mind then.

---

### Post by falconindy on 2010-01-23
I have no experience with these kinds of images, but I suspect you could mount them as any other kind of image (hdd image from dd or an .iso):
```
sudo mount -o loop /path/to/image.vfd /path/to/mount/point
```

---


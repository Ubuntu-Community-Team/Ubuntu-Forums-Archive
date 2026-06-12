---
title: "&quot;media/cdrom0 does not exist&quot;"
date: 2009-03-04
forum: New to Ubuntu
---

### Post by eimiandra on 2009-03-04
So, I'm having mounting troubles.

When I put the DVD in the computer, an error message immediately pops up saying, "media/cdrom0 does not exist"

When I go to terminal to mount it, this 
mount: can't find /media/cdrom0/ in /etc/fstab or /etc/mtab
happens.

and there is no cdrom0 in my media folder.  It can't be as easy as just making a folder entitled "cdrom0" there, can it?

If it helps I have intell hardware and am on a macbook.

---

### Post by taurus on 2009-03-04
Yeah.

```
sudo mkdir /media/cdrom0
```

However, there could be a syntax error in your /etc/fstab so post it here.

```
cat /etc/fstab
```

---


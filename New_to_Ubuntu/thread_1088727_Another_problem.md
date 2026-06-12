---
title: "Another problem"
date: 2009-03-06
forum: New to Ubuntu
---

### Post by Haioko on 2009-03-06
I tried to plug my external hards drive into my PC but I keep getting an error saying i's unable to mount.

It gave me some code to put in but nothing happened when I did enter it.

> mount -t ntfs-3g/dev/sdb1/media/Iomega HDD -o force

---

### Post by LowSky on 2009-03-06
Plug the external into a Windows Machine, then unmount it properly, then unplug it and plug it into the Ubuntu machine, and it should work.

This issue will occur any time you don't properly unmount hte external from the Windows PC

---

### Post by BrandonBan6 on 2009-03-06
Hi Haioko,

from terminal try this:

```
sudo mount -f /dev/sdb1 /media/Iomega HDD
```

---

### Post by kanikilu on 2009-03-06
> **Haioko said:**
> mount -t ntfs-3g/dev/sdb1/media/Iomega HDD -o force Is that the exact command you used, because that won't work. It should be:

```
mount -t ntfs-3g /dev/sdb1 /media/Iomega\ HDD -o force
```

Also, the mountpoint should exist prior to trying to mount it:

```
sudo mkdir /media/Iomega\ HDD
```

Take note of the spaces and escaping slashes in both commands...

---

### Post by egalvan on 2009-03-06
> **Haioko said:**
> I tried to plug my external hards drive into my PC but I keep getting an error saying i's unable to mount.


If the name of the drive (it's label) is 

Iomega HDD

then you will have problems because of the spaces...

You can either use work-arounds for the space (kanikilu (post #4) gives one example)
or rename the drive to something with no space.

Iomega_HDD

is an example.

As for me, I left Microsoft-type drive names behind, and switched to *nix-type names...
no spaces, all lower-case.

No more problems or work-arounds for me.


ErnestG

---

### Post by Haioko on 2009-03-06
Thanks for that. Sorry about all these questions lol

---

### Post by egalvan on 2009-03-06
> **Haioko said:**
> Thanks for that. Sorry about all these questions lol

Hey, it's how we all learned...

Asking questions, finding answers...

Glad to be of help...

And welcome to the *nix Club

---


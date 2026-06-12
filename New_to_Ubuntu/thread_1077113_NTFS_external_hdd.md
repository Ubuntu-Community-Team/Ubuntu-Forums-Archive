---
title: "NTFS external hdd"
date: 2009-02-22
forum: New to Ubuntu
---

### Post by KHAnet on 2009-02-22
ubuntu used to be able to read my ntfs hdd but now i can't get it to mount. what changed? do i need a program to read it?  please help. thanks in advance.

---

### Post by KuroYoma on 2009-02-22
What do you mean it wont mount.  Are you getting an error message or is it no doing anything at all.  If you are getting an error message what does it say?

---

### Post by konqueror7 on 2009-02-22
have you installed 'ntfs-config' from the repos?

---

### Post by KHAnet on 2009-02-22
just says unable to mount. can i force it? i don't think i properly disconnected it from my windows machine. i don't have a windows machine with me at the moment.

---

### Post by KuroYoma on 2009-02-22
```
sudo mkdir disk #if it doesnt alread exits
sudo mount -i /dev/[COLOR="Red"]sdb[/COLOR]/media/disk -o force
```

I believe that is the force line
Just replace sdb with your dev name

---

### Post by era86 on 2009-02-22
Try to mount the drive manually using:

mount -t ntfs /dev/sd- /media/disk

What does it say back?

If you don't have the /media/disk directory, be sure to make it first using mkdir.

---


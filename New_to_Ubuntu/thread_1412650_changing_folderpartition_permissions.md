---
title: "changing folder/partition permissions"
date: 2010-02-21
forum: New to Ubuntu
---

### Post by hermitical on 2010-02-21
hiya

just installed 9.10 and most things goign swimmingly.

I created a partition called 'stuff' for general stuff and then set it to mount automatically using this script:

```
/dev/sda6  /mnt/stuff  ext4  users,noatime,auto,rw,nodev,exec,nosuid 0 0
```

Now I realise that the part following ext4 affects who can write to it? The permissions now look like this:
```

drwxr-xr-x
```

and I can't save anything there.

Any help appreciated

---

### Post by bodhi.zazen on 2010-02-21
Change ownership with chown

```
sudo chown you:you /mnt/stuff
```

See : [How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131")

---

### Post by hermitical on 2010-02-21
champion - thanks!

---


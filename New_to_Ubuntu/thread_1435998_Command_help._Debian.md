---
title: "Command help. Debian"
date: 2010-03-22
forum: New to Ubuntu
---

### Post by Drenriza on 2010-03-22
Is their a command, that can show me if im running
ext2, ext3 or something else on a server?

And a command that can show me what the cluster size is on the server.

Thanks on advance

---

### Post by sahabcse on 2010-03-22
try 

#df -h

---

### Post by Alias1407 on 2010-03-22
I know I'm being a bit of a derp but you could always just output your entire system information and then trawl through all of it....

```
sudo lshw -html > ~/hardware.html
```

---

### Post by halitech on 2010-03-22
> **sahabcse said:**
> try 

#df -h

that will only give an output of it being Linux, doesn't say if it is ext2/3/4

to expand on what Alias1407 suggested, try this

```
sudo lshw -C volume -html > ~/hardware.html
```

---

### Post by gmargo on 2010-03-22
The **mount** command will show the filesystem type of each local filesystem.

The **tune2fs** command will show filesystem attributes such as block size (aka cluster size).

```

$ mount | grep /dev/sda1
/dev/sda1 on / type **ext3** (rw,relatime,errors=remount-ro)

$ sudo tune2fs -l /dev/sda1 | grep size:
Block size:               4096
Fragment size:            4096
Inode size:               128

```

---


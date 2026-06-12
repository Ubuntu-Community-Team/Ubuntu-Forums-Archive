---
title: "system cleanup"
date: 2009-03-16
forum: New to Ubuntu
---

### Post by nelskurian on 2009-03-16
The ubuntu advantage==>

A) Linux has no registry or equivalent, nothing to do there.
B) The /tmp folder gets cleared on every boot
C) Linux filesystems are genreally very resilient to fragmentation because of the way it determines where to write files stuff.

As for clearing apt's cached .debs, you don't need to unless you need the harddrive space. In my experience (much to my irritation, in fact), apt clears this on occaision when it decides that its getting too big (I think it was in the region of 600MB when it was clearing mine). As I say, no need to "sudo apt-get clean" because of point (C) above, unless you need the disk space.

Its a zero waste-of-time-maintenance OS :)

In system you free disk space by cleaning up the temporary dir where all your installation files (when u use apt-install) are stored by typing this code in the terminal:
```
sudo apt-get clean
```

A good tool to keep your file system clean is to use the "fslint" program:
[http://www.pixelbeat.org/fslint/]("http://www.pixelbeat.org/fslint/")

and installed with alien:
```
sudo alien -i fslint-2.12-1.noarch.rpm
```

---


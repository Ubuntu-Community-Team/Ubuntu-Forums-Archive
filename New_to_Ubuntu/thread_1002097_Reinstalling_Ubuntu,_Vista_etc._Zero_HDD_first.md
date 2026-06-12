---
title: "Reinstalling Ubuntu, Vista etc. Zero HDD first?"
date: 2008-12-04
forum: New to Ubuntu
---

### Post by spacesearcher on 2008-12-04
I have heard that it is not necessary to zero the hard drive first and i have also heard that it is better to do that. 
i have read that if i do:
```

dd if=/dev/zero of=/dev/sda bs=1024
```

it will wipe my whole hard drive. will it still be usable after i do this? i.e. it will not screw up any low level formating put on it by the manufacturer. I will be able to add partitions and reinstall the os right?

---

### Post by talsemgeest on 2008-12-04
It definitely shouldn't destroy your hard-drive and should have no ill effects. However, it is useless if all you are doing is reinstalling ubuntu, since most of what is on the hard drive is wiped anyway.

---

### Post by bumanie on 2008-12-04
There should not be any reason to 'zero' the whole hard drive just to do a reinstallation. Both vista and ubuntu will format the drive during installation. You could pre-format with something like gparted first if you like. Zeroing the drive is generally used to overwrite sensitive information (say if you are getting rid of a hard drive etc.) and is not necessary prior to an OS installation.

---


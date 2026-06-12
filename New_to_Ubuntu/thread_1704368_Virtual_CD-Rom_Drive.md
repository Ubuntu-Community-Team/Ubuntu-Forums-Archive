---
title: "Virtual CD-Rom Drive"
date: 2011-03-10
forum: New to Ubuntu
---

### Post by Jim2029 on 2011-03-10
When i used Windows i had a program Magic ISO to burn cd's and make ISO files, and also let me mount ISO files to virtual cd-rom drives. What would let me do this in Linux?

Thanks.

---

### Post by sandyd on 2011-03-10
> **Jim2029 said:**
> When i used Windows i had a program Magic ISO to burn cd's and make ISO files, and also let me mount ISO files to virtual cd-rom drives. What would let me do this in Linux?

Thanks.
you could do it in commandline...
but I don't think you wanna...

use acetoneiso.

---

### Post by Hedgehog1 on 2011-03-10
> **Jim2029 said:**
> When i used Windows i had a program Magic ISO to burn cd's and make ISO files, and also let me mount ISO files to virtual cd-rom drives. What would let me do this in Linux?

Thanks.

One way:

**Right click on the ISO file and select 'Open with Archive mounter'.**

Another Way:

```
sudo mkdir /media/iso
sudo mount -t iso9660 [COLOR="Red"]**yourisofilename.iso**[/COLOR] /media/iso -o loop
ls -la /media/iso
```

I am sure there are more...

***The Hedge***

:KS

---

### Post by Jim2029 on 2011-03-10
Thank you.

---

### Post by dprobst on 2011-06-15
Hi...I had this same problem for a while until I figured out that VLC Media Player can directly open an iso image from a DVD or whatever and play it.  So just install VLC Media Player, it should by default be in your repositories.

---


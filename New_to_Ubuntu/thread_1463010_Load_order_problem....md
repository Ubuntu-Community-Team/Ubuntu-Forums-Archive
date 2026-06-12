---
title: "Load order problem..."
date: 2010-04-26
forum: New to Ubuntu
---

### Post by EricBJ on 2010-04-26
I hope the subject is accurate...

I have a system that I am building, that has a single hard drive and a mirrored RAID.

On boot, the system loads the RAID first and I need it to load the single hard drive first.

Can I do this?

Thanks,
Eric

---

### Post by Bachstelze on 2010-04-26
You would have to change that in your BIOS, I believe.

---

### Post by EricBJ on 2010-04-26
Are you thinking that I am talking about a booting problem?

The OS is on the single drive and it boots fine.

I'm sorry, maybe I wasn't specific enough in my post.

I need to control the order because I need the single hard drive to be sda and the RAID to be sdb.

Can I control this?

Thanks again,
Eric

---

### Post by oldfred on 2010-04-26
I do not have raid but the drive order seems to be the SATA port order. 

I do not know if you can reorder drives with device.map or if that will confuse things. If you do reorder you will have to reinstall grub and possibly repair windows as the drive numbers have changed.

/boot/grub/device.map
(hd0)    /dev/sda
(hd1)    /dev/sdb

---

### Post by EricBJ on 2010-04-26
Thanks for the suggestion...

I'll look into device.map and see if it will sort things out...

Thanks,
Eric

---


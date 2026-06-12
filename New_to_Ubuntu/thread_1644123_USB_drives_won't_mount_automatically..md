---
title: "USB drives won't mount automatically."
date: 2010-12-12
forum: New to Ubuntu
---

### Post by MrTyler on 2010-12-12
My USB drive will not automount when I insert it.  The automount configurations are all set to mount it and open a folder for the drive, but it doesn't do that.

[https://help.ubuntu.com/community/Mount/USB#User](https://help.ubuntu.com/community/Mount/USB#User) Privileges

The help documentation suggest that I adjust settings in "System->Administration->User and Groups" and "System->Preferences->Removable Drives and Media." Unfortunately, neither of those locations seem to exist on my netbook.


There is one exception to this: If I plug my ipod in while there is another USB drive present (mounted or unmounted), the ipod will automount.  Otherwise, though, nothing will automount.

---

### Post by fabdango on 2010-12-26
It also happens to me. The iPod won't mount. Ubuntu tries to mount it as ext4 but it's a fat32 partition. Odd.

---


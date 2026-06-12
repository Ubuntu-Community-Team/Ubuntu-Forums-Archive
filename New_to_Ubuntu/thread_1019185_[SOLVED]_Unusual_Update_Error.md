---
title: "[SOLVED] Unusual Update Error"
date: 2008-12-22
forum: New to Ubuntu
---

### Post by icyest on 2008-12-22
I got this error after pushing "Check" in my "Update Manager"
like so:
[[IMG]http://img184.imageshack.us/img184/1926/screenshot2hg4.th.png[/IMG]](http://img184.imageshack.us/my.php?image=screenshot2hg4.png)

Here is the complete text from what was inside the dialog box:
> Failed to fetch cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/dists/hardy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

Failed to fetch cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/dists/hardy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

Some index files failed to download, they have been ignored, or old ones used instead.



---

### Post by taurus on 2008-12-22
Go into System -> Administration -> Synaptic Package Manager -> Settings -> Repositories and uncheck a box for Cdrom.  Then click Close and shut down synaptic.  Now, what happens when you run these commands from a terminal?

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get upgrade
```

p.s.  Make sure you close update-manager first before you open synaptic.

---


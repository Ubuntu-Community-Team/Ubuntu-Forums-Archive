---
title: "Update Manager"
date: 2009-02-22
forum: New to Ubuntu
---

### Post by pelee98 on 2009-02-22
Hey everyone.  

I'm not what you'd call proficient with this stuff, but this keeps coming back around, and I'm not sure if this is really an issue.  I've been ignoring it and it hasn't killed me yet

When I run update manager it will grab updates, but it keeps telling me that package information is 'X' number of days old. and then it gives me the following message:

Failed to fetch cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080701)]/dists/hardy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

Failed to fetch cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080701)]/dists/hardy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

Some index files failed to download, they have been ignored, or old ones used instead.

Do I keep ignoring this?  It sounds bad to my uneducated brain.  Is this really an issue?

Thanks

---

### Post by cwsnyder on 2009-02-22
You may want to go into System >> Administration >> Software Sources and removing the installation CD as a source to go to for updates.  That is what the warning is about.  You are probably not going to get an update from the original installation CD.

---

### Post by Rolcol on 2009-02-22
That is telling you that it's looking for the CD to find package updates but there's no disk inserted.  Go into System > Administration > Software Sources and uncheck the boxes next to the CD entries.  I think it's in the second tab.

Edit:  Dang... Too slow

---

### Post by metallicamike on 2009-02-22
go to system->administration->software sources and go to the third-party software tab and uncheck the one that says cd rom. that should do it

Edit: me too :( i hate that :lolflag:

---

### Post by pelee98 on 2009-02-22
Thanks.  That solved it.

---


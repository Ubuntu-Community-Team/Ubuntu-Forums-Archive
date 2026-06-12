---
title: "update manager errors....HELP!"
date: 2009-08-21
forum: New to Ubuntu
---

### Post by Cannon1230 on 2009-08-21
The following errors occur when I try to update...

Failed to fetch cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)/dists/jaunty/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)/dists/jaunty/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead.

I typed apt-cdrom into the terminal, and thought it would fix this, but it did not...What do I need to do???
Thanks! 
Cannon

---

### Post by marshmallow1304 on 2009-08-21
> **Cannon1230 said:**
> The following errors occur when I try to update...

Failed to fetch cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)/dists/jaunty/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)/dists/jaunty/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead.

I typed apt-cdrom into the terminal, and thought it would fix this, but it did not...What do I need to do???
Thanks! 
Cannon

It looks as if it's looking for a CD that's not there.  Use 
```
sudo gedit /etc/apt/sources.list
```

The beginning should look something like this
> # deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release amd64 (20090420.1)]/ jaunty main restricted
# deb-src [http://ubuntu.osuosl.org/ubuntu/](http://ubuntu.osuosl.org/ubuntu/) jaunty main restricted #Added by software-properties
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution. etc.

Notice the # before the first line, which is the cdrom line.  You'll need to add the # in your version of sources.list.


Alternatively, you can do this through the GUI by going to System->Administration->Software Sources and unchecking the cdrom option at the bottom.

---


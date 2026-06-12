---
title: "apt-get...Help Please"
date: 2009-08-21
forum: New to Ubuntu
---

### Post by sillyboy on 2009-08-21
I get this message when I try to download updates:

GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/dists/hardy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/dists/hardy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead.

Could someone please tell me what (and how) to do with this message.It will not go away.  This is a orange triangle (icon) with a exclamation point in it.  The red arrow (icon)update notice that points down always installs fine.

Thank You in advance

---

### Post by SuperSonic4 on 2009-08-21
I'm guessing you recently added a new repository? The command below should add the right key for the repo but be careful - ubuntu picks it's repo for a reason - security and stability

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 2EBC26B60C5A2783
```

---

### Post by starcraft.man on 2009-08-21
To get rid of the medibuntu message, you simply need to install the gpg key. You can follow above from supersonic, or please open a terminal (Applications > Accessories > Terminal) and then type in:

```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```
Same result.

To get rid of the rest of the messages, you'd either have to put the CD you originally installed in the drive or uncheck it from software sources (System Menu > Admin > software sources > Ubuntu Software Tab > Uncheck installable media section.

That should resolve all trouble. For more information on keys and installing, see guide in my sig.

---

### Post by aamr on 2009-08-21
Two things to do:

[LIST=1]
[*]Open "Software Sources" (System->Administration->Software Sources) and untick the checkbox beside "Ubuntu Official CDRom bla bla bla"
[*]Either remove the medibuntu software sources from your "Third Party Sources" list or simply add the GPG key by following this guide: [https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories](https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories)
[/LIST]

---

